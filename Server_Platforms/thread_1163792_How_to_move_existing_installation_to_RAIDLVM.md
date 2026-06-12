---
title: "How to move existing installation to RAID/LVM?"
date: 2009-05-19
forum: Server Platforms
---

### Post by Xianath on 2009-05-19
I have an Ubuntu Server 9.04 installation that runs from a single old 80GB IDE hard disk. I have six 1TB disks in this box all set up with software RAID and LVM2 and would like to get rid of the IDE disk and run entirely off the RAID.

Here is what each of the six SATA disks looks like:

```

/dev/sda1   *           1           7       56196   83  Linux
/dev/sda2               8        3977    31889025   fd  Linux raid autodetect
/dev/sda3            3978        4060      666697+  82  Linux swap / Solaris
/dev/sda4            4061      121601   944148082+   5  Extended
/dev/sda5            4061       28380   195350368+  fd  Linux raid autodetect
/dev/sda6           28381       52700   195350368+  fd  Linux raid autodetect
/dev/sda7           52701       77020   195350368+  fd  Linux raid autodetect
/dev/sda8           77021      101340   195350368+  fd  Linux raid autodetect
/dev/sda9          101341      121601   162746451   fd  Linux raid autodetect

```

I have sd[ace]1 and sd[bdf]1 in two md RAID0 volumes set up as a pair of PVs in a mirrored LV to serve as my boot partition (/dev/System/Boot). I also set up sd[abcdef]2 in RAID5 as a single PV/LV to use as my root partition (/dev/System/Root).

This is a headless box and plugging in a monitor will be a major pain. The BIOS is already set up to try IDE and then the first two SATA disks (hence the interleaved RAID0 disks). The question is, how do I safely move everything from the IDE HDD to the LVM2 setup without breaking stuff up? Basically I want to set it up, power off, remove the IDE HDD, boot it up and it should work. Everything I've found online so far describes how to *install* on a RAID/LVM2 but this is not an easy option to pursue. Any tips, hints or pointers to a FAQ I missed?

Thanks,
Peter

---

### Post by windependence on 2009-05-19
Not sure how this will work with software RAID because I generally don't use it, but if you use the logical device as the target, it SHOULD write a perfect image to the drive and zeros to the free space.

```
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror
```

sda is the source (old) drive and sdb is the target (RAID) volume. DO NOT REVERSE THE SOURCE AND TARGET AS YOU WILL OVERWRITE THE SOURCE WITH NO PROMPTING!

This is the fastest way to do this and will copy the drive bit by bit to the new volume. If anyone else has tried this on software RAID, please advise.

Oh, almost forgot, you will have to create a separate boot drive because you cannot boot from software RAID. This could be tricky. You may want to dd the boot sector (first 512 bytes) to the boot drive and then dd the rest of the partitions to the RAID volume if you are going to keep the software RAID.

My advice? Go get a cheap hardware RAID controller. They are out there and freely available. If you have trouble, I can probably suggest one.

-Tim

---

### Post by Xianath on 2009-05-19
Thanks Tim, but hardware RAID is not an option, this is a proof-of-concept box to demonstrate that software RAID can also cut it for certain applications. I'm afraid dd wouldn't work as the source is bigger than a target. GRUB supports RAID0, RAID1 and LVM, though not RAID5 or RAID6, hence I have my various partitions mounted on RAID5 but I have /boot and / mounted on RAID0/LVM.

The question is not so much as to how to get the installation across, that's straightforward. It's more along the lines of how grub, initramfs and fstab come together to make a bootable system. Linux has become so automated these days that I can no longer keep track of how things are assembled.

Thanks,
Peter

---

### Post by windependence on 2009-05-19
I'm just curious how the source can be bigger than the target. In that case, your drive isn't going to fit anyway no?

What are you trying to prove with this box - just curious. I do have one SAN running software RAID, but not linux, it's on FreeBSD. So far it has been stable, but I'm not sure I want to put any of my enterprise stuff on it yet. I'm just not convinced of what might happen if I have a drive failure. With hardware RAID, of course I just hot swap the drive.

-Tim

---

### Post by Xianath on 2009-05-19
Well, the source boot partition is 855MB partition, the destination is 164MB. Only 15MB are used but still, I can't just dd from one to the other.

The box will be used for an university project that's basically comparing various storage solutions and shows where a budget Linux-based NAS/SAN fits in. Hardware RAID has its merits but also its drawbacks (price, hardware dependency). People always tend to overlook the scenario where your RAID card fails three years from now when it's no longer in production (or the company has gone done under). With software RAID you can just move over the disks to a different box and it all works like magic.

I'll try copying over /boot and /, fixing /etc/fstab and running grub-install on all 6 MBRs. My guess is, I'll run into Error 17 but who knows, I might get lucky.

Cheers,
Peter

---

