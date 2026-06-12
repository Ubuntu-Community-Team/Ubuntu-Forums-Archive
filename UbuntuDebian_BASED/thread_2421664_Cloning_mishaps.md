---
title: "Cloning mishaps"
date: 2019-06-25
forum: Ubuntu/Debian BASED
---

### Post by donbcilly on 2019-06-25
About a week ago I made a bit of a grub mess. I clonezilled an existing installation onto a new SSD, "forgot" to change the UUID of the new disk,and in consequence had serious booting problems.
They were eventually solved and I'm now using 18,04 on the SSD. .

I still have two minor issues though, which are not actual problems, in  the sense that they don't (seem to) impair functionality, but they worry  me.
They may or may not be related:

1) I had two cloned Ubuntus, one on sd**a**2 (the original) and one on sd**b**1 (the copy).
With the messed up fstabs, if I ran the one on sdb, and proceeded to  mount sda - to get some things from it, it treated both partitions as  the same one, showed sda2 as mounted, and well... not nice. That was  solved.
But the thing is, I (repeatedly) installed and updated grub from the "new" one.
I also removed the EFI partition on the "old" disk.
Now, the grub menu at boot should show my new Ubuntu as default, and add an entry for the "old" one on sda2... right?
Wrong. It adds an entry for the one on sdb1 and if I boot the "default"... it's still the old one on sda.
So I'm slightly worried that if I eventually want to use sda2 for something else, my boot will turn into a shoe again.

Note: Of course, I could physically disconnect the old disk and "see  what happens". But, this motherboard is really finicky, if I touch the  SATAs it tends to die - I did try after cloning and it took me an hour  of fiddling before it revived - so I'd rather avoid it.

2) in order to fix some other -probably unrelated - problems, I had to play with initramfs.
And I noticed that *that* updated a kernel called 4.18.0-**22**-generic. My running kernel is reported (by inxi) as 4.18.0-**21**.
Now, update-grub says:
```
Found linux image: /boot/vmlinuz-4.18.0-22-generic
Found initrd image: /boot/initrd.img-4.18.0-22-generic
Found linux image: /boot/vmlinuz-4.18.0-21-generic
Found initrd image: /boot/initrd.img-4.18.0-21-generic
Found linux image: /boot/vmlinuz-4.15.0-52-generic
Found initrd image: /boot/initrd.img-4.15.0-52-generic 

```
The 4.18.0-22 entry is not present in the boot dir on the old  partition. Only the new one. Must have updated a kernel in the  meantime...
They smell to me as still being cloning mishaps.
Any suggestions on how to proceed to sniff (and snuff) them out?

---

### Post by oldfred on 2019-06-25
You cannot have duplicate UUIDs nor GUIDs.
UEFI uses GUID of ESP to know which partition to boot from.
Then in ESP is a 3 line grub.cfg that uses UUID to know which partition has the full grub.cfg for booting. And that grub.cfg has UUIDs for install.

Often easier just to do a new install & keep old install & old drive. Then copy /home, list of installed apps & perhaps some settings from /etc. These should be copied from your normal backup, and then you know you normal backup includes everything while you still have old drive to go back to and find anything you missed.

You can go thru this and compare all UUIDs. partUUID & GUID are same, so you compare those for UEFI boot entry and ESP partition.
       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
      New installs use a swap file, so you may not have swap partition, but if you do:
      
 if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

---

