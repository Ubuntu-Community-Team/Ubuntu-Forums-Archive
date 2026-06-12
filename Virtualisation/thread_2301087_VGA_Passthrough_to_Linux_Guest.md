---
title: "VGA Passthrough to Linux Guest"
date: 2015-10-30
forum: Virtualisation
---

### Post by zexelon2 on 2015-10-30
Just out of curiosity has anyone seen a tutorial for passing through a Videocard (preferably ATI) to a Linux Guest in either Xen or KVM? All the tutorials I have found to date are for passing a videocard through to a Windows guest and they dont seem to work for Linux guests...

---

### Post by KillerKelvUK on 2015-10-31
Why don't they work for linux guests?  Granted I've not got VGA passthrough to linux but I do have pci passthrough of a DVB-S2 and FXO card to linux guests and these work fine.

---

### Post by zexelon2 on 2015-11-02
I really dont know why its not working. The linux guests simply wont boot. They install and run fine before passing through the VGA card but as soon as I add the VGA card (ATI Radion 7970) they halt booting, no kernel panic or anything they just stop around detecting PCI drivers. I have not tried black listing the radion driver yet to see if its the cause. 

Windows Guests work just fine. 

Also havent tried Xen 4.6, this is the first thing I am going to try atm. I am currently running 4.5.

---

### Post by KillerKelvUK on 2015-11-02
> **zexelon2 said:**
> I really dont know why its not working. The linux guests simply wont boot. They install and run fine before passing through the VGA card but as soon as I add the VGA card (ATI Radion 7970) they halt booting, no kernel panic or anything they just stop around detecting PCI drivers. I have not tried black listing the radion driver yet to see if its the cause. 

Windows Guests work just fine. 

Also havent tried Xen 4.6, this is the first thing I am going to try atm. I am currently running 4.5.

Okay so my passthrough experience is with KVM not Xen but I'm struggling to see how without either stubbing or blacklisting drivers you can get this working for a Windows guest...I'm quiet possibly applying logic here which is just not valid in a Xen world so granted.  Do you have any error logs to share...assuming the host provides a DomU specific log file that might shed more light on the situation?

---

