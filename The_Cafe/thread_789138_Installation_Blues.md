---
title: "Installation Blues"
date: 2008-05-10
forum: The Cafe
---

### Post by kevinl on 2008-05-10
Dear Folks
I have installed a lot of Linux distros since 1997.  One thing often in common, with all of them, is difficulty with the video drivers which often cause the installation to crash.  I have just bought a VIA EPIA-EX board I'm experimenting with, and all versions of Ubuntu do not install; even the latest 8.xx ... but you can get Mandriva working with it so it is possible.  Soon after booting from the CD, electing the language and then selecting "Install Ubuntu", the screen goes black and that's effectively the end of the installation. You can install if you know how to drop down to the command line and then later download and install the Open Chrome or Proprietary Driver but that is a bit much to expect of a newbie and there is nothing anywhere in the installation screens to suggest following that course of action.  

As a constructive suggestion, I think it would be a good idea for the installation program to go all the way through using the most standard video possible, ie, the setting used on the banner screen.  At the end, the installation should try a video driver that it thinks is suitable for the detected hardware but with the requirement for the user to confirm it is OK.  If no response is received after, say 5 seconds, it reverts back to the same video display settings it started with in the banner screen and the user can try again.  Additionally, should the user be having trouble, ie, the user has rejected settings twice, the install should have a section or prompt explaining, in as simple terms as possible, how a newbie can install a new video driver.  All this would be very helpful for newbies.  Another approach is for there to be a set of drop-downs with the names of major makers and having made all of the selections, the program could check of an Internet connection and, if one exists, take the user to the correct place on the Internet to allow them to download the latest appropriate driver.  In this manner we avoid the hassles with licences and currency of drivers.  We need to encourage as many people as possible to participate in this great work - not unnecessarily create difficulties for them and frighten them away.  Comments anyone?
KevL:)

---

### Post by shanemanut on 2008-05-11
Could someone go through the process of how to drop down to the command line and then later download and install the Open Chrome or Proprietary Driver?  I am having this issue and cannot figure out how to install ubuntu from the black screen I am currently getting.  I previously ran Wubi on v.7.04 but have uninstalled that to do a new install of v8.04 without Wubi this time.  Is my best bet to use Wubi and install since I did get a display using that before?  Thank you for the help.

---

### Post by elvar92 on 2008-05-11
Hi! I'm new to Ubuntu and just installed it via Wubi. Now, I just rebooted my laptop after installing Ubuntu, chose Ubuntu on the boot screen and waited. Pretty soon I got the Ubuntu logo and a loading bar. After it finished loading, I just got a black screen. At first I just thought Ubuntu was loading or something but now I have waited for about an hour and nothing happens. What should I do? I'm afraid to turn my laptop off as I have read that it is dangerous.

---

### Post by kevinl on 2008-05-12
I have posted the idea presented above on the brainstorming forum and it didn't even rate a mention.  It seems the people driving Ubuntu don't regard this matter seriously.  It would be a simple matter not to try to change the video settings until very near the end of the installation.  I'm sure a lot of other people are experiencing the black screen problem and simply move to another distribution that has a better installation.  That is a pity as I want Ubuntu to succeed.  Suggest you write to support.  If a lot of people write, maybe someone with the ability to fix this will take note.  As for dropping into the command line, I will get back to you later on that matter.  I have an appointment to keep at the moment and in fact I shouldn't actually be looking at my posts!!  I'm supposed to be somewhere else.

---

### Post by Sef on 2008-05-12
Moved to Community Cafe.

---

### Post by OldTimeTech on 2008-05-12
I think we've all been told frequently that if you want some recognition on a question or a brainstorm from the developers/programmers, you need to send an email, not put it in the forums....developers/programmers don't have time to check the forums....

Now I didn't say this, but I've read it other places.

---

### Post by madjr on 2008-05-12
u could checkout the new

[http://linux.via.com.tw/](http://linux.via.com.tw/)

---

### Post by quinnten83 on 2008-05-12
Ubuntu brainstorm is separate from canonical-backed Ubuntu.
It's a different community effort.
I think your best bet would be to do a bugreport on launchpad. If the bug is serious enogh, they will address it.I believe i might have heard something about this before. If I am not mistaken, Ubuntu starts, but the frequency of the screen is out of range so only a black screen is displayed.
If you type alt+ctrl+F2 can you drop into a command shell? if so you might be able to adjust your X by configuring xorg.conf.

---