### Post by donbcilly on 2019-06-26
> **oldfred said:**
> You cannot have duplicate UUIDs nor GUIDs.
Well, I don't (anymore).
Look. blkid:
```
/dev/sda1: LABEL="K14" UUID="4d8f0727-3f74-46ca-9b8f-bb6aa04ac6f8" TYPE="ext4" PARTUUID="000aef22-01"
/dev/sda2: LABEL="NEON" UUID="879b2424-5b36-49b4-a53b-f51dbde63b30" TYPE="ext4" PARTUUID="000aef22-02"
/dev/sda3: LABEL="SDA3" UUID="9d8dfbea-7fc9-45fd-b4b4-9b359cdfc01d" TYPE="ext4" PARTUUID="000aef22-03"
/dev/sda4: UUID="81131765-cba3-490b-94c3-5815219f4deb" TYPE="swap" PARTUUID="000aef22-04"
/dev/sdb1: LABEL="SSD_Neon" UUID="3331581b-e3a3-4976-86a3-bbfc025262be" TYPE="ext4" PARTLABEL="Linux filesystem" PARTUUID="61b71598-66e2-4ce6-b00f-87d5734b5604"
/dev/sdb2: LABEL="SSD2" UUID="5c3af4ec-b016-4eea-accd-23d517b87248" TYPE="ext4" PARTLABEL="Linux filesystem" PARTUUID="3ffc76ce-bbce-4d7a-b0ac-2007a576d2d9"
/dev/sdb4: UUID="754B-22C4" TYPE="vfat" PARTLABEL="EFI System" PARTUUID="8d1db492-d814-4962-8504-db2af04e26ea"
/dev/sdb5: UUID="bbb7dbfc-e767-43c9-8b99-614bbaab2cc5" TYPE="swap" PARTLABEL="Linux swap" PARTUUID="460037c0-d0c6-4d3f-b149-bc2ce8add319"
/dev/sdc1: LABEL="K18" UUID="3733e2b4-b159-434d-a4d2-ab4cb0cfa031" TYPE="ext4" PARTUUID="85e3aaee-01"
/dev/sdc2: LABEL="joey" UUID="13a64598-bbd5-489d-a193-4ebc1cad8072" TYPE="ext4" PARTUUID="85e3aaee-02"
/dev/sdc3: UUID="239B-2FC4" TYPE="vfat" PARTUUID="85e3aaee-03"
/dev/sdc4: LABEL="joey-gnome" UUID="66336795-cced-40b0-93aa-0845872860fc" TYPE="ext4" PARTUUID="85e3aaee-04"
```

> UEFI uses GUID of ESP to know which partition to boot from.
Then in ESP is a 3 line grub.cfg that uses UUID to know which partition  has the full grub.cfg for booting. And that grub.cfg has UUIDs for  install.


/boot/efi/EFI/neon/grub.cfg:
```
search.fs_uuid 3331581b-e3a3-4976-86a3-bbfc025262be root hd1,gpt1 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

So, hd1,gpt1 is sdb1, which tallies with the UUID.


> Often easier just to do a new install & keep old install & old drive. Then copy /home, list of installed apps & perhaps ...

Yes, well. I have done in the past. The "list of installed apps" being the annoying bit, I opted to clone. In any case, it's what I did, and, after repairs, it works... except for those two little problems.


> New installs use a swap file, so you may not have swap partition, but if you do:
I do, it's sdb5. Looks correctly set up too. /etc/fstab:
```
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=3331581b-e3a3-4976-86a3-bbfc025262be /              ext4    defaults,noatime 0 1
UUID=754B-22C4                            /boot/efi      vfat    defaults,noatime 0 2
UUID=bbb7dbfc-e767-43c9-8b99-614bbaab2cc5 swap           swap    defaults,noatime 0 2

