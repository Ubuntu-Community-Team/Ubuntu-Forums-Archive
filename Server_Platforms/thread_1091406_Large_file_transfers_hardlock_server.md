---
title: "Large file transfers hardlock server"
date: 2009-03-09
forum: Server Platforms
---

### Post by chorca on 2009-03-09
Alright, this is an odd issue. I'm not sure how to troubleshoot this, so more than anything, I'm trying to figure out what paths to take to start figuring out the issue I'm having.
------------------------------------

I've just built myself a NAS. Intel D945GCLF2 Atom board, 2GB RAM, Promise Tx4 SATAII controller card with 4 WD Green WD10EADS 1TB drives running software RAID 5 through MDADM. Have Ubuntu Server 8.10 installed on an 8GB USB Flash drive (SanDisk Cruzer) with no swap and noatime, and it's been running just peachy.

Basically I'm moving all of my media (ISOs, large documents, videos, backups and such) over onto this machine. Most of it consists of large files and such, and since most all the other machines on the network are Windows-based, I thought I would just use Samba and everything would be peachy. Maybe take a hit on the transfer performance, but I've got time.

I set everything up on the system, got it all up and running. The RAID operates excellent, everything is going well. I left the rebuild running, and had transferred about 50GB of data to it, just to test the speed while the rebuild was occurring and to make sure that the shares were operating properly. Left the machine doing it's initial rebuild overnight, only to wake up to a locked machine.
The SSH connection had dropped. No video out on the local console, would not respond to keyboard commands. Pings were not returned. The machine was basically hardlocked, the rebuild had also halted, though it was supposed to continue into the morning, I knew as I could hear no disk activity happening.
I reset the machine, the rebuilt restarted from zero, and I left it run all day, keeping an eye on it remotely from work.

The rebuild finally completed, and I began to transfer about 200GB of data to it that night over SMB, without issue. It was running very smoothly and things were actually going fairly fast (44MB/sec transfers). Later on, I was streaming a show I had recorded from it, and the stream cut out. I checked the share, and the connection had dropped. I tried to SSH into the box, only to find it in the same hardlocked condition: No network, no video, no nothing. Reset, came back up quickly and began operating properly.

This past night after transferring another 200GB or so of data to it, I experienced the exact same hardlock. Again.

I'm now seeing some sort of pattern here, that I just don't understand. I've checked the logs, they don't show anything at all happening before the lockup. Right now the only odd parts of the setup are running off of a flash drive, and running no swap. I've been keeping an eye on memory, and real usage never goes over 10%. I started thinking it may be a kernel panic, but without having a monitor on it, turned on, with an image on it 24/7, it's kind of difficult to catch in the act. I'm wondering if the fact that it has a USB boot device is preventing it from writing a kernel dump? I really am not sure at this point, I have never had to troubleshoot something like this before. I updated the BIOS on the board to the latest version as well, but that didn't seem to resolve the issue.

Anyone have any ideas on what my next steps should be? Image the USB drive onto a regular HDD and try that? Create a swap partition? Any help is appreciated.

---

### Post by glantucan on 2009-05-15
Hey!

I'm having the same issue here with ssh in my laptop. No matter whether I secure copy from it or to it the system hangs when the ammount of data is big.

Anyone?

Glantucan

---

### Post by drave on 2009-05-15
hardlocks can be hardware/memory problems. can you leave it running memtest for a day

---

### Post by fjgaude on 2009-05-15
Also, I'm not sure how many of the Linux copy programs have been tested with huge file transfers. The drive size and movies are something relatively new. These terabye drives have to be considered as an issue and handled correctly by all the copy programs. <sigh>

---

### Post by drave on 2009-05-15
ive copied directories that had > 5 terrabytes, but that was on system using areca raid cards and 500G drives. 

worked, took ages

---

### Post by fjgaude on 2009-05-15
Yes, yes! I wonder if the individual file size has something to do with the issues some folks are facing? Lots of files, less than a Gigabyte each may not cause issues, but it's the 15TB ones that do?

---

### Post by 3L33T on 2009-05-16
> **chorca said:**
> 
Anyone have any ideas on what my next steps should be? Image the USB drive onto a regular HDD and try that? Create a swap partition? Any help is appreciated.

Consider using the old skool unix/linux 'dd' ('dd if=/dev/sdbXX of=/dev/sdcXX').

Or, use old skool 'ftp'.  I use 'vsftpd'.  I've used both methods flawlessly when moving my torrent HD movies from one disk/USB media to another.

---

### Post by windependence on 2009-05-16
> **3L33T said:**
> Consider using the old skool unix/linux 'dd' ('dd if=/dev/sdbXX of=/dev/sdcXX').

Or, use old skool 'ftp'.  I use 'vsftpd'.  I've used both methods flawlessly when moving my torrent HD movies from one disk/USB media to another.

Agree here and I'll add you can also use SCP.

Check out FreeNAS. Much cleaner, smaller, better performing solution IMHO.

-Tim

---

### Post by JohnnyVW on 2009-05-16
I've been having this same issue.  It happens with rsync via ssh.

