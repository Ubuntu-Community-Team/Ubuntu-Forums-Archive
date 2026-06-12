---
title: "ZFS zpool recovery"
date: 2016-06-28
forum: Server Platforms
---

### Post by Fush1986 on 2016-06-28
Hi 

**Back Story:**
A couple of weeks back I started running out of space on my ZFS raidz2 zpool 6x 2TB Drives. As a result I got my hands on a newer server and a 12bay jbod chassis which connected to the server via mini-sas. 

At first I added the old drives to the jbod and everything worked fine, and then added a new set of 6x4tb drives as a second vdev on the same zpool, the intention was the I would swap out the old 2tb drives for additional 4tb drives in the next few months, however shortly afterwards I started to get lots of checksum failures and got a couple of SMART errors.  So I rushed out and brought new 4tb drives and attempted swap out the the two bad drives with new disks.. however during the restripping a 3rd disk failed and everything came to a crashing halt... 

At that point I removed the old disks, and put all the new ones in, destroyed the original zpool and started from scratch with 12x4tb drives in raidz3 and its been working fine since (minus the loss of 8tb of data) 

Out of curiosity today I hooked up the failed drives to the old server and they actually spun up and started working, so I have started making images of the drives. 

**Actual Question:**
a) can I import the zpool using disk images instead of the physical drives?
b) is it possible to import a zpool (at least in read only mode) when there is a missing vdev?

both vdevs were in raidz2 and the second vdev had only been active for a week prior to the crash, so I assume not that much data would have been stored on the 2nd vdev.

I did try and import the zpool, but it appears to be complaining about the missing second vdev.

```
/dev$ sudo zpool import -f -d /dev
   pool: nas
     id: 9722703208013770464
  state: UNAVAIL
 status: One or more devices were being resilvered.
 action: The pool cannot be imported due to damaged devices or data.
 config:

    nas                        UNAVAIL  missing device
      raidz2-0                 DEGRADED
        sdb                    ONLINE
        sde                    ONLINE
        sdc                    ONLINE
        replacing-3            DEGRADED
          sda                  ONLINE
          sdf                  UNAVAIL
        sdf                    ONLINE
        replacing-5            DEGRADED
          sdd                  ONLINE
          5900837178850808708  UNAVAIL

```
Any advice would be helpful, I understand that its most likely gone, but if there is a slimier of hope that any of it could be recovered I would like to give it a try

Thanks Very Much

Fush.

---

### Post by MAFoElffen on 2016-06-28
Before recommending a solution, you know that importing something that is not at 100% health is flirting with danger and risking corrupting the rest of your zpool... so you might want to get enough media to make a snapshot of what you have to fall back on, right? Having thrown out that disclaimer...

I think since they are imaged copies instead of the originals, then you need to address the deivce id's of the copies. I think that these are pertinent:
[http://comments.gmane.org/gmane.os.solaris.opensolaris.zfs/47420](http://comments.gmane.org/gmane.os.solaris.opensolaris.zfs/47420)
[https://forum.proxmox.com/threads/import-convert-export-raw-images-to-zfs-volume.21241/](https://forum.proxmox.com/threads/import-convert-export-raw-images-to-zfs-volume.21241/)

I know this is going to show age, but I started using ZFS with OpenSolaris and Solaris 10, when Sun released the code as opensource in 2005. Besides Oracle's own ZFS Doc's ([http://docs.oracle.com/cd/E19253-01/819-5461/](http://docs.oracle.com/cd/E19253-01/819-5461/)), I tend to use these as reference:
[http://www.solarisinternals.com/wiki/index.php/ZFS_Troubleshooting_Guide](http://www.solarisinternals.com/wiki/index.php/ZFS_Troubleshooting_Guide)
[https://pthree.org/2012/12/10/zfs-administration-part-v-exporting-and-importing-zpools/](https://pthree.org/2012/12/10/zfs-administration-part-v-exporting-and-importing-zpools/)

---

### Post by lukeiamyourfather on 2016-06-29
ZFS can work with images instead of actual drives. All VDEV must be there for a pool to be imported though members of a VDEV can be missing assuming there's enough redundancy there to still function.

---

