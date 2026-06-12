---
title: "Guild Wars + Wine 1.1.31 crashes after login screen."
date: 2009-10-16
forum: Wine
---

### Post by willrockformilk on 2009-10-16
Hey everyone!

My first time post. Ive searched far and wide for this answer and cant seem to come up with an answer for it. 

So here is some info for you:

**Ubuntu Version**: Jaunty 9.04
**Wine Version**: 1.1.31
**vid card**: ATI Radeon HD 3200 yeah the integrated one. my vid card was DOA :(
**Video Drivers**: in windows we called ati drivers catalyst drivers but i believe on ubuntu the proprietary driver is called fglrx? Could someone explain why?
**Game**: Guild Wars


I have tried installing from both wine and PlayonLinux with both yield unique sets of problems.

When i execute it from PlayonLinux it seems to start up. The music starts playing and everything. It just is not on the desktop or anywhere else i can find. Tried alt-tab and ctrl-alt-arrows to move desktops to it. 

When i execute from wine i get to the login screen and everything is working great. When i type in my login information and attempt to move to the next screen, the video seems to reset and i get horizontal lines across my screen. 

It could be some sort of a video problem. 

Anyone have any ideas on what it could be?

---

### Post by asdfoo on 2009-10-16
> **willrockformilk said:**
> Hey everyone!

My first time post. Ive searched far and wide for this answer and cant seem to come up with an answer for it. 

So here is some info for you:

**Ubuntu Version**: Jaunty 9.04
**Wine Version**: 1.1.31
**vid card**: ATI Radeon HD 3200 yeah the integrated one. my vid card was DOA :(
**Video Drivers**: in windows we called ati drivers catalyst drivers but i believe on ubuntu the proprietary driver is called fglrx? Could someone explain why?
**Game**: Guild Wars


Ask ATI?  That's what they decided to call it.

> 

I have tried installing from both wine and PlayonLinux with both yield unique sets of problems.

When i execute it from PlayonLinux it seems to start up. The music starts playing and everything. It just is not on the desktop or anywhere else i can find. Tried alt-tab and ctrl-alt-arrows to move desktops to it. 

When i execute from wine i get to the login screen and everything is working great. When i type in my login information and attempt to move to the next screen, the video seems to reset and i get horizontal lines across my screen. 

It could be some sort of a video problem. 

Anyone have any ideas on what it could be?

if you have horizontal lines across the screen, it sounds like a familiar problem with ati's drivers, some sort of corruption.   check to see if there is a newer version that supports your card.

---

### Post by willrockformilk on 2009-10-16
[LEFT]Dont ask why but for some reason running a wine desktop in windowed mode made it start acting properly. Dunno what the deal is. I bet it is a ATI driver problem.
[/LEFT]

---

