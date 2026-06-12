---
title: "Mount bluray in fstab as NFS"
date: 2013-10-09
forum: Server Platforms
---

### Post by AmbiguousOutlier on 2013-10-09
Hello, 

How do I found out what the UUID is for my bluray drive, this is all I can see?

```
rhys@tomato:~$ sudo blkid
/dev/sda1: UUID="fcc56cbc-1732-4c7f-81ce-745b202dd076" TYPE="ext4" 
/dev/sda5: UUID="bae51a32-9dac-48b9-99ef-27264a0a24a8" TYPE="swap" 
/dev/sdb1: UUID="413368bc-0c08-41b1-a4d3-bd0246604706" TYPE="xfs" 
```

I want to mount the bluray on my server so it can accessed over the network. 

Any help is appreciated.

---

### Post by SeijiSensei on 2013-10-09
Did you have a disc in the drive when you ran blkid?  If not, then it won't show up in the list.

As a guess, the drive is probably /dev/sdc1, since "c" is the first available drive letter.  Try either running "dmesg" or using "tail -f /var/log/syslog" in a terminal while you insert the disc.  You should see log entries that will report device is assigned.

---

### Post by AmbiguousOutlier on 2013-10-13
Even if I load a disk it still doesn't show up. Not sure what to look for in dmesg and nothing was recorded in "tail -f /var/log/syslog".

I did have a go at;
```
rhys@tomato:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'	rwrw-- : 'HL-DT-ST' 'BDDVDRW GGC-H20L'
-------------------------------------------------------------------------

```

```
rhys@tomato:~$ sudo sg_map
/dev/sg0  /dev/sda
/dev/sg1  /dev/sr0
/dev/sg2  /dev/sdb
```

so I tried
```
rhys@tomato:~$ sudo mount -t udf /dev/sr0 /media/bluray
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Now I am lost, any help?

---

### Post by SeijiSensei on 2013-10-14
Is this a commercial Blu-ray?  They are encrypted using AACS and will not mount as an ordinary device.  There are [ways]("http://www.makeuseof.com/tag/what-you-need-to-know-about-watching-blu-ray-on-linux/") to watch commercial BR discs, but I doubt you can mount one and share its files.

If this is an unencrypted BR disc being used for data storage, are you sure it is using the [UDF]("http://en.wikipedia.org/wiki/Universal_Disk_Format") format?  I don't have a BR device in my computer, so I can't help much there.

---

### Post by AmbiguousOutlier on 2013-10-14
I'm not trying to view commercial discs, I'm actually not too bothered about it's ability to read blurays, I'm currently trying to get it to read my CD's. 

I have done nothing to get Ubuntu to recognise the device and I've just assumed UDF would be the correct format based on other threads I've read.

EDIT: 

> 
Sometimes you would like to listen to your favorite music and when you try mount music cd with a command above you can get problems like:

```
linuxcareer.com# mount -t iso9660 /dev/hdc /media/cdrom0/
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

linuxcareer.com# 
```

This is because music CD's does not contain standard iso9660 filesystem as such. In fact the story with music CDROMs is easier as it is with data CDROMs using iso9660 filesystem.

In order to listen to a music CD all what needs to be done is to insert music CD ( Compact Dics ) into CD-ROM/DVD-ROM drive and fire up you favorite music CD player. The only thing you may need to be concerned about is whether  "kdemultimedia-kio-plugins" package for KDE or "gnome-media" package for gnome window manager are installed. Those packages allow you to listen to music CD content.

In case you would like to see a content of your music CD or perhaps convert some music trakcs to MP3 / OGG format just start "KONQUEROR" and enter location:

audiocd:/ 

into Konqueror's navigation bar.

So how do I access a CD using CLI?

---

