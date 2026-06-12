---
title: "Sorting algorithm in Lucene"
date: 2011-12-27
forum: Server Platforms
---

### Post by salmontres on 2011-12-27
Hi guys,

I'm reading through the Lucene docs in an attempt to understand how their weighting algorithm works for relevancy ranking. I wanted to implement a modified version of their relevancy ranking not to files, but to objects which contain text fields. (Such as merchandise in a store database, which contains a major_field=games and a minor_field=PS3Games, for instance.)

However, I can't seem to find the relevant source files that talk about the weighting algorithm and was wondering if anyone else is working on something similar. What files did you focus on?

---

### Post by rubylaser on 2011-12-27
I've used [Thinking Sphinx]("http://freelancing-god.github.com/ts/en/searching.html") in Ruby on Rails apps for weighting fields before.

---

### Post by Vegan on 2011-12-28
I suspect quick sort is being used as its the primary general purpose algorithm.

I can do faster with my sort.h header for specialized data. I can sort on O(n) in even zip codes.

---

