---
title: "Adding another harddrive to a LVM2 server?"
date: 2007-07-01
forum: Server Platforms
---

### Post by gmc on 2007-07-01
Hi Folks,

I recently upgraded my server here at home. This server currently has 3 harddrives operating under LVM2 and formatted as JFS and I'm trying to add a 4th drive (/dev/sda1). The problem is that the howto at [http://www.tldp.org/HOWTO/LVM-HOWTO/recipeadddisk.html](http://www.tldp.org/HOWTO/LVM-HOWTO/recipeadddisk.html) talks about ext2fs.


After fooling around, I managed to get vgdisplay to report the following:

```

  --- Volume group ---
  VG Name               archive
  System ID             
  Format                lvm2
  Metadata Areas        4
  Metadata Sequence No  28
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                4
  Act PV                4
  VG Size               745.23 GB
  PE Size               4.00 MB
  Total PE              190778
  Alloc PE / Size       190778 / 745.23 GB
  Free  PE / Size       0 / 0   
  VG UUID               dTVTyh-4P0j-aKmx-M8WW-eQNY-VKon-OMrGkY

```Note that the VG Size is reporting 745.23GB, however when I 
issue a '**df -h**', I get the following report:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/pvr
                      513G  288G  225G  57% /home/pvr
root@vsrv:/home/pvr# 

```The question is, it appears that I'm missing 232GB, which sounds reasonable as the additional drive is a 250G?

Can anyone help?

Gord

Addendum:

I found the solution to my problem, though I didn't actually use it. Because I'm using JFS, I should have used the information found on [http://www.tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://www.tldp.org/HOWTO/LVM-HOWTO/extendlv.html) (search for JFS).

What I actually did was backup my data to a set of USB external harddrives, and then reformat the lvm2 partition. So the moral of the story is "If there's a hard way to do something, just ask me: :-)

---

