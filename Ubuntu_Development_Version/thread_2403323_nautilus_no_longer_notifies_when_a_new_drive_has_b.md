---
title: "nautilus no longer notifies when a new drive has been added"
date: 2018-10-10
forum: Ubuntu Development Version
---

### Post by PaulW2U on 2018-10-10
For me, Ubuntu 18.10 has been the most problematic release during the development phase since the introduction of Unity back in 2011. I recently installed the beta after reverting to Ubuntu 18.04 for a month or two and found that most of my problems had gone.

Last night I decided to look into why nautilus is no longer notifying me when a new drive is added. I certainly get a notification in Ubuntu 18.04 and also do when using the Cosmic beta in a live session. My Cosmic installation no longer notifies me which is something that I can reproduce using yesterday's ISO (20181009) in a live session on two PCs.

Anyone else? I'll check today's ISO when it's available later today.

Bug report: [nautilus no longer notifies when a new drive has been added]("https://bugs.launchpad.net/bugs/1797052")


Edit: today's ISO (20181010) tested in a live session. Again no notification.

---

### Post by dino99 on 2018-10-10
I have no such a issue with mine (gnome on xorg session), but its not a fresh install like yours (ex bionic dist-upgraded).
The first thing that come up to my mind is about the 'recommend' packages: are they installed by default as dependencies ?
Do you have the DE metapackage installed ?

---

### Post by PaulW2U on 2018-10-10
Thanks for your reply dino99. Yes, 'Recommends' are installed by default. 'ubuntu-desktop' is definitely in place and received an update yesterday.

My main concern is that I'm also seeing this in a live-session without any changes being made. This did not happen with my first live-session test which was with the beta ISO. So something has changed since the beta's release. I get other notifications such as a backup starting or finishing on my external drive it's just the notification of the initial connection of that drive that now fails to appear.

---

### Post by dino99 on 2018-10-10
oh, then the beta install package you have used is incomplete/corrupted/....  :confused: (is it the packaging/ubiquity/dependence fault ?)
i remember a bad experince of my own with a bionic fresh install  which let me with a working system, but getting 96 MTU instead of 1500 as usuel. Never found the solution to repare that bad installation. I have used a script to force MTU but finally did a new fresh install.

---

### Post by PaulW2U on 2018-10-10
The beta ISO was fine and.as I have already said yesterday's test using it was successful in a live session as the notifications were displayed. 

My installation after being updated and two recent ISOs are the problem.

I'm away from home for a while now. Hopefully someone can test today's ISO and confirm the bug or maybe point to what has changed recently so that I can investigate further.

---

### Post by P-I H on 2018-10-10
Downloaded the [COLOR=#3B3B3B][FONT=&quot]20181010.1[/FONT][/COLOR]  version and used "Try Ubuntu"
Used an USB with an iso image and used an USB with ext4 data.
I didn't got any notifications, but the USB:s were mounted OK. Got notifications when I unmounted the USB:s.
Installed the ISO with no problems. Actually looked very good.
Tested with the USB:s and got no notifications.
My main system running a fully updated Cosmic has actually the same behaviour.
Added me to the bug report.

---

### Post by PaulW2U on 2018-10-10
> **P-I H said:**
> Added me to the bug report.
Thanks for confirming. I don't like bugs that affect only me.  :)
I see from IRC that the Desktop Team are aware of the bug report. Hopefully they'll look into it and fix before next Thursday.

---

### Post by PaulW2U on 2018-10-10
Just received an update to gnome-shell (3.30.1-2ubuntu1) and amazingly the issue is fixed. So again, I find a problem, report a bug, post here and the fix appears within hours. Obviously it was already being worked on although I can't see anything in the changelog to indicate what the problem actually was.

I've also tested with today's second ISO, 20181010.1 and after fully updating a live session I see that the notification appears as expected when plugging in a USB drive. 

I'll mark this as 'solved' as the problem was rectified by an update.

---

### Post by P-I H on 2018-10-10
Yes, works OK on both my systems after update and reboot.

---

### Post by Frogs Hair on 2018-10-10
I get notifications for USB and  also read/write privileges are working again on Cosmic after a bug with Bionic.

---

