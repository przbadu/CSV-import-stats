### How to test

*Install ruby*

*Generate CSV file first*

below command will generate `data.csv` file with 1,000,000 records

```ruby
ruby generate_csv.rb
```

### Check Benchmark

You will see 2 useful information for each method

- Time it consumed to read whole CSV records 
- more importantly *Memory* it consumed to process above request.

*Check benchmark of `CSV.read` method

```ruby
> ruby csv_read.rb
Sum: 499999500000
Time: 11.74
Memory: 1887.02 MB
```

*Check benchmark of `CSV.parse` method

```ruby
> ruby csv_parse.rb
Sum: 499999500000
Time: 9.68
Memory: 2193.36 MB
```

*Check benchmark of `CSV.for_each` method

```ruby
> ruby csv_for_each.rb
Sum: 499999500000
Time: 5.74
Memory: 1.8 MB
```

As you might see, there is no huge *Time* difference in each CSV methods to read csv, but
there is huge performance difference on how much memory each methods take.

Always use `CSV.for_each` if you know your CSV has lots of data in it, because it will always read csv data per row.