```

 > if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid
Well, /etc/initramfs-tools/conf.d/ is there, but it's empty...

So... thing is, UUIDs match, fstab looks correct, system works.
Except, update-grub is weird - in the sense that it makes a secondary entry for the current system and puts another one as default.
And it boots with the "older" kernel.

About boot-repair... I've had some not-too-pleasant experiences with it in the past, if it can be avoided... I can supply the required information myself, I hope.

---

### Post by oldfred on 2019-06-26
Boot-Repair report should not cause issues.
But with multiple installs and/or multiple drives, only advanced mode should be used as default usually is not the best fix.
Before Boot-Repair we used bootinfoscript and the first part of Boot-Repair's report is still bootinfoscript. I regularly run bootinfoscript as part of my weekly backup. Its just now Boot-Repair add additional commands to see more info. The bootinfoscript has not be regularly maintained.
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

Is it UEFI entry or grub entry that is duplicated? update-grub is normally only grub menu, and reinstall of grub updates UEFI entries.
Post this:
sudo efibootmgr -v

---

### Post by donbcilly on 2019-06-26
Well, it's not exactly duplicated.
I install grub to sdb. From sdb. I update it from the sdb system.
It makes the default entry the one on sda and adds a separate onr for the one on sdb.
 efibootmgr -v:
```
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0003,0001,0004,0005
Boot0000* neon  HD(4,GPT,8d1db492-d814-4962-8504-db2af04e26ea,0x3a18c000,0x1f8800)/File(\EFI\neon\shimx64.efi)
Boot0001* Hard Drive    BBS(HD,,0x0)..GO..NO........o.C.T.5.0.0.M.X.5.0.0.S.S.D.1....................A...........................>..Gd-.;.A..MQ..L.9.1.3.1.1.E.6.F.3.C.5.4. . . . . . . . ........BO..NO........u.W.D.C. .W.D.3.2.0.0.A.A.J.S.-.0.0.L.7.A.0....................A.................................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.V.A.J.2.9.2.7.2.9.4........BO..NO........o.W.D.C. .W.D.1.0.E.Z.E.X.-.2.2.M.F.C.A.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.6.C.5.Y.N.X.J.V.F.A........BO
Boot0003* ubuntu        HD(3,MBR,0x85e3aaee,0x12c1a784,0x9fd38c)/File(\EFI\ubuntu\shimx64.efi)
Boot0004* USB   BBS(USB,,0x0)..GO..NO........m.T.O.S.H.I.B.A....................A...................................4..Gd-.;.A..MQ..L.2.0.1.8.0.9.2.0.0.0.1.3.1.1.F........BO
Boot0005* UEFI: TOSHIBA PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/USB(4,0)/HD(1,MBR,0xe6471ab6,0x800,0x74705cb0)..BO
```

Consider that the "Hard Drive" and "USB/TOSHIBA" are not used, don't do anything if used, and... the TOSHIBA is just a USB external drive that I just happened to have connected at boot. It's usually disconnected, and the entries do not appear.

---

### Post by oldfred on 2019-06-26
Are you then booting into Neon, not Ubuntu.
Grub update in UEFI entries, normally makes that install first. 

You can change order using efibootmgr -o
See also 
man efibootmgr

       Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 3,0,1

---

### Post by donbcilly on 2019-06-26
Yeah, well, I actually *want* to boot into Neon...
Still, Neon is Ubuntu... mine is basically Kubuntu 18.04 with more updated repositories.
I was just playing the politician (lying) a bit. But not too badly. I hope.
See, I thought, Ubuntu forums, I start talking Neon... :-\"

[P.S.] Hey, I do have Ubuntu on this machine.With Gnome. I even have an Ubuntu phone. :cool:

---

### Post by oldfred on 2019-06-26
If not directly Ubuntu, we have a sub-forum for other operating systems.
Moved to Ubuntu based distributions.

---

### Post by donbcilly on 2019-06-27
Ok. Not that it changes much, does it, as what we're talking about applies to any *buntu anyway, but then

I disconnected the external drive, so efibootmgr looks like:

```
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0003,0004
Boot0000* neon  HD(4,GPT,8d1db492-d814-4962-8504-db2af04e26ea,0x3a18c000,0x1f8800)/File(\EFI\neon\shimx64.efi)
Boot0003* ubuntu        HD(3,MBR,0x85e3aaee,0x12c1a784,0x9fd38c)/File(\EFI\ubuntu\shimx64.efi)
Boot0004* Hard Drive    BBS(HD,,0x0)..GO..NO........o.W.D.C. .W.D.1.0.E.Z.E.X.-.2.2.M.F.C.A.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.6.C.5.Y.N.X.J.V.F.A........BO..NO........o.C.T.5.0.0.M.X.5.0.0.S.S.D.1....................A...........................>..Gd-.;.A..MQ..L.9.1.3.1.1.E.6.F.3.C.5.4. . . . . . . . ........BO..NO........u.W.D.C. .W.D.3.2.0.0.A.A.J.S.-.0.0.L.7.A.0....................A.................................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.V.A.J.2.9.2.7.2.9.4........BO

```

Then I thought, that ugly "Hard Drive" entry, I don't use it, do I need it?
So I deleted it, 
```
not@all:~$ sudo efibootmgr -b 4 -B
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0003
Boot0000* neon
Boot0003* ubuntu

