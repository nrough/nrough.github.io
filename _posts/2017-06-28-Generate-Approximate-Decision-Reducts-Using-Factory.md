---
layout: post
title: 'Generate \( \smash(F, \varepsilon) \\\)-Approximate Decision Reducts'
tags:
  - reducts
  - samples
published: true
---
{% highlight csharp linenos %}
//load data
var data = Data.Benchmark.Factory.Golf();

//set parameters for reduct factory
var parm = new Args();
parm.SetParameter(ReductFactoryOptions.DecisionTable, data);
parm.SetParameter(ReductFactoryOptions.ReductType, 
	ReductTypes.ApproximateDecisionReduct);
parm.SetParameter(ReductFactoryOptions.FMeasure, 
	(FMeasure) FMeasures.Majority);
parm.SetParameter(ReductFactoryOptions.Epsilon, 0.05);

//compute reducts
var reducts = ReductFactory.GetReductGenerator(parm).GetReducts();

//output reducts and attributes
foreach (IReduct reduct in reducts)
	Console.WriteLine(reduct.Attributes.ToArray().ToStr());
{% endhighlight %}