I discovered it when I was "backing up" my ./home directory to the server.  I initially did it through a SMB shared drive, then tried it through rsync.  It hard-crashed the networking part of the server.  No http, no smb, no ssh, etc.  It did recover once without a reboot...  I came back after about an hour or so (probably happened quicker) and I could connect again.


Granted I do have some larger files, but certainly not many gigabytes or terrabytes.

---

### Post by hictio on 2009-05-16
Another options you might want to test are limiting the bandwidth and also reducing the CPU priority via nice?
To reduce the bandwidth using scp you'll have to use the option '-l' and on rsync suing '--bwlimit='.
To reduce the CPU priority, add this to the beginning of your command '/bin/nice -n +19'.

---

### Post by JohnnyVW on 2009-05-16
> **hictio said:**
> Another options you might want to test are limiting the bandwidth and also reducing the CPU priority via nice?
To reduce the bandwidth using scp you'll have to use the option '-l' and on rsync suing '--bwlimit='.
To reduce the CPU priority, add this to the beginning of your command '/bin/nice -n +19'.

Thanks, hictio!

So, something like this?

```
rsync -l -e ssh -avz /home/johnny johnny@ubuntuserver.local:/media/music/johnny_BU
```

( /media/music is my 100GB drive )

---

### Post by hictio on 2009-05-16
> **JohnnyVW said:**
> Thanks, hictio!

So, something like this?

```
rsync -l -e ssh -avz /home/johnny johnny@ubuntuserver.local:/media/music/johnny_BU

```

( /media/music is my 100GB drive )

Is this rsync going over the network? 'ubuntuserver.local' is the same box you are executing the rsync? 
If so, you don't need the ssh bit, and I doubt you'll get any benefit from adding a  bandwidth throttle either.
Just pass the nice option to what you posted above:

```

/bin/nice -n +19 rsync -avz /home/johnny johnny@ubuntuserver.local:/media/music/johnny_BU

```

---

### Post by JohnnyVW on 2009-05-16
> **hictio said:**
> Is this rsync going over the network? 'ubuntuserver.local' is the same box you are executing the rsync? 
If so, you don't need the ssh bit, and I doubt you'll get any benefit from adding a  bandwidth throttle either.
Just pass the nice option to what you posted above:

```

/bin/nice -n +19 rsync -avz /home/johnny johnny@ubuntuserver.local:/media/music/johnny_BU

```

No, ubuntuserver.local is not the same machine.  I'm runing this over the network.  So, I'm backing up my desktop PC's home directory to the server over the network.

I'm running the first command I posted now with the  "-l " option.  It's better, but it's stalling right now.  I noticed on my local machine, the network monitor shows a little red clock symbol when it stalls.  I'm almost wondering if it's this machine and not the server???  Hmmm...

Attached is the little clock symbol on this PC.

---

### Post by JohnnyVW on 2009-05-16
Yeah, now it stalls, but then continues.  Before the " -l " command, it'd just stall, then fail.

---

### Post by hictio on 2009-05-16
> **JohnnyVW said:**
> No, ubuntuserver.local is not the same machine.  I'm runing this over the network.  So, I'm backing up my desktop PC's home directory to the server over the network.

I'm running the first command I posted now with the  "-l " option.  It's better, but it's stalling right now.  I noticed on my local machine, the network monitor shows a little red clock symbol when it stalls.  I'm almost wondering if it's this machine and not the server???  Hmmm...

Attached is the little clock symbol on this PC.

Cool, if its over the network, then, it is like this:

```

/bin/nice -n +19 rsync -e ssh -avz --bwlimit=20 /home/johnny johnny@ubuntuserver.local:/media/music/johnny_BU

```

This puts a 20 Kbps limit, but, this is useful if the files are big, say, a couple of MB in size, if they are small, it doesn't have that much effect.
Oh, yeah, the '-l' argument is not for rsync, but for scp.

---

### Post by JohnnyVW on 2009-05-16
> **hictio said:**
> Cool, if its over the network, then, it is like this:

```

/bin/nice -n +19 rsync -e ssh -avz --bwlimit=20 /home/johnny johnny@ubuntuserver.local:/media/music/johnny_BU

```

This puts a 20 Kbps limit, but, this is useful if the files are big, say, a couple of MB in size, if they are small, it doesn't have that much effect.

Very cool!  I'll try it a little later (I have some errands to run).  Thanks for the help!!!

I'll report back on what happens.  :guitar:

---

### Post by JohnnyVW on 2009-05-16
I have good news and bad news...

The good news:  it's working well.  

The bad news:  it has been running for 6 hours.  

It seems we're on the right track, though!  It's on a few 350MB video files.  Eash are taking ungodly amounts of time to transfer.  There are some 1 and 2 GB files ahead...  :shock:

My head is not quite wrapped around what we did here...  Well, kinda.  I realize that we have throttled the bandwidth and CPU usage.  What about "--bwlimit=50" or more?  Why did you say 20? 

Once again, it is working...

