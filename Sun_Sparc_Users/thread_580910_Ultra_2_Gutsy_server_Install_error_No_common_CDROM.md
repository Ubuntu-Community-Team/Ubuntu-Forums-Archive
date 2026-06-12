---
title: "Ultra 2 Gutsy server Install error No common CDROM drive detected"
date: 2007-10-19
forum: Sun Sparc Users
---

### Post by sandpiper on 2007-10-19
Great to see the announcement of a new release for Ubuntu
Just attempted to do a clean install of Gusty server version on my Ultra 2 "workstation" hardware.  Didn't get very far ... Error during initial install of "No common CD-ROM was detected"   Did not have this error message with previous version Fiesty. Any help on what I should do appreciated?  Puzzled because I have not changed the CDROM hardware....Chris

---

### Post by jawong on 2007-10-21
I have the same error, I've tried all combinations from 7.04, but haven't figured it out yet.

---

### Post by sandpiper on 2007-10-21
> **sandpiper said:**
> Great to see the announcement of a new release for Ubuntu
Just attempted to do a clean install of Gusty server version on my Ultra 2 "workstation" hardware.  Didn't get very far ... Error during initial install of "No common CD-ROM was detected"   Did not have this error message with previous version Fiesty. Any help on what I should do appreciated?  Puzzled because I have not changed the CDROM hardware....Chris

Follow-up:  Have looked at the dmesg output and lsmod using Alt F2 to get a terminal screen up. Looks like the scsi driver is not being loaded.

Now I am assuming this still to be "esp".
Cannot find this by searching the directories loaded during the install process.  ie I  looked in 2.6.22-14-sparc64/kernel/drivers/scsi...... 

I also tried the "modprobe esp" as advised by Netztier June last year. This comes up wih the message "esp module not found" as expected

Also from the command "lsmod" I see the cdrom  listing refers to " ide_cd" This is a puzzle because I am definitively running a SCSI CDROM.. Checking Fiesty that I am running now confirms that the esp driver is used  .. So..... Questions; What  I do now?  Does 7:10 Ubuntu no longer support the Ultra 2?   Is there an alternative SCSI driver I should be looking for? Help really appreciated Chris.

---

### Post by sandpiper on 2007-10-22
> **sandpiper said:**
> Follow-up:  Have looked at the dmesg output and lsmod using Alt F2 to get a terminal screen up. Looks like the scsi driver is not being loaded.

Now I am assuming this still to be "esp".
Cannot find this by searching the directories loaded during the install process.  ie I  looked in 2.6.22-14-sparc64/kernel/drivers/scsi...... 

I also tried the "modprobe esp" as advised by Netztier June last year. This comes up wih the message "esp module not found" as expected

Also from the command "lsmod" I see the cdrom  listing refers to " ide_cd" This is a puzzle because I am definitively running a SCSI CDROM.. Checking Fiesty that I am running now confirms that the esp driver is used  .. So..... Questions; What  I do now?  Does 7:10 Ubuntu no longer support the Ultra 2?   Is there an alternative SCSI driver I should be looking for? Help really appreciated Chris.

Follow-up 2:  Looks like this is a common issue for Sparc's from reading this thread. 

[http://lists.auroralinux.org/pipermail/aurora-sparc-user/2007-October/004801.html](http://lists.auroralinux.org/pipermail/aurora-sparc-user/2007-October/004801.html)

I am puzzled that with the absence of the esp drivers how a network install would work..... Certainly it would remove the dependency on the CDROM drive but what about harddiscs..... Chris

---

### Post by sandpiper on 2007-10-25
> **sandpiper said:**
> Follow-up 2:  Looks like this is a common issue for Sparc's from reading this thread. 

[http://lists.auroralinux.org/pipermail/aurora-sparc-user/2007-October/004801.html](http://lists.auroralinux.org/pipermail/aurora-sparc-user/2007-October/004801.html)

I am puzzled that with the absence of the esp drivers how a network install would work..... Certainly it would remove the dependency on the CDROM drive but what about harddiscs..... Chris

Follow-up 3:  Well it is confirmed...... Entry in syslog says
hw-detect: Missing Modules 'sunhme (HAPPY MEAL 10/100 Ethernet), esp (ESP SCSI) 

Can any one advise me on how I can get the relevant esp module at install time. As I said in a previous post "Modprobe esp" doesn't work .   If no one can offer a way forward I presume that the  Ultra 2 hardware is no longer supported by Ubuntu and I am wasting my time here......Comments?

---

### Post by sandpiper on 2007-10-26
> **sandpiper said:**
> Follow-up 3:  Well it is confirmed...... Entry in syslog says
hw-detect: Missing Modules 'sunhme (HAPPY MEAL 10/100 Ethernet), esp (ESP SCSI) 

Can any one advise me on how I can get the relevant esp module at install time. As I said in a previous post "Modprobe esp" doesn't work .   If no one can offer a way forward I presume that the  Ultra 2 hardware is no longer supported by Ubuntu and I am wasting my time here......Comments?

Follow-up 4:  After some further searching on the Ubuntu support links I found this bug description today that seems close...

[https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/22367](https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/22367)
I quote.....
"  I did an install on sparc64 today, and because the installer cannot detect my
ethernet and scsi controller (sbus, not PCI), I had to manually select it from
the installer's list."

Can any one help me (being a Linux newbie)  as to how I can manually "select it from the installer's list"  What and where  is the installers list Is it loaded at initial boot time? Any simple hints  ...Chris

---

