---
title: "ubuntu home server beginner here"
date: 2015-01-25
forum: Server Platforms
---

### Post by krustybuntu on 2015-01-25
Hello everyone,

I have a pc that I used to use for gaming, but not anymore since I just got a new better beast.
Hence I decided to convert it to a home file server.

I've been having a lot of trouble trying to create one that works properly.
The guide that I initially followed is: [http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu](http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu)

As it turns out, pysdm is no longer supported, and hence i decided to search out for guides on how to setup samba.
Upon reading and trying out many guides, I still cannot properly configure the server to "mount" my data hdd automatically upon boot.
I have to physically go to the server and open the mounted hdd through gui before i can access it from other computer - makes me think this is not a server if I have to do this!

So, I'm totally fed up now with the server and ready to re-build the os.
Can the community help me in providing a guide (even just a link to a guide that works will do) on how to do it properly? I'm tired of trying all sorts of guides that turn up on page 1-2 of google search "setup ubuntu home server" and failed miserably.

I want to use the server to/as:
1. File server
2. Torrent box
3. Store my research dataset in mongodb and process some dataset using hadoop and hive
4. Website server - this is not so important

My setup: 32GB SSD for boot and 3TB HDD for storage (already have my files and backups in it, so i don't want to lose it when i'm rebuilding the os).

Thanks

---

### Post by NilPointer on 2015-01-26
> 1. File server

There are several options for setting up a file server, depending on intended usage. For a personal home file server (that is, you don't want to let other people, such as friends in) the best option is setting up a SFTP server. It's very secure and setting it up is as easy as installing and configuring sshd (and you get remote control over server on top of that). However, if you want to share your file server with someone, configuring SFTP gets slightly more complicated, as you have to set up separate chrooted account without access to remote command execution for safety reasons, but it's still pretty doable. Things like FTP are very outdated and expose your passwords and files to anyone, however they're still suitable for public servers that anyone can access.

Depending on your intended usage of file server, configuring steps are pretty different, so you need to clarify that first.

---

### Post by krustybuntu on 2015-01-26
Hmm I guess the best description will be a personal home file server.
I just want to set it up in a way that only those who are connected to my home network can access it (no vpn from outside, like you need to be physically home and connect the computer to my network to access the file server).
So no one outside of the home network can access it. I figure it's safer to leave the file server only accessible from home.

---

### Post by nerdtron on 2015-01-26
If have your home router, and did not open any ports or setup port forwarding, you'll be generally safe from the outside world.

Just configure anything you like on the ubuntu machine (even without activating the firewall) and start sharing files on your home network.

---

### Post by NilPointer on 2015-01-26
Well, if it's only to be accessible from home network, then even simple FTP or SaMBa would work. Just make sure that something (router's NAT or firewall) is blocking connections to file server ports from the Internet.

> I figure it's safer to leave the file server only accessible from home.

Not at all. If properly configured, SSH and SFTP is very secure to be used over Internet. Brute-force attack on RSA public-key encryption scheme used in SSH is virtually impossible. I personally run my home server's sshd 24/7 as a file server and there weren't any security-related incidents.

---

### Post by Lars Noodén on 2015-01-26
+1 for Samba if it is LAN-only access and no plans for accessing it over the Internet

+1 for SFTP if it is to be both LAN and Internet access

-1 for [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) in general

SFTP is built into the package OpenSSH-server and is the easiest to set up.  These days the file managers support it out of the box so no special clients are needed.

---

### Post by SeijiSensei on 2015-01-26
As for mounting the drive at boot, you need to add an entry to [/etc/fstab]("https://help.ubuntu.com/community/Fstab").

---

### Post by krustybuntu on 2015-01-26
> **SeijiSensei said:**
> As for mounting the drive at boot, you need to add an entry to [/etc/fstab]("https://help.ubuntu.com/community/Fstab").

Yeah I did that, and ubuntu complained it can't mount the hdd upon booting. Thus I have to skip the mounting all the time for it to boot.

Ok I think samba should do the job, but how to configure it so the hdd is accessible after a boot without me having to lift a finger?

---

### Post by coldraven on 2015-01-26
> Yeah I did that, and ubuntu complained it can't mount the hdd upon booting
Did you make a mount point for the drive?
Something like:
```
sudo mkdir /mnt/my_big_fat_drive
```

Also I think that I'm correct in thinking that you might have tried to mount the drive but not the partition that's on it.
So you should use  /dev/sdb1 instead of /dev/sdb

---

### Post by krustybuntu on 2015-01-26
> **coldraven said:**
> Did you make a mount point for the drive?
Something like:
```
sudo mkdir /mnt/my_big_fat_drive
```

Yes I did

> **coldraven said:**
> Also I think that I'm correct in thinking that you might have tried to mount the drive but not the partition that's on it.
So you should use  /dev/sdb1 instead of /dev/sdb

Hmm that might be the problem.
I'll see if that's it and report back.
From my memory, the error was along the line it doesn't have a permission to mount or something.

---

### Post by Bucky Ball on 2015-01-26
*Thread moved to **Server Platforms**.*

Once you've made your mount point, to mount it there, you'd end up with something like:

```
sudo mount /dev/sdb1 /mnt/my_big_fat_drive
```

