---
title: "[SOLVED] XP won't start in VirtualBox 1.62"
date: 2008-06-09
forum: Virtualisation
---

### Post by dansan on 2008-06-09
In Ubuntu Studio 7.10 I was running VirtualBox 1.54 with an XP guest with no problems, and after updating to 8.04 this didn't change until I installed the KDE4 desktop. Then VB failed to start, and, what was worse, this continued even after I changed the session back to Gnome. I didn't save that diagnostic, but searching on this forum turned up advice to remove the current, old version, download the latest one. VB still didn't start, and that diagnostic was 

"PIIX3 cannot attach drive to the Secondary Master.
VBox status code: -102 (VERR_FILE_NOT_FOUND)."
 
and I found a post saying the writer had cured this by creating a new machine and attaching his vdi to it. So I tried that. Now VB 1.62 starts without a hitch, but XP flashes a blue screen while loading and aborts into the "We apologize for any inconvenience" screen. There is text on the blue screen, shown in the attached snapshot. 

Does this mean my vdi is whacked? Or is there some way to fix it?

Daniel

---

### Post by cdaringe on 2008-06-09
i'll be honest, i have no idea.  does it behave similarly when run as root?

---

### Post by Ubeaut on 2008-06-10
There's a change to the default machine settings in VB 1.6.2.  Try going into your newly created machine settings and look for General>Advanced>IDE Controller Type.

It's probably set by default at PIIX4.  Change it to PIIX3, which was the default when you created your vdi disk in a previous version.  Now try starting the machine again and it may be able to read your disk.

---

### Post by dansan on 2008-06-10
Hey, Ubeaut, 

This is the quickest fix I've ever done in Ubuntu. Nice call!

XP started without protest, and I am writing this reply from there.  Saved my bacon because I use VB for text dictation (DNS 9.5), which I do nearly all day, every day.

---

### Post by himagain on 2008-06-14
Hey Dansan,
I'm TRYING to get going with Dragon9.5 in VBox too! 
Running Kubuntu 8.0 as Server with VBox holding XPPro.  
I have not been able to get sound in Kubuntu, much less inVBox. 

My problem isn't hardware and no problem in Windoze with sound. 
It is SOMETHING in my install of Kubuntu/VBox. 

Any hints mightily appreciated.

BTW: what mic system are you using? 
I'm just going "mobile" and bought a Sony Digital Recorder on the advice of a very happy with his,  writer friend.

---

### Post by dansan on 2008-06-22
> **himagain said:**
> Hey Dansan,
I'm TRYING to get going with Dragon9.5 in VBox too! 
Running Kubuntu 8.0 as Server with VBox holding XPPro.  
I have not been able to get sound in Kubuntu, much less inVBox.

I have no experience getting sound to work inside Kubuntu, but you can read about the little I know about giving sound to work inside Ubuntu [here]("http://ubuntuforums.org/showthread.php?t=713132"). I hope this helps you.

> **himagain said:**
> BTW: what mic system are you using? 


Plantronics CS/60 or an old GNetComm wired mic. I think any quality mic will perform well in the Ubuntu VBox setup.

---

