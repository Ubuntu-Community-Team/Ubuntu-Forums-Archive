---
title: "LVM setup for media server - do I need to worry about disk failure?"
date: 2009-09-15
forum: Server Platforms
---

### Post by habrys on 2009-09-15
I just set up a headless Ubuntu 9.04 x64 server, which main purpose is to be a media server and download station (usenet, torrents etc.). It should have huge disk space, which should be easily scalable. So I went with LVM setup. Additionally it should be pretty secure, so encrypted LVM (I chose this option during installing of the system - it asks now for a passphrase on each reboot, which suites me well).

Now to the LVM configuration. It's all one huge encrypted logical volume formated as ext3, with root filesystem mounted (/), and also media directories inside. Everything together.

It's spanned between several physical volumes (disks). Such setup is extremely comfortable when it comes to resizing, adding new disks, etc. All media files sit in one place, no need to worry about new directories, new shares etc., when new disks are installed. I also wanted OS itself encrypted and this setup meets this requirement.

But...

What happens if one of the disks fails - I mean physically? Do I have some reasonable option to rescue some data? At least from the other disks? Would it be very complicated?

The data I store there is not so valuable for me to consider RAID 1, so this is not an option. Backups are also not an option - because of sheer amount of the data and see above. But still... it would be pain to lose 4 TB of data because... let's say the oldest 250 GB HDD failed some day.

Another question.
smartctl tells me, that my oldest HDD worked over 8000 hours so far. It's MTBF is 500 000 hours. Should I take is seriously? It's 57 years. Somehow I can't believe, that a harddisk will survive 57 years without failure, even if only on average. Right?

---

### Post by stlsaint on 2009-09-15
Disaster recovery may be an issue. Please see [LVMWiki]("http://en.wikipedia.org/wiki/Logical_volume_management") for more.

---

### Post by grantemsley on 2009-09-15
I would strongly recommend using software raid 5 if possible.  That would allow you to survive a disk failure with no data loss.  You can still upgrade the drives to larger ones, or add more drives as your server grows.

---

### Post by habrys on 2009-09-17
RAID 5 is an interesting option, but has some limitations. LVM is much more flexible. The worse one for me is, that it's practically limited to disks of the same size - at least 3 as I understand. I do have three 1 TB drives right now (and one old 250 GB, which could be used for /root outside of RAID or LVM), but I was planning to buy larger drives in the future, as the prices drop - 1.5 TB and 2 TB. RAID 5 (or RAID 1) configuration is not very practical under these requirements, right?

Well... for now I just split the space I have among 2 logical volumes:
250GB, encrypted, ext3, where / filesystem resides (the old 250GB disk)
3TB, encrypted, xfs for data (3 new 1TB disks)

This way at least if the old 250GB drive fails, it won't have impact on data. And manipulation on data logical volume is easier, because I can unmount it with OS still running. It's xfs now, so it shouldn't be neccessary even for shrinking of filesystem, but still...

---

### Post by Udayakiran on 2009-09-17
I think there is mirroring in LVM, but i dont know how dependable it is.
An option is to create a number of smaller RAID volumes (eg: 250GB) and spread volume groups over them. That way, you have a single large volume group. The next time you expand the capacity of your server, again create small partitions and extend the LVM over them. Creating small partitions offers lot of flexibility.
You can also try using smaller volume groups so that if one of the disks fail, only the VGs on that one will be affected. Like you can use a VG for media or one for movies and one for songs, etc. It all depends on your patience to organize stuff. To the user and applications, it all appears as folders, so once you have set it up, no big deal after that.
Fragmentation is beneficial to a certain degree.

---

### Post by habrys on 2009-09-20
> **grantemsley said:**
> I would strongly recommend using software raid 5 if possible.  That would allow you to survive a disk failure with no data loss.  You can still upgrade the drives to larger ones, or add more drives as your server grows.

Ok, you convinced me. I've read some articles about RAID 5, bought another 1 TB drive and am in the process of configuring the server this way:

- 4 x 1TB disk in RAID 5 array
- 1 big LVM logical volume using all the space on top of it
- LUKS encryption on top of it
- XFS filesystem for best performance with large media files

