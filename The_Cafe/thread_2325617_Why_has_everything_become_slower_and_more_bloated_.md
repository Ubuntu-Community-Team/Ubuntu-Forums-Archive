---
title: "Why has everything become slower and more bloated over time?"
date: 2016-05-23
forum: The Cafe
---

### Post by user1397 on 2016-05-23
It seems to me that operating systems and software in general have become slower and more bloated over the past 20 years (ever since I started playing around with them, starting with Windows 95).  I can't speak for anything before that, simply because I didn't exist and therefore have no experience hehe.

People often talk about how it's just Windows that has gotten slower and more bloated, but it feels like almost everything has, including most applications.

Ubuntu itself seems to have gotten much slower (I don't count window managers and purposefully-fast setups, just the major DEs) since I began using it with version 5.10.

I even downloaded 6.06 dapper drake the other day and booted it up in virtualbox to see how responsive it was, and it flew!  

I did the same with Windows XP some time ago...it just blew Windows 7, 8, and 10 out of the water, AND it was through a virtual machine which should make it at least a bit slower...

So what is the inherent reason?  Is it that we keep adding more and more features which bloats things and this makes things slower over time?  Is it because there are more coders but less competent ones so the code itself is written poorly and tends to be slower than old, more efficient code?  Is it all the legacy crap in our kernels (like floppy disk support in 2016)?  It surely cannot be the hardware, as that has advanced tremendously and our machines are way more powerful now than they were even 5 or 10 years ago...so what exactly is it?  And why is no one really talking about this?

---

### Post by mcduck on 2016-05-24
Things have developed to be more user-friendly, to add convenience features, prettier user interfaces, automatic systems so for average user the computer "just works"(tm). All that takes resources. You can just plug in a device and expect it to work, instead of installing drivers, setting up hardware interrupts and DMA channels by hand and so on. Every small automatic little convenience adds up a bit of weight in the system.

For example it's easy to think how heavy web browsers have become since the early days of Firefox, but then you'd also have to compare how web pages and content have changed since those days. And suddenly the browser itself isn't the issue any more.

Also I can still run Ubuntu on extremely low-memory setup, I have a testing VM which runs a desktop with less than 50MB of RAM, and even has some nice things like compositing support for transparency & drop shadows.. However to do that I need to give up many things people would, in general, expect their computers to do automatically or have easy-to-use configuration tools and systems for. 

So yes, the hardware has advanced over the years, but the assumptions and requirements people have have also changed.

---

### Post by buzzingrobot on 2016-05-24
Most consumers do not buy new hardware often enough to keep pace with new capabilities.  As they add new software written to leverage hardware that is newer than their hardware, inevitably they will notice a performance hit.

Hardware capabilities progress and increase, so developers are quick to exploit them to add new software capabilities that marketers hope will attract buyers. Linux and other FOSS developers frequently exploit the same capabilities to remain competitive.

Today, software from 1995 runs just the same -- no faster, no slower -- on 1995 hardware.  If you run it on 2016 hardware, of course it will run faster.

In regard to Microsoft, all pre-XP and pre-NT versions of Windows were DOS-based (essentially, DOS extenders) and were incapable of delivering many of the capabilities we expect and take for granted today.  Ditto Apple and Macs before OS X.

Legacy code is maintained for compatibility.  It's presence in an actual kernel binary does not necessarily mean it is loaded or otherwise places a demand on a system as long as it isn't needed.

---

### Post by poorguy on 2016-05-24
> **user1397 said:**
> 
So what is the inherent reason?  Is it that we keep adding more and more features which bloats things and this makes things slower over time?  Is it because there are more coders but less competent ones so the code itself is written poorly and tends to be slower than old, more efficient code?  


That is exactly what it is.

I wish someone would make a no frills basic OS without all the unnecessary software that the developers seem to think people need or want. 
Go ahead and develop all of that software but don't include it in a normal install but make it available for download if users want it.

---

### Post by buzzingrobot on 2016-05-24
> **poorguy said:**
> That is exactly what it is.

I wish someone would make a no frills basic OS without all the unnecessary software that the developers seem to think people need or want. 
Go ahead and develop all of that software but don't include it in a normal install but make it available for download if users want it.


People would not use it. "No frills" generally means steeper learning curve.  

Having software available for download wouldn't work because few people would know what they needed to add.

In any case, today we can use something "no frills" like LXDE or Openbox or even FVWM or some other ancient window manager (and take time to learn how to manually configure it) or use a Unity or a Gnome or a KDE.

---

### Post by poorguy on 2016-05-24
> **buzzingrobot said:**
> People would not use it. "No frills" generally means steeper learning curve.  

Having software available for download wouldn't work because few people would know what they needed to add.

In any case, today we can use something "no frills" like LXDE or Openbox or even FVWM or some other ancient window manager (and take time to learn how to manually configure it) or use a Unity or a Gnome or a KDE.

I guess since I'm willing to learn I figure everyone else is also. 

It seemed like a good idea but yeah I can see what you are saying. 

God forbid if people had to think that would not be easy for some.

---

### Post by grahammechanical on 2016-05-24
Apple do not have this problem because the corporation has convinced its believers to keep up to date with their religion by buying new hardware. Microsoft tried this kind of tactic by advertising new Windows machines instead of advertising the new version of Windows.

Of course Linux of 10 years ago run blisteringly fast on the machines on the market 10 years ago. That is because Microsoft had pushed the demand for ever more powerful hardware well beyond the minimum requirements for running Linux.

The minimum requirements for Linux are still well below the minimum requirements for Windows but Microsoft & Apple have shown users what a User Interface can look like and do when it is running on powerful hardware. And let us be frank about this. The Linux UI of 10 years ago was indeed on a par with Win98 & Win95. Better than Windows 3.1, I will admit that.

The visual expectations of users are now higher. And I do indeed have higher visual expectations than when I first installed Ubuntu 7.04. I do not called this progress "bloat." Sure, the number of lines of code in the Linux kernel is now many times greater than it once was. But then we expect today's Linux kernel to be compatible with the hardware that all those Windows XP users are running on. And many of those XP users who see a need to get a secure OS see no need to junk working machines. They expect Linux to run on them. 

That is what causes bloat in an OS.

Regards.

---

### Post by buzzingrobot on 2016-05-24
> **poorguy said:**
> I guess since I'm willing to learn I figure everyone else is also. 

It seemed like a good idea but yeah I can see what you are saying. 

God forbid if people had to think that would not be easy for some.

I suspect it's not an unwillingness to think but eyeglazed boredom about computing and an expectation that the whole point of computers is that they do things for us, not the other way around.

We could, for example, reduce footprint by eliminating package managers and dependency resolvers and go back to installing from tar archives and identifying and chasing dependencies ourselves. Or, remove the code that automagically populates menus.

New features that are often seen as nice-to-haves when introduced very often become essentials down the road.  It's the nature of technology to be derivative like that.

---

### Post by QIII on 2016-05-24
"Seems" is subjective.

Do you have any objective measure?

Define "bloated".  Does feature-rich == bloated?

---

### Post by oldos2er on 2016-05-24
> **poorguy said:**
> I wish someone would make a no frills basic OS without all the unnecessary software that the developers seem to think people need or want. 


Ubuntu Server. I did this myself a few years back, installed Server then installed X and i3wm on top of it, mostly as an exercise to increase my own knowledge. Ran this setup for six months or so.

---

### Post by grahammechanical on 2016-05-24
And then there is the mini ISO image. Where we make the decisions as to what is installed and can get a  desktop environment & user interface and not much else other than a terminal and a few settings utilities. Not even a web browser.

Regards.

---

### Post by mikodo on 2016-05-24
> **grahammechanical said:**
> Of course Linux of 10 years ago run blisteringly fast on the machines on the market 10 years ago. That is because Microsoft had pushed the demand for ever more powerful hardware well beyond the minimum requirements for running Linux.

+1

My Windows Vista designed 2007 Quad-core intel machine is still blazing fast on Linux. Even with, the resource hungrier full .iso Unity/Gnome/KDE desktops with all it comes with and anything I could want to install. I think we have reached an equilibrium where general duty machines (even the modestly specked ones of today) are going to remain over-powered for many many years once they are bought, regardless of the OS/platform. With ARM microprocessors for mobile now the trend, I don't see this ever reversing. I think the bubble of needing more powerful machines every new install of an OS, is gone.

I think this whole thread is just frivolousness. Something else to complain about for we humans who like to complain.

---

### Post by QIII on 2016-05-24
There is also some consideration that must be given to what our expectation of "fast" was 10 or 20 years ago.

I imagine that 10 years ago an OS that could go from boot splash to full desktop in 15 seconds would have been considered magical.  Now, it's expected.

---

### Post by poorguy on 2016-05-24
> **grahammechanical said:**
> And then there is the mini ISO image. Where we make the decisions as to what is installed and can get a  desktop environment & user interface and not much else other than a terminal and a few settings utilities. Not even a web browser.

Regards.

The mini ISO image may be a good place to start and I do like the idea of being able to install what I need.

---

### Post by Irihapeti on 2016-05-24
> **QIII said:**
> "Seems" is subjective.

Do you have any objective measure?

Define "bloated".  Does feature-rich == bloated?

"Bloat" is a vaguely disparaging word that means "has stuff that I don't want". :)

