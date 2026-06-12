---
title: "Unable to boot Ubuntu Server on Dell R710 with UEFI, raid5 VG"
date: 2020-10-21
forum: Server Platforms
---

### Post by Surfrock66 on 2020-10-21
I'm having a very strange issue, and solutions other people have used appear to not work for me.  I'm stumped and not sure what to do.  I installed Ubuntu Server 19.10 last year, and at the time tried to boot UEFI, but the system wouldn't boot at all so I switched back to Legacy.  The system was consistently unbootable, and I should have aborted this operation then, but the hardware it replaced died and I had to rush it into production knowing as long as it didn't reboot it stayed up fine.  At the time I believed it was an installer bug which I submitted here: [https://bugs.launchpad.net/subiquity/+bug/1857789](https://bugs.launchpad.net/subiquity/+bug/1857789)

This is a Dell R710 with a single Raid5 virtual disk partitioned with a 1GB UEFI partition and 3.99TB for everything else.

I do have backups, but I want to avoid reverting to backups and rebuilding from scratch for as long as I can.  The system was working perfectly so long as I didn't reboot it, and I would rather try to solve the boot problem now than all the other problems that potentially coming up off backups.

Following a kernel update, I could no longer get the system to boot from GRUB.  It worked so long as I used the older kernel.  I documented the process in 2 threads:
[https://www.linuxquestions.org/questions/linux-server-73/ubuntu-server-boots-to-grub-rescue-after-every-kernel-upgrade-have-to-revert-to-older-kernel-to-boot-wrong-disk-in-grub-4175683582/](https://www.linuxquestions.org/questions/linux-server-73/ubuntu-server-boots-to-grub-rescue-after-every-kernel-upgrade-have-to-revert-to-older-kernel-to-boot-wrong-disk-in-grub-4175683582/)
[https://askubuntu.com/questions/1282224/ubuntu-server-boots-to-grub-rescue-after-every-kernel-upgrade-have-to-revert-to](https://askubuntu.com/questions/1282224/ubuntu-server-boots-to-grub-rescue-after-every-kernel-upgrade-have-to-revert-to)

Following that advice, I did the grub-install but the system now is completely unbootable.  I've tried a ton of stuff and the conclusion I've seen is that I need to switch to UEFI.  This also doesn't seem to work; initially it gave me an issue related to secureboot (which is not supported on the R710) grub rescue, when I bring up ls, just shows (hd0) and cannot find the gpt partitions on it.  At one point I almost got it to boot, though there was an issue which led me to google a solution saying to delete shimx64 and copy grubx64 in its place, and that was the final nail in the system.

I booted to a live environment and ran boot-repair, with secureboot support disabled (though I tried the other way as well and it didn't matter).  Here is the output from boot-repair: [https://paste.ubuntu.com/p/M5jTK6yVZX/](https://paste.ubuntu.com/p/M5jTK6yVZX/)

Past that, when I went into the UEFI boot manager, I made sure the option for "ubuntu" pointed to the only drive it saw on the RAID controller, then EFI/ubuntu/grubx64.efi.  When doing this, I'm returned to a grub rescue screen when I try to manually boot, I get "Error: no such partition" and when I ls, I just see (hd0) which I cannot ls as it says "Filesystem is unknown".  When I boot to a live environment, the drive works fine.

Is there anything else I can do to get this system back or am I starting from scratch?

---

### Post by oldfred on 2020-10-21
With some older BIOS systems and then with some newer systems there have been issues of boot files too far into a drive. Most of those were resolved, but I thought that was up to 2TiB.
You are using a 4TB drive. I might try a much smaller / (root).
Do you have a lot of software that goes into / normally. Servers can have large databased or web sites.
But my desktop install is in a 30GB partition and uses about 9GB of that including /home, but all my data is in separate data partition(s).

---

### Post by Surfrock66 on 2020-10-22
I've posted this to linuxquestions.org as well and gotten some feedback there, I'll summarize the current state now: [https://www.linuxquestions.org/questions/linux-server-73/ubuntu-server-boots-to-grub-rescue-after-every-kernel-upgrade-have-to-revert-to-older-kernel-to-boot-wrong-disk-in-grub-4175683582/](https://www.linuxquestions.org/questions/linux-server-73/ubuntu-server-boots-to-grub-rescue-after-every-kernel-upgrade-have-to-revert-to-older-kernel-to-boot-wrong-disk-in-grub-4175683582/)

I went through the RAID configuration; as far as I can tell everything is correct. It's a 5-disk raid5 made from 1TB disks, which specifically should be ok as the PERC 6/i has an issue with disks over 2TB in size (not virtual disks, individual disks, reference: [https://community.spiceworks.com/top...-dell-perc-6-i](https://community.spiceworks.com/top...-dell-perc-6-i) ). The bootable VD is correct (the only one) and "Enable controller BIOS" is checked. Pictures attached.

I created the partition (it's 16MB because if I didn't do that, the efi partition got moved to start at 14MB on the disk). Picture attached.

I did the grub install exactly as indicated from the live environment:

```
mount /dev/sda2 /mnt
grub-install --target=i386-pc --boot-directory=/mnt/boot /dev/sda
```

It said no errors to report. I rebooted, it returned to grub rescue. When I do "ls" I get the following:

(proc) (hd0) (cd0)

When I do set I see "prefix=(hd0)/EFI/ubuntu" but when I do ls of (hd0) or any sub directory I get "error: unknown filesystem."

I guess grub is no longer seeing the gpt partitions?  In gparted from the live environment, everything looks fine and I can see all my data.  Doing "insmod part_gpt" doesn't help

---

### Post by darkod on 2020-10-22
Couple of things... First, I have no extensive experience with physical servers, so what I say might not apply fully. :)

1). When doing grub-install from live mode, be careful whether it is actually UEFI. I can't say 100% if you only need to make sure you boot the dvd/usb in UEFI mode so that grub is installed as UEFI. But what I do know is that when you want an UEFI installation then you start the install iso in UEFI mode. Otherwise it installs legacy grub.

2). Using raid5 might not work, period. When using SW raid with mdadm I believe the consensus was not to use arrays that split the boot files in pieces. So, only raid1 (no raid0 or raid5 or raid6). Not sure if that still applies. But it could be your issue. Even though the OS will see one virtual disk, the actual files will be written in chunks on the actual disks. Your problem is that you have HW raid. If you used mdadm the solution is easy because it works with partitions, not whole disks. Make a small partition on each disk and corresponding raid1 array for root, and the rest big raid5 array for data.

Bottom line, I think your problem is actually the HW raid5 but I can't actually prove it. :)

---

### Post by Surfrock66 on 2020-10-22
Interesting, and sounds plausible...in that case, my best bet is to revert to legacy/bios boot?  If so, is that a safe thing to do?

---

### Post by darkod on 2020-10-22
It depends. But legacy vs uefi boot still does not resolve your raid5 problem, if it is really a problem.

My personal preference is legacy boot with gpt partition table on the disks. But on desktop (standard) HW I have seen cases where some motherboards do not like that combination. For example my desktop Intel NUC6 wanted to work only with msdos table when choosing legacy boot, and gpt table when choosing uefi boot. But I couldn't mix gpt table with legacy boot.

You have server HW so it might be more tolerant of those combinations.

I would say your bigger problem is the HW raid, not the type of boot.

---

### Post by Surfrock66 on 2020-10-22
I just realzied, I have a 64GB SSD sitting around, should I toss that in and try to install the efi partition to that, then have it recognize the GPT partitions on the HW raid?  I think I understand the process, but I'd like someone to walk through how they'd do it to make sure I don't screw it up.

---

### Post by darkod on 2020-10-22
In such case I would put the root (OS) on that disk, and use the raid5 array for big data partition. For example mount point /data or similar.

But not just EFI partition on the SSD. If you do put it in the server, use all of that for the system partition.

PS. Of course, when I say one big data partition it doesn't literary have to be one fixed partition. You can use the raid5 array to be physical device for LVM and then work with LVs according to your needs and with all the flexibility it offers you.

---

### Post by Surfrock66 on 2020-10-22
I want to avoid rebuilding; it's not gonna be practical to move / to the ssd without reinstalling, is it?  I should be able to move the boot environment there though, right?

---