I started with RAID 5 array consisting of just 2 disks, moved some files onto it (it's nearly full now, over 900 GB) and started expanding it using the third, empty drive then (after moving of files).

Like this:
```
sudo mdadm --add /dev/md0 /dev/sdc
sudo mdadm --grow /dev/md0 --raid-devices=3
```

It seems to work as expected, but the array is reshaping now and it takes forever:
```
sudo mdadm --detail /dev/md0
...
 Reshape Status : 66% complete
  Delta Devices : 1, (2->3)

```

66% is done after over 15 hours, so the whole 1 TB drive will take about 24 hours. Is it normal?

Will the recovering of the array after disk failure take that much time as well? (I know, the array will be usable in degraded status in the meantime, but still...)

It all happens online, with the filesystem mounted and doesn't affect performance that much, so no big deal. I'm just curious. 

The disks are:
2x Samsung SpinPoint F1 HD103UJ
2x Samsung SpinPoint F2EG HD103SI

---

### Post by ene_dene on 2009-09-20
> **habrys said:**
> 
66% is done after over 15 hours, so the whole 1 TB drive will take about 24 hours. Is it normal?
I don't know what time is normal, but you should be aware that disk encryption has a price in terms of performance.

---

### Post by habrys on 2009-09-20
> **ene_dene said:**
> I don't know what time is normal, but you should be aware that disk encryption has a price in terms of performance.

I don't think encryption makes a difference here. As I understand reshaping of the matrix is just calculating checksums based on data chunks. They are not decrypted for this. Decryption comes on the filesystem level, which is way higher, than RAID level in my setup.

Anyway, it took about 20 hours and was successful. Now I have a 3 disk RAID 5 array + 1 spare disk, which is good enough for my needs. Until I run out of this 1.82 TB of space that is...

Now it would be interesting to pull out the cable from one of the disks and see what happens. Theoretically the matrix should heal itself without any intervention, right? Use the spare disk to reshape itself automagically. I'll test it sooner or later, when I have some time :)

---

### Post by openfly on 2009-09-21
Disk encryption on media drives is going to be some SERIOUS cpu overhead on what may already be a serious cpu intensive task... (playback of highdef video encodes).

May not yield the results you will be happy with.

---

### Post by NullHead on 2009-09-21
@habrys:

If you want to lessen CPU load, and overall improve the speed of your RAID5 setup, I think it'd best for you to get an actual RAID controller. They come in all shapes and sizes, but they're generally much faster and easier to setup. 

I wouldn't get one that isn't on the PCI-E bus though. A PCI/PCI-X card just wouldn't be worth it.

I agree with openfly. After mdadm + decryption, you'll have some serious slow downs there. That is, unless you have some kind of multi-core beast of a server. Then you should be fine ;) 

I tend to think of myself as paranoid (like never using the mv command. Always cp then rm ..), but I've never worried about encryption for any of my disks. Honestly, if somebody wants my stuff that badly, they might as well ask me for it.

---

### Post by habrys on 2009-09-21
> **openfly said:**
> Disk encryption on media drives is going to be some SERIOUS cpu overhead on what may already be a serious cpu intensive task... (playback of highdef video encodes).

May not yield the results you will be happy with.

Well... I never before experimented with encryption on Linux natively (LUKS), but I was using Truecrypt pretty long on Windows and Linux and never had any problems with streaming HD video content from encrypted drives (1080p, DTS, x264, bitrates about 15000 kbps even). In my current setup with RAID 5, LVM and LUKS encryption, video playback over network is also smooth like charm. In fact it was smooth even 2 days ago, while the RAID array was rebuilding/reshaping itself - I watched some movie in the evening then. :) The bottleneck is the 100 Mbps LAN anyway, which is enough for HD streaming. I think even for BluRay rips, which tend to have 2 or 3 times higher bitrates, than x264 mkvs. But I admit, I didn't test that.

And I don't have any beast machine. Just my old desktop with some added disks. It's an AMD X2 4200+, which runs on 1000 MHz instead of native 2.2 GHz almost all the time to save energy (thanks to good work of the "ondemand" governor).

