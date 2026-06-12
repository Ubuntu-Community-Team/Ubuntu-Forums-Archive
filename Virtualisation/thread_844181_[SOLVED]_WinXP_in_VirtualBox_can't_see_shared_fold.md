---
title: "[SOLVED] WinXP in VirtualBox can't see shared folder in vboxsvr"
date: 2008-06-29
forum: Virtualisation
---

### Post by samjh on 2008-06-29
I've install Windows XP Home with SP3 on Ubuntu Gutsy x86_64, using VirtualBox 1.6.2.

To make a shared folder, I've created a directory called "vboxshared" (without quotes) in ~/.

From VirtualBox, I have specified the directory path and name using the GUI, but my WinXP installation cannot find the directory.  I've tried My Network Places -> Entire Network -> VirtualBox Shared Folders; as well as Map Network Drives; and also the [FONT="Courier New"]net use x: \\vboxsvr\vboxshared[/FONT] command (the latter returns "System error 67" and "The network name cannot be found").

I've trawled through a whole host of pages with suggested solutions, but to no avail.  I prefer not to try setting up a Samba share, as that is wholly beyond my experience.

Does anyone have suggestions on how to overcome this problem?

(PS: Guest Additions is installed, if that's relevant.)

=========================================================

**SOLVED!** :)

I just re-installed Guest Additions, rebooted, and it worked!

Very strange.

---

### Post by cuh on 2008-06-29
Same thing happened with me: Folder sharing did not work on gutsy x86_64 host / XP Pro SP2 guest. I was clueless but your comment helped me, I have reinstalled Guest Additions and it solved my problem. Maybe it is a bug of the 64bit version of virtualbox? Anyway thanks for sharing the information!

---

### Post by hongleong on 2008-06-30
Reinstalled "Guest Additions" and rebooted. Now it works. Thanks samjh. :)

---

### Post by samjh on 2008-06-30
Glad to be of help! :)

I struggled with it for nearly three hours.  My Google skills were put to a hard test! :p  Hopefully this will save others from the trouble.

---

### Post by Skuttles on 2008-07-05
Thank you!
Was about to call it quits after searching through google and trying everything.
Reinstalled the guest additions and its now working like a charm.

---

### Post by Jozza The Wick on 2008-07-09
Reinstall of the Guest Additions on v1.6.2 also worked with 32bit Ubuntu 7.10.

Thanks, all!

---

### Post by loudnlownoma on 2008-07-12
Just confirming and bumping - same problem and fix here on two different machines!  Yay for having shared folders again!

---

### Post by victorbrca on 2008-08-05
Confirm that I had the same problem and the fix worked.

---

### Post by Mujaheiden on 2009-02-25
I have ubuntu 8.10, wit Virtualbox 2.04. Ive installed Win XP, and reinstalled three times GuestAdditions 2.04, but my shared folders, or the vboxsvr dont show up, although it indicates they should be there

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=104598&stc=1&d=1235568289[/IMG]

What am I doing wrong?

---

### Post by edwardtilbury on 2009-08-14
me too..

I'm running x64 bit 9.04 Ubuntu and the latest vbox 3.04 but it does not see the shares.. 

I've reinstalled the vmtools 4 times.. deleted the folders from the sun launcher, added them, added them while in the OS.. nothing works..

I think that fix only works for the 32 bit versions.

im going to reboot and try a samba share locally.

---

### Post by abansb on 2009-08-15
> **Mujaheiden said:**
> I have ubuntu 8.10, wit Virtualbox 2.04. Ive installed Win XP, and reinstalled three times GuestAdditions 2.04, but my shared folders, or the vboxsvr dont show up, although it indicates they should be there

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=104598&stc=1&d=1235568289[/IMG]

What am I doing wrong?

I am having the same problem with Ububtu 8.04.3 I have to go into control panel and add the shared folder to network places every time I need it

---

### Post by nrk62 on 2010-01-13
> **samjh said:**
> I've install Windows XP Home with SP3 on Ubuntu Gutsy x86_64, using VirtualBox 1.6.2.

To make a shared folder, I've created a directory called "vboxshared" (without quotes) in ~/.

From VirtualBox, I have specified the directory path and name using the GUI, but my WinXP installation cannot find the directory.  I've tried My Network Places -> Entire Network -> VirtualBox Shared Folders; as well as Map Network Drives; and also the [FONT="Courier New"]net use x: \\vboxsvr\vboxshared[/FONT] command (the latter returns "System error 67" and "The network name cannot be found").

I've trawled through a whole host of pages with suggested solutions, but to no avail.  I prefer not to try setting up a Samba share, as that is wholly beyond my experience.

Does anyone have suggestions on how to overcome this problem?

(PS: Guest Additions is installed, if that's relevant.)

=========================================================

**SOLVED!** :)

I just re-installed Guest Additions, rebooted, and it worked!

Very strange.
Thanks, it worked for me using 9.10 and VirtualBox 3.0.8!

---

