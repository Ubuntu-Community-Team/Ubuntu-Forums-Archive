---
title: "lvm2 : Adding LVMCACHE functionnality"
date: 2014-10-06
forum: Server Platforms
---

### Post by Gkar on 2014-10-06
Hi, 

  I would like to use my new ssd ... or a part of it as a cache but it seems that i need some upgrade for my lvm2 package.

  I'm using Ubuntu Server 14.04 LTS 64 bits

  Does anyone heard about lvm2 upgrade for version 2.02.112 in near futur ? 

  I found some information from this blog : [Richard WM Jones blog]("http://rwmj.wordpress.com/2014/05/22/using-lvms-new-cache-feature/")

  And manpage could be found [there]("http://man7.org/linux/man-pages/man7/lvmcache.7.html") 

Thanks for your help.

Best regards

---

### Post by josef-netzagentur on 2014-10-08
Hi,
just yesterday I've also noticed this interesting new feature in LVM2.

I'm using Ubuntu Utopic repositories.

I've already tried to compile the package from debian testing aka. lennie: [https://packages.debian.org/jessie/lvm2](https://packages.debian.org/jessie/lvm2)
This version already keeps this lvmcache feature.

But: it does not compile, because it depends on libcman-dev, which is a library for clustering and this library has been last in Ubuntu Precise.

Also checked that lvm2 is not even in the proposed branch.

So, for now I will wait some days and watch this thread...

---

### Post by wd5gnr2 on 2014-10-24
I am interested in this also. I've used enhanced IO but it has problems with newer kernels.

---

### Post by gmoutso on 2015-04-29
I just managed to boot with lvmcache. Here is what I did

0)
You should have installed ubuntu (or better kubuntu!) on an lvm. My lvm looks like this and they are all on sda5 (on the hdd)
LinuxVG/rootLV (mount as /)
LinuxVG/swapLV (use as swap)
LinuxVG/varLV (mount as /var)
LinuxVG/homeLV (mount as /home)

I also use a separate partition for /boot (I use sdb1 on the ssd), but /boot could also be in the lvm.

In the above set up I will cache rootLV and homeLV which explains why I put somewhere separate the /var (I don't want to cache this) and separate /boot (boot cannot be cached)

installing ubuntu with lvm is easy, just set it up on a console (or a konsole!) from the instalation usb before running the installation program. Instructions are here
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
note: you can use a partition manager rather than fdisk in those instructions. 

In my case I made a 1G sdb1 for boot and 21G sdb2 for the caching (sdb on SSD) and I had about 600G on sda5 for my lvm on the hdd.

Install k/x/ubuntu on your hdd and enjoy your system without ssd caching

1) I also installed lvm2 version v2_02_118 from upstream because v2_02_111 has had many bugfixes related to lvmcache (already many in 112 but that has had some bugfixes too). Installing from source presented no problems: ./configure; make; make install
[https://www.sourceware.org/lvm2/](https://www.sourceware.org/lvm2/)

2) 
On sdb2 (on the ssd) I have about 21G that I will split into two lv's: one for rootLV and one for homeLV. I will use the writethrough method for safety. 

```
sudo vgextend LinuxVG /dev/sdb2
sudo lvcreate -L 10G -n rootCacheLV LinuxVG /dev/sdb2
sudo lvcreate -L 24M -n rootCacheMetaLV LinuxVG /dev/sdb2
sudo lvcreate -L 10G -n homeCacheLV LinuxVG /dev/sdb2
sudo lvcreate -L 24M -n homeCacheMetaLV LinuxVG /dev/sdb2
sudo lvconvert --type cache-pool --poolmetadata LinuxVG/rootCacheMetaLV --cachemode writethrough LinuxVG/rootCacheLV
sudo lvconvert --type cache-pool --poolmetadata LinuxVG/homeCacheMetaLV --cachemode writethrough LinuxVG/homeCacheLV
sudo lvconvert --type cache --cachepool LinuxVG/rootCacheLV LinuxVG/rootLV
sudo lvconvert --type cache --cachepool LinuxVG/homeCacheLV LinuxVG/homeLV

```
more information on setting up lvmcache here:
[http://blog-vpodzime.rhcloud.com/?p=45](http://blog-vpodzime.rhcloud.com/?p=45)

At this point, the caching is up and running BUT I will not be able to reboot. This is because the boot image lacks the dm_cache modules and the executable cache_check

3)
Install cache_check with
```

sudo apt-get install thin-provisioning-tools

```

Do an lsmod and see what modules are running. These will be needed to be in the boot image, since the root will be cached and they are needed to mount it before. I have four:
```
sudo echo "dm_cache" >> /etc/initramfs-tools/modules
sudo echo "dm_cache_mq"  >> /etc/initramfs-tools/modules
sudo echo "dm_persistent_data"  >> /etc/initramfs-tools/modules
sudo echo "dm_bufio"  >> /etc/initramfs-tools/modules
```
(or sudo su first)

Now add a hook to also add cache_check to the boot image. Simply save and chmod +x the script into /etc/initramfs-tools/hooks/
```

    #!/bin/sh

    PREREQ="lvm2"

    prereqs()
    {
        echo "$PREREQ"
    }

    case $1 in
    prereqs)
        prereqs
        exit 0
        ;;
    esac

    if [ ! -x /usr/sbin/cache_check ]; then
        exit 0
    fi

    . /usr/share/initramfs-tools/hook-functions

    copy_exec /usr/sbin/cache_check

```

Finally
```
sudo update-initramfs -u
```

