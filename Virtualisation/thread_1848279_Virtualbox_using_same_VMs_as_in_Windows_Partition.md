---
title: "Virtualbox using same VMs as in Windows Partition"
date: 2011-09-22
forum: Virtualisation
---

### Post by dakiluxa on 2011-09-22
Hi guys, I have a PC with both ubuntu and win 7 installed. What I'd like to do is use the same VMs that I use on windows, on my ubuntu.
I tried going to properties and changing the predetermined VM folder to the one in my windows partition but it's not picking them up.
Any ideas?

---

### Post by dcstar on 2011-09-22
> **dakiluxa said:**
> Hi guys, I have a PC with both ubuntu and win 7 installed. What I'd like to do is use the same VMs that I use on windows, on my ubuntu.
I tried going to properties and changing the predetermined VM folder to the one in my windows partition but it's not picking them up.
Any ideas?

Please ask VM questions in the Virtualization forum.

---

### Post by haqking on 2011-09-22
> **dakiluxa said:**
> Hi guys, I have a PC with both ubuntu and win 7 installed. What I'd like to do is use the same VMs that I use on windows, on my ubuntu.
I tried going to properties and changing the predetermined VM folder to the one in my windows partition but it's not picking them up.
Any ideas?

place your VM's on an external HDD, thats what i have, then you can use it in whatever OS you like, though i suspect some configuration changes.

Using a VM in a different OS could change its configuration and may cease to operate in the other OS and Vbox installation etc.

---

### Post by nothingspecial on 2011-09-22
Moved to Virtualisation

---

### Post by searchfgold6789 on 2011-09-22
Yeah, you can do that. When you go to make a *new* vm, just select the hard disk off of your Windows partition and set it to bot from there. Easy as pie.

---

### Post by dakiluxa on 2011-09-22
> **searchfgold6789 said:**
> Yeah, you can do that. When you go to make a *new* vm, just select the hard disk off of your Windows partition and set it to bot from there. Easy as pie.

I tried that but my vm ends up with a black screen and unresponsive. I get the menu for normal boot, safe mode etc but nothing after that.

---

### Post by Habitual on 2011-09-22
"Export Appliance" from the VirtualBox File menu.

"Import Appliance" at the target.

---

