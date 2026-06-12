---
title: "Net-upgrade from Fedora to Ubuntu - without physical access to server"
date: 2005-02-03
forum: Server Platforms
---

### Post by steffen on 2005-02-03
Hi folks,

I have a Fedora Core 3 server, without any important stuff on it. This server is not accessible by me physically (it's in another part of the world), but I am in complete control of the server through SSH, and I'm able to re-install Fedora automatically thrugh a web control panel, so if anything goes wrong it won't be a problem

Is it possible, under this system, to install Ubuntu? I.e. can I download a CD image, boot from the CD image through SSH, remove Fedora, and install the system without touching it physically?

If anyone thinks this could be possible, I will attempt this - partly to see if it I manage, and partly because after having run Ubuntu I've become a fan, and I'd really want to use Ubuntu for all my Linux operations!

 8)

---

### Post by alastair on 2005-02-03
I'd be vaguely interested in if this is possible - but  I would say that you would need the remote help i.e. physical on-site. The problem is the reboot and making sure you can establish  the network link. On-site help is essential I think.

---

### Post by flyinglizard on 2005-02-04
This can be done but it takes some planning.  I have done it in the past using the swap partiton as a temporary boot point. 

A quick google for 'debian "remote install"' came up with the following:

[http://www.underhanded.org/papers/debian-conversion/remotedeb.html](http://www.underhanded.org/papers/debian-conversion/remotedeb.html)

You can find more information on using debootstrap for Ubuntu in the forums.  

If possible practice on a computer you have physical access to.

---

### Post by az on 2005-02-04
With debian, you can try:

[http://www.debian.org/releases/stable/i386/ch-preparing.en.html#s-linux-upgrade](http://www.debian.org/releases/stable/i386/ch-preparing.en.html#s-linux-upgrade)

apt-get dist-upgrade from woody to warty is working perfectly.


You need to have the partition to which you will be chrooting already made, though.

---

### Post by jdong on 2005-02-08
Risky, but not impossible. What you need is a huge initrd, like a few hundred MB, that can hold a preconfigured Ubuntu base. I have no clue how to make that kind of initrd though!!

---

### Post by Rottweiler on 2005-02-16
I know some folks who do Fedora upgrades remotely by booting from the FC disks and having a second machine that is connected to the target via a serial (tty) port. And they control it by doing a character-mode install via that method.
 
 The same could be done for Ubuntu and it would be fairly certain you wouldn't lose contact with it since the contact point would not be the one being upgraded.
 
 Whatever you do, make sure to get sshd installed and running before rebooting the Ubuntu system as it is not there by default.

---

