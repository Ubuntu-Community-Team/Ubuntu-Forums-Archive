---
title: "Parallella '$99' 'supercomputer'"
date: 2012-10-05
forum: The Cafe
---

### Post by ssam on 2012-10-05
Have you seen the [Parallella: A Supercomputer For Everyone]("http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone") Kickstarter.

They are working on making 1000 core co-processors for cheap low power 'supercomputing'. The kickstarter is for a dev board with a dual-core ARM A9 (similar to a pandaboard, much faster than a raspberrypi), with a 16 core epiphany coprocessor for $99. (if they meet $3M there will be a $200 64 core version). The 16core version uses 270mW and 2 mm^2 of silicon.

They have some demo videos running ubuntu. the patches for their custom cpu cores is in GCC since 4.7.

As far as I can tell, even though it would loose to GPU on raw GFLOPS, because the cores are more independent, it could accelerate more real world code.

For the cpu nerds, this document is quite detailed,  [http://www.adapteva.com/wp-content/uploads/2011/06/adapteva_mpr.pdf](http://www.adapteva.com/wp-content/uploads/2011/06/adapteva_mpr.pdf)

---

### Post by hakermania on 2012-10-05
Your link is broken but I figured it out !

Seems interesting!

---

### Post by ssam on 2012-10-05
oops, sorry about link, i think a mod has fixed it. thanks.

---

### Post by Linuxratty on 2012-10-05
OoOHhhhhh! Me want! :P:)

---

### Post by CharlesA on 2012-10-05
I wonder how well those would run something like BOINC.

---

### Post by ssam on 2012-10-06
> **CharlesA said:**
> I wonder how well those would run something like BOINC.

You would have to recompile the project for their epiphany architecture, but it could work very well for some projects. It looks like they are already think of doing a distributed project

> 
Thank you everyone for giving us hope! We still have a long way to go but having 1000 people believe in us and a parallel future means we have a chance!!

The Parallella project is now a distributed computer with 18,000 CPUs, 25 TFLOPS (peak spf) of performance and 1000 system administrators, consuming about 5KW with about $100K spent. We don&#8217;t know what kind of crazy collaborative projects people can come up with, but we think the cost point is pretty cool!! (kind of like SETI@home.) To put this in perspective, the famous Earth Simulator from 10 years ago had 5120 CPUs, a peak performance of 35 TFLOPS (linpack DFP), consumed over 5MW, and cost 50B yen to develop [[http://en.wikipedia.org/wiki/Earth_Simulator](http://en.wikipedia.org/wiki/Earth_Simulator)].


[http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone/posts/319199](http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone/posts/319199)

---

### Post by ssam on 2012-10-07
They have just released a bunch more documentation of the architecture.
[http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone/posts/323691](http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone/posts/323691)

---

### Post by will1982 on 2012-10-07
This sounds seriously cool.

---

### Post by greatsirkain on 2012-10-07
I've looked at the rasberry pi (even tried to order one, apparently I can have one sometime between now and my death) but I also saw some folks chatting about the OU senseboard (which I just received as part of my tu100 course) and the possibilities of linking the two although when I looked for specifications of the senseboard I got nothing. I feel like I might be a little out of my depth, can't see any ram or cpu to speak of, definitely nothing like the PI, anyone know what's going on with that?

---

### Post by MrHouch on 2012-10-11
It's an incredible cool project. It's sad to see that the big ones doesn't report about the Project. It will have a so great future.

---

### Post by ssam on 2012-10-25
there is a new video up. out of the box this is a useful low power (5W) ubuntu computer. once developers get hold of it i will be a very powerfull (at processing).
[http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone](http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone)
2 days to go and the kickstarter might just make it.

---

