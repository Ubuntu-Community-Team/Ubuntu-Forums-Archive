---
title: "Cant get GRUB_GFXMODE to work with LVM encrypted partitions"
date: 2012-06-24
forum: Server Platforms
---

### Post by [StarChild] on 2012-06-24
Hi, I'm quite new to linux and especially to Ubuntu Servers.
So, I installed Ubuntu Server 12.04 and during the installation I chose Guided LVM partition with encryption (whole disk) and replaced all old partitions on the disk. After the installation process I was going to change the GRUB_GFXMODE in /etc/default/grub  to a known working value (actually tested with several), and is valid according to vbeinfo. This seemed to have no effect at all, which was strange because it have worked in the past (without encrypted disks). So I started to troubleshoot and find out that it had to do with the encryption. If I do exactly the same installation procedure but without the encryption, just guiden lvm option, GRUB_GFXMODE works just fine. I have also made a virtual machine that confirmed the problem just to verify that it has nothing to do with my physical PC. Other parameters in /etc/default/grub like boot delay take effect as it should be. I also tested without encrypted home folder to exclude that. I also cant find someone else with this problem when I google it, so Im stuck.

This is with a completely clean installation, and no other OS on the disk. Tested directly after the installation without changing anything else. Tested without apt-get update/upgrade and also after the upgrade of all available updates. I have used update-grub. "grub-install --version" gives me 1.99-21ubuntu3.1

Why is this so? Is it some restriction that I don't know about? I cant understand why grub should have problem with this just because I use encrypted partitions, /boot isn't encrypted right?

If you need any info from my system or partitions just let me know and I will get it for you.

//StarChild

---

### Post by [StarChild] on 2012-06-28
bump

---

### Post by drs305 on 2012-06-28
Did you install it using the Alternate CD? I know from posts on this forum that systems using LVM and RAID should be installed using the Alt CD rather than the normal CD. (I don't have experience with either, so that is about all I can offer.)

---

### Post by [StarChild] on 2012-06-28
> **drs305 said:**
> Did you install it using the Alternate CD? I know from posts on this forum that systems using LVM and RAID should be installed using the Alt CD rather than the normal CD. (I don't have experience with either, so that is about all I can offer.)
No, I use ubuntu-12.04-server-i386.iso and no RAID.
I also disabled my network card within the VM so grub didn't get updated during the installation process. And with grub 1.99-21ubuntu3 doesn't work either. Also tested install with no extra modules at all.

---

### Post by nosmadar on 2012-06-29
Are you by chance using a KVM switch?  I've had some bad experiences and eventually gave up and hard wired a monitor to my server.

---

### Post by [StarChild] on 2012-06-30
> **nosmadar said:**
> Are you by chance using a KVM switch?  I've had some bad experiences and eventually gave up and hard wired a monitor to my server.
Nope, no KVM either. Right now I have monitor (VGA cable, its an old racket-server), USB keyboard, nothing more.

---

