---
title: "unable to launch Virtualbox VM"
date: 2012-04-10
forum: Virtualisation
---

### Post by davidson27 on 2012-04-10
ive been using vbox to run windows xp, i havent used it for a month or so and yesterday when i went to use it it wouldnt load. instead of seeing a version of xp running i got these...
 [IMG]http://ubuntuforums.org/attachment.php?attachmentid=215801&stc=1&d=1334040285[/IMG] ive tried installing the dkms and the uninstalling and reinstalling it again ive uninstalled vbox and reinstalled the newest version directly from oracle when i run /etc/init.d/vboxdrv setup in the terminal i get... [IMG]http://ubuntuforums.org/attachment.php?attachmentid=215802&stc=1&d=1334040638[/IMG]

anyone have any clue whats the deal ive heard that oracle is slow at kernel updates but i thought thats what the dkms was supposed to do, im not very fluent with ubuntu so any help would be nice.

---

### Post by Elfy on 2012-04-10
*Thread moved to **Virtualization**.*

---

### Post by DWade on 2012-04-15
> **davidson27 said:**
> ive been using vbox to run windows xp, i havent used it for a month or so and yesterday when i went to use it it wouldnt load. instead of seeing a version of xp running i got these...
 [IMG]http://ubuntuforums.org/attachment.php?attachmentid=215801&stc=1&d=1334040285[/IMG] ive tried installing the dkms and the uninstalling and reinstalling it again ive uninstalled vbox and reinstalled the newest version directly from oracle when i run /etc/init.d/vboxdrv setup in the terminal i get... [IMG]http://ubuntuforums.org/attachment.php?attachmentid=215802&stc=1&d=1334040638[/IMG]

anyone have any clue whats the deal ive heard that oracle is slow at kernel updates but i thought thats what the dkms was supposed to do, im not very fluent with ubuntu so any help would be nice.

could not see your pictures.  but when a new kernel loads in ubuntu you have to reload VirtualBox use this command in a terminal.
"sudo /etc/init.d/vboxdrv setup"

---

### Post by haqking on 2012-04-15
either follow the message presented to you which is to run

```
sudo /etc/init.d/vboxdrv setup
```

or just reinstall virtualbox

peace

---

### Post by SeijiSensei on 2012-04-15
> **haqking said:**
> ```
sudo /etc/init.d/vboxdrvsetup
```

Should be
```
sudo /etc/init.d/vboxdrv setup
```

In order for DKMS to rebuild the VBox kernel driver when the kernel updates, you need to have the source for the matching kernel headers.  After you install these the first time, they'll update along with the kernel.  You'll also need to install the build-essential package to provide the compiler.

```

sudo apt-get install build-essential
sudo apt-get install linux-headers-$(uname -r)
sudo /etc/init.d/vboxdrv setup

```

The $(uname -r) construct runs the uname command to get the current kernel version and returns it as a string.  For instance, $(uname -r) on my system returns "3.2.0-21-generic".

---

### Post by haqking on 2012-04-15
> **SeijiSensei said:**
> Should be
```
sudo /etc/init.d/vboxdrv setup
```

ahh yeah whoops typo, edited.

Cheers

---

### Post by davidson27 on 2012-04-16
Thanks SeijiSensei your suggestion fixed the problem.

---

