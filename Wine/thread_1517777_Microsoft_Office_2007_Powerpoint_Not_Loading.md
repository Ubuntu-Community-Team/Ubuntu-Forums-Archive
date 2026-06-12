---
title: "Microsoft Office 2007 Powerpoint Not Loading"
date: 2010-06-25
forum: Wine
---

### Post by glowell on 2010-06-25
Hi,

I am running the newest Ubuntu Desktop edition operating system and stuff of that sort. Everything is updated and just installed it today. I'm very pleased with it. I successfully installed Microsoft Office 2007 through Wine HQ. Every application in Office 2007 Enterprise Edition works perfectly through Wine. But Microsoft Office Power Point 2007 seems unable to do so...

Why is that?

Also I was wondering my college campus uses the Cisco NAC Clean Access Agent to log into the campus network. Would I be able to install that application onto my Ubuntu through wine hq and log onto it succesfully?

Thanks for the feedback and assistants in this problem.

---

### Post by minio on 2010-07-01
Hi - to run Powerpoint you have to go to configure riched20 override
Go to applications -> wine -> configure wine
Then select Libraries tab, select from dropdown menu riched20 and click add.
Now you should see something like riched20(native, builtin). Click OK and Powerpoint should now run OK. 

I do not know how to help you with your second question. I would just try to install the program and look if it works or not.

---

### Post by lunatico on 2010-08-09
> **glowell said:**
> 
Also I was wondering my college campus uses the Cisco NAC Clean Access Agent to log into the campus network. Would I be able to install that application onto my Ubuntu through wine hq and log onto it succesfully?


Is this for a VPN connection?

---

### Post by lunatico on 2010-08-09
> **minio said:**
> Hi - to run Powerpoint you have to go to configure riched20 override


Yeah I have this and everything work fine but today I tried to open more than one PowerPoint at the same time and for some reason the second one I open comes over the first one. You can see both on the panel in the buttom, but they seem to be merged into one window with the second one on top and to able to show the first one.
Seen this?

---

