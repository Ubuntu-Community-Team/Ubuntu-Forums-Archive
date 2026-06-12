---
title: "Starling dissatisfaction and how to get out of it?"
date: 2013-01-12
forum: System76 Support
---

### Post by kokoshmusun on 2013-01-12
We purchased a Starling netbook about 1.5 years ago.  We felt like it was a bit more pricy than comparable netbooks in the market, but we wanted to support System76 and the linux world. 

The Starling was a bit dissatisfactory for us.  It had Ubuntu 11.10 and then we upgraded to 12.04.  The fan worked a bit hard and it was slow.  But no major problems. To make it run a bit better, I just installed xubuntu 12.04 on it.  And we need MS Office (unfortunately, LibreOffice doesn't do for our purposes) so I installed virtualbox.  However, I was unable to install Win7 Pro 64-bit, because it wanted me to change something in the bios related to VT-x/AMD-V but I couldn't find that option in the bios. 

So, getting impatient and being worried about how Win7 Pro will perform in xubuntu virtualbox in a netbook, I decided to try to install Win7 Pro directly.  This time, ethernet and some other peripherals needed drivers, and I didn't know how to get them. 

I'm thinking about installing xubuntu again and trying Win7-32 bit.  However, I felt that at this point, I wanted some help about how to make the best use of Starling and whether it will perform well with this setup.  Will Win7+MS Office run well under xubuntu in virtualbox?  If not, where can I get the drivers for Win7?  And why is the fan working a bit too much and it's a little slow.  

I hope I can like Starling better after some support.  Thanks.

---

### Post by 2F4U on 2013-01-12
Not sure what you expect. The specs I was able to find on the net said something about an Atom processor with 1 GB or 2 GB of RAM. This is by all measures not a power horse. It is a netbook intended to be light and small.
Seems to me as if you should have bought a more powerful machine if you want to run virtualization software.

This is a list from Intel which lists all the processors with virtualization support built into their hardware. 

[http://ark.intel.com/Products/VirtualizationTechnology](http://ark.intel.com/Products/VirtualizationTechnology)

Only a few Atom's have virtualization support.

---

### Post by kokoshmusun on 2013-01-12
You're right, part of it is our fault, we should have chosen a more powerful computer.  My wife needed something lightweight to carry around, and that's why we went with this.  But even for just regular stuff, like barebones Ubuntu running and web browsing, we are not very happy with how much the fan works and how slow it is.

---

### Post by nevius on 2013-01-13
What specific MS Office applications do you need? I have had good success running Office 2003 and Office 2007 [excel and word] in wine (no need to set up a VM).

If you want a quick and simple way of installing it, buy a copy of crossover office and run MS Office there.

[URL="https://www.codeweavers.com/store/"]https://www.codeweavers.com/store/
[/URL]

---

### Post by kokoshmusun on 2013-01-13
We really just needed Word.  Didn't know of crossover, that could be very helpful.  Thanks!  In the meanwhile, we gave up on the idea of using Word on this computer, and I installed puppy linux on it.  It feels a bit different since I'm so used to ubuntu and similar distros, but if my wife can't get used to it, I'll put lubuntu on it.

---

### Post by nevius on 2013-01-14
> **kokoshmusun said:**
> We really just needed Word.  Didn't know of crossover, that could be very helpful.  Thanks!  In the meanwhile, we gave up on the idea of using Word on this computer, and I installed puppy linux on it.  It feels a bit different since I'm so used to ubuntu and similar distros, but if my wife can't get used to it, I'll put lubuntu on it.

You can also get a 30 day free trial to test out crossover. Codeweavers is a great company that contributes back to the wine project.

---

### Post by BBQdave on 2013-01-16
> **kokoshmusun said:**
> ...I just installed xubuntu 12.04 on it.

I think that is your best shot at performance and modern system. And as mentioned before, a netbook is not good hardware for virtual machines - multiple running OS's. Best to stick with a straight install of Xubuntu 12.04 or 12.10 :)

---

### Post by kokoshmusun on 2013-01-19
I'm a big fan of xubuntu, have used it for a long time on another machine, but it wasn't as fast as I expected.  Put puppy linux on the hard drive (1st time I did that), was super fast, but it feels a bit foreign after having been on ?ubuntu systems for so long.  So tonight I installed lubuntu 12.04.  Hopefully, this will stay.  I'm forgetting about virtualization and all that.  Obviously, we didn't know what we were doing when we bought this computer.

---

### Post by Ghostmn on 2013-01-20
I'd suggest trying out xubuntu 12.10 just to see if libreoffice 3.6.x has what you need.

I mean, you're probably not going to get a smooth experience running Word through crossover or wine.

---

### Post by nealaustin on 2013-04-10
What is wrong with Libreoffice? You can set it to save to Microsoft Office formats. Presentation has been a little problematic for me sometimes.

---

