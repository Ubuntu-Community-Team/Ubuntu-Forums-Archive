---
title: "Darter Upgrade Edgy -&gt; Feisty : had to edit fstab in between"
date: 2007-05-10
forum: System76 Support
---

### Post by cowbean on 2007-05-10
In case this helps anyone:

I waited to upgrade to Feisty (via Upgrade Manager "Upgrade" over network option) until there was a fix for the no-CD hanging problem.  Once I saw that there was apparently a fix, I went ahead with the upgrade.

The upgrade seemed to happen flawlessly till it got to the last step, where it should reboot into the newly upgraded version.  Upon reboot, I was kicked out to a console, logged in as root, with a hilarious message to the effect of:

""apt-get" is not currently installed.  Install it by running "apt-get install apt"."

I got a good laugh out of that one, and showed it to my coworkers.

I poked around and found out that fdisk -l revealed sda (scsi?) drives, whereas /etc/fstab listed the drives as /dev/hda .  Vi was not accessible, so I thought I'd get to enjoy the adventure of learning ed.  However, someone suggested nano, and it turns out that worked. ed will have to wait for next time, I guess.

I backed up /etc/fstab, then edited it to change all "hda" references to "sda".

Strangely, when doing sudo reboot, x started and the Gnome login window appeared.  I could log in, but lots of things were broken-looking.  I rebooted.

Again, I get kicked out to a root console, and again notified of the existential paradox regarding apt.  This time, fdisk -l revealed all hda drives, and of course /etc/fstab still referenced sda.  So I went and restored the backup I had made before editing.

Rebooted after that, and everything has worked well since.

---

### Post by AusIV4 on 2007-05-11
I ran into the same problem when trying to upgrade. I gave up, reverted to a back-up of edgy, and did a fresh install of feisty on another partition. It is interesting to know how the problem could have been resolved though.

---

### Post by thomasaaron on 2007-05-11
cowbean, I'm glad you're on our side!
Tom

---

### Post by cowbean on 2007-05-11
> **thomasaaron said:**
> cowbean, I'm glad you're on our side!
Tom

As if there was any other side to be on.  ;) 

Seriously though, at least in linux you have a chance to tinker and maybe learn how to fix something.  Using windows is like being force-fed incompetence, in comparison.

---

