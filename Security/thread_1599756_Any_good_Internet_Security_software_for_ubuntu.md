---
title: "Any good Internet Security software for ubuntu?"
date: 2010-10-18
forum: Security
---

### Post by tweaktolive on 2010-10-18
I am new and i am worried about my data. So i want an Internet Security software for ubuntu.

Recomendations please!!!!!

Thanx

---

### Post by amauk on 2010-10-18
Linux is not Windows
Unless you're doing anything server-ish (Ie. SSH, FTP, etc.), there's no need for any extra security software at all

Maybe be a bit more specific about what you're looking to do / achieve

---

### Post by tweaktolive on 2010-10-18
OK what is iSH whatever?

---

### Post by amauk on 2010-10-18
server-ish
anything resembling a server

Anyway,
For desktop use, you do not need any security software

Can you tell us exactly what you're machine will be doing (Desktop computer?)

---

### Post by tweaktolive on 2010-10-18
I love tweaking stuff and i like to know new things . I do my tweaking in windows xp so please tell me what is that server - ish you were saying.

---

### Post by amauk on 2010-10-18
> **tweaktolive said:**
> I love tweaking stuff and i like to know new things . I do my tweaking in windows xp so please tell me what is that server - ish you were saying.There is no server called "ish"

I think we're lost in translation, so forget everything I said

Let me re-write my first post to be a bit clearer

> **amauk said:**
> Linux is not Windows
Unless you're doing anything server related there is no need for any extra security software at all

Maybe be a bit more specific about what you're looking to do / achieve

---

### Post by tweaktolive on 2010-10-18
I know English !!!! I am an Indian !!!! Just a bit lazy to write thought you would understand

---

### Post by HermanAB on 2010-10-18
Yup, there's excellent security software out there.  It is called Linux and you are already running it.

Relax and enjoy your new, secure system.

---

### Post by tweaktolive on 2010-10-18
HaHa 
Thanx!!!!

---

### Post by Malcolm Waterman on 2010-10-18
If you're really worried about internet security, Ubuntu has a inbuilt firewall. You can access it either through the command line or by installing a GUI program, e.g. Firestarter. If you install Firestarter, it seems that you have to manually add auto-run at startup capabilities. Firestarter is under Applications -> Internet -> Firestarter.
 
For anti-virus you can install Clamtk which can be accessed from Applications -> Accessories -> Virus Scanner. From there you can scan about any file on your system. To update Clamtk, go to terminal and enter "sudo freshclam"

Correction: No need to add auto-run at startup for ipconfigs, the Ubuntu firewall. It doesn't give any indications that it's running. Firestarter is a one-run application also.

---

### Post by tweaktolive on 2010-10-18
i would like to have the commands for installing
Thanx!!!!

---

### Post by tweaktolive on 2010-10-18
what are the commands to install security software?

---

### Post by Velnias on 2010-10-18
Actually, antivirus in linux makes more trouble than benefit. There was vulnerabilities in antivirus code... and probably will be more discovered in future.

PS wanna thinker with security - go use SELinux in Ubuntu.

---

### Post by fancypiper on 2010-10-18
> **tweaktolive said:**
> what are the commands to install security software?As noted before, if you aren't running server stuff you should be secure on the internet out of the box.

If you are running Ubuntu the apt-get utility can be used:

sudo apt-get install <package name>

Or, for a GUI, run synaptic.

[How to install ANYTHING in Ubuntu!](http://amitech.50webs.com/installing/index.php.html)

See how hard it is to write a virus for Linux?
[The Linux Virus Writing HOWTO](http://virus.bartolich.at/virus-writing-HOWTO/_html/index.html)

---

### Post by cariboo on 2010-10-18
> **Malcolm Waterman said:**
> If you're really worried about internet security, Ubuntu has a inbuilt firewall. You can access it either through the command line or by installing a GUI program, e.g. Firestarter. If you install Firestarter, it seems that you have to manually add auto-run at startup capabilities. Firestarter is under Applications -> Internet -> Firestarter.
 
For anti-virus you can install Clamtk which can be accessed from Applications -> Accessories -> Virus Scanner. From there you can scan about any file on your system. To update Clamtk, go to terminal and enter "sudo freshclam"

If you are going to recommend software, you should at least know how it works. Firestarter is set and forget,  You run the app to set the firewall rules, then just close irt and forget about it from then on. the rules are applied every time you boot. There is no need to have it running all the time. As a matter of fact it may be a bad idea running it all the time, as you need to run it as root, which could lead to security problems.

---

