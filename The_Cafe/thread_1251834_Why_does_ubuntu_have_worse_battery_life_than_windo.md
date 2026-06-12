---
title: "Why does ubuntu have worse battery life than windows?"
date: 2009-08-28
forum: The Cafe
---

### Post by Sashin on 2009-08-28
Why is it that to have acceptable battery life on Ubuntu you have to sacrifice alot of basic functionality? like CD rom polling, does anyone know of a way to get life comparable to windows without much sacrifice?

At the moment this is the biggest flaw in my experience with it on my new laptop. Other than that everything is perfectly smooth, like on my desktop.

---

### Post by the.dark.lord on 2009-08-28
I must say the battery works better than on Windows on my laptop.

---

### Post by Sashin on 2009-08-28
Did you have to tweak it somehow, if so tell me?

---

### Post by kpkeerthi on 2009-08-28
powertop might help save a bit.

---

### Post by the.dark.lord on 2009-08-28
> **Sashin said:**
> Did you have to tweak it somehow, if so tell me?

No. I use 64 bit, perhaps that makes a difference.

---

### Post by binbash on 2009-08-28
Play with laptop-mode configuration files. I am getting same battery life with Windows 7 / Vista after configuring them. However, at Ubuntu Karmic there is a USB auto suspend bug so if you are using Karmic do not enable USB auto suspend thing.

---

### Post by Paqman on 2009-08-28
What version of Windows, and are you running Compiz?

---

### Post by ssam on 2009-08-28
depends strongly on hardware. some devices don't have good powersaving modes in their linux drivers.

when the drivers are good linux can be better than windows
[http://www.networkworld.com/research/2008/060908-green-windows-linux.html?page=1](http://www.networkworld.com/research/2008/060908-green-windows-linux.html?page=1)

lots of work is being done to make linux better. [http://lwn.net/Articles/345007/](http://lwn.net/Articles/345007/)

---

### Post by Gen2ly on 2009-08-28
Not to be glum here but Linux is still primarily developed for servers.  Powersaving came late in the game and still has a way to go in Linux, there are guides around that can get you to near efficiency that Windows has if you're willing to put in the time and effort (though my google-fu isn't so good at the moment).

---

### Post by Johnsie on 2009-08-28
Ubuntu runs very hot on my netbook and has less run time than Windows 7. I also prefer the power managment tool on Windows 7 as it is quite well organised and seems to give me even more usage time.

I don't really want to be playing around with config files and I certainly don't want my netbook overheating because of some setting I got wrong.

---

### Post by Sashin on 2009-08-28
I use 64-bit, as well as compiz. I'm not sure about where the configuration files are let alone how to edit them, and I've tried powertop and done some of the things that don't involve sacrifice.

---

### Post by Skripka on 2009-08-28
I cannot recall off the top of my head, but does Ubuntu include a CPU throttler by default?  That could easily do it.

---

### Post by darthmob on 2009-08-28
> **Skripka said:**
> I cannot recall off the top of my head, but does Ubuntu include a CPU throttler by default?  That could easily do it.It depends on the hardware. It throttles the CPU on my notebook but it still has more than half an hour less runtime on linux than on windows.

---

### Post by shiva.n on 2009-08-28
I have tried tweaking the laptop-mode, and also tried out powertop suggestions, and still my battery time is less than an hour on DELL Inspiron 6400, whereas it used to be about 2.5 hours on Windows XP.
 
Until the battery life issue is resolved there will be no penetration into the laptop/netbook market.
 
Has anyone had these complaints on any of the netbooks that come preloaded? Is this issue only with Ubuntu and not other flavors of Linux?
 
<Edit> And I used to used to be on GNOME with compiz, but now am on Openbox with only very little improvement</Edit>

---

### Post by Skripka on 2009-08-28
> **darthmob said:**
> It depends on the hardware. It throttles the CPU on my notebook but it still has more than half an hour less runtime on linux than on windows.

Which CPU throttle, and how is it set?

AMD-Powernow has 3 or 4 levels to determine what causes the CPU to clock back up, you can also set how low the CPU underclocks.  Intel, I don't know about.

---

### Post by Tristam Green on 2009-08-28
> **johnsie said:**
> ubuntu runs very hot on my netbook and has less run time than windows 7. I also prefer the power managment tool on windows 7 as it is quite well organised and seems to give me even more usage time.

I don't really want to be playing around with config files and i certainly don't want my netbook overheating because of some setting i got wrong.

+6

---

### Post by Skripka on 2009-08-28
> **shiva.n said:**
> I have tried tweaking the laptop-mode, and also tried out powertop suggestions, and still my battery time is less than an hour on DELL Inspiron 6400, whereas it used to be about 2.5 hours on Windows XP.
 

Batteries don't last forever.  It sounds like yours is nearing EOL.  Usually those critters don't last more than a few years--there's a reason batteries are on a separate 90-day warranty from the computer itself.

---

### Post by ssam on 2009-08-28
> **Skripka said:**
> Which CPU throttle, and how is it set?

AMD-Powernow has 3 or 4 levels to determine what causes the CPU to clock back up, you can also set how low the CPU underclocks.  Intel, I don't know about.

CPU speed is automatically adjusted by the kernel using the ondemand governor by default. this run the processor at full speed when needed and low speed when idle.

this will save power compared to limiting the speed, because the fast you get a task done, the sooner you can drop into a lowpower idle mode.

if you have anything that keeps waking the CPU, then it will drain a lot of power. the powertop utility can track down these.

---

### Post by bailout on 2009-08-28
On my Acer netbook the installed linpus os gives much better battery life and cooler running than Ubunutu despite being based on the relatively old redhat 8.

---

### Post by RiceMonster on 2009-08-28
My laptop gets the same battery life with both Fedora 11 and Windows Vista

---

### Post by shiva.n on 2009-08-28
> **Skripka said:**
> Batteries don't last forever.  It sounds like yours is nearing EOL.  Usually those critters don't last more than a few years--there's a reason batteries are on a separate 90-day warranty from the computer itself.

Good point. Battery woes and Skype with pulseaudio have been my only negative experiences with Ubuntu. Might have to try new batteries and Skype2.1 this weekend...

---

