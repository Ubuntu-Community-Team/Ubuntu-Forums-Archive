---
title: "how do so many modern movies get rendered with linux?"
date: 2010-02-18
forum: The Cafe
---

### Post by nerdy_kid on 2010-02-18
I thought gfx on linux sucked too much to do that kind of rendering....

---

### Post by Simian Man on 2010-02-18
They don't use real-time graphics like OpenGL which is what games use and commodity graphics cards are optimized for.

They do "offline" graphics such as [ray tracing]("http://en.wikipedia.org/wiki/Ray_tracing_%28graphics%29").  It's a totally different beast.

---

### Post by phrostbyte on 2010-02-18
> **Simian Man said:**
> They don't use real-time graphics like OpenGL which is what games use and commodity graphics cards are optimized for.

They do "offline" graphics such as [ray tracing]("http://en.wikipedia.org/wiki/Ray_tracing_%28graphics%29").  It's a totally different beast.

They might use GPUs for rendering too these days, GPUs have a programmable graphics pipeline since the GeForce 3. Nvidia cards are about par (or better) performance on Linux anyway.

---

### Post by Warpnow on 2010-02-18
The programs used in hollywood on linux systems are made by a company called autodesk, their most popular linux application begin smoke. It is distributed not as a program, but as a distrobution based on red hat, with a custom kernel. Without this custom kernel, you can't run Smoke. Makes it pretty hard to crack/pirate, and its very proprietary. 

Basically, it sucks unless you have the very expensive (5 figures minimum) hardware/software packages.

---

### Post by james.paige on 2010-02-18
Avatar... Enough said.

[http://jordanhall.co.uk/general-articles/avatar-film-rendered-with-enormous-ubuntu-server-farm-4701468/](http://jordanhall.co.uk/general-articles/avatar-film-rendered-with-enormous-ubuntu-server-farm-4701468/)

---

### Post by Tibuda on 2010-02-18
Not using Pitivi, Kdenlive or Openshot.

---

### Post by cariboo on 2010-02-18
Check out this [article]("http://www.linux-netbook.com/10-blockbusters-made-with-the-help-of-linux") about a few movies that were rendered using Linux.

---

### Post by Lightstar on 2010-02-18
I was rendered in linux :)

---

### Post by audiomick on 2010-02-18
It is a bit like professional sound work, I think. The market leader is pro-tools, and the work isn't done by the computer it is running on, but rather on the proprietary "sound farms" that go with it. They are hardware modules with dedicated DSP hardware in them. The computer just "steers" them.
Also, there is no guarantee that any of that video stuff is being processed real time. I don't know really, but I had assumed that stuff on that scale is a matter of setting up the routine, telling the computer to do it, then going off to have a coffee, the same as sound editing was in the mid 80's. In those days, a mac needed about 15 minutes to put a 12 song playlist together...;)

---

### Post by dragos240 on 2010-02-18
> **james.paige said:**
> Avatar... Enough said.

[http://jordanhall.co.uk/general-articles/avatar-film-rendered-with-enormous-ubuntu-server-farm-4701468/](http://jordanhall.co.uk/general-articles/avatar-film-rendered-with-enormous-ubuntu-server-farm-4701468/)

He didn't ask for an example.

---

### Post by cariboo on 2010-02-18
In the case of rendering movies, it's more like going for a short vacation while things render. :)

---

### Post by audiomick on 2010-02-18
> **cariboo907 said:**
> In the case of rendering movies, it's more like going for a short vacation while things render. :)
I am quite sure that you are right.;)

---

### Post by Frak on 2010-02-18
They don't use normal graphics cards, they use workstation and render graphics cards. Render cards, such as the Nvidia Tesla, work amazingly under Linux and can almost fully offset the rendering load off the main processor (depending on the job) if utilized in such a way..

---

### Post by koleoptero on 2010-02-18
> **danielrmt said:**
> Not using Pitivi, Kdenlive or Openshot.

Not even Blender.

---

### Post by Sporkman on 2010-02-18
Inexpensive mass number-crunching.

---

### Post by perce on 2010-02-19
When I was in graduate school I had some office neighbours who worked at CERN. They told me they use Linux because it's the best in parallel computing. Probably it is the same reason why it is used on movies.

---

### Post by BuffaloX on 2010-02-19
> **nerdy_kid said:**
> I thought gfx on linux sucked too much to do that kind of rendering....

It has nothing to do with how well Linux handles graphics.
The rendering process is pure number crunching and is an ideal task to split up in thousands of threads. The job of number crunching is then distributed on a cluster that is usually called a render pool, which consist of multiple computers with multiple CPUs and cores.

In theory this process could be split up between millions of cores.

Linux handles clusters and multiple CPUs (render pools) better than most OS's, and is therefore very well suited for such tasks.
Buying a Unix license for each system in the cluster would be very expensive, and would not perform any better.
Windows doesn't handle such tasks nearly as well and would still be more expensive.

The real question is why Linux was chosen over BSD, which I have no real answer for, but I suspect it's because the GPL license ensures sharing of improvements better than the BSD license does, and Linux simply outgrew BSD.

---

### Post by ssam on 2010-02-19
[http://www.top500.org/country/146](http://www.top500.org/country/146)

the fastest computers in newzealand, all but one are owned by WETA and running linux. i guess they mostly rendering films.

---

