---
title: "Take my ubuntu install to a new drive?"
date: 2009-05-18
forum: The Cafe
---

### Post by robllewellyn on 2009-05-18
Hi all

I'm a n00b to ubuntu. Weeeellll someones gotta be :)

Its working out for me on my new netbook, does exactly what I need it to do, have learned loads about Grub specifically and terminal commands, although I am still at the "copy and paste code from the forum without really knowing what its doing" phase of my education. Learning slowly.

I am planning to swap my HDD for a SSD and I wondered if its possible to pack up my current ubuntu installation, applications and config and move it wholesale over to my SSD when I install it.

I can obv just do a fresh install (always cathartic) but I'd like to save some time if I can.

Is this possible or beyond my n00b skills?

Any advice/discussion happily received.

Rob

---

### Post by monsterstack on 2009-05-18
What I always used to do was copy the contents of my /home folder over to a new install, and re-install the packages. All of the user configuration settings are stored in your /home/user folder, so any settings you had before instantly take effect. It's not an ideal solution, though. I too wonder if there's a better way of doing this.

---

### Post by toupeiro on 2009-05-18
monsterstack is on the right page.

If you are not upgrading versions of ubuntu, you could do the following:

From a command line type:

> dpkg --get-selections | grep install | awk '{print $1}' >> ~/installed_applications.list

Then take that file and put it on a usb disk or something.

back up your home directory as monsterstack stated, then copy that file into your home directory along with all the other contents you backed up.

now, type:

> sudo apt-get install `cat ~/installed_applications.list`

What you already have, it will tell you that you already have, what you don't have, it will bring up to the same level you had on your old system.

---

### Post by frodon on 2009-05-18
I did this once and wrote a tutorial about it unfortunately only in french. All i can say you is that it is a bit time consuming but it works like a charm.
[http://doc.ubuntu-fr.org/installation/transferer_son_installation_sur_un_autre_disque](http://doc.ubuntu-fr.org/installation/transferer_son_installation_sur_un_autre_disque)

Basically you need to ghost your OS(s) with the tool of your choice (an additional backup is always more secure).

You need to:
- Put your new disk in place and do the partition table (think to add the boot flag on the ubuntu partition).
- Boot a live CD and put yout ubuntu partition image on your new ubuntu partition.
- Modify you fstab through the live CD to fit your new partition uuid
- Modify your menu.lst through the live CD to fit your new partition uuid
- Modify you device.map file to point on the right partition names
- Install GRUB from the live CD

And you're done and your install is back running as it was previously (you may need to enter the BIOS to select your new drive as device to boot on).

---

### Post by robllewellyn on 2009-05-18
thanks for the responses guys, appreciated.

I'll give them a go later this evening.

Rob

---

