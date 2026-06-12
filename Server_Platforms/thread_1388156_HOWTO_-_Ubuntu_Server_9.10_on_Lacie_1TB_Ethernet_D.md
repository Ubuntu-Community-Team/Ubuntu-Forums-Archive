---
title: "HOWTO - Ubuntu Server 9.10 on Lacie 1TB Ethernet Disk"
date: 2010-01-22
forum: Server Platforms
---

### Post by David.Johnson on 2010-01-22
Hi Everyone

First post here, so bear with me... I'm a long time linux user ('01 - '02) and cut my teeth on Gentoo. Switched over to Ubuntu about a year or so ago. I was rummaging through some old equipment & came across an old 1U rack mount Lacie 1TB Ethernet Disk NAS we had. These things ran an ugly flavor of Win XP Embedded, and I always had problems with it. So, I figured I would give Ubuntu Server a shot on it.

Browsing the Interwebs for a while yielded little clues - I guess these particular boxes were not that popular.. or everyone just stuck with XP on it. So I figure a HOWTO on it will at least be out there now.

I took an Ubuntu laptop & put Sun VirtualBox on it. I used this to create a VM from which to load Ubuntu Server on an USB HD I had. Worked great so far. The idea here is to use the 4 HDs in the Lacie just for RAID - software RAID mind you.. the box has no RAID controller. I would then use an USB HD to run the OS from. If there were any issues, I could just get a new USB HD without worrying about the HDs & their data.

Initial boot.. well, it didn't. Stuck on 'Loading Grub...'. Tried a few different HDs and eventually one booted! Then it started to randomly crash... so things obviously were not going well. mdadm was not working well either.. not rebuilding the array after a reboot, etc. Something was obviously wrong. Investigation yielded that this box runs a Via C3 processor... and that was causing the problems. In order to run the Via C3 you need the -386 kernel, and this is not installed by default with Ubuntu Server. So here's how I fixed it & resurrected this old NAS box :D

Get a USB HD and install Ubuntu Server using Virtual Box with USB support.
Mount the HD on your Linux machine. I'll call it /media/usbhd
Open Terminal and mount your machine's /proc and /dev to the HD

#sudo mount -o bind /dev /media/usbhd/dev
#sudo mount -o bind /proc /media/usbhd/proc

Now, chroot into the HD

#sudo chroot /media/usbhd

Now, all your operations will be performed with the USB HD as your new root system. You can then apt-get to install your 386 kernel of choice

#sudo apt-cache search kernel | grep 386

should show you the available options. apt-get will configure your grub to work with the new kernel since you chroot'ed into the HD.

Now, exit and unmount the HD. Connect it to your Lacie box and watch it boot happily!

I've been running for  a few days now, activated the RAID array and rebooted with absolutely no issues.

FYI - the Lacie network adapter is recognised as eth2 by default. You can deal with that or change it however you like. Just took me a second to realize eth2 was the interface.

Hope this helps someone!

---

### Post by frillip on 2010-07-12
Exactly what I've been looking for. Been wanting to rid my Ethernet Disk of that woeful Windows XP Embedded for a long time.

Thanks!

Phil

---

### Post by alpha1echo on 2013-02-26
Thanks, I inherited an 8TB one of these and working with XP embedded is unbearable.

Is there a way to install Linux on the internal storage rather than booting from a USB disc?

---

### Post by stascrash on 2013-10-31
hey Alpha1echo,
i was looking for the same answer, i came across this link, maybe it will help you. i know its been a little while since your post, but what if ?)?
i haven't tried this myself, but if you do get to it - please let me know if this worked out for you and also, list specs of you lacie box.
link: [http://lacie-nas.org/doku.php?id=debian_install](http://lacie-nas.org/doku.php?id=debian_install)

---

