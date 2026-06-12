---
title: "Rootkit questions"
date: 2008-01-16
forum: Server Platforms
---

### Post by yeleek on 2008-01-16
Hi,

Checked my machine with chkrootkit and it found the following:

Searching for suspicious files and dirs, it may take a while... 
/usr/lib/firefox/.autoreg
/lib/modules/2.6.22-14-generic/volatile/.mounted
/lib/linux-restricted-modules/.nvidia_new_installed

Which i don't think is an issue... can someone please confirm?

Then ran rkhunter which said the following:

System checks summary
=====================

File properties checks...
    Files checked: 124
    Suspect files: 0

Rootkit checks...
    Rootkits checked : 109
    Possible rootkits: 0

Applications checks...
    Applications checked: 3
    Suspect applications: 0

The system checks took: 51 seconds


With only one warning of:
[08:55:56]   Checking for hidden files and directories       [ Warning ]
[08:55:56] Warning: Hidden directory found: /dev/.static
[08:55:56] Warning: Hidden directory found: /dev/.udev
[08:55:56] Warning: Hidden directory found: /dev/.initramfs

I'm guessing neither of these are anything to worry about?

Thank you

---

### Post by Vinno on 2008-01-16
Looks about fine, if you want to check more info on it, google the string it outputs.

---

### Post by yeleek on 2008-01-16
Thanks for that - thought they were non-events but wanted to check having come from an ms point of view.

Difficult to get use to little in the way of threats to linux when compared to Windows.

---

### Post by HermanAB on 2008-01-16
I have *never* found a Linux rootkit, not even on severely compromised machines.  So rootkit risk is probably much exagerated.  Linux isn't Windows.

---

### Post by Salazar420 on 2008-01-20
> **HermanAB said:**
> I have *never* found a Linux rootkit, not even on severely compromised machines.  So rootkit risk is probably much exagerated.  Linux isn't Windows.

I have. Just recently, actually. 'sudo rkhunter --check' revealed nothing suspicious, yet 'sudo chkrootkit' revealed that a. i have hidden files,much like that dude up there; b. apparently my sandbox account either didn't logout and/or was deleted; and c. that i had a rootkit installed. 

I would quote the output, but unfortunately i'm running from the live cd just to be safe. I'm going to make an try my hand at VGA anti-rootkit for linux, because it worked for my windows system last night. I'm thinking what happened was that I temporarily dropped all of my iptables security measures or whatever using lokkit (for random experiment) and was then infected. After that, I'm assuming the rk managed to afflict my linked system via the wire, but I can't be sure (both are fixed wireless adapters).

---

