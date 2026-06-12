---
title: "Internet Works in Ubuntu, not in Vista"
date: 2009-07-12
forum: The Cafe
---

### Post by iampriteshdesai on 2009-07-12
In Vista my internet has stopped working. I tried the network manager, etc. I tried trouble shooting, but it tells me to turn off my modem for 10 sec and turn it back again. I tried that, but it isn't working.
I get a prompt to install drivers for my PCI modem (internal)
Now I have the cd of the drivers and I used it in Vista to install them, but I get an error saying code:10
the device is stopped.
Few days ago, when internet was not working in Vista I tried the Ubuntu Live CDS and internet worked in it. Ithen I logged into Vista and internet worked even there.
But the same modem/PCI works with Ubuntu, which I installed today,flawlessly .  What can I do? Except reinstalling vista?

Is there any way to find out which version PCI card I am using?

---

### Post by stwschool on 2009-07-12
Have you tried using your ubuntu install to grab the latest vista driver from the manufacturer's website? It may well be a vista reinstall though if the driver's not working.

---

### Post by lisati on 2009-07-12
> **stwschool said:**
> Have you tried using your ubuntu install to grab the latest vista driver from the manufacturer's website? It may well be a vista reinstall though if the driver's not working.

+1: I noticed a similar "flakiness" with Vista recently - the installer for the software for my near-new phone crashed when I first tried it. After a fresh install of Vista, the installer worked, but the other day, the drivers "went south", and the installer crashed again. I suspect that one or more of the updates to Vista might have messed something up somewhere. (I eventually fixed it by uninstalling the drivers via the Vista device manager, plugging the phone in, and directing Vista to the relevant folder on the CD when it detected the "new" hardware)

---

### Post by Swarms on 2009-07-12
Reinstall of vista sounds like the way to go.

---

### Post by iampriteshdesai on 2009-07-12
> **Swarms said:**
> Reinstall of vista sounds like the way to go.
I have installed Ubuntu via Wubi, so I dont want to reinstall Vista... it'd take 5 hrs to do so :(

---

### Post by SuperSonic4 on 2009-07-12
Perhaps now is the time to do a full install of ubuntu ;). A broken vista would be an excellent reason to set up the drive the way you want it instead of the way Microsoft wants it :p
Remember that if you build a top range attack on top of a rickety house then the attic will be wrecked when the house collapses.

I'd imagine it is a firmware thing though - I noticed when I was on vista a couple of days ago there was an nvidia network controller update which I chose to ignore

---

### Post by iampriteshdesai on 2009-07-12
> **SuperSonic4 said:**
> Perhaps now is the time to do a full install of ubuntu ;). A broken vista would be an excellent reason to set up the drive the way you want it instead of the way Microsoft wants it :p
Remember that if you build a top range attack on top of a rickety house then the attic will be wrecked when the house collapses.

I'd imagine it is a firmware thing though - I noticed when I was on vista a couple of days ago there was an nvidia network controller update which I chose to ignore
;)
No thanks, I need and like using Vista as I like Ubuntu... 
I tried partioning once and don't want to do it again..
how can I find the PCI card that I use   in Ubuntu?

---

### Post by SuperSonic4 on 2009-07-12
> **iampriteshdesai said:**
> ;)
No thanks, I need and like using Vista as I like Ubuntu... 
I tried partioning once and don't want to do it again..
how can I find the PCI card that I use   in Ubuntu?

Fair enough :), it was partially in jest anyway XD

To find out a list of PCI cards in ubuntu type in ```
lspci | grep network
``` in a terminal. I don't know how it will work with a wubi install though. I believe vista can do it through device manager

---

### Post by sdowney717 on 2009-07-12
if you have enough memory, you can use ubuntu and do virtual machine of vista using vmware server or virtualbox.
A VM puts the entire guest OS into a single file.

---

### Post by iampriteshdesai on 2009-07-12
> **sdowney717 said:**
> if you have enough memory, you can use ubuntu and do virtual machine of vista using vmware server or virtualbox.
A VM puts the entire guest OS into a single file.
Why try that, when I can boot into windows in 2 min?

---

### Post by lisati on 2009-07-12
> **iampriteshdesai said:**
> 
Is there any way to find out which version PCI card I am using?

from a terminal (Applications->Accessories->Terminal) you can type in  ```
lspci
```
This will list PCI devices that Ubuntu recognizes in your system.

---

### Post by SunnyRabbiera on 2009-07-12
> **iampriteshdesai said:**
> Why try that, when I can boot into windows in 2 min?

Its something worth trying.
In any case I think this shows how good linux has become with hardware as of late.
Linux's hardware detection is much better then people in the commercial world give it credit for.