I used:
```

/usr/bin/nice -n +19 rsync -e ssh -avz --bwlimit=20 /home/johnny johnny@ubuntuserver.local:/media/music/johnny_BU

```

---

### Post by hictio on 2009-05-16
> **JohnnyVW said:**
> I have good news and bad news...

The good news:  it's working well.  

The bad news:  it has been running for 6 hours.  

It seems we're on the right track, though!  It's on a few 350MB video files.  Eash are taking ungodly amounts of time to transfer.  There are some 1 and 2 GB files ahead...  :shock:

My head is not quite wrapped around what we did here...  Well, kinda.  I realize that we have throttled the bandwidth and CPU usage.  What about "--bwlimit=50" or more?  Why did you say 20? 

Once again, it is working...

I used:
```

/usr/bin/nice -n +19 rsync -e ssh -avz --bwlimit=20 /home/johnny johnny@ubuntuserver.local:/media/music/johnny_BU

```

Yeah, sure it was just an example, you can taylor the "--bwlimit" value to suit your needs.

---

### Post by JohnnyVW on 2009-05-16
Thanks, hictio!

I'll try a few settings!

---

### Post by kaspar128 on 2009-05-17
I have a similar problem. I recon that there is a problem with ubuntu handling raid5 devices? Everything to/from/on my server goes well except when i'm copying(rsync,cp etc. etc.) from the RAID5 drive to another mounted device, then the whole system freezes within seconds.
But in my case the RAID5 device is controlled by hardware.

([http://ubuntuforums.org/showthread.php?t=1162165]("http://ubuntuforums.org/showthread.php?t=1162165"))

---

### Post by fjgaude on 2009-05-19
I copy large files from mdadm raid5 to other drives on the same machine or down the LAN without issue.

---

### Post by grantemsley on 2009-05-25
I had similar issues with a shuttle computer, hard locks when copying over the network.  Turns out it had some stability issues with the hardware.  Underclocking the RAM from 800MHz to 667 (or 667 to 533, i forget which) fixed it for me.

---

### Post by JohnnyVW on 2009-05-25
I'm still trying to get this working...

One thing grantemsley just mentioned that triggered something in the back of my mind...  hardware...

Both the server and client (my desktop) have built-in NIC's.  I wonder if that has anything to do with it?  I may try firing off a bunch of files to my regular desktop from the laptop (uses a PCMCIA NIC) or even to the laptop to see what happens.

I have been playing with the "--bwlimit" switch.  I went nuts and set it to 2000.  Nope...  then 1500...  nope, then 1000, nope, then 500, nope...  still stalls.

I play with video files and they can get quite large.  A 3-day backup is unacceptable.  I can't even move/copy a large file via samba, scp, etc. without the networking on the server borking.  *sigh*

so, for now, I have an external drive hooked up for backup purposes. 

The idea for the server was to be able to backup my wife's XP machine, my Ubuntu machine, the Xubuntu laptop and my work laptop (XP) to the server.

---

### Post by Vegan on 2009-05-26
My main workstation is Windows based, but my IBM is my web server and it runs the Ubuntu with a LAMP stack fine.

I am slowly building a new machine and will be using it as a file server. Depending on funds will see how fast it comes to life.

I have some other machines and some have Linux on them.

On the IBM I use Samba to share the /var/www folder. Now given say 2 servers, call them OLD and NEW for want of a name.

What I did was use Windows to select the files on one server and drop them onto the other. No problems at all with all manor of files from PHP pages to MP3 and computer chess tablebases which can run to 1 TB each or even more.

My LAN is very fast so moving files from one server to another is fairly quick. I am not sure how to move files with the CLI from machine to machine effectively.

---

### Post by grantemsley on 2009-05-26
Have you checked /var/log/messages and dmesg for any hardware related errors?

A flaky network card could cause symptoms like that.

You could also try putting in a PCI network card if you have one and see if that helps.

If the BIOS will allow you, try underclocking the RAM and see if that helps.  I've had systems that will pass memtest just fine but won't run reliably at their rated speeds when the rest of the system is heavily loaded.

---

### Post by JohnnyVW on 2009-05-27
I think you guys are onto something.  Hardware.

I'm running the rsync through ssh from my desktop PC to my Xubuntu laptop and it's going fine.  No stalls.  I think I'm still throttled to 1500KBps, but I have made it through my video files with flying colors.  I think I need to get a PCI NIC for the server and disable the internal NIC.

As far as underclocking...  Not sure how to do that in the BIOS.  The server is a Compaq Presario S3200NX.  It's an older PC (AMD XP2000+) with 1GB (512MB X 2) of DDR PC2700 RAM.

---

### Post by grantemsley on 2009-05-27
> **JohnnyVW said:**
>  The server is a Compaq Presario S3200NX.  It's an older PC (AMD XP2000+) with 1GB (512MB X 2) of DDR PC2700 RAM.

If it's a major manufacturer's computer, it probably doesn't have over/under clocking options in the BIOS.  They remove them so people don't go "hey...I wonder what this does" and fry something.

Hopefully the PCI nic will work out.

---

