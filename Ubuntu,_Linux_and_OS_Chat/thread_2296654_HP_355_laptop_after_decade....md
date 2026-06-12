---
title: "HP 355 laptop after decade..."
date: 2015-09-27
forum: Ubuntu, Linux and OS Chat
---

### Post by craige2 on 2015-09-27
Hello guys. 

I have ordered this laptop -> [http://www.ebuyer.com/705954-hp-355-quad-core-laptop-with-ubuntu-l8b55es](http://www.ebuyer.com/705954-hp-355-quad-core-laptop-with-ubuntu-l8b55es)  I should have it in a couple of days. That would be my first laptop after 10+ years...

I was happy that I ordered it until a couple of friends gave me some warnings about it. They said, sadly the 14.04.3 is a no go option.

They strongly suggested to either keep 12.04 or install Windows on it ( I got a spare Windows licence  ). 

They said they had either of the following issues:
- The 14.04.3 and amd drivers cause some overheat ( louder )
- Unity 3D was laggy on 14.04.3
- It is a headache to make peripherals work, like touch-pad, blue tooth etc ( after the installation of 14.04.3).

They both installed Windows on it, since 12.04 LTS EoL is close. ( I'd rather not )

Does anyone else got this laptop?

Anyone with similar hardware to give me a feedback about the 14.04.3 performance with Unity 3D and GPU?

What would you suggest for graphic drivers? fglrx, fglrx-update or the xorg.amd, the ones from the site?

it's been a while since my last laptop , I got no clue how laptops are nowadays and how Ubuntu acts on laptops.

Are there specific images for Ubuntu on laptops, depending on manufacturer or specific tweaks that I should know of?


Thanks in advance guys.



P.S I know it's a limited laptop, would be used as secondary for demonstrations, presentations and some minor Netbeans and Eclipse based development.

---

### Post by ajgreeny on 2015-09-27
I note on your linked page that several owners say that they have updated either to Ubuntu 14.04 or Mint 17.1 or even CentOS and several do not appear to have had any big problem.

There is nothing in the specs that would suggest major problems are likely, but of course, there may be things that are not immediately obvious.  If you do decide to upgrade I suggest you do a clean install of Ubuntu 14.04.1, not the later point versions with their updated hardware enablement stacks that will need further updating of the hardware enablement stack again soon.

You can download that version from the "Other Images" section (scroll just over half way down) of [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads) using your nearest mirror country's site.

Watch out for UEFI when you install; all necessary details [here]("https://help.ubuntu.com/community/UEFI")

---

### Post by grahammechanical on 2015-09-27
Pardon me but I think that your friends do not know what they are talking about.

Stop and think for a moment. You are buying a computer with an OS pre-installed. You would expect it to work, as they say, right out of the box. If it doesn't then you demand your money back. The product would clearly not be fit for retail. There should be no messing around with drivers at all.

I have a computer that has a much lower hardware specifcation and it runs Ubuntu 15.10 development version with Unity 7 very well. There is no lag with Unity. And that is with only 1 GB RAM. That machine will have 4 GB RAM and a much more powerful GPU as well as a much more powerful CPU, than those in my machine. Try Ubuntu 14.04.3 from a live session. Dual boot with it before you upgrade. 

Today, even low end laptops are more powerful than high end desktops of 10 years ago.

Regards.

---

### Post by mastablasta on 2015-09-28
> **grahammechanical said:**
> 
Stop and think for a moment. You are buying a computer with an OS pre-installed. You would expect it to work, as they say, right out of the box. If it doesn't then you demand your money back. The product would clearly not be fit for retail. There should be no messing around with drivers at all.



I will then say "stop and read" :P

they mentioned that 12.04 works and laptops is preloaded with that version. we talk about 14.04 here. 

from my experience with dm1 - it came windows 7 starter preloaded but here is how Kubuntu 64bit did on it (note I believe laptop was ubuntu certified):
12.10 - perfect experience - all works out of the box.
13.04 - some minor issues - touchpad on/off button no longer works
13.10 - some FN keys no longer work, Bluetooth can not be turned off (energy drain?!)
14.04 - most Fn keys does not work. PrtSc does not register. all previous issues remain. GPU is slightly hotter, battery life has not improved at all. there are some work arround I needed to implement to get functionality that was previously available out of the box and where new and unresolved bugs were introduced.


on the other side win 7 works well, and I was told that windows 10 (should I choose to do the free upgrade) will work good as well. 


so windows stay consistent while Ubuntu get's worse and worse. Bugs are files, others have them bugs are not resolved just moved on to next kernel, next features etc. etc. I am not sure if drivers for firmware are opensourced or not and hoe they are made, but the fact is issues in previous versions were not there. then they appeared. people reported the problems but no one seem to bother to resolve them. or they don't know how.

if 16.04 is even worse I will delete the Linux partition and upgrade to windows 10 & increase the ram a bit. there is no reason to use an OS that is not supported and where developers don't think they should find the time to solve my problems. I mean obviously there should be a way to get the old drivers that were working back but no, let's go with the new and buggy ones instead.

---

### Post by night_sky2 on 2015-09-28
I've read in the comments that people report decent experiences on this laptop with Linux Mint 17.1.

 Linux Mint 17xx is built on a Ubuntu 14.04 LTS base. So if hardware recognition is good, there really shouldn't be a problem with Ubuntu 14.04 either. They are exactly the same under the hood.

But Unity is not the most lightweight of DE, so to prevent overheating issues perhaps the OP should try Xubuntu or Ubuntu MATE instead which are proven to be easier on ressources.

---

### Post by mastablasta on 2015-09-29
> **night_sky2 said:**
> 
 Linux Mint 17xx is built on a Ubuntu 14.04 LTS base. So if hardware recognition is good, there really shouldn't be a problem with Ubuntu 14.04 either. They are exactly the same under the hood..

not necessarily. Mint uses Ubuntu as base but is modified. most is same but not all. check some of the reviews and you will see that there is some stuff that doesn't work in Kubuntu for example (I think it was printer recognition via SAMBA!?! ), yet in Mint it works out of the box. 

I had similar events within Ubutnu derivatives. Fn keys for sound recognised by Xubuntu but not by Ubuntu and such.

---

### Post by Bucky Ball on 2015-09-29
You can upgrade from 12.04 LTS to 14.04 LTS via the net and directly from your current 12.04 install, leapfrogging the interim releases in between. There is no reason for a clean install.

---

