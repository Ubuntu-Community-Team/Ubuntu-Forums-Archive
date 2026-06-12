---
title: "Is Ubuntu Server ONLY for 64 bit?"
date: 2010-11-10
forum: Server Platforms
---

### Post by listerdl on 2010-11-10
Hi am I correct that the machine that you install ubuntu server must be 64 bit?

thanks

---

### Post by CharlesA on 2010-11-10
No. There is a 64-bit and 32-bit version.

You can find them here:

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by James78 on 2010-11-10
64 bit is highly recommended, i.e. use it if the computer is at all capable of doing it. However if your server can't do it, there is a 32 bit version available. My server unfortunately cannot run 64 bit, but I'm running 32 bit in production, and have 0 problems related to architecture, so there's nothing to worry about. But go 64 bit if you can, it's always the better choice, especially when dealing with servers.

---

### Post by arrrghhh on 2010-11-10
> **James78 said:**
> 64 bit is highly recommended, i.e. use it if the computer is at all capable of doing it. However if your server can't do it, there is a 32 bit version available. My server unfortunately cannot run 64 bit, but I'm running 32 bit in production, and have 0 problems related to architecture, so there's nothing to worry about. But go 64 bit if you can, it's always the better choice, especially when dealing with servers.

Why do you say that?  Typically compatibility is better on 32-bit, and with a PAE kernel you can run up to 64gb of RAM... Yes, that's sixty-four gigabytes of RAM - no 4gb limitation...

---

### Post by CharlesA on 2010-11-11
> **arrrghhh said:**
> Why do you say that?  Typically compatibility is better on 32-bit, and with a PAE kernel you can run up to 64gb of RAM... Yes, that's sixty-four gigabytes of RAM - no 4gb limitation...

While that may be true (the compatibility and PAE kernel things), if your machine can handle a 64-bit OS, why not use a 64-bit OS?

I only have 2 machines that are running 32-bit OSes, but that's cuz they don't have 64-bit CPUs in them. :P

---

### Post by James78 on 2010-11-11
> **arrrghhh said:**
> Why do you say that?  Typically compatibility is better on 32-bit, and with a PAE kernel you can run up to 64gb of RAM... Yes, that's sixty-four gigabytes of RAM - no 4gb limitation...
Typically for Desktop OS's that's more true. I run 64 bit on some of my OS's and compatibility is typically just as good, and when you get into the server area of 64 bit OS's, because compatibility is pretty much just as good, why not allow the server to use it's extra power to make a better server for you? I see no reason against it, only for when using a Desktop OS. I wasn't saying use 64 bit if you can because of any 4GB limitation, I was saying that because it's just a good idea if you're running a server. :)

There's a reason that most servers are running on 64 bit OS's afterall. Of course, if you can't do 64 bit because your processor won't allow you to, it's no biggie, but I think it's a good idea to do it if you can when we're talking about servers.

---

### Post by arrrghhh on 2010-11-11
My processor can definitely handle 64-bit, but I chose 32-bit because of media compatibility issues... Maybe those are moot now, I'm not sure.  I hate rebuilding this server, so I haven't since 10.04 launched :p

---

### Post by lisati on 2010-11-11
I use 64-bit on my server and laptop, mainly because I can. Other than my server having only a single core CPU, and perhaps some more RAM would be nice, I don't have any issues. 

I also have an older machine running Ubuntu 6.06 which I can use as a backup for my web server if I need to. It has fairly low specs by today's standards: it can only handle 32-bit, and choked (mainly due to lack of memory and HD space) when I tried to install a gui.

---

### Post by James78 on 2010-11-11
> **arrrghhh said:**
> My processor can definitely handle 64-bit, but I chose 32-bit because of media compatibility issues... Maybe those are moot now, I'm not sure.  I hate rebuilding this server, so I haven't since 10.04 launched :p
Ya, that's pretty much the reason why I don't suggest 64 bit for a Desktop OS, coming from experience too lol.

> **arrrghhh said:**
> ... Maybe those are moot now, I'm not sure.
Well, they're still there, not as much, but still existent. They're usually negligible, but the main problems are when you come into Flash support for 64 bit, ohhhhh it's a pain. How they have it setup is using the nsplugin (or whatever it is) to run the 32 bit flash plugin. It works, but there's small issues, like for me, going to other tabs and back to that one, then wherever the flash was, there's just this piece of white screen. Sometimes it even causes a kernel hardware crash, and your computer freezes. Support is getting better over time and with each release however, at least. But like I said, all these problems aren't related to servers really, because most people don't go running Firefox and watch a Youtube video using Flash on their servers, or other things media-ish related, like the Desktop version, and from experience, packages related to architecture, e.g. apache2, mysql, ruby, etc, have never ever had a problem with me.

---

### Post by Vegan on 2010-11-11
My spare tower is a Pentium 2-300 with 512 MB of SDRAM. It can run Linux server fine as long as the boot disk is not too small. The machine has a 32-GB limit but I have a PCI card to attach another disk.

My current web server is a Celeron 335 that uses DDR RAM. It only has 256 MB until I can find more memory. The disk is much better with 160 GB of room and I have several older EIDE disks so it can be used a long time if needed. Ubuntu server works fine on this machine.

Once I get a CPU for it, I can upgrade the Acer to a 64-bit system and be able to use more recent SATA disks.

So as long as you have enough RAM you are OK. Linux needs a fair bit of RAM to run well.

My server load is light so the Acer is fine as is. The goal for the 64-bit upgrade is for a chess project.

---

