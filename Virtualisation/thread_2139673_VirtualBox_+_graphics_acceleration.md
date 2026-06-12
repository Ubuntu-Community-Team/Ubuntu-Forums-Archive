---
title: "VirtualBox + graphics acceleration"
date: 2013-04-27
forum: Virtualisation
---

### Post by madnbri on 2013-04-27
Hello,
I'm using 12.10 (wating minimum 1 week normally with system upgrade) and tried to install win 7 ultimate in VirtualBox.
I couldn't set up my graphical acceleration in guest. I followed a lot of instructions from net, but nothing changed.
There are many settings, so I do not insert everything here, please ask **any** You need.
Here comes some:
hardware: [http://paste.ubuntu.com/5609249/](http://paste.ubuntu.com/5609249/)
VirtualBox settings: [http://paste.ubuntu.com/5609275/](http://paste.ubuntu.com/5609275/)
Has anybody got idea?

---

### Post by gordintoronto on 2013-04-27
Virtualbox creates a virtual machine. The virtual video adapter is not related to the actual video adapter in your computer. If you want acceleration, use dual-boot.

---

### Post by madnbri on 2013-04-28
> **gordintoronto said:**
> Virtualbox creates a virtual machine. The virtual video adapter is not related to the actual video adapter in your computer. If you want acceleration, use dual-boot.
Thanks.

---

### Post by kamranm1200 on 2013-04-28
> **gordintoronto said:**
> Virtualbox creates a virtual machine. The virtual video adapter is not related to the actual video adapter in your computer. If you want acceleration, use dual-boot.

Thank you! You helped me as well! :)

---

### Post by ARooster on 2013-04-28
I never bothered to get 3D acceleration running on VirtualBox so I cannot confirm this, but I think Direct3D needs VirtualBox guest additions installed. So have you installed them? It was in experimental phases last time I saw so don't expect it to run too smoothly.

---

### Post by madnbri on 2013-04-28
> **ARooster said:**
> I never bothered to get 3D acceleration running on VirtualBox so I cannot confirm this, but I think Direct3D needs VirtualBox guest additions installed. So have you installed them? It was in experimental phases last time I saw so don't expect it to run too smoothly.
I've changed, but nothing happened. The solution is multi booting, I think. I need an extra hdd.

---

### Post by ARooster on 2013-04-28
Ah, then this is not about virtualisation, the question is in fact how to run two separate operating systems on the same computer. And you only need an extra HDD if the one you have is not large enough to accomodate two separate systems and all the data and software you need. If the hard drive is large enough just create multiple partitions.

---

### Post by madnbri on 2013-04-28
> **ARooster said:**
> Ah, then this is not about virtualisation, the question is in fact how to run two separate operating systems on the same computer. And you only need an extra HDD if the one you have is not large enough to accomodate two separate systems and all the data and software you need. If the hard drive is large enough just create multiple partitions.

No. The question was: howto set up graphics acceleration in VirtualBox. The answer is: no way.
I need an extra HDD, but this is my own problem.

---

### Post by howefield on 2013-04-28
> **madnbri said:**
> No. The question was: howto set up graphics acceleration in VirtualBox. The answer is: no way.

Dual booting is probably the best method depending on what you want it for, but you can get acceleration within virtualbox, albeit experimental as mentioned above.

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

---

### Post by madnbri on 2013-04-28
> **howefield said:**
> Dual booting is probably the best method depending on what you want it for, but you can get acceleration within virtualbox, albeit experimental as mentioned above.

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

I've read this source before asked.
But have got an idea:
Maybe my 3D acceleration doesn't work in Ubuntu, therefore doesn't work in VB hosts.
Does somebody know howto test it in Ubuntu?
Googling...

Done.
glxgears in mesa-utils package shows some rotary gears in 3D: it woks fine - this isn't be the problem

---

### Post by ARooster on 2013-04-28
look for nVidia X Server Settings app in Dash. Seeing as you've got an nVidia graphics card it should be there, I think, if your drivers are set up as they should be.

It will give you lots of information on OpenGL, X.org etc. See what you've got and see what you're missing. In my personal experience, nVidia 304 graphics work best, but try playing around with that if it works. Mind you, it is also my experience that Ubuntu 12.10 has the most issues with nVidia drivers. I find both 12.04 as well as the new 13.04 to be more stable.

---

### Post by madnbri on 2013-04-28
> **ARooster said:**
> look for nVidia X Server Settings app in Dash. Seeing as you've got an nVidia graphics card it should be there, I think, if your drivers are set up as they should be.

It will give you lots of information on OpenGL, X.org etc. See what you've got and see what you're missing. In my personal experience, nVidia 304 graphics work best, but try playing around with that if it works. Mind you, it is also my experience that Ubuntu 12.10 has the most issues with nVidia drivers. I find both 12.04 as well as the new 13.04 to be more stable.

OK, there is something incorrect at me.
I do not know what Dash is and searched some alternatives to detect my VGA. No useful found. This system a bit strange for me: every important settings made by program instead of me. That's why I cannot find settings in config files, else I do not understand these (because of large and unique generated files).

May I get help?
Which files do we need?

---

### Post by heiko_s on 2013-04-29
> **madnbri said:**
> Hello,
I'm using 12.10 (wating minimum 1 week normally with system upgrade) and tried to install win 7 ultimate in VirtualBox.
I couldn't set up my graphical acceleration in guest. I followed a lot of instructions from net, but nothing changed.
There are many settings, so I do not insert everything here, please ask **any** You need.
Here comes some:
hardware: [http://paste.ubuntu.com/5609249/](http://paste.ubuntu.com/5609249/)
VirtualBox settings: [http://paste.ubuntu.com/5609275/](http://paste.ubuntu.com/5609275/)
Has anybody got idea?

I hope this isn't off-topic, but have you considered Xen or kvm? The reason I'm asking is that in my experience (with Xen) this is about as good as dual-boot in terms of performance. The great disadvantages of using either Xen or kvm with VGA passthrough (that's the term for making the graphics card available to your guest machine) is that its success depends on the hardware, and you need a spare graphics card or GPU for your guest system.

When you get 3D acceleration under VirtualBox working, I would be curious to know how well it performs compared to native (i.e. Windows directly installed, running the vendor's graphics driver). A Unigine Heaven 3.0 benchmark would be nice, or the Passmark results. Here my Passmark results with a Windows 7 64bit Pro guest running on Xen: [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013&start=40#p702361]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013&start=40#p702361").

Good luck with the 3D graphics acceleration!

---