More information about the booting problems at:
[http://forums.debian.net/viewtopic.php?f=5&t=119644#p564446](http://forums.debian.net/viewtopic.php?f=5&t=119644#p564446)
[https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/1423796](https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/1423796)

Now, if everything goes well, you will also be able to reboot into your system with root and home cached by an ssd!

If it doesn't, you will be thrown into a shell. Did your lvmcache work at step 2? Then it is only the booting that is problematic. You can remove the cache from the shell and boot with something like (for v118)
```
lvm lvconvert -uncache LinuxVG/rootLV
lvm lvconvert -uncache LinuxVG/homeLV
lvm vgchange -ay LinuxVG
exit
```
For v111 the --uncache command is not there so you should do instead something like
```
lvm lvremove LinuxVG/rootcacheLV
lvm lvremove LinuxVG/homecacheLV

```
note what is removed! It is not the origin lv!

Good luck!

---

### Post by gmoutso on 2015-04-29
If anyone is watching... I am not sure how well the cache is working. I am presented with no problems nor has the system slowed down. Perhaps, it needs some time before I notice the speed increase.

But here are some new messages from syslog that I did not have before
```
Apr 29 23:41:11 Miro systemd-udevd[377]: conflicting device node '/dev/mapper/LinuxVG-rootLV_corig' found, link to '/dev/dm-3' will not be created
Apr 29 23:41:11 Miro systemd-udevd[380]: conflicting device node '/dev/mapper/LinuxVG-homeCacheLV_cdata' found, link to '/dev/dm-6' will not be created
Apr 29 23:41:11 Miro systemd-udevd[383]: conflicting device node '/dev/mapper/LinuxVG-rootCacheLV_cdata' found, link to '/dev/dm-1' will not be created
Apr 29 23:41:11 Miro systemd-udevd[393]: conflicting device node '/dev/mapper/LinuxVG-rootCacheLV_cmeta' found, link to '/dev/dm-2' will not be created
Apr 29 23:41:11 Miro systemd-udevd[377]: conflicting device node '/dev/mapper/LinuxVG-homeCacheLV_cmeta' found, link to '/dev/dm-7' will not be created
Apr 29 23:41:11 Miro systemd-udevd[380]: conflicting device node '/dev/mapper/LinuxVG-homeLV_corig' found, link to '/dev/dm-8' will not be created
Apr 29 23:41:11 Miro systemd-udevd[391]: conflicting device node '/dev/mapper/LinuxVG-rootLV' found, link to '/dev/dm-4' will not be created
Apr 29 23:41:11 Miro systemd-udevd[383]: conflicting device node '/dev/mapper/LinuxVG-homeLV' found, link to '/dev/dm-9' will not be created
Apr 29 23:41:11 Miro systemd-udevd[390]: conflicting device node '/dev/mapper/LinuxVG-varLV' found, link to '/dev/dm-5' will not be created
Apr 29 23:41:11 Miro systemd-udevd[378]: conflicting device node '/dev/mapper/LinuxVG-swapLV' found, link to '/dev/dm-0' will not be created
Apr 29 23:41:11 Miro systemd[1]: Starting Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling...
Apr 29 23:41:11 Miro systemd[1]: Started Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling.
Apr 29 23:41:11 Miro kernel: [    0.716972] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
Apr 29 23:41:11 Miro kernel: [    0.779574] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo only pio slum part deso sadm sds apst 
Apr 29 23:41:11 Miro kernel: [    4.983901] EXT4-fs (dm-4): mounted filesystem with ordered data mode. Opts: (null)
Apr 29 23:41:11 Miro kernel: [   12.301149] EXT4-fs (dm-4): re-mounted. Opts: errors=remount-ro
Apr 29 23:41:11 Miro kernel: [   12.580590] EXT4-fs (dm-9): mounted filesystem with ordered data mode. Opts: (null)
Apr 29 23:41:11 Miro kernel: [   12.606575] EXT4-fs (dm-5): mounted filesystem with ordered data mode. Opts: (null)

```

Running sudo lvs I get
```
sudo lvs -o +cache_policy,cache_settings

  LV     VG      Attr       LSize   Pool          Origin         Data%  Meta%  Move Log Cpy%Sync Convert Cache Policy Cache Settings
  homeLV LinuxVG Cwi-aoC--- 495.79g [homeCacheLV] [homeLV_corig] 0.44   8.02            0.00             mq                         
  rootLV LinuxVG Cwi-aoC---  38.00g [rootCacheLV] [rootLV_corig] 0.23   5.37            0.00             mq                         
  swapLV LinuxVG -wi-ao----   2.00g                                                                                                 
  varLV  LinuxVG -wi-ao----   2.00g           
```

I cannot find any information on the internet about the "conflicting node"!

---

### Post by gmoutso on 2015-04-29
the ration of hits/misses can be read with
```
sudo lvs -o cache_read_hits,cache_read_misses 
  CacheReadHits    CacheReadMisses 
              2032            11438
              3951            24183

```

---

### Post by gmoutso on 2015-05-01
```
sudo lvs -o cache_read_hits,cache_read_misses,cache_write_hits,cache_write_misses,cache_settings

  CacheReadHits    CacheReadMisses  CacheWriteHits   CacheWriteMisses Cache Settings                             
             43207            76724           126433           143872 random_threshold=4,migration_threshold=2048
              6142            20097              256              312              
```

For my problem with "udev: conflicting node, link will not be created" I asked a question at [http://ubuntuforums.org/showthread.php?t=2276261](http://ubuntuforums.org/showthread.php?t=2276261)

---

