---
title: "How could I complain to Canonical about the kernel .config file that Ubuntu uses?"
date: 2010-05-03
forum: The Cafe
---

### Post by Shining Arcanine on 2010-05-03
Phoronix did [some benchmarks between Ubuntu Linux 10.04 and Windows 7]("http://www.phoronix.com/scan.php?page=article&item=linux_windows_part1&num=1") and the benchmarks suggest that Linux is worse than Windows most of the time at gaming. Being a Gentoo Linux user, I know that Ubuntu's kernel is not properly optimized for desktop computing and no matter how many times I post about it on Phoronix's forums, my requests for more a more clear picture of Linux's actual capabilities via the inclusion of a custom kernel are ignored.

Because of this, I would like to try to solve the problem at the source by asking Canonical to modify the .config file that they use to compile kernels for Ubuntu so that in the desktop ISO, 1000Hz operation, dynamic ticks, Kernel Preemption and RCU Preemption are all enabled. As far as I know, none of these things are enabled and they are needed for a lag free desktop. Had these been enabled, Phoronix's benchmark results would have been  different.

I realize that providing another variation of the stock kernel would require that Canonical support even more  kernels than it already does, but this is necessary for good desktop  performance and I hope that Canonical will realize that.

So that leaves me with the question, how can I complain to Canonical to hopefully have the kernel .config file changed?

---

### Post by ssam on 2010-05-03
maybe write a blueprint
[https://blueprints.launchpad.net/ubuntu](https://blueprints.launchpad.net/ubuntu)

gather as much data as you can. see you can make a benchmark showing the difference. show that there are no bad side effects (better interactivity may lead to lower throughput, or higher power consumption).

post to the devel-discuss mailing list.

try to get it on the agenda for the next UDS, and show up if you can

---

### Post by swoll1980 on 2010-05-03
File a bug report.

---

### Post by koleoptero on 2010-05-03
> **swoll1980 said:**
> File a bug report.

/thread

---

### Post by phrostbyte on 2010-05-03
The results of those tests have to do far more with graphics drivers than anything else. Unless there is a .config for fixing that. :)

---

### Post by Shining Arcanine on 2010-05-03
> **ssam said:**
> maybe write a blueprint
[https://blueprints.launchpad.net/ubuntu](https://blueprints.launchpad.net/ubuntu)

gather as much data as you can. see you can make a benchmark showing the difference. show that there are no bad side effects (better interactivity may lead to lower throughput, or higher power consumption).

post to the devel-discuss mailing list.

try to get it on the agenda for the next UDS, and show up if you can

Being an undergraduate student, that seems like more work than I have time to do. At the same time, the semester is coming to an end, so I will I see what I can do about getting a blue print together.

The Ubuntu Developer Summit for 10.10 is in Brussels, Belgium and I definitely will not be able to attend that. Since I am preparing for my finals, it is doubtful that I could have a blue print ready and accepted by then, much less attend.

> **phrostbyte said:**
> The results of those tests have to do far more with graphics drivers than anything else. Unless there is a .config for fixing that. :)

A desktop enviornment and games require low latencies. The video driver is no exception to this. The kernel configuration that Ubuntu has by default is great for maximum throughput, but not so great for low latencies. People have been using the realtime kernel that Canonical provides to get low latencies, but that is overkill for the purposes of an OS that will run a desktop environment and games and introduces far more overhead than necessary.

---

### Post by Mazin on 2010-05-03
I think the best thing to do would be to recompile the kernels yourself, with your wanted options, and then benchmark them against the stock Ubuntu kernel and Windows.

Do try to ask the devs for an explanation of why they chose their kernel configs, but asking them to do another kernel might be too much.

---

### Post by Shining Arcanine on 2010-05-03
> **Mazin said:**
> I think the best thing to do would be to recompile the kernels yourself, with your wanted options, and then benchmark them against the stock Ubuntu kernel and Windows.

Do try to ask the devs for an explanation of why they chose their kernel configs, but asking them to do another kernel might be too much.

I already compile my own kernel, but doing that does not do much with regard with benchmarks by sites like Phoronix which have no interest in figuring out why things are and only want to make their sponsors (like Canonical) happy by producing benchmarks that do not necessarily mean anything in terms of what is actually possible.

---

### Post by xir_ on 2010-05-03
> **Shining Arcanine said:**
> I already compile my own kernel, but doing that does not do much with regard with benchmarks by sites like Phoronix which have no interest in figuring out why things are and only want to make their sponsors (like Canonical) happy by producing benchmarks that do not necessarily mean anything in terms of what is actually possible.


how about you prove this using some other phronix benchmarks?

Im not sure what distros use what defaults but there are enough results for you to show a qualitative difference between distros with different defaults.

From what i recall fedora isn't that much faster then ubuntu.

---

### Post by LowSky on 2010-05-03
How can you compare a Linux machine to a Windows machine in gaming. Windows gaming is light years ahead. Blame the industry adoption of DirectX.

---

### Post by elkikin on 2010-05-03
One of the great things about openSUSE is that they have several "flavours" of the current kernel available for their users, including a default one, great for servers and old computers, and a desktop one, with better performance for opengl and multimedia. This was done because their users requested it: [https://features.opensuse.org/305694](https://features.opensuse.org/305694)

Maybe Ubuntu should have a similar policy?

---

### Post by Simian Man on 2010-05-03
> **LowSky said:**
> How can you compare a Linux machine to a Windows machine in gaming. Windows gaming is light years ahead. Blame the industry adoption of DirectX.

Except that they used games that were based on the Quake 3 engine, and thus OpenGL.  DirectX has absolutely nothing to do with it.

---

