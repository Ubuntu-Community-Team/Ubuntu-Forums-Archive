---
title: "Using Perf tool for 100% CPU usage"
date: 2015-07-07
forum: Ubuntu Application Development
---

### Post by rohit19 on 2015-07-07
Hi ,

I have a software that runs 5 processes simultaneously. This software tests a few test cases , about 200 odd. The total time required for testing all test cases is 14-15 hours. 

Now what happens is that after running the test cases for 4-5 hours the GUI of the software freezes and i am unable to move the GUI. When I checked the CPU usage it shows that it has touched 100% CPU usage.

I would like to know two things:

1) Which process is touching 100 % CPU usage

2) Which section of the code is touching 100 % CPU usage.

In one of the forums I have found that we can use perf tools for finding this. But i am not sure how I can use the perf tools command for this purpose. The reason being  that in the tutorials there are a number of commands for different purposes.

Could someone help me with the exact command which would help me do this.

---

### Post by ajgreeny on 2015-07-07
You might be able to do what you want by running **top** in a separate terminal simultaneously with whatever else you are running.  In the top terminal use upper case C to sort by cpu and keep an eye on the top terminal.

There may even be a way to log the top output at intervals to see what is going on over time, but I don't know the details of top well enough.

---

### Post by gordintoronto on 2015-07-07
It sounds like your computer might be overheating. I use Conky to keep tabs on the temperatures of various components. A useful utility is lm-sensors. Both those things have a bit of learning curve.

To investigate "Which section of the code is touching 100 % CPU usage." you would need the source code for the program and relevant debugging tools.

---