```

rebooted and... sure enough, it's back, with Nº 5.
Now, see, it seems to contain entries for all three disks.

```
lshw:                efibootmgr:
WDC WD10EZEX-22M --> W.D.C. .W.D.1.0.E.Z.E.X.-.2.2.M.F.C.A.0
CT500MX500SSD1 --> C.T.5.0.0.M.X.5.0.0.S.S.D.1
WDC WD3200AAJS-0 --> W.D.C. .W.D.3.2.0.0.A.A.J.S.-.0.0.L.7.A

```

So it probably **is** needed. By this BIOS anyway.

So... EFi seems correctly set up, grub acutally works, except it sets another OS, on another disk (which has no EFI partition on it) as default, and makes the "current" one (the one where it updates from) a separate entry.
And it boots a kernel which is not the latest one, but is the latest one on the other disk.
Bit of a mystery, isn't it?
I'll do the boot-repar thing and let you know.

---

### Post by donbcilly on 2019-06-27
There you go.
paste.ubuntu.com/p/tFYm6gwRnK/

Changed to this so we can just click on it:
[http://paste.ubuntu.com/p/tFYm6gwRnK/](http://paste.ubuntu.com/p/tFYm6gwRnK/)

---

### Post by oldfred on 2019-06-27
Your sda is MBR and has grub for BIOS boot.
Your sdb is gpt and has an ESP for UEFI boot. But in UEFI mode grub always wants an ESP on sda.
Your sdc is MBR but also has an ESP, which can work but not recommended as gpt is standard with UEFI.

If you have newer UEFI hardware, better to use UEFI with gpt.
But if you really want BIOS you can still use gpt but then need a bios_grub partition for grub to correctly install to gpt's protective MBR.

But whichever you want better to have all as BIOS boot or all as UEFI/gpt boot.
Since installs are on separate drives, you can dual boot, but not from grub, only directly from UEFI boot menu. 
Once you start booting in one mode, you cannot switch. Or grub then can only boot other installs in same boot mode, which you started with.

---

### Post by donbcilly on 2019-06-27
Well, so what would you advise I do?
I can easily convert MBR to gpt on all disks - if that would help.
I can re-create the EFI/ESP partition on sda... and/or delete the one on SDC.

I thought it would be a good idea to have at least two for redundancy - in case of failures.
And I deleted the one on sda because... well, I couldn't install grub so it would boot "properly" from sdb - it mixed up the entries and booted an older kernel... which it still does, obviously.

I really find the whole grub/EFI/BIOS boot thing confusing.
There's just some logic in it that for some reason totally escapes me. What can I try?

[EDIT] sda might be failing. I was running Neon on it, started getting errors, fsck-d them, got me a new disk (sdb, SSD) and cloned it to that.

---

### Post by donbcilly on 2019-06-28
> **donbcilly said:**
> 
I really find the whole grub/EFI/BIOS boot thing confusing.


Well, it seems everyone else does too ;·)
Anyway, I changed MBR to gpt on all disks, re-created the EFI/ESP partition on sda, installed grub to sda, and, no change.
It still sets the wrong entry as default and boots an older kernel (two versions older now - in the sense that I have a newer newer one and it ignores that as well).

And sda is definitely failing, gparted gave more errors and I had to fix them.

---

### Post by donbcilly on 2019-06-28
Thing is...
...in my grub.cfg, the "default" menuentry has "set root='hd1,gpt1'", which is correct. It's sdb1.

If I press 'e' at the boot menu on the default one (which boots to sda) it has "set root='hd0,msdos2'.
Now, "msdos" does not appear anywhere in my grub.cfg. I converted all disks to gpt.
Also, my grub.cfg has the neon on sdb1 (correctly) as the default and a separate entry for a neon on sda2.

My grub **boot menu** has the reverse - with a "non-existent" msdos-type entry.
So, I install and update grub (from sdb, to both sda and sdb) and what gets written is **not** my actual grub.cfg.                         

So, you see, it looks likely that even if I **do** re-install neon, it won't make any difference.
As the alien clone ghost zombie- grub has taken over the world... well, mine anyway, and... oh, I don't know.

---

### Post by donbcilly on 2019-06-29
You know what?
I just installed rEFInd and ditched grub.
Everything is fine and I have 4.18.0-**25 **as kernel

---

