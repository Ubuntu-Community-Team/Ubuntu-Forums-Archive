---
title: "wxMaxima interpretting trig solutions and graphing tan"
date: 2016-04-13
forum: The Cafe
---

### Post by haplorrhine on 2016-04-13
I had trouble finding the solution to 5x + 2sin(x) = 0, or the intersection of -5x = 0 and 2sin(x) = 0.

solve([(5*x)+(2*sin(x))], [x]) gives as output x = -2sin(x)/5.
to_poly_solve ([(5*x)+(2*sin(x))], [x]) gives "unable to solve".

The second is useless, but even the first is ambiguous to me.  Without an additional "where x is", it's just another equation rather than a solution set.

I'm also having difficulty graphing tangent in wxplot2d.  Whether it's tan(x) or sin(x)/cos(x), the graph is just vertical lines extending from the x-axis, even if I add or subtract a value that should offset the middle from the x-axis.  Oddly enough, sin(x), cos(x), and sin(x) (*/+/-) cos(x) all seem to graph, but not sin(x)/cos(x).

I tried adding the shared repository and installing ntrig and atrig1 (or atrig and ntrig1), but they weren't located.  Maybe I didn't add it properly.

Thank you!

---

