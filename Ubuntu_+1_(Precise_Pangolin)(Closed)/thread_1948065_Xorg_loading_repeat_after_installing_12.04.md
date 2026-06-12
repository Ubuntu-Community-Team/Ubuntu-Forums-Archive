---
title: "Xorg loading repeat after installing 12.04"
date: 2012-03-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by oc666 on 2012-03-27
Hey All
As a tester of 12.04 beta, I've installed Precise Pangolin. The installation was fine. After reboot I get the X mouse Icon but after it X shutdown and restart. This happends repeatedly and stuck with this scenrio until I shutdown computer. I've try to move to console but I can't cause each time it restart the X the focus back to the X from the console. Is there any shortcut to shutdown X and go to console?
I've try rescue option in the grub menu but nothing helps in the menu popup after choose that, including X safe mode (same scenrio happends again).
I'm using Dell e6220 and upgraded from 11.10.

Please advice.

---

### Post by oc666 on 2012-03-29
I've manage to get into the console root via rescue option in the grub and click on root shell option in the rescue menu. 
Eventually, the filesystems are read-only and I can mount my home partition cause it's encrypted filesystem.
Please advise.

---

### Post by dino99 on 2012-03-29
in recovery mode from grub menu, need to check that:

- xorg.conf is removed (sudo rm /etc/X11/xorg.conf)
- the graphic driver is activated (sudo jockey-gtk)
- third party repo are not outdated, like ppa (sudo synaptic)

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a (can take a while, dont stop it)

sudo rm ~/.local (clean rebuilt on next boot)
sudo reboot

---

### Post by oc666 on 2012-03-29
> **dino99 said:**
> in recovery mode from grub menu, need to check that:

- xorg.conf is removed (sudo rm /etc/X11/xorg.conf)
- the graphic driver is activated (sudo jockey-gtk)
- third party repo are not outdated, like ppa (sudo synaptic)

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a (can take a while, dont stop it)

sudo rm ~/.local (clean rebuilt on next boot)
sudo reboot

Thanks for responding.
I can't mount my disks. The root is read-only on rescue and home is encrypted. Perhaps I need to run those command from chroot. How could I chroot from Ubuntu installation disk?

Thanks

---

### Post by dino99 on 2012-03-29
Mount Encrypted Home Directory

Type the following command:
$ ecryptfs-mount-private

---

### Post by effenberg0x0 on 2012-03-29
Or, as a secondary option to Grub Rescue, you could simply switch to a VT (Ctrl+Alt+F6 for VT6, for example) and kill X so you have a chance of looking at logs at /var/logs, grep them, and see what's happening. I find it more comfortable than rebooting / using rescue mode.

Regards,
Effenberg

---

### Post by oc666 on 2012-03-29
> **effenberg0x0 said:**
> Or, as a secondary option to Grub Rescue, you could simply switch to a VT (Ctrl+Alt+F6 for VT6, for example) and kill X so you have a chance of looking at logs at /var/logs, grep them, and see what's happening. I find it more comfortable than rebooting / using rescue mode.

Regards,
Effenberg

I can't switch to a VT cause it looks like X is killed and start over. This happens in infinite loop. I try even fail-safe-X and it does not help. I think chroot required. How could I chroot ubuntu from liveCD?

---

### Post by oc666 on 2012-03-29
> **dino99 said:**
> Mount Encrypted Home Directory

Type the following command:
$ ecryptfs-mount-private

I've try this one but I'm receiving:
```

$ ecryptfs-mount-private
Inserted auth tok with sig [...] into the user session kerying 
open: No such file or directory
Error locking counter

```
I assume this is happens cause the root file-system mounted as read-only. How could I remount it as writable.

---

### Post by cryptotheslow on 2012-03-29
When first booting into recovery remount option to mount the / filesystem read/write - press ENTER when prompted:
[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/recoveryremount2.png[/IMG]

You are then presented with a slightly different menu - select the bottom option to drop to a root shell:
[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/recoveryconsolerootprompt.png[/IMG]


I have a feeling you may also need to su to your own username before that ecryptfs command will work (just a thought - not sure).

---

### Post by oc666 on 2012-03-29
I don't have remount option in the rescue menu.

---

### Post by oc666 on 2012-03-29
I've chroot in liveUSB and I've seen that not all upgrades was applied.
I've run:
```

dpkg --configure -a

```

---

### Post by effenberg0x0 on 2012-03-29
You should have the option to remount rw... anyway, you can do it manually:
mount -o remount,rw /

Regards,
Effenberg

---

### Post by oc666 on 2012-03-29
Thanks you all. After dpkg -a --configure, The X works fine.
Thanks for wonderful support, Ubuntu community!

So now, let's continue to testing.

---

