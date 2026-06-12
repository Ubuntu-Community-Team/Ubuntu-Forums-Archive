---
title: "xubuntu 14.04 daily Dec-18-2013 boots to password request"
date: 2013-12-19
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2013-12-19
I downloaded the daily image of 32bit xubuntu 14.04 yesterday and put it on a multiOS USB flash drive which I have used for some time and which I made following the info at [http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604).

On my Netbook with MBR BIOS it boots to a lightdm login screen (I presume it's lightdm) and asks for a user and password.  I enter xubuntu for user, leave password blank and login to the live session with no problem.

On my UEFI desktop machine I try to do the same at the login screen but the the user xubuntu and blank password just returns me to lightdm with a wrong password error message.

Actually on both it boots to a Bangladesh language desktop, but that can be  changed to English_GB at login screen. I mention that for info only.

What could be going on here?  Why will it boot OK to live session on one machine but not the other?

As a general comment, however, it looks very good at the moment on the netbook, and pretty fast as well

---

### Post by OrangeCrate on 2013-12-19
^, If I understand what you're trying to do here, on the machine that won't open, use "xubuntu" as the user name, and leave the password field blank. That worked for me to get in.

---

### Post by ajgreeny on 2013-12-19
> **OrangeCrate said:**
> ^, If I understand what you're trying to do here, on the machine that won't open, use "xubuntu" as the user name, and leave the password field blank. That worked for me to get in.
Yes, that works fine on my netbook, but as I said in my post, on my desktop machine which boots with UEFI doing that simply returns me to the login screen with an "Incorrect password" error.

I do exactly the same on both machines; one works the other doesn't.

---

### Post by OrangeCrate on 2013-12-19
I did misunderstand, sorry. I have no advice to offer with your issue. I hope someone will come along to help...

---

### Post by ajgreeny on 2013-12-19
Well, it's sorted, or partly so, though it still leaves me a bit baffled as to why it worked on my netbook but not on my desktop.

I today downloaded the 64 bit version of the same xubuntu 14.04 (well a day later version, I admit) and that boots fine to the desktop with the xubuntu user and blank password.  I wonder if this is something to do with the system being UEFI, not MBR BIOS, and therefore needing 64bit OS.  If that were so I would not have expected the 32bit version (yesterday's download) to have even got to the login screen.

Still gives me the bangladesh language if I don't change it, but that was easily overcome.

---

### Post by Elfy on 2013-12-20
There are bugs reported for the few user sessions bugs we've been seeing - simply put you need to

set session to Xubuntu
set language
use xubuntu for username

[http://xubuntu.org/news/xubuntu-14-04-alpha-1/](http://xubuntu.org/news/xubuntu-14-04-alpha-1/)

I do try to float around here, catching what's going on - but have failed a bit lately, I'm more likely to see quickly at

[http://webchat.freenode.net/?channels=xubuntu-devel](http://webchat.freenode.net/?channels=xubuntu-devel)

[http://webchat.freenode.net/?channels=ubuntu-quality](http://webchat.freenode.net/?channels=ubuntu-quality)

or [http://webchat.freenode.net/?channels=ubuntu+1](http://webchat.freenode.net/?channels=ubuntu+1)

Most people in xubuntu-devel would be able to point you in the right direction

---

### Post by ajgreeny on 2013-12-20
> **Elfy said:**
> There are bugs reported for the few user sessions bugs we've been seeing - simply put you need to

set session to Xubuntu
set language
use xubuntu for username

Thanks Elfy, but as I said in post #3, that worked on my 32bit netbook but not my 64bit desktop that uses UEFI rather than legacy BIOS.

I am a bit green still on the detailed requirements of UEFI for booting live media, but I still can not figure out why on the UEFI machine it boots to a login screen, but will simply not move on to a xubuntu live session.

As you can see from my post #5 I have now also downloaded the 64bit daily which does boot to a xubuntu session though still via the login screen.

---

### Post by oldfred on 2013-12-20
There are no 32 bit Linux UEFI versions. I am surprised that it even started to boot.

       Don't ship 32-bit UEFI firmware on x86
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)

Some new 64 bit low cost systems with 32 bit UEFI
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)

    
And these new 32 bit systems are Class 3 UEFI which means only UEFI no CSM/Legacy/BIOS boot mode.

---

### Post by ajgreeny on 2013-12-20
Thanks, oldfred.

As I say, my detailed knowledge of UEFI is pretty limited, though it was not difficult to get Xubuntu 12.04 installed as a single boot (no windows here) using UEFI, not legacy BIOS or CSM.

I assume what you mean is that no 32 bit OS will boot on a UEFI system; am I correct?  If so, I am also surprised that it got as far as the login screen.  Maybe some parts of the OS were running but the the whole required OS?  Is that even possible.

Whatever your answer, I have now updated the daily iso files with zsync, and they both still show the problem of booting to the login screen before the live session and both still using bangladesh language as default.

---

### Post by oldfred on 2013-12-20
There seems to now be a 32 bit Windows UEFI for some of those Atom processors. But it seems they then are in effect locked to Windows like an ipad is, as they know that no Linux has a 32bit version. 

If enough demand or some system programmer buys one then someone may eventually create a 32 bit Linux UEFI system.

---

