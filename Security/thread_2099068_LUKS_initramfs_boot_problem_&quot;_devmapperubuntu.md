---
title: "LUKS initramfs boot problem: &quot; /dev/mapper/ubuntu-root does not exist.&quot;"
date: 2012-12-28
forum: Security
---

### Post by jdeks on 2012-12-28
Hi everyone,

Long time lurker,  first time poster, having spent 2 days searching now to no avail!

I am new to Linux/Ubuntu, hence putting this in the Beginners section. But I learn quick. Since first 'testing out' Ubuntu 3 weeks ago, Windows has disappeared entirely  from my digital life (and hard drive), and I'm learning more about computers than ever before. But I think I may have gone in over my head a bit here. Please forgive the essay below - the problem is a little unusual

I'm running 12.04 on a laptop (with UEFI BIOS), with full disk encryption set up up using the Alternate CD. I recently made a backup image of the entire hard drive using dd, to an external USB hdd. Having recently made some changes on the laptop, I tried to plug in the external USB clone to copy the files to it. Despite getting the password prompt and having it appear in the Disk Utility as a logical volume group, it would not actually mount the external drive, saying it was 'not a mountable file system'. Tried it on my desktop, and it mounted up just fine (once I installed lvm2). 

Using pvdisplay, I noticed that both the external drive and internal laptop drive had the same UUID (duh, it's a clone!). So, on the desktop, I used pvchange -u to change the external drive's uuid. Plugged it into the laptop, alas, still no joy. Gave up, turned off the laptop (drive still plugged in), went and had dinner. Came back, unplugged external drive from now-off laptop, tried to boot. Problems!

It boots to the password prompt screen like normal. Enter the password, and after a long wait, it drops to an initramfs prompt, with the error: 

"ALERT! /dev/mapper/ubuntu-root does not exist."
Poop. 

If I reboot, and plug back in the external drive, it boots up, seemingly running root off the USB drive. I have tried the solution [here]("http://ubuntuforums.org/showthread.php?t=1399810"), entering /dev/sda3 (and yet more variants) instead. No bingo, still get exactly the same messages. The fact I'm using LUKS with a LVM seems to complicate things. I think I've muddled a config file somewhere, probably by plugging in two drives with the same UUID (stupid!) and now it thinks /root is on the external drive. I'm stumped as to how to get it back. 

Any help would be really appreciated. Thanks in advance (especially if you read all that).

Update:

Removed the internal laptop drive, plugged it into my desktop and it wouldn't read it.
Ran lvscan and pvscan, and it doesn't pick it up as being part of a logical volume group.

Did the same thing to the backup clone: detects it just fine. Belongs to the 'ubuntu' volume group, mounts everything OK.

Any ideas? Anyone??

C'mon, no-one? I'm really up the creek without a paddle here, and I need to get this thing back on-line for work in the new year. Even if I can just find a way to read the encrypted volume off another computer to I can salvage my un-backed up data.

The crux of the issue seems to be that the internal laptop drive has a logical volume, but doesn't seem to have a logical volume group. Is there any way to re-create the volume group without nuking the logical volume?

And I'm serious about the beer.

---

### Post by steeldriver on 2012-12-29
I don`t know anything about disk encryption but it sounds like the LV (or parent VG) might not be activated

With the drive plugged into your desktop what are the actual outputs of 

```

pvscan
vgscan
lvscan

```Have you run lvdisplay on the LV

```
sudo lvdisplay /dev/*vgname*/*lvname*
```

---

### Post by jdeks on 2012-12-30
Thanks for the reply.

pvscan of the borked internal drive yeilds this (note the distinct lack of a volume group!):

```
  PV /dev/dm-6                      lvm2 [59.20 GiB]
  Total: 1 [59.20 GiB] / in use: 0 [0   ] / in no VG: 1 [59.20  GiB]
```lvscan and vgscan both give "No Volume groups found". Can't  run lvdisplay either, because I've got no vgname to put in. If I try  'ubuntu' (what it should be', it just says it can't find that group.


ON the other hand, pvscan of the** working backup **yeilds this:

```

  PV /dev/dm-6   VG ubuntu   lvm2 [59.20 GiB / 0    free]
  Total: 1 [59.20 GiB] / in use: 1 [59.20 GiB] / in no VG: 0 [0   ]
```lvscan gives:

```
  ACTIVE            '/dev/ubuntu/root' [55.28 GiB] inherit
  ACTIVE            '/dev/ubuntu/swap_1' [3.92 GiB] inherit
```vgscan gives:

```
  Found volume group "ubuntu" using metadata type lvm2
```"lvdisplay /dev/ubuntu/root" gives


```
  --- Logical volume ---
  LV Name                /dev/ubuntu/root
  VG Name                ubuntu
  LV UUID                vVIhVO-aUa8-XgSc-zd57-e0Bl-X9Sd-eqJoaQ
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                55.28 GiB
  Current LE             14151
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:7
```The backup boots if I put it in my  laptop and start it up, and also mounts fine when plugged into my  desktop, and is recognized in disk utility as an LVM device.

The borked internal drops to initramfs if I try to boot off it, and any  attempt to mount it on the desktop system results in an 'Not a mountable  file system' error.

> **steeldriver said:**
> I don`t know anything about disk encryption but it sounds like the LV (or parent VG) might not be activated

With the drive plugged into your desktop what are the actual outputs of 

```

pvscan
vgscan
lvscan

```Have you run lvdisplay on the LV

```
sudo lvdisplay /dev/*vgname*/*lvname*
```

---

### Post by steeldriver on 2012-12-30
So it seems to know that the PV is /dev/dm-6 (not sure why - that sounds like a fakeraid volume - maybe that's how LUKS disks appear?) - so what does pvdisplay say?

```
sudo pvdisplay /dev/dm-6
```(or just [FONT=Courier New]sudo pvdisplay[/FONT] which should display details about all PVs)

I guess [FONT=Courier New]vgchange -ay[/FONT] doesn't find anything, right?

---

### Post by jdeks on 2012-12-30
Yeah tried vgchange already, same ol' "No volume groups found"

pvdisplay yields this:

```
~$ sudo pvdisplay /dev/dm-6
  "/dev/dm-6" is a new physical volume of "59.20 GiB"
  --- NEW Physical volume ---
  PV Name               /dev/dm-6
  VG Name               
  PV Size               59.20 GiB
  Allocatable           NO
  PE Size               0   
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               ySycxZ-O7b0-zBcJ-qrRX-0hCK-6w86-D1ShZX
```

[SIZE=4]I FIXED IT!!
[SIZE=2]For the references of future generations[SIZE=2][SIZE=2], heres how:[/SIZE][/SIZE][/SIZE]

[SIZE=2]The problem was that[SIZE=2] by pluggin[SIZE=2]g the [SIZE=2]a clone of the system I was r[SIZE=2]unning into it, [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]I'd [SIZE=2]"confused" my system as [SIZE=2]to which drive [SIZE=2]to w[SIZE=2]rite to, and somehow [/SIZE][/SIZE][/SIZE][/SIZE]nuked the Volume Group metadata for the ori[SIZE=2]ginal internal drive[SIZE=2]. L[SIZE=2][SIZE=2]uckily[/SIZE], I still had the meta[SIZE=2]data f[SIZE=2]rom the clone I'd made.

[SIZE=2]This meant that I could plug in the working backup, unlock it, and use vgcfgbackup to make a copy of its metadata.

[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
```
~$ sudo vgcfgbackup -f /tmp/trousers
  Volume group "ubuntu" successfully backed up.
```This creates a text file with the metadata in /tmp called trousers (called it whatever you like, makes no difference)

Then, I dismounted and unplugged the functioning backup clone, and plugged in the borked internal drive. Unlocked it like I did the backup, then run:

```

 sudo vgcfgrestore -f /tmp/trousers ubuntu
  Restored volume group ubuntu
```Upon doing this, the volume group suddenly sprang to life in disk utility,  and the borked internal was unborked, mountable and readable again!

Critical bit here is that 'ubuntu' was the name of the original volume group. You can verify this by opening up the 'trousers' file in gedit and looking at the entry on the line below "creation_time".

Also worth noting that this only worked because the backup was an *exact clone* of the original internal, and hence the VG metatdata file had all the correct UUID's in place. I actually got an error message first time round because I'd originall manually changed one of the UUID's on the external drive.  I had to use pvdisplay on the original internal to find its UUID, and then manually edit the 'trousers' file to get it to work.

Anyway, hope that helps someone one day.

---

