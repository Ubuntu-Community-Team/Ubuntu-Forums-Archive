---
title: "Setting up dual boot with 9.10 Karmic"
date: 2009-11-02
forum: System76 Support
---

### Post by andrewdied on 2009-11-02
Does the knowledge base [article]("http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine") for setting up a dual-boot machine with linux and windows still work for a fresh karmic install?  It uses the new grub, so it looks like menu.lst goes away for grub.cfg, and seems more "spread out".  

I have a single hard drive at /dev/sda, with a (now blank) windows partition at /dev/sda1, a root ext4 partition at /dev/sda2, and swap and home later down in extended partitions.

I think this still makes my windows hd(0,0) but I thought I'd check.  The windows partition is not currently marked bootable, but I reckon the windows installer will take care of that, if needed.

---

### Post by sliketymo on 2009-11-03
> **andrewdied said:**
> Does the knowledge base [article]("http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine") for setting up a dual-boot machine with linux and windows still work for a fresh karmic install?  It uses the new grub, so it looks like menu.lst goes away for grub.cfg, and seems more "spread out".  

I have a single hard drive at /dev/sda, with a (now blank) windows partition at /dev/sda1, a root ext4 partition at /dev/sda2, and swap and home later down in extended partitions.

I think this still makes my windows hd(0,0) but I thought I'd check.  The windows partition is not currently marked bootable, but I reckon the windows installer will take care of that, if needed.

Good info here:

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by thomasaaron on 2009-11-03
Good point.

menu.lst doesn't exist anymore.

We are going to have to update that article. If anyone out there already has this figured out, feel free to update it. Otherwise we'll get to it once we get caught up.

---

### Post by andrewdied on 2009-11-03
> **sliketymo said:**
> Good info here:

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

That's a good one for a karmic 9.10 install upgraded for 9.04, since it uses the old grub.  I'm working from a fresh 9.10 install, so it's using grub2.

[This]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") may be the way to go, but anything that uses chroot is really higher math.  You'd think there was an easier way.  

I can understand why they rewrote part of grub (who mixes # comments with commands that start with # in a config file?), but the GNU folks sometimes make working with windows deliberately harder than it needs to be.

[This]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") article is great for earlier versions, and will probably be edited later to include grub2.

---

### Post by dar25 on 2009-11-03
Yep, menu.lst is no longer there for new 9.10 installs.
I've seen references to /etc/default/grub and /boot/grub/grub.cfg instead.

---

### Post by andrewdied on 2009-11-03
> **thomasaaron said:**
> Good point.

menu.lst doesn't exist anymore.

We are going to have to update that article. If anyone out there already has this figured out, feel free to update it. Otherwise we'll get to it once we get caught up.

I've found two other good resources, but haven't tried to put them in practice yet.  I need to have some time set aside before I go down that route.  The first one is [http://members.iinet.net/~herman546/p20.html]("http://members.iinet.net/~herman546/p20.html").  It has various sub-pages that talks about grub2.  The second is Ubuntu's [https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2").  It's nice because it goes through the directory and file structure of grub2, which is *much* different than grub legacy.

It may be that I can do something as simple as installing windows in /dev/sda1 (I left the first primary position available because Windows XP can get cranky if it's not there), then run ```
sudo update-grub2
```

---

### Post by andrewdied on 2009-11-06
I managed to get dual-boot Ubuntu and XP working, and may have done it the "right" way, too.

Configuration: I started with Ubuntu 9.10 (karmic) installed.  The partitions looked like this:
[LIST]
[*]sda1: fat32 (for windows)
[*]sda2: /root, ext4, *bootable
[*]sda3: extended partition
[*]sda4: /home, xfs
[*]sda5: swap
[/LIST]

After backing up my /home partition I installed XP on sda1.  The install told me it was going to mark sda1 bootable, and remove the boot flag on sda2.  (Obviously, in more Windows-drive language.)   I did a long format, ntfs, on sda1.  Install went perfectly.

Next I used the 9.10 beta CD I had and booted into it "live."  For testing I did "boot the first hard disk", but that just booted Windows.  The steps I followed are in the Ubuntu wiki article at [https://wiki.ubuntu.com/Grub2#Recover Grub 2 via LiveCD]("https://wiki.ubuntu.com/Grub2#Recover Grub 2 via LiveCD")  I got the expected "Cannot find list of partitions!" error, but that was OK.

The short version of those commands is:
```
sudo mount /dev/sda2 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
update-grub
grub-install /dev/sda
<See list of partitions error>
^D
sudo umount /mnt/dev
sudo umount /mnt
<reboot into Ubuntu>
sudo update-grub
sudo grub-install

```

---

