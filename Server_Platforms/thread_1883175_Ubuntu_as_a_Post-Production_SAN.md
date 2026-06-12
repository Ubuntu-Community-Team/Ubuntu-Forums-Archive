---
title: "Ubuntu as a Post-Production SAN?"
date: 2011-11-18
forum: Server Platforms
---

### Post by Zahne on 2011-11-18
Has anyone tried using Ubuntu Server as a Storage Area Network for video editing a media production?

I work with folks that use Final Cut Pro, After Effects, Sony Vegas, Kdenlive. So we are all using different software systems and different Operating Systems. 

I have an Ubuntu desktop PC with 4 drive bays. I'd like to set up a RAID, and edit straight from it with a gigaswitch using videos files that have a bitrate of up to 200mbps. 

I'd also like to other users be able to access media assets remotely to download and upload. 

If for example I have someone on the other side of the country that needs to download an assignment. Completes and can then upload the finished product, that would be really solid. 

There are also servers prebuilt for just this purpose but they are in the $5,000-$20,000 cost. But I am not a huge broadcast company so that'd be excessive. 

I've read that there are servers by Synology that do this pretty nicely without much work. They are also cheaper around $1,200. But I have a pretty good Core2Duo that I could turn into a server. All I think I need is a gigbit switch, RAID card and drives. 

In brief:

1. Read/write high bit rate video files locally on my network
2. RAID set up to protect the scratch disk
3. Remote access to download and upload content
4. Clients on linux, mac and windows

Would love some help if this is A. doable B. what it would take to do

Thanks in advance!

---

### Post by spynappels on 2011-11-20
Hi,

200Mb/s (25MB/s) is doable on GbE network just about, but I'd recommend a GbE switch which supports Link Aggregation and get a 4 port GbE card from Intel for the server. That way, you have a 4GbE line into the switch for when multiple users try to access the video data simultaneously.

What size of storage do you need? You'd really need to be looking at SATA III drives and 4 bays is not really a lot of storage. You also need to think about redundancy and rebuild times for your RAID solution. For example, with 4 x 2TB disks in RAID5, you would have 6TB storage, but if a disk failed, you could not start rebuilding until you replace a disk, and rebuilding is already a slow process, so you could face more downtime. However, having 4 x 2TB disks in RAID5 + Hotspare would give you only 4TB storage, but if a disk died, the array would start rebuilding on to the spare disk immediately, saving some time.

You'd probably want to install the OS on a Flash based drive (USB, CF, SD or if you have plenty of cash, SSD). This segregates your data from the OS.

Downloading such volumes of data remotely across the Internet would be a very slow and laborious process unless both sides have a 100Mb connection, and even then it would not be quick.

This would be a very interesting project, I've done similar setups but not for video, they were for Medical Imaging Archiving, but still involved 4-5GB blocks of data, and it worked flawlessly. Network design is important too though.

Let me know if I can be of any more help to you.

Stefan.

---

### Post by ian dobson on 2011-11-20
Hi,

With cifs (samba) it's possible to get > 25Mb/sec over a Gigabit lan.

```
dd if=/dev/sda of=/mnt/video/tmp/test.txt  bs=4K count=2000000
2000000+0 records in
2000000+0 records out
8192000000 bytes (8.2 GB) copied, 130.544 s, 62.8 MB/s
root@myth-frontend:~# dd if=/mnt/video/tmp/test.txt of=/dev/null  bs=4K count=2000000
2000000+0 records in
2000000+0 records out
8192000000 bytes (8.2 GB) copied, 142.158 s, 57.6 MB/s

```

Tests run on the following hardware:-
Server: QuadCore 2600,16Gb ram, 5 drive RAID5 array running mdadm, ext4 filesystem.
Client: e5200 2.5GHz,2Gb ram, slow ssd as drive.

Gigabit lan/HP 8port switch, which other/general TCP/IP trafic on the same network at the same time.

I've had to optimize the smb.conf file quite abit to get these results, but if anyone is interested I'll post them here.

Regards
Ian Dobson

---

### Post by Zahne on 2011-11-21
> **spynappels said:**
> Hi,

200Mb/s (25MB/s) is doable on GbE network just about, but I'd recommend a GbE switch which supports Link Aggregation and get a 4 port GbE card from Intel for the server. That way, you have a 4GbE line into the switch for when multiple users try to access the video data simultaneously.

What size of storage do you need? You'd really need to be looking at SATA III drives and 4 bays is not really a lot of storage. You also need to think about redundancy and rebuild times for your RAID solution. For example, with 4 x 2TB disks in RAID5, you would have 6TB storage, but if a disk failed, you could not start rebuilding until you replace a disk, and rebuilding is already a slow process, so you could face more downtime. However, having 4 x 2TB disks in RAID5 + Hotspare would give you only 4TB storage, but if a disk died, the array would start rebuilding on to the spare disk immediately, saving some time.

You'd probably want to install the OS on a Flash based drive (USB, CF, SD or if you have plenty of cash, SSD). This segregates your data from the OS.

Downloading such volumes of data remotely across the Internet would be a very slow and laborious process unless both sides have a 100Mb connection, and even then it would not be quick.

This would be a very interesting project, I've done similar setups but not for video, they were for Medical Imaging Archiving, but still involved 4-5GB blocks of data, and it worked flawlessly. Network design is important too though.

Let me know if I can be of any more help to you.

Stefan.

Hi Stefan,

Thanks so much for the in depth response. I think I can get my hands on an SSD for install of the OS. As for downloading and uploading, it's true that the speeds won't be great but it won't be worse than or current solution which is Dropbox. I'm going to talk with a buddy of mine and see what we can muster up and make sure that this is the most affordable way. If we commit to it then I'll definitely keep you all posted!

Thanks and I might have more questions!

---

### Post by Jonathan L on 2011-11-21
Hi Zahne

> Would love some help if this is A. doable B. what it would take to do

Sounds perfectly doable to me.   As the others have said, think about your network design, and strip the server down to its minimum.  And of course fill it with RAM.

It is against current orthodoxy, but are you certain you need RAID "to protect the scratch disk"?  In my experience of media environments (edit suites and sound studios) one of the most important things is simplicity and time-to-fix.  So I'd just check you really need it -- RAID0 for performance might be necessary, but if you can make anything simpler I'd recommend it.

Your raw video will arrive (I assume) on portable hard disks with a bit of FTP, and you copy it to the working drives.  If your working drives are removable, that's really practical for managing multiple projects and for example, parking an edit while you do something else.  And when something breaks you can normally reimport from the transit disks more quickly than fool around with the server -- but it all depends on what kind of edits you do.  If it's news, for example, you probably don't have anything lying around for any amount of time anyway.

If you're able to present FTP to your colleagues across the country, you may find that works really well for distribution if elapsed time is cheap.  One recent time I had to ship video we just set it going and waited until it finished (approx a week) as it wasn't consuming any resource we cared about.

Re OS disk.  I'm working with a number of systems now for audio which boot (from USB, as it happens) and copy everything into ramdisk: very cheap, delightfully swift once booted, and maximally stable as the USB stick is read-only.

Just some thoughts, hope they're helpful.

Kind regards,
Jonathan.

---

