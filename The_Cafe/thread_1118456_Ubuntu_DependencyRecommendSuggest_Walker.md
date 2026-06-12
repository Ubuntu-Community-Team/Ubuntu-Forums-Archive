---
title: "Ubuntu Dependency/Recommend/Suggest Walker"
date: 2009-04-07
forum: The Cafe
---

### Post by Deo Favente on 2009-04-07
Ok, if you haven't played with yEd from yworks then you gotta try it, its a neat graphing thing that. But thats not my point, yet. I was bored one day so I made a small program that gets all the depends / recommends / suggests of the packages, then gets all the depends of those packages etc. and puts it into a graphml format for yEd. yEd then makes it look pretty and exports it to different file types.

Heres a short dependency walk for libc6 as an example. Red edges = depends, green = recommends, and blue = suggests, just like packages.ubuntu.com. 

Main link:
[http://whitehat.servehttp.com/tools/updw/libc6.html]("http://whitehat.servehttp.com/tools/updw/libc6.html")

For people without at least a semi-working flash plugin:
[http://whitehat.servehttp.com/tools/updw/libc6.svg]("http://whitehat.servehttp.com/tools/updw/libc6.svg")

I think I should add links to the nodes maybe...
Edit: I don't know whats up with debconf-doc, i have to look into that

---

