---
title: "Application memory"
date: 2009-11-07
forum: The Cafe
---

### Post by Xbehave on 2009-11-07
I have not done computer sciences, but I would like to learn about application's in memory, but I don't know enough to get google to do what i want and i haven't found a good guide so can somebody point me in the right direction.

A few questions i would like to understand are:
[LIST=1]
[*] When a program I loaded into memory does it remain unchanged?
e.g do the bits that are in /usr/bin/firefox sit fixed in memory
and does this vary by langauge?
[*] Does this mean that all the variable data is in the heap and stack?
[*] How does a program know where it is when you ctrl+z/restore it? I mean if i press ctrl+z when firefox is loading a page then restore it latter how does it know that it was half-way through executing the render page calls
[*] What does [anon] mean when i run pmap on a program?
[*] Is there a tool i can use to dump out the data of a program? and if so could i put it back on the same executable latter to keep it working?
[/LIST]

thx for answers or links or anything?

---

### Post by clonne4crw on 2009-11-07
I would love to know too! I know theres a ton of stuff that does this stuff in Windows, but is there something like this for Linux?

---

### Post by 3rdalbum on 2009-11-08
This is waaay out of my knowledge stream, but I think in answer to number 3, it probably doesn't actually know when it has been paused (or if it knows, it doesn't need to do anything about it). The kernel just preserves the contents of the program's memory, and does not give the program any CPU time until the program is resumed.

---

### Post by koenn on 2009-11-08
maybe this: [http://www.memorymanagement.org/articles/begin.html](http://www.memorymanagement.org/articles/begin.html) will give you a few links / keywords to search with

---