---

### Post by user1397 on 2016-05-24
> **mikodo said:**
> I think this whole thread is just frivolousness. Something else to complain about for we humans who like to complain.meh...if you think that way, you can apply that to pretty much every thread in the cafe...

I didn't mean to sound like I'm complaining...it's just something I've personally noticed (maybe it's just me?) and I was curious as to know what might be the reason.

---

### Post by ventrical on 2016-05-24
> **user1397 said:**
> meh...if you think that way, you can apply that to pretty much every thread in the cafe...

I didn't mean to sound like I'm complaining...it's just something I've personally noticed (maybe it's just me?) and I was curious as to know what might be the reason.

My experience  since being a vacume tube tester apprentice at the age of 8 years old is that computers have become faster. Linux programs , especially  ones developed by canonical - ie; LXD and containers is blazingly fast. Despite the widgetry and GUI gadgetesque, ubuntu and Linux in general have become faster, not slower.

However, all things being relevant to one another, I can see where one would start off with a Windows 95 CD and think .. "wow .. is this ever fast" until after the first automatic update and  there is a sort of 'phantom effect' where it seems time is bending or slowing down somewhat. You may have found yourself working on a real simple problem , say started at 11:00pm, and then the next thing you know it is 6 O'clock in the morning and you ask yourself where the time has gone  - ie; ' boy ..time flies' right ?

  So hardware became more heavy weight, ie; like the Laundry Hamper days of Apple Desktop Towers and bigger towers for the Microsoft bent, those heavy, clumsy Dells that need a blowtorch and machine shop to bring up to swapable compatible Industry Standard Architecture. And people kept buying into it. The loftware buisness raking in trillions of dollars all for the razzle and the dazzle to keep the glorified VCR on your table working  while dust  was collecting on your CPU heat-sync.

 Well.. it's not just you.  People who have smoked cigarettes for a long time and then quit have a terrible reaction to second hand smoke. They cannot be within 100 yards of someone smoking. I have had this same reaction when I migrated over to Ubuntu. Friends and customers who still work Windows 7/ 10  call me up with malware problems. I cringe, tremble and fidget .. while I attempt to hold back telling them that windows *is* the malware problem and that their computer will never be the same. I actually get ill even working on extremely fast windows Machines. Yes.. Windows is like second hand smoke to me.

  Now .. back to topic ... what helps me is that I try to immerse myself in development version projects of ubuntu. Specifically ubuntu because it has been the fastest, leanest and most reliable operating system on the planet and this keeps my outlook fresh and therefore my enthusiasm! Enthusiasm is important.  I am by no means a psychologist but I can surmise perhaps the human mind becomes so accustomed of what to expect next within MS-Windows-bent-GUIs  (or even linux systems) that it may have a verisimilitude in that it seems slower .. that the human mind is anticipating quicker response times and they are not happening hence seemingly slower than usual and the individual user may be bored and become subconsciously complacent and there for the apps seem complacent also.

The remedy? I don't know. Like I said I immerse in ubuntu. It is always faster than I can anticipate and there is a good feeling bringing some old metal out of the attic and link it back up to the matrix :)

regards..

---

### Post by mikodo on 2016-05-24
> **user1397 said:**
> meh...if you think that way, you can apply that to pretty much every thread in the cafe...

I didn't mean to sound like I'm complaining...it's just something I've personally noticed (maybe it's just me?) and I was curious as to know what might be the reason.

I apologize.

That was mean-spirited and malicious on my part. It was uncalled for. I have no excuse.

---

### Post by user1397 on 2016-05-24
> **mikodo said:**
> I apologize.

That was mean-spirited and malicious on my part. It was uncalled for. I have no excuse.
No worries! Not a big deal at all, I didn't even think of your comment that way :)

---

### Post by vasa1 on 2016-05-24
An example of what _I_ consider bloat:```
07:26 AM ~ $ ls -lh /usr/share/icons/gnome/scalable/apps/libreoffice*.*
-rw-r--r-- 1 root root 465K Apr  8 05:02 /usr/share/icons/gnome/scalable/apps/libreoffice-base.svg
-rw-r--r-- 1 root root 1.3M Apr  8 05:02 /usr/share/icons/gnome/scalable/apps/libreoffice-calc.svg
-rw-r--r-- 1 root root 624K Apr  8 05:02 /usr/share/icons/gnome/scalable/apps/libreoffice-draw.svg
-rw-r--r-- 1 root root 550K Apr  8 05:02 /usr/share/icons/gnome/scalable/apps/libreoffice-impress.svg
-rw-r--r-- 1 root root 142K Apr  8 05:02 /usr/share/icons/gnome/scalable/apps/libreoffice-main.svg
-rw-r--r-- 1 root root 659K Apr  8 05:02 /usr/share/icons/gnome/scalable/apps/libreoffice-math.svg
-rw-r--r-- 1 root root 142K Apr  8 05:02 /usr/share/icons/gnome/scalable/apps/libreoffice-startcenter.svg
-rw-r--r-- 1 root root 534K Apr  8 05:02 /usr/share/icons/gnome/scalable/apps/libreoffice-writer.svg
07:26 AM ~ $ 
```I'm sure files of such size (and detail) are useful to someone somewhere and that's why they're installed by default for all of us. (The files are also in the corresponding hicolor folder.)

---

### Post by poorguy on 2016-05-25
I to started in the vacuum tube radio / television days of electronics and have witnessed a lot of changes in technology.

I also like seeing old computers being connected and used again and use them myself. 
I have found by matching hardware with certain Linux OS you can take old computers and make them fast. 
Ok sure they aren't going to be as fast as newer high performance hardware of today but they will run well.

I have built game computers that fly when they are new but after so long you become use to their speed and they don't seem as fast as when built. 
So now you feel that a newer faster build is needed. 
Never satisfied.

I also find that when I get back on a computer that runs Windows I notice how slow it runs and had I never started using Linux I wouldn't have ever noticed any difference and probably been quite happy.

---

