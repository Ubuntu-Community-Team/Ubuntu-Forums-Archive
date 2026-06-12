---
title: "No Pre-installed C Complier?"
date: 2009-04-07
forum: Server Platforms
---

### Post by HighCommander540 on 2009-04-07
Hello, so I have a problem that I would like to be resolved if possible. I installed my Ubuntu server to originally run a web server and so that I could always have a server to study C on, but i found that the server doesn't come with a pre-installed C complier.

What program should I use for a C complier? What do people recommend? Also, can you point my to a tutorial on how to set it up properly and efficiently, because this is a webs server I need it to take up the least amount of CPU and time that I can get it too.

---

### Post by Peasantoid on 2009-04-07
You probably want gcc: the GNU C Compiler / Compiler Collection.
```
sudo apt-get install build-essential
```

---

### Post by HighCommander540 on 2009-04-07
Thank, you very much. I was thinking GCC myself, but I just wanted to know if there was anything better. I also had no idea how to install it, I tried sudo apt-get install gcc, but that didn't work too well, because of all of the ******** it didn't have.
Thanks!

---

### Post by HighCommander540 on 2009-04-08
Hey, I was wondering if there is a better way to install the GNU C Complier, other than with build-essential? Because it installs a lot of packages. Like I said I am trying to get the least best fastest install.

Are there any of the packages that build essential installs that aren't really needed and the complier will still working perfectly? Or are they al needed? Or maybe some of them just add more functions or something?

---

### Post by ad_267 on 2009-04-08
You probably don't need dpkg-dev

You could install just libc6-dev, g++ and make

---

### Post by kencom on 2009-04-13
> **ad_267 said:**
> You probably don't need dpkg-dev

You could install just libc6-dev, g++ and make
I have a similar problem to HighCommander540, less demanding, but I suspect I know a lot less about the problem than he does.  My system also has a dual core AMD 64. I see from the Synaptic Package list that libc6-dev-amd64 is offered as an alternative library intended for 64 bit processors, so presumably is needed if your compiled program is to exploit the extra instructions.

I am puzzled by the availability also of libc6-amd64, which is described differently from libc6-dev-amd64.  Is this an alternative or are both needed?

Rusty old-timer, using Hardy Heron on AMD 64 dual core

---

### Post by ad_267 on 2009-04-13
To run 64 bit applications you need libc6-amd64, but to compile them you need libc6-dev-amd64.

The libc6-dev-amd64 package contains only header files and other requirements for actually compiling programs.

---

### Post by kencom on 2009-04-13
> **ad_267 said:**
> To run 64 bit applications you need libc6-amd64, but to compile them you need libc6-dev-amd64....
Thanks. I am beginning to realise how pampered I was when I was in employment: if I needed a new compiler on our mainframe I just asked one of my staff to install it. I shall get the hang of it all eventually.

My local advisers (my daughter and her partner) helped me install Ubuntu and recommended its 32-bit version as possibly more complete.  They now suggest that to run 64-bit applications I would also need the 64-bit version of Ubuntu.  The documentation on the help.ubuntu.com site makes no mention of this need but is not particularly full.  Following their advice I installed the 32-bit version and would rather leave it for the present, and possibly upgrade to the 64-bit version later.  However, the description of upgrades on the help.ubuntu.com site makes no mention of a 32 -> 64 bit change, and if I have to make this change as a new installation it would be better to do it now, to save lots of back-up and restore.  Please will you advise or point me at more complete documentation, which I would be very happy to read if I could find it.

---

### Post by ad_267 on 2009-04-13
You should be fine sticking with the 32 bit version. There are no applications that require 64 bit that I know of. The only advantage you'll get with 64 bit is improved performance from a few applications.

If you want to do a 32 to 64 bit change then I think you have to do a completely new installation, rather than just an upgrade.

---

### Post by kencom on 2009-04-14
> **ad_267 said:**
> You should be fine sticking with the 32 bit version. [...]
Thanks for your prompt reply.  Now for GCC.

---

### Post by HighCommander540 on 2009-04-14
Thanks, for helping me with this info I found that just installing, gcc++ and make. Did the trick because it just got all the needed packages for compiling C/C++.

For anyone that wants to have a minimal gcc install I recommend that. It works wonders and doesn't tax your system! On the other hand if you want everything it has to offer like advanced debugging, get the build-essential.

I am currently running it on my beta back-up servers thanks!

> **kencom said:**
> Thanks for your prompt reply.  Now for GCC.

Actually, I wouldn't just listen to that without thinking about it. The reality of the matter is, that 64-bit gives your better performance. I have both types of systems and I have a lot better performance on the 64-bit (with all OSes). That is to say if you have a 64-bit processor, go for the 64-bit.

Especially since it supports more RAM and eventually everything computers is going to be 64-bit (so take the plung now and learn), and 32-bit will be out the window. Pretty much everything is supported for 64-bit, especially since you can get a GCC add-on that will convert 32-bit apps to 64-bit on compile.

And it isn't just performance from a few apps. With the ability to process more info at once it is just straight up faster. Especially for a system like Ubuntu who is built to run in 64-bit. My advice to you sir, is that if you can do it!

Also, yes there is no way to upgrade, because it uses completely rewritten base files. You have to do a completely new install.

---

