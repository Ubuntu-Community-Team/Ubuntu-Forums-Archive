---
title: "Pro's and Con's with going to 32-Bit Ubuntu on PanP5"
date: 2009-10-06
forum: System76 Support
---

### Post by samalex on 2009-10-06
Hi,

I'm thinking of moving back to the 32-bit version of Ubuntu when 9.10 is released, but for those who have worked with both the 32-bit and 64-bit versions what are the caveats?  Do the drivers provided by System76 work the same on both?  Will the 32-bit version run noticeably slower?  

I've ran into several applications that are not available for 64-bit Linux, but generally I get buy with finding something else or just moving on... but Flash is one of the straws breaking this horse's back because the wrapper is just not cutting it very well.

Several folks have suggested dualbooting, but I'd rather not do that. I want an all or none system.

Thanks for any insight in this.  Either way I won't be making the move until December when my online course is complete because it took some time to get Firefox tweaked just right, so maybe some of the problems I'm running into will be squashed by then, namely Flash.

Thanks and take care --

Sam

---

### Post by jdb on 2009-10-06
> **samalex said:**
> Hi,

I'm thinking of moving back to the 32-bit version of Ubuntu when 9.10 is released, but for those who have worked with both the 32-bit and 64-bit versions what are the caveats?  Do the drivers provided by System76 work the same on both?  Will the 32-bit version run noticeably slower?  

I've ran into several applications that are not available for 64-bit Linux, but generally I get buy with finding something else or just moving on... but Flash is one of the straws breaking this horse's back because the wrapper is just not cutting it very well.

Several folks have suggested dualbooting, but I'd rather not do that. I want an all or none system.

Thanks for any insight in this.  Either way I won't be making the move until December when my online course is complete because it took some time to get Firefox tweaked just right, so maybe some of the problems I'm running into will be squashed by then, namely Flash.

Thanks and take care --

Sam

If you don't have over 3 gig of memory 64 bit might not be doing much for you anyway.
Here is a good article:

[http://en.wikipedia.org/wiki/64-bit]("http://en.wikipedia.org/wiki/64-bit")

You can just skip down to the "Pros and cons" section.

jdb

---

### Post by bruno9779 on 2009-10-06
It is true that some app do not exist in 64 bit, but you can always:

- compile from source (where available): best option for results, worst for speed
- Install ia32 (32 bit environement) and use "dpkg -i --force-architecture". To install a 32 bit deb on a 64 bit system

The second solution seems to work great for some that have flash issues (flash 64bit works fine for me, but I don't use it much anyway):
you remove firefox 64 bit and install firefox 32bit .deb. All the plugins for it will be 32 bit ones.

---

### Post by Lee_Machine on 2009-10-06
There is a native 64bit version of Flash for Linux, no need for the wrapper...which is a HUGE CPU cycle hog! 

Also Adobe is releasing a new flash player with OpenGL support, meaning it will now move some, even most of the computing to your GPU. 

Ive attached a script to install it correctly. (the native 64bit version)

This is not in the Ubuntu repos as it's still in Alpha development, has been for months. Although I have very little problems with it, even less than the wrapper..."Yay it caused Firefox to crash again!" :lolflag:


The big things that used to hurt me with 64bit was Flash, and Java web plug-in. Now there is Native 64bit for both. Iceweasle doesn't work for sites I use Java for. i.e ninjavideo.

One big Program for me is Boxee, which oddly does not have 64bit yet. So I just use 32bit on my Media PC.

Other issues would be not being able to use more that 3GB of memory...on the standard Kernel. You can install a server kernel and use up to 6 I think. (Not a recommended way, just a workaround for servers that need full 32bit support) 

I would personally stick with 64bit. The support gets better every day, and I see starting next year 64 bit will be the recommended industry standard for everyone. Window, Linux, and Mac (already is) 

I'm not sure about the drivers, there's no needs really anymore on my PanP4n. Using Ubuntu 9.10 Beta to post this.
   

My conclusion would be, if you need to have full 32bit support for some program than do it, but look for alternatives first. Some programs have an "unofficial" 64bit version.

---

### Post by Lee_Machine on 2009-10-06
Oh and here is the article/blog about the script, and plug-in.

[http://reformedmusings.wordpress.com/2009/07/03/installing-64-bit-adobe-flash-support-into-ubuntu-jaunty-9-04/](http://reformedmusings.wordpress.com/2009/07/03/installing-64-bit-adobe-flash-support-into-ubuntu-jaunty-9-04/)

---

### Post by Penguin Guy on 2009-10-06
I don't see any difference between the two at all, after trying both I tossed a coin and went for 32-bit. If you have 4GBs of memory, then 32-bit will only allow you to use 3.2GBs of it, but I don't find this a problem.

---

### Post by thomasaaron on 2009-10-06
Other than memory detection...

Make sure you test suspend/resume in 32-bit. That's half the reason we moved to 64-bit in the first place.

---

### Post by Lee_Machine on 2009-10-06
> **thomasaaron said:**
> Other than memory detection...

Make sure you test suspend/resume in 32-bit. That's half the reason we moved to 64-bit in the first place.

Suspend/Resume is blazingly fast in 9.10 64bit. You open that laptop lid, and its ready to go. ( or unlock)

---

### Post by jsteiner on 2009-10-06
An option that you may want to consider is installing a 32 bit VirtualBox virtual machine to handle any of your 32 bits apps that wont run under a 64 bit OS.  VirtualBox is a great easy to use solution. 64bit is the way all software is trending so you probably don't want to go back to 32 bit.  However a 32bit vm will buy you the time you need to run your apps until a 64 bit version of the app get released.  This will also accommodate older sw that will never have a 64bit release.  Just my .02.

---

### Post by thomasaaron on 2009-10-06
jsteiner,

*Excellent* point.

---

### Post by HotShotDJ on 2009-10-06
> **jsteiner said:**
> An option that you may want to consider is installing a 32 bit VirtualBox virtual machine to handle any of your 32 bits apps that wont run under a 64 bit OS. Great idea.  I've attached a launcher icon that you can use for it in your panel.

---

### Post by samalex on 2009-10-07
Hey Guys...

I'll try the 64-bit flash again, but the last time I tired it Firefox just crashed on any Flash enabled site with a Segmentation Fault error so I stuck with the wrapper.  I didn't know about ia32 though so I might try that if I can't get the latest 64-bit Flash installed since I think Adobe has updated it since I last tired.

As for VirtualBox, I do use it and it's awesome... though I only have Windows installed. I'd love to get my webcam working through virtualbox so I could use Flash sites that take advantage of the webcam, but thus far I haven't been able to get VirtualBox to see it.

I also didn't know about the 3 Gig limit on RAM. I have 4 Gigs and using VirtualBox as much as I do I need every bit I can... so that right there will keep me on 64-bit Linux.  

Thanks for the replies and great info... 

Sam

---

### Post by miniyak on 2010-01-12
I just recently used my panp5 with 32bit, w/out the graphics driver and a slower 5500rpm WD Blue Scorpio drive

I noticed the performance difference and i only have one dimm of 2gb

miro crashed once
cpus were constantly being utilized about 80-90% 
things just felt slow IMHO

64 bit karmic, w/ stock 7200rpm hitachi, w/out graphics driver= Better

Both were fresh full installs... (I borked grub... and just decided to back up and reinstall everything, long story)

---

