---
title: "What makes a computer fast?"
date: 2009-06-11
forum: The Cafe
---

### Post by sertse on 2009-06-11
Fast defined by the only metric people actually care about in the end - How responsive it is and quickly it "does things". The overall user experience. 

At first glance it seems like a simple question that you "of course" know the answer to, but consider the fact that hardware, distro and application selection all play a role. 

We all heard stories where a older computer running Linux is faster than a new one in Windows. Within Linux, we know there are fundamental differences between Ubuntu compared to e.g. Arch, Slackware or source based distros that make the latter faster on otherwise identical systems. Then there is app selection; using something like Fluxbox, Pcmanfm etc will be lighter and faster than a full GNOME or KDE setup.  

How much does each part play in the final result?

EDIT: 

Adding to this, is there a point where one component is so far ahead that the others don't matter anymore? If I got a state of the art computer, could the sheer grunt of my hardware power through that I'll feel no difference if I lightened the other two factors. 

Or more personally, I already run imo, an pretty light setup through my choice of apps, built from a Debian minimal install. Resource usage is quite low. Would I see much improvement changing distro, but perhaps I'll hit some kind of limit where it doesn't matter anymore.

---

### Post by Regenweald on 2009-06-11
It's difficult to measure, hence the 'bottlenecking' term. To me, everything plays a factor: Motherboard BUS, Proc Speed, Memory speed, Hard Drive rpm/cache/latency. On top of all that, efficiency of the OS. Linux/BSD types run better on relics because they are simply more efficient and need less resource overhead.

---

### Post by keplerspeed on 2009-06-11
For me, its the harddisk. Maybe go to Solid state?? But then the cpu would be my slowest component.

RAM is generally the cheapest, easiest way to boost performance.

---

### Post by gn2 on 2009-06-11
> **sertse said:**
> We all heard stories where a older computer running Linux is faster than a new one in Windows. 

Most of these stories are somewhat dubious.

---

### Post by swoll1980 on 2009-06-11
> **gn2 said:**
> Most of these stories are somewhat dubious.

Agreed, as are the compiled kernels are faster, and source distros are faster theories. I've wasted several hours of my life compiling kernels, and installing source distros to increase performance, only to find out that it makes absolutely no difference at all.

---

### Post by raymondh on 2009-06-11
I think the bottleneck is in the FSB

---

### Post by mr-woof on 2009-06-11
I would say generally the bottle necks on systems are either the hd and or the ram.

---

### Post by NightwishFan on 2009-06-11
All of the components are relative as was said. For example, you can have 4gb of ram, however if it is slower ram, or you have a disk that copies to ram slowly, performance may seem lesser than a PC with only 1gb of ram, unless of course you run RAM heavy applications, or many at once. Some insights:

CPU: Processes that need cpu (encoding/rendering) generally benefit from higher clock and multiple cores (if optimized).

RAM: Keeps data 'current' much faster than the disk. More RAM means faster access to ram heavy applications, such as games and media players.

DISK: At first data is loaded off the disk. It is very crucial to performance. You need to trade off some performance to remain reliable though.

GPU: Same as CPU, though for 2D/3D performance. Main goal is to take stress off of standard CPU and RAM.

It mainly boils down to how the software is optimized to make use of the hardware. If you want a responsive GUI, meet it's requirements. Using 'lighter' software may not seem faster, though it will use less CPU cycles and RAM, and possibly access the disk less. Modern displays generally are accelerated on the GPU.

---

### Post by Bölvaður on 2009-06-11
Real time kernel!!!

---

### Post by SunnyRabbiera on 2009-06-11
warp drive!

---

### Post by Maheriano on 2009-06-11
Flux capacitor.

---

### Post by gn2 on 2009-06-11
Put it in the passenger seat of a Bugatti Veyron.

---

### Post by mousestalker on 2009-06-11
Well some computers fast because of politics. HPs are particularly progressive and engage in hunger strikes. 

Macs tend towards anorexia so its more a matter of narcissism with them.

Dells never fast. Not ever. They do throw up from time to time, but they don't fast.

;)

---

### Post by stmiller on 2009-06-11
An apple logo.

:)

/end sarcasm

---

### Post by Pogeymanz on 2009-06-11
Why hasn't anyone said software? Or was it too obvious and I missed the memo?

Software is the biggest bottleneck.  I have a ten year old Dell with a P3 and 128MB RAM that boots up just as fast into Arch + Openbox as this Compaq Laptop with DualPentium and 1GB RAM and Ubuntu + XFCE/Compiz. And it's just as responsive... Until you open Firefox with 10 tabs...

---

### Post by dragos240 on 2009-06-11
RAAAAAAAAAAAM makes a computer fast.
(random access memory)

---

### Post by CharmyBee on 2009-06-11
The "intel inside' sticker.

Fast RAM helps but isn't the end-all solution. RAM was inflated in price in '99 and it was advertised as the #1 upgrade ever. Not really true. You'd rather get an Athlon Classic then.

A good video card helps too, but the ones with proportionally huge price tags don't give much more than minor differences and big markitecture. Oddly though, for the best Linux experience for free, you have to splurge on the most expensive parts and specific brand names.

---

### Post by doas777 on 2009-06-11
well traditionally the slowest hardware process is always IO. nowadays we have ultra-fast FSB/system buses, and fast multi-synchronous expansion buses (like PCIe and Sata) to speed it up, but as others have said before, the mechanical aspect to current hard disks is probably the biggest hardware bottleneck most of us face. unfourtunatly unless you are gonig to SSD, there is no good way to upgrade to address that issue.

adding ram only helps speed you up, if you are already short on ram. it adds capacity, not speed. it will never make your box faster, but it will allow you to do more stuff, before you start to experience slowdowns due to paging.

my CPU on my desktop is a 2007 model, and it still almost never hits 100% long enough for a process monitor to read it. getting a faster proc is not really indicated. like ram, unless you are already using it all up, getting a faster one won;t actually cause your PC do run any faster (but some specific tasks may run in less time).

software efficiency and the way it works with hardware probably represent the largest real bottle neck we all experience. I don't think we'll ever see a box that will boot xp in less than 30 seconds, no matter how new the tech it's running on is. the software simply makes too many lame decisions to allow it.

 my laptop boots about 40 seconds faster using jaunty than intrepid, because it was specifically optimized to do it. 

too often, nowadays, over-the-top hardware allows programmers to get away with sloppy work. that is prolly the biggest problem

---

