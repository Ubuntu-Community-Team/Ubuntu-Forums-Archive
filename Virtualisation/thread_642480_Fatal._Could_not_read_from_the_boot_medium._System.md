---
title: "Fatal. Could not read from the boot medium. System halted."
date: 2007-12-16
forum: Virtualisation
---

### Post by Proshka on 2007-12-16
Hi,

I want to use an original Win98 CD under VirtualBox to make my scanner work (a Lexmark). I managed to install VB without any trouble, gave 128 Mb RAM and 2 Gb disk space to the virtual disk, started, pressed F12, selected the CD-ROM option from the VirtualBox temporary boot menu and ended having this message: "Fatal. Could not read from the boot medium. System halted." I have also tried Qemu and VMWare (same results) and even burned another ISO, to no avail.

I am running Gutsy on a Toshiba Satellite A75-S226 with 512 Mb RAM and 1Gb swap.

---

### Post by benpage26 on 2008-02-29
Hi

I am getting the same problem on a toshiba sattelite also.
Is there a solution.

Ben

---

### Post by jg77 on 2008-12-25
Hey to all of you. I had the same problem and i solved it like this:

Go to system>administration>usersandgroups>manage groups>vboxusers
and set a mark at all

now log off and log in. after this the process has to work!

---

### Post by theophiles on 2009-04-15
I had to do that. I also noticed that I had to mount the cd drive inside VB :p . I can't believe I didn't notice that :roll: but thought I'd better post in case someone else didn't notice too.

---

### Post by judywawira on 2010-01-29
i have checked the manage groups and those are diasbled so i cannot change anything on them
What exactly do you mean i put the iso file for the VM to pick it?

---

### Post by Yitzhak on 2011-02-12
> **jg77 said:**
> Hey to all of you. I had the same problem and i solved it like this:

Go to system>administration>usersandgroups>manage groups>vboxusers
and set a mark at all

now log off and log in. after this the process has to work!

it dind't work for me

---

### Post by Rubi1200 on 2011-02-12
If you already have a VM installed and want to use a CD to do something else, try this.

When the VM entry is highlighted, do not start it but select Settings > Storage > you should see an icon for the CD drive. If it says Empty then highlight it and from the drop-down list on the right select your CD device then OK.

After that, try again to start > F12 > c to boot from CD drive.

Hope this helps.

Note that this seems to be only good for one session and I haven't found a way yet to make it permanent.

---

### Post by CharlesA on 2011-02-12
Follow what Rubi posted.

Thread close due to necro.

---

