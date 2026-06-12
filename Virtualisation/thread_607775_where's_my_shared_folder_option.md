---
title: "where's my shared folder option?"
date: 2007-11-09
forum: Virtualisation
---

### Post by shmengie on 2007-11-09
hi there.

okay, so i've got vmware server 1.0.4 installed on my gutsy 7.10 box. i then installed xp sp2 as my guest. i then installed the vm tools. i can see and access the vm tools icon in the systray on the guest. but, in the vmware options, the 'shared folders' section never showed up. i've reinstalled the tools a couple of times to no avail. can anyone advise?

thx!

---

### Post by shmengie on 2007-11-09
okay, so i decided to try virtualbox instead. it has some problems (most notably, mounting the install cd. but, i found the fix for that). and, after installing the guest additions and running the 'net use' command from the guest (wxp, sp2), i am able to use the shared folders. BUT...

is it possible to share a folder outside of the host os? specifically, i have a second physical hard drive with data and reinstall exe's on it.and, most notably, what i want to do is: install itunes on my guest xp system and access my library on this second drive, without having to copy it over to my gutsy partition.

alternatively, if i can get the shared folders working in vmware, can i accomplish this?

thx!

---

### Post by P4man on 2007-11-12
I haven't found a way to let the windows guest access disks directly, but why would you ? You could share that "itunes" disk as a shared network folder through ubuntu.

---

### Post by shmengie on 2007-11-12
thanks for the tip. at this point, i've decided against virtualization and have instead opted for a dual-boot system: ubuntu as my full-time, day-to-day surfing, email, etc., box. and wxp for anything usb-device related (blackberry, harmony remote, ipod). i think that's a pretty good setup for a noob. and, as i get more comfortable with the architecture, (long-time windows guy. the folder hierarchy is quite befuddling for now) perhaps i can make to move to a full-timer.

anyways, thx again.

---

### Post by P4man on 2007-11-12
Keeping your dual boot for now makes sense, but why give up on virtualization ? its so much more convenient than rebooting each time.  Is there something not working in your VM that justifies rebooting each time? Or do you not have enough ram or perhaps?

---

### Post by shmengie on 2007-11-12
good question. even after finally getting the usb working via [this](http://www.virtualbox.org/wiki/User_FAQ), i could not get my blackberry working in my xp guest system. i could maybe live without updating my harmony remote, and i could prolly get rhythmbox configured to work with my ipod the way i want (rhythmbox see and plays my ipod. but, i couldn't get the podcast subscriptions to work), but i cannot be without or mess around with my blackberry.

maybe the next release of virtualbox will work better for me. the whole thing with having to fudge the boot cd irks me a bit. and, they should have the usb thing sorted out by then. maybe vmware is a better way for me to go, but i couldn't get the shared folder option to show, even after installing the vm tools.

so, for now, i'm a dual-boot kinda guy. and yeah, dual-booting is kind of a pain. but hey, change is painful! :)

---

### Post by theZoid on 2008-05-30
Has anyone got Blackberry Desktop Manager to sync with their Blackberry in VirtualBox?  If so, I'd like to know how.  I'm running VB 1.6.0 in Hardy with usb enabled.  XP virtual machine seems the RIM device, but desktop manager can't detect it.

Anyone?   :D

---

