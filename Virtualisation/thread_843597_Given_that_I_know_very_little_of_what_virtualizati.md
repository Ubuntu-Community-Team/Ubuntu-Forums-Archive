---
title: "Given that I know very little of what virtualization is and what it does,"
date: 2008-06-28
forum: Virtualisation
---

### Post by koopatrol on 2008-06-28
would it be possible to use VMWare in such a way that I run Windows Vista x86-64 within a fresh x86-64 Hardy install?

I've been using Ubuntu on-and-off for quite some time, and I imagine that if there were some reliable way that I could run Adobe's Illustrator & InDesign CS3 within Linux, I'd be able to make the switch entirely.

Any resource would be a great help. The problem I have with figuring the concept thus far is a lack of what I'd consider to be a reliable resource from which to learn the concept in full. Anything of that nature would be ridiculously helpful.

---

### Post by fjgaude on 2008-06-28
It's  not too difficult to install VMware Server, using the HOW-TO at the top of this forum. It will take a little study, reading to understand it all but it works great... I've been using it for over two years with Adobe products... couldn't do without vmware and its copy-cut-paste capabilities from Ubuntu to Windows and back.

Give it a try and see what you think.

---

### Post by koopatrol on 2008-06-28
> **fjgaude said:**
> It's  not too difficult to install VMware Server, using the HOW-TO at the top of this forum. It will take a little study, reading to understand it all but it works great... I've been using it for over two years with Adobe products... couldn't do without vmware and its copy-cut-paste capabilities from Ubuntu to Windows and back.

Give it a try and see what you think.

Is VMware going to allow me to install the x86-64 version of Vista? It's the only version I currently legally possess, and I'd prefer to use it if at all possible.

---

### Post by fjgaude on 2008-06-28
Gosh, I can't say for sure... I use XP for all my graphic design... maybe there's others here that have installed Visa in VMware... I vaguely remember it can be done just like any other OS. Let me look and see... yes, it shows in the install memu of vmware 1.0.5... 1.0.6 is out so you are good to go.

Follow the how-to at the top of this forum for the Server, not the Workstation.

Hope you have lots of RAM, at least 2GBs, for you are gonna need half or more of that for Vista... <smile>

Let us know if you run into troubles...

---

### Post by koopatrol on 2008-06-28
> **fjgaude said:**
> Gosh, I can't say for sure... I use XP for all my graphic design... maybe there's others here that have installed Visa in VMware... I vaguely remember it can be done just like any other OS. Let me look and see... yes, it shows in the install memu of vmware 1.0.5... 1.0.6 is out so you are good to go.

Follow the how-to at the top of this forum for the Server, not the Workstation.

Hope you have lots of RAM, at least 2GBs, for you are gonna need half or more of that for Vista... <smile>

Let us know if you run into troubles...

Vista's running like a dream. It's a tad on the slow side, but I've only got 512MB of RAM, but I expect it'll speed up once I finish installing Vista and can install VMware tools.

---

### Post by fjgaude on 2008-06-28
The Tools make everything work normally... only 512MB of RAM... not good, especially with Vista. With XP it is doable, but...

Good luck learning all the things there is to learn.

---

### Post by koopatrol on 2008-06-28
[COLOR="Gray"]I can't seem to figure out how to adjust the amount of memory dedicated to the virtual machine. The whole of the dialog box is inaccessible.

Ex,[/COLOR]

**Update:** It seems I was merely suspending my virtual machine, not powering it down. The aforementioned problem is now fixed.

However, becoming aware of this problem has brought my attention to a different problem entirely: my network seems to be inoperable, with Vista complaining about there being no connection present. I currently have it set up as a bridged network, as shown in the following screenshot.

---

### Post by fjgaude on 2008-06-29
Okay, power-off and set the network connection to NAT... that should give you an auto connection.

I should have told you to use defaults in installing vmware. The how-to did that, eh? Also, use on only one core, not more, for speed. It works, trust me.

---

