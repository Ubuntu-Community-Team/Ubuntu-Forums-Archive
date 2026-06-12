---
title: "UEFI boot issues"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by pulpo69 on 2012-04-02
i've build a new computer just now. all new motherboards have an uefi-bios.
i'm unable to install ubuntu (12.04 or 11.10), because if i try it only
shows up: install, running ubuntu without install, repair and no one of the
options work, after choosing one black screen. no windows installed, new hd.

---

### Post by BigCityCat on 2012-04-02
Insert liveCD, open terminal
Find linux partition

> sudo fdisk -l

confirm that **LINUX** is sda[COLOR="Red"]#[/COLOR] Where # = **YOUR** Linux partition

> sudo mount /dev/sda# /mnt

> sudo grub-install --boot-directory=/mnt/boot /dev/sda

If no errors on previous commands reboot into working system and run this:

> sudo update-grub

---

### Post by oldfred on 2012-04-02
Moved to new thread. Issues may be enough different that previous thread does not apply.
for ref old thread was on UEFI but different user:
[http://ubuntuforums.org/showthread.php?t=1941973](http://ubuntuforums.org/showthread.php?t=1941973)

@BigCityCat
Your instructions are correct if in BIOS boot mode which many system with UEFI have.

Lets see what is installed where. It also is possible it is booting and it is a video issue after grub has loaded.

Run the boot info script from this using liveCD or USB. Only the git version which now Boot-Repair uses has been updated to also parse efi partitions.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

