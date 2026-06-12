---
title: "Suggestion: Self-burning iso"
date: 2007-01-16
forum: The Cafe
---

### Post by mushroom on 2007-01-16
This is a suggestion for Ubuntu to include on the download page a program for Windows that is essentially a "wrapper" for the iso that burns it to a CD for the user (hooray for run-ons). It solves the problem of "so...what do I do with this file?" Here is a mockup I did in Glade (obviously it would look different on Windows):

This would be the startup window:
[IMG]http://img.photobucket.com/albums/v331/mushroomadvance/ub1.png[/IMG]

The actual burning:
[IMG]http://img.photobucket.com/albums/v331/mushroomadvance/ub4.png[/IMG]

When "Cancel" is clicked:
[IMG]http://img.photobucket.com/albums/v331/mushroomadvance/ub3.png[/IMG]

After burn:
[IMG]http://img.photobucket.com/albums/v331/mushroomadvance/ub2.png[/IMG]

Would this be in any way feasible?

---

### Post by PriceChild on 2007-01-16
[https://wiki.ubuntu.com/install.exe/Prototype](https://wiki.ubuntu.com/install.exe/Prototype)

---

### Post by mushroom on 2007-01-16
Hey, cool. Any chance of that becoming standard in the future?

---

### Post by Brunellus on 2007-01-16
> **mushroom said:**
> Hey, cool. Any chance of that becoming standard in the future?
I hope not.  an install.exe will trigger the howls of thousands of manual-resistant windows users who unwittingly hosed their Windows installs by not thinking that they were installing a whole new OS.

---

### Post by mushroom on 2007-01-16
I would think they would know what they were installing if they downloaded it.

---

### Post by Brunellus on 2007-01-16
> **mushroom said:**
> I would think they would know what they were installing if they downloaded it.
that's not a guarantee.  

The sheer number of people who fail to grasp what an operating system is and what installing an operating system might entail will surprise you.  If it's one thing I've learned, it's never to assume that the operator of any computer is wholly competent.

---

### Post by mushroom on 2007-01-16
But it's not like having to burn an iso really changes that. Plus, this is supposed to preserve the Windows install, and is supposed to be easily removed.

---

### Post by Brunellus on 2007-01-16
> **mushroom said:**
> But it's not like having to burn an iso really changes that. Plus, this is supposed to preserve the Windows install, and is supposed to be easily removed.
I'll believe it when I see it.  I still forsee Windows users posting to these forums irately demanding that we fix their broken windows.

---

### Post by rai4shu2 on 2007-01-16
The main problem will be using the Windows bootloader to load GRUB. Lots of systems probably won't support that.

---

### Post by mushroom on 2007-01-16
> I'll believe it when I see it. I still forsee Windows users posting to these forums irately demanding that we fix their broken windows.

But how would this installer exacerbate the situation? If anything, it would make it better.

---

### Post by Brunellus on 2007-01-16
> **mushroom said:**
> But how would this installer exacerbate the situation? If anything, it would make it better.
Giving Windows users an INSTALL.EXE makes them think:  "Oh.  that Ubuntu thing.  what a great Windows program!"

At the moment, it's hard enough getting people to understand that Linux is not windows.  Having Ubuntu installable directly from Windows blurs the distinction even more.  

I guess my main concern/complaint is that this sort of thing raises unrealistic expectations.

---

### Post by G Morgan on 2007-01-16
That is highly different to a self contained disc burner/image though. What he wanted was the equivalent of a self extracting archive, the details of extraction are handled in the executable rather than by a 3rd party program. It is certainly doable but it probably won't happen because it would only work in Windows while an ISO is generic. It would only take about 5 minutes to set it up with the correct software though.

---

### Post by maniacmusician on 2007-01-16
yeah I agree. People dont need to be super technical to learn how to use Linux, but they should at least be able to burn an ISO; at least with the help of a guide (which they can easily find if they try and search for it). Making installation easy for users is one thing...but this goes a little too far.

---

### Post by G Morgan on 2007-01-16
> **maniacmusician said:**
> yeah I agree. People dont need to be super technical to learn how to use Linux, but they should at least be able to burn an ISO; at least with the help of a guide (which they can easily find if they try and search for it). Making installation easy for users is one thing...but this goes a little too far.

They may not necessarily have the software needed.

---

### Post by mushroom on 2007-01-16
Obviously you'll have to learn to use Linux, but I see not implementing something like this out of some disdain for the non-computer literate is deliberately making things harder than they have to be. ISOs are trivial to most of us, but remember Ubuntu's audience.

---

### Post by maniacmusician on 2007-01-16
> **G Morgan said:**
> They may not necessarily have the software needed.

[http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu) -> in the "Burning a CD" section, advisory on free software is given.

> **mushroom said:**
> Obviously you'll have to learn to use Linux, but I see not implementing something like this out of some disdain for the non-computer literate is deliberately making things harder than they have to be. ISOs are trivial to most of us, but remember Ubuntu's audience.

It's not purposely making it harder, it's refraining from making it too easy. If people are too lazy to google for how to burn an ISO, they they'll never have the motivation to tackle the learning curve Linux has.

---

### Post by FuturePilot on 2007-01-16
> **Brunellus said:**
> Giving Windows users an INSTALL.EXE makes them think:  "Oh.  that Ubuntu thing.  what a great Windows program!"

At the moment, it's hard enough getting people to understand that Linux is not windows.  Having Ubuntu installable directly from Windows blurs the distinction even more.  

I guess my main concern/complaint is that this sort of thing raises unrealistic expectations.
Yeah, I sometimes get the classic "Linux? Is that Windows?":p 
I think having an Install.exe takes all the fun out of the process. For me waiting for that 700MB ISO to download gets me excited and I can't wait till it finishes and I get it burned to a CD. It's fun:mrgreen:

---

### Post by banjobacon on 2007-01-17
> **maniacmusician said:**
> [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu) -> in the "Burning a CD" section, advisory on free software is given.

That guide requires people download two applications in addition to the Ubuntu file (you don't really need to download md5summer, but the guide suggests you do). Should that really be necessary? 

Arguing that this is a bad idea because it will lead to ignorant users hosing their systems is pretty far-fetched. The .exe file would burn a CD, not install Ubuntu. If the program were limited to only burn Live CDs, the system is in no more danger than usual.

---

### Post by maniacmusician on 2007-01-17
> **banjobacon said:**
> That guide requires people download two applications in addition to the Ubuntu file (you don't really need to download md5summer, but the guide suggests you do). Should that really be necessary? 

Arguing that this is a bad idea because it will lead to ignorant users hosing their systems is pretty far-fetched. The .exe file would burn a CD, not install Ubuntu. If the program were limited to only burn Live CDs, the system is in no more danger than usual.

I don't think it'll lead to people hosing their system (or at least that doesn't concern me), but I'm kind of worried if people aren't willing to install two extra apps to burn an ISO. It's not that difficult. Quite honestly, I think we've got way more important things to focus on. We get a steady influx of new users already. Our best bet now is to 1. educate them 2. Improve the OS itself.

Of course, that is just my opinion.

---

### Post by jdhore on 2007-01-17
i really don't like this whole install.exe/self-burning iso idea...i think having the technological knowledge to burn an ISO makes for a good prerequisite for Linux...simply, if you can't burn an ISO, you don't have the knowledge to run Linux

---

### Post by maniacmusician on 2007-01-17
> **jdhore said:**
> i really don't like this whole install.exe/self-burning iso idea...i think having the technological knowledge to burn an ISO makes for a good prerequisite for Linux...simply, if you can't burn an ISO, you don't have the knowledge to run Linux
it's not so much that you wouldn't have the knowledge, but more that you wouldn't have the capacity to adjust to the learning curve. People can come to Linux with no knowledge, and still learn to use it. Similarly, they can learn to burn an ISO (which is a hell of a lot easier)

---

### Post by jdhore on 2007-01-17
> **maniacmusician said:**
> it's not so much that you wouldn't have the knowledge, but more that you wouldn't have the capacity to adjust to the learning curve. People can come to Linux with no knowledge, and still learn to use it. Similarly, they can learn to burn an ISO (which is a hell of a lot easier)

true, true, but that's exactly what i'm saying...you have to be willing to work a little bit on your OS to run Linux...if you're not at least willing to burn or learn how to burn an ISO, you shouldn't run linux cuz you'll come to the point where you want to have everything just handed to you and not have to work at all

---

### Post by Mathiasdm on 2007-01-17
> **jdhore said:**
> i really don't like this whole install.exe/self-burning iso idea...i think having the technological knowledge to burn an ISO makes for a good prerequisite for Linux...simply, if you can't burn an ISO, you don't have the knowledge to run Linux
I totally disagree.

Anyone who can run Windows, can run Linux.

However, people that can't burn an ISO, will probably not be able to set up Linux (which is a different thing).

That's why there should be an option to (in Windows) press 'Uninstall'.

Linux is about choice, right? Why not leave people the choice to install any possible way?

---

### Post by mushroom on 2007-01-17
If you really think that users should have to download an extra program in addition to the 600+ MB iso just to stick it to them, why not just advertise that on the download page? "If you can't burn this iso, you're too stupid to use Ubuntu." This isn't only a matter of making it easier to new users, it's a matter of making it easier *period*. To install this OS, no one should have to install an extra program just to do so. If we have the means to accomplish this, why not? Not only would Ubuntu be easier to install, but it would bring an end to all those "I burned the file to a disc, but it didn't boot" problems because they didn't know simply burning the file wouldn't work. This is a self-contained program that would do it for them.

This wouldn't be hand-holding, this wouldn't be intrusive, and it wouldn't make Ubuntu any more intimidating. It would make it more convenient. I don't see why anyone would think this is a bad idea (not tooting my own horn, someone thought of it before I did).

---

### Post by maniacmusician on 2007-01-17
well in truth, if you **have** a CD burner, you should already have a CD burning program installed. Anyways, like I said before, there's a lot of more important things to be focusing on, things that are actually real deterrants.

---

### Post by mushroom on 2007-01-17
They have a CD burning program because it probably came with the computer. The average user probably has never used it for an iso. And what's this about "focus"? It's not like there's a group of people at Canonical whose job is to finish one feature at a time. If that were so, nothing would ever get done.

---

### Post by Randomskk on 2007-01-17
Right, but that's somewhat like saying "don't work on making X pretty work on getting the kernel stable" - two different teams of people.

It's a nice idea, I think. Not having to find and download a suitable program makes installing Ubuntu when on a fresh windows install quicker anyway, even if you do know how to do it.

At the same time, of course, you are effectively writing your own ISO burning program under windows - perhaps a bit of a stretch for a Linux OS.

Perhaps a quick link on the downloads page to a good ISO burner and a link to a brief guide on using it would suit everyone?

edit: mushroom, didn't see your post in time: exactly, I agree.

---