---

### Post by iampriteshdesai on 2009-07-12
> **lisati said:**
> from a terminal (Applications->Accessories->Terminal) you can type in  ```
lspci
```
This will list PCI devices that Ubuntu recognizes in your system.
I need drivers for this thing:
VT8237/VX700 PCI Bridge, Inc VT8237/VX700 PCI Bridge

where can I find it?

---

### Post by sdowney717 on 2009-07-12
for the sheer fun of doing it.;

---

### Post by iampriteshdesai on 2009-07-12
> **sdowney717 said:**
> for the sheer fun of doing it.;
there are other ways of having fun, you see ;)

---

### Post by sdowney717 on 2009-07-12
ok, one advantage of a VM is that the guest OS will see a very standardized hardware layout. The Host OS takes care of the hardware directly, the guest OS just sees the hardware that was programmed into the app virtualbox or Vmware. SO, this means it is more likely to work, you wont need to find drivers for your hardware. Vista will likely just work.

---

### Post by jskandhari on 2009-07-12
It is basically IPv4/IPv6 conflict if it is still not working on your Vista many modem/wireless routers tend to give problem try providing the IP address mannually and it should work fine... and to find the setting for Ip add use connection information in the network applet in ubuntu.

---

### Post by Flying caveman on 2009-07-12
> **iampriteshdesai said:**
> Why try that, when I can boot into windows in 2 min?

So you can use Vista with your wireless working.

---

### Post by Skrean on 2009-07-12
I got a similar problem with the Win Vista when I had just acquired my Dell Laptop.

It came preloaded with vista but wouldn't go online. 

It said connection local only, i.e, no internet.
 I tried everything that the network support team suggested.. did not work. I tried reinstalling a new version of the driver for the network card..did not work.

I thought that as Vista has an issue with certain hardware downgrading to windows XP would have done the job...did not work either.

However, when I tried with my Ubuntu Hardy Live CD... Lo And Behold..Internet Works.

I wiped out the entire Hard Disk and Installed Ubuntu.


However, the problem was that there was an issue with the laptop Motherboard that had to be replaced later on. Only Ubuntu was good at bypassing the hardware problem to make my computer usable!

Hope this helps in your search of a solution!

---

### Post by monsterstack on 2009-07-12
Don't listen to the haters. Yeah it has a few problems, and most people see Windows as an OS for geeks and hobbyists, but that's all starting to change. I predict that pretty soon it'll be an operating system that normal people can use, so long as the hardware bugs are ironed out and it gets a bit more professional software. 2010 will be the year of Windows on the desktop. :)

---

### Post by arcdrag on 2009-07-12
Similar issue for me, my HP printer doesn't work in Vista or XP, but works without ever having to do a thing in Ubuntu.  

I hate looking for drivers, and only use my Windows partition for gaming anyway, so its not that big of a deal to me.

---

### Post by Skrean on 2009-07-13
> **monsterstack said:**
> Don't listen to the haters. Yeah it has a few problems, and most people see Windows as an OS for geeks and hobbyists, but that's all starting to change. I predict that pretty soon it'll be an operating system that normal people can use, so long as the hardware bugs are ironed out and it gets a bit more professional software. 2010 will be the year of Windows on the desktop. :)

Using Ubuntu doesn't necessarily mean hating windows. I have a dual boot win/ubuntu system...However Ubuntu gave me much more liberty to do things with a computer than Windows XP or Windows Vista did and helped me to solve my problem when I had one and I should acknowledge that.

Windows has its uses as well as Ubuntu and I do not think using Ubuntu comes with dumping Windows as a prerequisite!

---

### Post by iampriteshdesai on 2009-07-13
> **Skrean said:**
> I got a similar problem with the Win Vista when I had just acquired my Dell Laptop.

It came preloaded with vista but wouldn't go online. 

It said connection local only, i.e, no internet.
 I tried everything that the network support team suggested.. did not work. I tried reinstalling a new version of the driver for the network card..did not work.

I thought that as Vista has an issue with certain hardware downgrading to windows XP would have done the job...did not work either.

However, when I tried with my Ubuntu Hardy Live CD... Lo And Behold..Internet Works.

I wiped out the entire Hard Disk and Installed Ubuntu.


However, the problem was that there was an issue with the laptop Motherboard that had to be replaced later on. Only Ubuntu was good at bypassing the hardware problem to make my computer usable!

Hope this helps in your search of a solution!

I tried the device manager and deleted drivers for my ethernet card..
vista scanned and installed them automatically and now internet works :)
Thankyou to all of you for helping!
Ubuntu Forums is the Best!
even for Vista problems... hahaha

):P

---

