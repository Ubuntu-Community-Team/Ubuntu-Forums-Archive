---
title: "Will it run fast enough?"
date: 2010-01-27
forum: Virtualisation
---

### Post by MindFusion on 2010-01-27
Hi guys, 

I have a 4 GIG RAM, Nvida 8200 M, 2.1 Ghz dual core AMD x64 processor laptop, which has dual boot vista and ubuntu 9.10 on it.

I've dual booted the system because i found there aren't any good video editting software available for ubuntu, but recently i've seen some awesome stuff at a friend of mine, who can run windows 7 with no sweat on his ubuntu, really smoothly.

But... my system crashed a day ago when i plugged in a camera (on Vista), and i'm tired of this nonsense, so i'd like to solely partition it to Ubuntu only.

The question rather is, (i have the vista install cd), if i download virtual box for my ubuntu and install windows and install adobe ulead video editting software, will it run smoothly with my hardware specs or will it go slowly?

---

### Post by howefield on 2010-01-27
You should be golden with that setup.

You might need to experiment to get the right amount of RAM for the guest and you needs, but your hardware should cope fine.

---

### Post by MindFusion on 2010-01-27
Also a small question: if i install windows in virtualbox, do i need to install drivers for that windows inside the virtualbox as well?

This is because instead of vista i'd like to put windows xp (to me still much more reliable) in the virtualbox, but i didn't keep it on my laptop originally because HP (the manufacterer of my laptop) didn't provide any drivers for my built-in wifi, so i couldn't access the internet with xp installed...

---

### Post by howefield on 2010-01-27
> **MindFusion said:**
> if i install windows in virtualbox, do i need to install drivers for that windows inside the virtualbox as well?

No you won't, virtualised guests use virtual drivers supplied by Virtualbox.

Once you have installed XP, you will want to install guest additions, which will provide improved drivers to give you better screen resolutions, non capture of mouse and a variety of other benefits.

You wireless will be fine, if it is working in the host, it'll work in the guest.

---

### Post by MindFusion on 2010-01-27
Do you have to have a legal version?

---

### Post by howefield on 2010-01-27
What kind of answer are you expecting ?

Of course you do. You wouldn't want to run software you didn't have a right to, would you ?

---

### Post by chrisinspace on 2010-01-27
Your rig will have no problem running a single virtualized copy of XP.  I'm running Server 2008, Server 2003, and a couple copies of Ubuntu at the same time with less specs than that. Like howefield said, you might have to adjust how much RAM you give the VM, especially if you want to run video editing software.

Windows licensing works exactly the same in the virtual environment as it does on a physical box.  If you don't have a key, you're going to have to crack it and then you run into the same legal and reliability issues you would if you tried to install a pirated copy on a regular PC.  I wouldn't recommend it.  If you look around, you can still find some decent pricing on a legal copy.

---

### Post by MindFusion on 2010-01-27
Hey, I wasn't suggesting I'd use pirated software. It was just a question.

---

### Post by Capt. Blackwood on 2010-01-27
Regardless of legal or illegal. The physical set up looks good. As long as you do nothing too hardcore, i.e. Half-Life 2 or above. you should be good.

---

### Post by MindFusion on 2010-01-28
Oh crap, Half-life 2 was one of the games i was planning to run:p 

This does not go well you say?

---

### Post by Old_Grey_Wolf on 2010-01-31
Install VirtualBox on your Ubuntu partition and try it out. 

I have Vista running in VirtualBox on a laptop computer with a 1.7 GHz dual core processor with 4 GB of RAM. It works fine; however, I'm not a gamer. I reserve 1 GB of RAM for Ubuntu and the rest goes to Vista. If I have have Ubuntu 32-bit then Vista gets 2 to 2.5 GB and Ubuntu 1 GB of RAM. If I have Ubuntu 64-bit then Vista gets 3 GB and Ubuntu 1 GB of RAM. 

I use a CPU temperature monitoring application when running Vista in VirtualBox on my laptop. Vista does use a lot of resources, and the CPU does run hotter.

---

### Post by Telecaster72 on 2010-02-02
Mindfusion, technically speaking it is no problem to install a cracked XP, legally ofcourse is a different question.
Microsoft wouldnt be as dominant and widespread as they are if it wasn't for all those pirate copies of XP floating around  anyway....

---

### Post by MindFusion on 2010-02-03
I never said i'd do it in an illegal way - i think you guys got me wrong here ... i just wondered if virtualbox required you to install a legit copy ...

---

### Post by andrea000 on 2010-02-05
Yes it should with 4GB of ram.I run autocad 2008
on vbox with 2 GB going to ubuntu and 2GB going
to xp and they both run great so just try it out.

---

### Post by tipiglen on 2010-02-05
Andrea,  100% Microsoft-free?  except virtually, I guess
;-)

A friend sent me an xp iso (as a file) and it works fine in VB - won't update, though...

---

### Post by andrea000 on 2010-02-22
100% Microsoft-free at home i use vbox on linux at work only
long story there i can't get a legal copy of autocad for home
use and i don't have a need to.

---

