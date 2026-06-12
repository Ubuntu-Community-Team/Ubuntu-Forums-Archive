---
title: "Tale of Woe - Snaps"
date: 2021-11-18
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2021-11-18
Got told off too many times for going on wife's machine (mate 20.04).  As it is a day to day work machine I have her using snaps as I've had some minor issues on my machine where I have removed snaps completely.  All has been fine until her machine would not boot this morning.  Why(?)  the / partition was too full (separate / and /home).  Via a livecd I found the culprit - /var/lib/snapd/snaps/ - it grows over time.  Searching around I discovered that you can limit the number of snap versions this directory holds and there is a script to do this - however, I could not find a way of running this script/reducing the size of the directory via a livecd.  So it's / rebuild time.   One of the things I have always likes about ubuntu is the small footprint - especially / It seems along with all the other 'moaning complaints' about snaps  I have discovered another - the growing size of /.  How big should we make / on a new install?  15GB, 20gb, 30gb, 40gb, 50gb?

---

### Post by Tadaen_Sylvermane on 2021-11-18
Maybe try this?  [https://askubuntu.com/a/1106133](https://askubuntu.com/a/1106133) No need for rebuild, just set and forget it looks like.
I never considered this being an issue as I only use a few of them. Just never came up. Is good to know.

To your specific question my suggestion would be to redo the whole damn thing with LVM. Then create a lv just for snaps mounted @ /var/lib/snap. Then you can expand as needed without worrying about anything else. As to a root size it's hard to suggest without knowing your current partition size.

---

### Post by TheFu on 2021-11-18
+1 to using LVM. I'm on record here about that way too much. ;)

---

### Post by GhX6GZMB on 2021-11-19
To me, there's a good reason that "snap" rhymes with "cr*p".
For .deb installs 20...30 GB for / is par today. For snap, perhaps 1 TB? I don't know.

---

### Post by guiverc on 2021-11-19
The recommended minimum size for / has been 25GB since Ubuntu 17.10.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

It was increased from the prior recommended minimum by Will Cooke who has Project Lead of Ubuntu Desktop at the time.

Since then a 8.6GB minimal for a clean *minimal* install without any additional added software, also assuming well maintained (ie. upgraded packages are not let pile up) has been added - but few of us tend to do that (but hey, some do).

Personally I find I want 32GB for / , but my current system is living with 27GB and I'm constantly needing to clean the system with the lack of 5GB costing me time on a very regular basis (ie. upgrades cannot be applied due to lack of disk space..)

We all have different habits, and different software needs (thus different space requirements).

FYI:

```
guiverc@d960-ubu2:/de2900/xubuntu_64$   du -hs /var/lib/snapd/snaps
1.9G    /var/lib/snapd/snaps
```

I see only two of any of my snaps in there.. Ubuntu-MATE does use snaps; I saw a request for *sanity checks* of a new *Ubuntu Mate Welcome* last night on the QA area of discord (Ubuntu-MATE) with updates of those snaps occurring as required.

---

### Post by TheFu on 2021-11-20
With 20.04+, I think 35G is fine, assuming the swap is placed somewhere else.
My 20.04 desktop with very little bloat:
```
$ dft
Filesystem                 Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--root ext4   19G   11G  [COLOR="#008000"]6.9G [/COLOR] 62% /
/dev/mapper/vgubuntu--home ext4   12G  7.0G  [COLOR="#008000"]4.3G[/COLOR]  63% /home
/dev/vda1                  vfat  511M  7.1M  504M   2% /boot/efi

$ sudo lvs
  LV     VG       Attr       LSize  Pool Origin Data%  
  home   vgubuntu -wi-ao---- 12.00g                                           
  root   vgubuntu -wi-ao---- 19.00g                                           
  swap_1 vgubuntu -wi-ao----  4.10g     

$ sudo vgs
  VG       #PV #LV #SN Attr   VSize  VFree
  vgubuntu   2   3   0 wz--n- 39.49g [COLOR="#008000"]4.39g[/COLOR]

```
As you can see, I keep swap separate and have just 40G total allocated for the system with just over 4G free for future needs.
To be fair, I have lots and lots of network storage available to this desktop, many TBs, which is where most of the data lives.

On a stand-alone desktop, I'd use
35G for / ext4
3G for /var ext4
50G for /home ext4
4.1G for swap
600M for /boot (ext2/4)
50M for /boot/efi (FAT32)
and I'd leave the rest of the storage unused, but as part of a large partition with a single VG.  If using btrfs, I do the same, but with subvolumes instead of LVs for var, home, swap and boot.  If using btrfs, I'd only have 1 storage device. Do not cross devices, though it is tempting and don't run virtual machines using CoW on btrfs storage - CoW doesn't like CoW. Bad things can happen.

Anyways, the great things about using btrfs or LVM is that if/when a storage area runs out of space, it is trivial to add more, where it is needed, without any downtime.  By having a little extra space unused, we can create snapshots for all sorts of great reasons too.  Never fully allocate storage for file system use - never.

---

### Post by mikewhatever on 2021-11-23
```
$ du -hs /var/lib/snapd/snaps
415M	/var/lib/snapd/snaps
```

Hey, why doesn't mine grow? How long do I have to wait for my own "tale of moo"?!:mrgreen:

---

