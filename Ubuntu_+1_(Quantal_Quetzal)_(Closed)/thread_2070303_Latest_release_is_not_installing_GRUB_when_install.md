---
title: "Latest release is not installing GRUB when install is complete?"
date: 2012-10-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Gizim on 2012-10-12
Just tried to install Beta 2 on my desktop and dual boot it with Windows. At first it never detected that I had two drives in the box. I pulled the power on the 2nd drive so that it would only see the 1st drive that has Windows. It installed just fine but when it rebooted it went right into Windows and never gave the option to boot into Ubuntu. Tried this a few times any reason why it's not installing GRUB?

---

### Post by cariboo on 2012-10-12
Could it be that the system saw the drive you disconnected, as the first drive in the system, and installed grub on it?

---

### Post by balloons on 2012-10-12
Gizim, the RC iso's are out. Try testing one of those and if you continue to have this issue, please report a bug from that installation. You can use 'ubuntu-bug ubiquity' to file the bug if needed.

[http://iso.qa.ubuntu.com/qatracker/milestones/240/builds](http://iso.qa.ubuntu.com/qatracker/milestones/240/builds)

---

### Post by Gizim on 2012-10-12
> **cariboo907 said:**
> Could it be that the system saw the drive you disconnected, as the first drive in the system, and installed grub on it?

Before pulling the 2nd drive I went back into Windows and removed the partition and created free space out of it. I was able to reboot and it goes right into Windows so GRUB doesn't seem to have been installed at all. 

I did a reinstall on just the 1st drive and still same thing when I reboot it goes right into Windows with no options to boot into Ubuntu.

---

### Post by Gizim on 2012-10-12
> **guitara said:**
> Gizim, the RC iso's are out. Try testing one of those and if you continue to have this issue, please report a bug from that installation. You can use 'ubuntu-bug ubiquity' to file the bug if needed.

[http://iso.qa.ubuntu.com/qatracker/milestones/240/builds](http://iso.qa.ubuntu.com/qatracker/milestones/240/builds)

Will update this weekend, thanks

---

### Post by balloons on 2012-10-12
> **Gizim said:**
> Will update this weekend, thanks

No trouble. There's been grub changes since beta 2 -- I want to make sure they fix your issue, instead of making it worse.

---

### Post by Gizim on 2012-10-12
> **guitara said:**
> No trouble. There's been grub changes since beta 2 -- I want to make sure they fix your issue, instead of making it worse.

Okay just tried and same thing no change. It installs just fine but then reboots and goes right into Windows with no GRUB menu. What sucks is on both drives now I've lost 75gigs that are unusable to NTFS.

---

### Post by cariboo on 2012-10-12
Have you tried chrooting your / partition, and installing grub from inside the chroot?

To chroot your installation, use the following instructions:

First boot from a Live CD, or USB drive, then in a terminal, type the following commands:

```
sudo mount /dev/sdaX /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt
```

**Note** /dev/sdaX = the partition you have Ubuntu installed on.

Once you have your install chrooted, use the following commands to install grub:

```
grub-install /dev/sda
```

once the above command has run, type this:

```
update-grub
```

After running the above command, you should see a listing of your Ubuntu install, memtest, and Windows.

Once update-grub has finished. press Ctl-d twice, to close the terminal.

While you're still running from the Live CD, you can use gparted, to change one of the ext4 partitions, to a format that Windows can use. Press Alt-F2 and type:

```
gparted
```

then select one of the 75GiB partions, and format it to ntfs.

---

### Post by Gizim on 2012-10-12
I'll give that a go tomorrow - just wondering why for no reason GRUB isn't installing itself.

> **cariboo907 said:**
> Have you tried chrooting your / partition, and installing grub from inside the chroot?

To chroot your installation, use the following instructions:

First boot from a Live CD, or USB drive, then in a terminal, type the following commands:

```
sudo mount /dev/sdaX /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt
```

**Note** /dev/sdaX = the partition you have Ubuntu installed on.

Once you have your install chrooted, use the following commands to install grub:

```
grub-install /dev/sda
```

once the above command has run, type this:

```
update-grub
```

After running the above command, you should see a listing of your Ubuntu install, memtest, and Windows.

Once update-grub has finished. press Ctl-d twice, to close the terminal.

While you're still running from the Live CD, you can use gparted, to change one of the ext4 partitions, to a format that Windows can use. Press Alt-F2 and type:

```
gparted
```

then select one of the 75GiB partions, and format it to ntfs.

---

### Post by Gizim on 2012-10-14
Just tried this everything went fine with no errors at all - rebooted ... straight to Windows no GRUB menu...

> **cariboo907 said:**
> Have you tried chrooting your / partition, and installing grub from inside the chroot?

To chroot your installation, use the following instructions:

First boot from a Live CD, or USB drive, then in a terminal, type the following commands:

```
sudo mount /dev/sdaX /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt
```

**Note** /dev/sdaX = the partition you have Ubuntu installed on.

Once you have your install chrooted, use the following commands to install grub:

```
grub-install /dev/sda
```

once the above command has run, type this:

```
update-grub
```

After running the above command, you should see a listing of your Ubuntu install, memtest, and Windows.

Once update-grub has finished. press Ctl-d twice, to close the terminal.

While you're still running from the Live CD, you can use gparted, to change one of the ext4 partitions, to a format that Windows can use. Press Alt-F2 and type:

```
gparted
```

then select one of the 75GiB partions, and format it to ntfs.

---

### Post by oldfred on 2012-10-14
Lets see what BootInfo says. Post link it creates for the report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Gizim on 2012-10-15
I will give this a try tonight, question do I have to do step 1? or can i go right to step 2 and just install Bootinfo with apt?

> **oldfred said:**
> Lets see what BootInfo says. Post link it creates for the report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by oldfred on 2012-10-15
BootInfo is part of Boot-Repair. The Bootinfoscript is run as part of the BootInfo report that Boot-Repair runs, but BootInfo adds some extra info.

---

### Post by Gizim on 2012-10-15
Got it - I'll update tonight. Thanks

> **oldfred said:**
> BootInfo is part of Boot-Repair. The Bootinfoscript is run as part of the BootInfo report that Boot-Repair runs, but BootInfo adds some extra info.

---

### Post by Gizim on 2012-10-15
Woohoo finally
[http://paste.ubuntu.com/1282241/](http://paste.ubuntu.com/1282241/)

It pops into GRUB gives me Ubuntu and 2 listings of Windows both on different partitions.. but im in! - SOLVED

[QUOTE=oldfred;12296891]BootInfo is part of Boot-Repair. The Bootinfoscript is run as part of the BootInfo report that Boot-Repair runs, but BootInfo adds some extra info.[/QUOTE

---

