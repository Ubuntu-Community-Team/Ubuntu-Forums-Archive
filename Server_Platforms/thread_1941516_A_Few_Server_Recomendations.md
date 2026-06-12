---
title: "A Few Server Recomendations"
date: 2012-03-15
forum: Server Platforms
---

### Post by Kyledoo on 2012-03-15
Hello, I am starting to configure my Ubuntu Server. It is going very well and I am super happy with the performance and ease of configuring it!

However, I have hit a few minor speed bumps

Let's start with the one that may make a few people laugh...
I want to share my server's floppy drive
Yes, it HAS a floppy drive, and we do have many floppy disks in the house with old files on them that have not been put onto other media yet. This is owned by several people and I figured the best way to be able to access this data is to make the floppy drive on the server accessible via SAMBA. It is shared properly, however, it doesn't seem to mount properly. 

The configuration for it follows:
[Floppy]
comment = Floppy
path = /media/floppy0
read only = no
writable = yes
guest ok = yes
locking = no
preexec = /bin/mount /media/floppy0
postexec = /bin/umount /media/floppy0

Which I modified from the example to share a CD-ROM drive (Which is working perfectly, btw)

**Is there some magic I need to use to make the floppy mount/un mount properly?** The available space on the network drive mapped to this share is showing the free space on my main file system hard drive. 

Next, Flash drive mounting
It would also be cool to share a flash drive from the server (mainly for access from smartphones/tablets) This is working properly for me, however, since the flash drive is mounted under root (no user is logged into the console), **none of the other users (and therefore no samba user) has write permissions on the drive**. Is there a way to make this work (and make it work automatially? Currently the drive becomes available almost immediately after plugging it in, and I'd like for it to stay that way)

Next, internet configuration
I would like to make at least the web server and the ftp server available over the internet. I am using proFTPd for the FTP server and I do have webmin installed and this is how I first installed proFTPd. **Any tips on how to make these securely accessible over the internet?** Is it possible to configure an additional "virtual" web server (for example, one for an intranet page and one for a public web site)? For FTP, which security method should be used? I know FTP transfers passwords over plain text and that is non-ideal. I do have a dynDNS account and my router (wndr-3700 running dd-wrt) has this option, I am just not sure of how to make the requests go to the server (whose IP address on my network is 192.168.1.2)

Next, Media server
I am currently using miniDLNA. It is rock solid and doesn't take up many resources. I LOVE IT! However, a primary goal of setting this server up in the first place was to watch our media on our Google TV, which does not support that many formats. For this reason, **I am looking at setting up something that does transcoding.** I have had a little trouble setting up MediaTomb(including getting an error message on the client when trying to play a video: something along the lines of "an internal error occured"). What would you suggest? If it is Mediatomb, what are some helpful configuration options? I am really trying to do as much of this as I can without installing a desktop environment, because my server is running on a P4 with 512Mb ram, and I don't want it using any more resources than necessary.

And Finally (for now)
What is all this I hear about running a VM on the server and connecting to it with a VNC client? **That sounds VERY cool and I would be interested in running an Ubuntu desktop VM as well as a Windows XP, or (if my machine can handle it) Win7.** I have an android tablet(transformer prime) well... had it... broke the screen and am waiting for them to become available to buy another. I can see how this would VASTLY improve the function of that tablet especially if I can remotely connect to this VM over the internet. A few questions I have about this is: **How resource intensive is it? How is the speed when connecting over a 10/100 network? Level of difficulty of installation?**
**Also, how do you easily START one of these VM's from a workstation (or my tablet)**

I know this is a lot of questions, but I wanted to start one thread rather than possibly bringing others off track.

---

