---
title: "Init not found after RAID setup."
date: 2011-04-04
forum: Server Platforms
---

### Post by Valise on 2011-04-04
Hi,

I have the current disk setup :

disk1 :
```

sda:
  (primary) sda1 ntfs
  (primary) sda2 ext3 (mounted as / )
  (primary) sda3 swap
  (extended) sda4:
     (logical) sda5 ntfs
     (logical) sda6 raid (250Gib)

```disk2 :
```

sdb:
  (primary) sdb1 raid (250Gib)

```Before i set up the raid, but with this exact partitioning, the system booted perfectly. When i installed mdadm and created the raid1 mirroring on sda6 and sdb1, the init got screwed up, and all i get is a shell on initramfs, from where i can inspect that sda is binded on md, and cat /proc/mdstat tells me that i have an inactive sda[4]. I can't mount the root partition (sda2), because it's busy (i suspect dmraid to lock it), which is, i guess, why init cannot be found.

I wonder if my error is to setup a raid array using a logical partition contained in an extended partition (but i hardly see why it would not work - but the sda bind and the sda[4] in mdstat seems to tell me that it does not), or it's just the initrd that is improperly configured. The other things that bothers me, is that changing the partition type of the raid partitions (fd to 0 - Empty), to disable raid autodetection, resulted in the same behavior on boot. Which might lead me again to think about configuration file problem instead of improper setup.

But from here, i am stuck. The live cd doesn't not seem to recognize raid, so i can't inspect problems any further, but i could inspect system configuration, but i don't really know where to start.

Thanks for reading, i am looking for any kind of help.

---

### Post by Kljuka on 2011-04-04
I[SIZE=2]'ve had problems with booting reassebmled raid as well. My problem was that after inserting new drive into raid, bootloader (or however it is called) was not copied to new drive, so the machine didn't know how to start.

This is a note I've made for myself for the future. I hope it helps you:[/SIZE] [SIZE=2]

[/SIZE]>  [SIZE=2]_SERVER WON'T START_
[/SIZE]   [SIZE=2]In case the server doesn't start and drops you into console (initramfs console), the system couldn't assemble raid array to start normally. Assemble it manually in console (using mdadm) and then **exit**. The machin should boot normally. Now you have to save this configuration for future:
[/SIZE]  [SIZE=2]**mdadm -–Es >> /etc/mdadm/mdadm.conf**    copy all info about assemled arrays into mdadm.conf
[/SIZE]  [SIZE=2]**vim mdadm    **edit that each raid has only one line (UUID)
[/SIZE]  [SIZE=2]**update-initramfs -u    **update kernel boot image (with accurate raid config)
 [/SIZE]

---

### Post by Valise on 2011-04-05
Thanks for your tip !

Since the system was installed on sda2, outside the raid array, i did not need to assemble it manually. But i actually did not have a proper mdadm.conf saved in the initramfs, which was the source of problems : mdadm decided to hijack the whole sda disk for some reason, preventing the root filesystem, sda2, to be mounted.

By chance (but i should have tested that earlier), another older kernel available in grub did not have the initrd with and bad mdadm.conf, so that i managed to boot the system, remove the ARRAY from mdadm.conf, and rebuild the initrd as you specified. Now the raid array is entirely auto-detected on boot, but after mounting sda2 as the root.

---