From my experience: when something stutters, it's almost always fault of the HTPC itself, not the server or NAS (codecs, video driver, refreshing rates don't match etc.)

What I just meant in my previous post is, that encryption shouldn't matter when it comes to RAID array recovering/reshaping. RAID driver (or controller) doesn't know and doesn't care about encryption, right?

---

### Post by habrys on 2009-09-21
> **NullHead said:**
> 
If you want to lessen CPU load, and overall improve the speed of your RAID5 setup, I think it'd best for you to get an actual RAID controller. They come in all shapes and sizes, but they're generally much faster and easier to setup. 

I looked into it, but true RAID controlers (with hardware RAID 5 support) are too expensive for my needs. And I don't really need better performance for now, as I wrote in the previous post :)

> **NullHead said:**
> 
I agree with openfly. After mdadm + decryption, you'll have some serious slow downs there. That is, unless you have some kind of multi-core beast of a server. Then you should be fine ;) 
Well.. I do have a dual core AMD, but I think a single core would be enough too. I just happened to have an old desktop with dual core CPU lying around in my basement, so...

> **NullHead said:**
> 
I tend to think of myself as paranoid (like never using the mv command. Always cp then rm ..), but I've never worried about encryption for any of my disks. Honestly, if somebody wants my stuff that badly, they might as well ask me for it.
I'm totally paranoid when it comes to passwords, encryption, backups etc. I admit, that using encryption is more for fun though. I would stop immediately if the performance penalty was too great.

Oh... and I do us mv command. :D  And pretty often lately, with all this moving of terrabytes of data between different partitions...

---

### Post by openfly on 2009-09-21
The multiple cores will help A LOT.

---

### Post by habrys on 2009-09-21
So... I felt itching in my fingers today and decided to test my new RAID 5 array. It's better to know  what to do in case of emergency when really valuable data is on risk, right?

It's 4x 1TB array with 3 active disks and 1 hot spare one.

I opened the case and unplugged the data cable of one of the active disks. Without shutting down the system, on a running machine! SATA interface is supposed to support it after all, right? Quickly to the ssh terminal... it's frozen... nothing works... but just for a few seconds. After a short while of terror mdadm reported:

```
...
State : clean, degraded, recovering
...
    Number   Major   Minor   RaidDevice State
       3       8       16        0      spare rebuilding   /dev/sdb
       1       8       48        1      active sync   /dev/sdd
       2       8        0        2      active sync   /dev/sda

       4       8       32        -      faulty spare

```

As far as I can tell all data is intact. Streaming of HD video content, music etc. works without any glitches, even while recovering of the matrix. With LVM and encryption on top of it. Now, I expected this, but I'm still pretty impressed. Cool or what?

Another thing I noticed is, that rebuilding is much faster this time (last time it was called reshaping). It's already 20% complete, after half an hour or so.

So I suppose, I can assume, that my data is pretty safe now :)

---

### Post by habrys on 2009-09-21
> **openfly said:**
> The multiple cores will help A LOT.

Sure. But in my case top reports over 90% idle CPU time while streaming HD content over network. From RAID 5 + encrypted partition. So with one core it would be over 80%, right? This is why I suspect, that single core would be enough.

Maybe if there was some serious load on the server. Web service, mail server for many users or something like that, then yes - multiple cores would be a must.

---

### Post by openfly on 2009-09-21
Stream is probably not decoding / encoding.  Probably just a file transfer over network.  NFS / CIFS or something.

I was more concerned about direct playback off the system or a stream that required a transcode or something... ala xmpp.

---

### Post by habrys on 2009-09-21
> **openfly said:**
> Stream is probably not decoding / encoding.  Probably just a file transfer over network.  NFS / CIFS or something.

I was more concerned about direct playback off the system or a stream that required a transcode or something... ala xmpp.

That's right, in my case it's just transfering of data from a samba share. Decoding is handled by the client (HTPC) using CUDA. Ok, looking at "media server" in the title of my post you could assume, that decoding happens on the server side, my bad :)

---

