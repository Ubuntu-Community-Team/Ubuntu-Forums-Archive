---
title: "Ubuntu 10.10 and VMware Player 3.1"
date: 2010-08-11
forum: Virtualisation
---

### Post by fjgaude on 2010-08-11
Has anyone gotten these two, the subject line, to work yet?

---

### Post by karolinger on 2010-08-15
I have tried without success.

---

### Post by astrotest on 2010-09-05
Go here:
[https://bbs.archlinux.org/viewtopic.php?pid=815476](https://bbs.archlinux.org/viewtopic.php?pid=815476)

read the last post:
"
For 2.6.35 kernel and VMware7.1.1, there's a script to patch the VMware sources :
$ cd /tmp
$ wget [http://www.sputnick-area.net/scripts/vm &#8230; .6.35.bash]("http://www.sputnick-area.net/scripts/vmware7.1.1-patch-kernel-2.6.35.bash")
# chmod +x vmware7.1.1-patch-kernel-2.6.35.bash
# ./vmware7.1.1-patch-kernel-2.6.35.bash



First install VMware Player. 

Then apply the Patch (.bash-command).
Then execute VMware Player and wait a few minutes to compile and finish. 



It works with 10.10 and VMware Player 3.1 

Just installed this a few minutes ago. 

It WORKS!

---

### Post by fjgaude on 2010-09-06
Thanks, that gets us going. I wonder if VMware will fix Player as 10.10 comes out of Beta testing.

---

### Post by schms on 2010-09-10
It works for me.


# uname -a
Linux niesen 2.6.35-20-generic #29-Ubuntu SMP Fri Sep 3 14:55:28 UTC
#

1. First, uninstall current vmware-player
2. Download vmware-player 3.1.1 and install it
3. Follow the instruction in the top post
4. Start vmware-player for the first time

---

### Post by Azazel on 2010-09-11
thanks! works great!

note to others: make sure the package build-essential OR patch is installed before running the patch

if you run the patch and it fails, it won't run again (you just get some output that says hey this is already installed or something like that). what i did to fix this was go into the patch and remove lines 177, 178, 179, and 181, save and run patch again.

---

### Post by fjgaude on 2010-09-14
Okay, getting around to installing Player into a fresh 10.10 Beta Ubuntu.

How do you install Player 3.1.1 when there is no installer to do it? I can't patch the kernel code if I can't install the Player... a catch-22 situation. Can you install the Player Installer separately?

Help!

Please!

---

### Post by =not4prophet= on 2010-10-27
I had VMware Player 3.1 installed under 10.04.  The bash script successfully repaired the install after my upgrade to 10.10.

---

### Post by fjgaude on 2010-10-27
> **=not4prophet= said:**
> I had VMware Player 3.1 installed under 10.04.  The bash script successfully repaired the install after my upgrade to 10.10.

Yes, mine too. Always some workaround works! <smile>

---

### Post by WiFi Ed on 2010-10-31
Thank you very much for this post, I was stumped trying to install VMware in 10.10, but this patch took care of the problem!

Thanks again!

---

### Post by Neo@Matrix on 2011-02-16
Might be useful for less experienced users this way:
*Download VMware-player-xxx.xx..bundle, 
*Right click on it,chose permissions,mark "Allow executing file as program" and change permissions to read-write for all .
*Run gksu nautilus from terminal.
*navigate to the VMware file.
*Double click on it.
Follow the on screen instructions.

That is all I needed to make it work like charm.

Hope it helps.Also might work for similar install issues.

---

### Post by fjgaude on 2011-02-17
As best as I can tell VMware Player 3.1.3 installs with versions of Ubuntu from 9.04 to 10.10 without a patch, it just installs.

Now we wait for 3.1.4 to work with 11.04. <smile>

---