That should mount it (replacing what you need to to suit your config, obviously).

---

### Post by mastablasta on 2015-01-27
so you followed that guide and installed desktop on your server :)

by the way there are specialised distros out there that are preconfigured, preset for your needs. try Openmediavault. Debian based. easy to setup. you control it via web browser or if you want command line interface you can use putty or terminal to access it.

you can also just go with Ubuntu server image and then add some GUI for Administration that will make it easy to control server via web browser. for example officially supported is Zentyal (you can imnstall it form ubutnu or use their own image), which will for your case and might even be a bit of an overkill. and then there is also Ajenti and few others such as webmin for example and similar. if you want to use something Redhat (CentOS) based you can look at Nethserver and ClearOS for a beginner friendly, easy, out of the box server setup.


one thing you mentioned ssd - make sure to move /swap partition to hard disk or if you have plenty of ram available you can remove swap completely or at least reduce swapiness.

---

### Post by krustybuntu on 2015-01-27
> **mastablasta said:**
> so you followed that guide and installed desktop on your server :)

by the way there are specialised distros out there that are preconfigured, preset for your needs. try Openmediavault. Debian based. easy to setup. you control it via web browser or if you want command line interface you can use putty or terminal to access it.

you can also just go with Ubuntu server image and then add some GUI for Administration that will make it easy to control server via web browser. for example officially supported is Zentyal (you can imnstall it form ubutnu or use their own image), which will for your case and might even be a bit of an overkill. and then there is also Ajenti and few others such as webmin for example and similar. if you want to use something Redhat (CentOS) based you can look at Nethserver and ClearOS for a beginner friendly, easy, out of the box server setup..

Well before going ahead with the desktop edition, I installed the server edition. However, I didn't manage to work out how to download something via torrent without web browser and how to use deluge with just cli.
So then I installed lightweight gui like lubuntu (I think it was lubuntu) on it. To my demise, there were errors every time i brought the gui up, and it was pretty sluggish.
Then I decided to install the desktop edition, and voila here i'm :P


> **mastablasta said:**
> one thing you mentioned ssd - make sure to move /swap partition to hard disk or if you have plenty of ram available you can remove swap completely or at least reduce swapiness.
Ah thanks for mentioning this. This has totally slipped my mind!

---

### Post by krustybuntu on 2015-01-27
Another question, like I mentioned in the thread, I would like to use this server to run hadoop and mongodb for my dissertation work.
I configured the computer on my desk at uni as hadoop server, and apparently some hackers tried to exploit it by making a large number of
DNS requests of the Uni server for resolution of boot[DOT]servequake[DOT]com.
It just crosses my mind that if this happens to my home server, i'll be in big trouble.
What's the best way to secure the server if i'm to use it for my research purpose?

Alternatively, I have a raspberry pi that's sitting around not being used. I can use that for my dissertation work - only got 6 months left :P

---

### Post by SeijiSensei on 2015-01-27
You also set up that computer so it was visible over the public Internet.  If I were your university, I'd be upset that you were using our network for what appears to be a Quake server.

At home everything is likely behind your firewall router.  Just don't forward any ports to the hadoop server.

---

### Post by krustybuntu on 2015-01-27
> **SeijiSensei said:**
> You also set up that computer so it was visible over the public Internet.  If I were your university, I'd be upset that you were using our network for what appears to be a Quake server.

At home everything is likely behind your firewall router.  Just don't forward any ports to the hadoop server.

Yeah I wasn't too sure what I was doing. Tbh I don't actually know how to set the computer up so that it was visible over the public internet.
In fact, I don't actually know how did the computer become a quake server in the 1st place. 
I just followed this tutorial [http://www.michael-noll.com/tutorials/running-hadoop-on-ubuntu-linux-single-node-cluster](http://www.michael-noll.com/tutorials/running-hadoop-on-ubuntu-linux-single-node-cluster) pretty much to the dot, and nothing else.

---

### Post by coldraven on 2015-01-28
> I didn't manage to work out how to download something via torrent without web browser

Is this any help?
[http://www.webupd8.org/2009/12/setting-up-transmission-remote-gui-in.html](http://www.webupd8.org/2009/12/setting-up-transmission-remote-gui-in.html)

---

### Post by krustybuntu on 2015-01-28
> **coldraven said:**
> Is this any help?
[http://www.webupd8.org/2009/12/setting-up-transmission-remote-gui-in.html](http://www.webupd8.org/2009/12/setting-up-transmission-remote-gui-in.html)

Thanks for that!
I was going to follow this one: [http://www.havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html](http://www.havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html)
But i suppose they are the same except that the link i put up is for deluge. I presume transmission and deluge are equally as good.

---

### Post by krustybuntu on 2015-01-31
> **coldraven said:**
> Is this any help?
[http://www.webupd8.org/2009/12/setting-up-transmission-remote-gui-in.html](http://www.webupd8.org/2009/12/setting-up-transmission-remote-gui-in.html)

Ok, I'm stuck.
I have followed the guide linked above, and i still can't download.
Transmission will complain error: <download folder> permission denied few seconds into the download starts.
I set up the downloads folder to be my data hdd.
I have changed it to the home folder, and it's still coming up with same error.
I have rebooted, and still nothing changes.

---

