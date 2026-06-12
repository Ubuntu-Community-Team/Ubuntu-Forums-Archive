---
title: "VirtualBox Seamless Mode Cursor Problem"
date: 2010-01-29
forum: Virtualisation
---

### Post by Bradj47 on 2010-01-29
I enable seamless mode without any problem except one: Cursor integration is still enabled. That kinda defeats the purpose of seamless mode if you ask me. I'm running Windows XP on a guest OS of Ubuntu 9.04. I'm using VirtualBox 2.1.4 OSE. Yes, I know it's an outdated version. If anyone knows how to upgrade VirtualBox without losing all the data on my guest OS, that would also help a lot. In fact, the problem might be fixed by upgrading. So I don't know. I'm open to suggestions. 

Thanks in advance, 
Brad

---

### Post by howefield on 2010-01-29
What do you mean by cursor integration ?

Do you mean the mouse is captured in the guest and you have to execute a keyboard shortcut to free it ?

If so, that should be fixed in a later version of guest additions than you are running.

---

### Post by Bradj47 on 2010-01-29
> **howefield said:**
> What do you mean by cursor integration ?

Do you mean the mouse is captured in the guest and you have to execute a keyboard shortcut to free it ?

If so, that should be fixed in a later version of guest additions than you are running.

How do I check what version of guest additions I'm using?

---

### Post by howefield on 2010-01-29
> **Bradj47 said:**
> How do I check what version of guest additions I'm using?

I'd guess it will correspond with your Virtualbox version.

I'm not sure if you can update guest additions without also updating Virtualbox itself. 

As you suggested, I'd recommend updating to the latest version of Virtualbox, doing this will prompt an update of guest additions when you next boot your guest.

The improvements made since version 2.1.4 are significant, so it is probably a good idea to update, in any event.

---

### Post by Bradj47 on 2010-01-29
> **howefield said:**
> I'd guess it will correspond with your Virtualbox version.

I'm not sure if you can update guest additions without also updating Virtualbox itself. 

As you suggested, I'd recommend updating to the latest version of Virtualbox, doing this will prompt an update of guest additions when you next boot your guest.

The improvements made since version 2.1.4 are significant, so it is probably a good idea to update, in any event.

But how do I do that without losing all the data on my guest OS?

---

### Post by howefield on 2010-01-29
Your VMs will be unaffected.

You could copy them elsewhere if you felt it safer ;) 

I take a back up of all vms in any event.

---

### Post by Bradj47 on 2010-01-29
> **howefield said:**
> Your VMs will be unaffected.

You could copy them elsewhere if you felt it safer ;) 

I take a back up of all vms in any event.

So do I just sudo apt-get install virtualbox? Here's what I get when I try that: 

```

brad@rockstar:~$ sudo apt-get install virtualbox-ose
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose is already the newest version.
The following packages were automatically installed and are no longer required:
  libots0 libaiksaurusgtk-1.2-0c2a latex-xft-fonts libaiksaurus-1.2-0c2a
  link-grammar-dictionaries-en libt1-5 libaiksaurus-1.2-data libwv-1.2-3
  libgdome2-0 libgdome2-cpp-smart0c2a liblink-grammar4 libgtkmathview0c2a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
brad@rockstar:~$ 

```

I'm downloading the .deb package for 9.04 right now. I'm pretty sure It's not OSE though. I'll post back with results after I download & install.

---

### Post by Bradj47 on 2010-01-29
I get this error when I try to install the deb package: 

> 
Error: Conflicts with the installed package 'virtualbox-ose'
Conflicts with the installed package 'virtualbox-ose'


So to back up my guest OS I assume I back up the name of the directory that matches the name of my guest OS in $HOME/.VirtualBox/Machines. I'm going to remove the old version and install the new one. I'll post back again.

---

### Post by howefield on 2010-01-29
> **Bradj47 said:**
> I'm downloading the .deb package for 9.04 right now. I'm pretty sure It's not OSE though. I'll post back with results after I download & install.

I don't think there are OSE .debs on the website. So it probably is the PUEL version, which is better featured, unless you are a stickler for the OSE version.

I'll hang around for a little while, in case you hit a snag.

---

### Post by Bradj47 on 2010-01-29
> **howefield said:**
> I don't think there are OSE .debs on the website. So it probably is the PUEL version, which is better featured, unless you are a stickler for the OSE version.

I'll hang around for a little while, in case you hit a snag.

I don't really mind whether it's OSE or PUEL. The only reason I had OSE installed before was because it was the only one I could find in the Ubuntu repos. 

OK, it just finished installing. I would like to make a note that VirtualBox didn't show up in the Applications menu. I had to try a few command in the Terminal to figure out which one ran VirtualBox. It turns out it's 'VirtualBox' (note the capital V and B). I tried both 'virtualbox' and 'vbox' before getting to 'VirtualBox'. 

But now, even though the newer version is installed, I still have the cursor integration problem. I'll try looking for a new guest additions .iso file then post back again.

---

### Post by howefield on 2010-01-29
> **Bradj47 said:**
> OK, it just finished installing. I would like to make a note that VirtualBox didn't show up in the Applications menu.

It most likely will, after a reboot. If not make a new entry.

> I still have the cursor integration problem. I'll try looking for a new guest additions .iso file then post back again.

It's the guest additions that will do it :)

Might also be worth adding the virtualbox repository, so you stay updated with minimum fuss.

---

### Post by Bradj47 on 2010-01-30
> **howefield said:**
> It most likely will, after a reboot. If not make a new entry.


It did after reboot. 

> **howefield said:**
> 
It's the guest additions that will do it :)

Might also be worth adding the virtualbox repository, so you stay updated with minimum fuss.

I installed the latest Guest Additions and all the mouse problems were solved. Thanks for all the help.

---

### Post by howefield on 2010-01-30
Thanks for the update, glad you're sorted.

---

