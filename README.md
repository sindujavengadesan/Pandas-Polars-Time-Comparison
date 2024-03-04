# Pandas-Polars-Time-Comparison
We all know what Pandas is, right? 

-	Was designed for ease of use and versatility for data manipulation and analysis, written in C in the backend.
-	Operations are not parallelized across multiple cores, meaning it typically uses single thread internally for all its operations
  
Possible issue? 

-	This might cause a bottle neck in CPU bound tasks (for example, aggregation over a large dataset), that could otherwise benefit from the multi-core parallel execution. 
-	Do not have a native “lazy” Evaluation operation, Pandas operations are by default “eager” 
Polars enter the discussion now.

So what is polars? 
-	Was also designed for ease of use with respect to anything data, written in Rust 
Why is it better? 
o	It is optimized for parallel processing across multiple cores 
o	Has ‘Lazy Evaluation’
Pandas and Polars work similarly when it comes to small data, there might be a case where Pandas might give better performance comparatively, when the dataset has, say a few thousand rows. 
If we work with a dataset that has 10M or 100M rows, then a stark contrast between the two is visible clearly. 

What is Eager and Lazy Evaluation? 
-	Eager Evaluation: operations are evaluated immediately when they are encountered. 
-	Lazy Evaluation: operations are evaluated only if its result is needed. It creates a computation plan and optimizes it before execution. 
With respect to the two libraries in discussion, 
-	Pandas uses Eager Evaluation 
-	If we do pd.read_csv(), it immediately reads the whole csv and loads it up in the memory. If we need a subset of this dataset, pandas will load the entire dataset and then filter out the subset that we need. 
-	Lazy Evaluation as the name suggestions, works lazily. It only computes the result, with compute () method, if it’s necessary. 
-	Polars is Eager by default, but we have the option to evaluate Lazily and causes the performance to improve.

  
Both Pandas and Polars focus on working in-memory, meaning it works well when the dataset fits in the memory. What if we have a dataset that doesn’t fit? More often than not, we come across huge datasets and both these libraries won’t work as expected.
Another popular library, Dask comes into picture now. 

A few basic things to know about Dask, 
-	Dask is Lazy by nature
-	It can scale from a single machine to a cluster, therefore supporting large data files. 

One can read much more about these libraries using the following links 
https://pola.rs/
https://docs.dask.org/en/stable/
Dataset used: https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95/about_data





