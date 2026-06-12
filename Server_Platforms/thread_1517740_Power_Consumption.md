---
title: "Power Consumption"
date: 2010-06-25
forum: Server Platforms
---

### Post by MerlinCoder on 2010-06-25
Hey guys!

Over the weekend I am going to set up a Linux server to host a portfolio webpage. I want to have full control over the various systems so free hosting isn't really an option.

Now, me and my friend were recently talking about the costs of running a computer 24/7 and apparently a 400w power supply can cost about £20 a month.

Looking at a website like rackspace, they can offer something that will probably suit my needs for a much more attractive £15/month.

My question is: is it possible to scale Ubuntus power usage?

I'm not really much of a technical wiz and don't really know too much about the inner power workings of a computer, software has always been much more my bag, but as I understand it, the GPU will take a large chunk of the overall power required. 
I do not expect it to stop drawing simply because there is no monitor plugged in but is there a way to instruct ubuntu to turn it off?

I am quite new to Linux and brand new to Ubuntu so I am just talking in theory at the moment, but it will be interesting to hear what you guys think.

---

### Post by MerlinCoder on 2010-06-25
Another question I have is just how much grunt does a server running Apache PHP and MySQL need, the most basic rackspace isn't very much compaired to the power you get from buying a computer for about £400 quid.

---

### Post by t1nm@n on 2010-06-25
hope this helps out

[http://ubuntuforums.org/showthread.php?t=816746](http://ubuntuforums.org/showthread.php?t=816746)

---

### Post by Bachstelze on 2010-06-25
How did you come with that number of £20/month? Just because your server's PSU says "400W" does not mean your computer will be constantly eating 400W, it means the PSU can deliver a maximum of 400W. If the computer needs less, it will consume just what it needs.

---

### Post by Bucky Ball on 2010-06-25
For a server always a good power supply. It is the heart of the machine. If you want my complete rave on that subject it is in the link to the energy efficient build in my signature. 

Make sure the PSU is rated 80+. 85+ even better. These usually have a longer working life. Will save you so worth spending a bit extra now. A silver box power supply generally rated 70% or worse. Your electricity makes heat rather than powering your machine efficiently.

---

### Post by tgalati4 on 2010-06-25
[http://ubuntuforums.org/showthread.php?t=1460267&highlight=power+watt](http://ubuntuforums.org/showthread.php?t=1460267&highlight=power+watt)

---

### Post by volkswagner on 2010-06-26
If power consumption is a concern and full control is needed, won't a VPS from a provider give you what you need.  To give the 24/7 reliability of a commercial VPS provider you will need redundant ISP connections, power supplies, router/switches etc.

For a single site you won't even eat up 20% of the most modest hardware.

Other considerations if you still want to host yourself:
[LIST]
[*]Verify your ISP rules allow you to host
[*]Verify your ISP does not block any of the necessary ports
[*]You will want a static ip from your ISP for best joy.
[*]Consider total cost of needed equip to make it reliable
[/LIST]

For a power efficient server look into an Intel atom based server with a low power video chip such as the 410/510 series.  Even an old Pentium2 or Pentium3 box will run at under 50watts. 

Enjoy

---

