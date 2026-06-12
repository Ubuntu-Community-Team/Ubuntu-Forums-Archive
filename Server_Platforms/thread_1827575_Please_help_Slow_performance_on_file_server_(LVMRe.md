---
title: "Please help: Slow performance on file server (LVM/ReiserFS/SoftwareRAID)"
date: 2011-08-18
forum: Server Platforms
---

### Post by lotharz0r on 2011-08-18
Hi.
I'm having a bit of a headache with my file server.
It stores all my important stuff, as well as some music and movies.
I use a second linux box in my living room to "stream" content via NFS or SAMBA share.

The streaming tends to stop several times during playback, and needs to fill up its buffer again before continuing to play.

I also have some Windows XP and 7 based computers that connect to this file server.
I have noticed that directory listing is VERY slow, and there is a huge lag when I want to save/read a file from/to my home directory.

This is my setup:

[LIST]
[*]Ubuntu Server 10.10 64 bit (I have the same problem with 32bit ubuntu)
[*]3 RAID5 arrays with 4 hard drives each
[*]LVM on top of the 3 raid5 arrays.
[*]The Logical Volume i use is about 6.5TB, and I use the ReiserFS file system
[/LIST]

This LVM has grown over the years, and has had som replaced disks. So I have used the pvmove, and extend commands a bit.

I have tried using IOTop and top to check if there is not enough resources available, but that doens't seem to be the problem.

I haven't been able to find out why streaming over the network stops, but I know it is the server that causes the problem.


Does ReiserFS have any performance problems with large logical volumes? Would changing to EXT4 or some other FS give any performance gain?

Are there any settings I can do on the LVM to get better performance?

---

### Post by ian dobson on 2011-08-18
> **lotharz0r said:**
> Hi.

Does ReiserFS have any performance problems with large logical volumes? Would changing to EXT4 or some other FS give any performance gain?

Are there any settings I can do on the LVM to get better performance?

How do you know it's the server and not a network/protocol problem.

What do you get with a network performance tool (iperf)?
Whats the performance like reading/writing directly on the server?
Whats the servers hardware config (CPU,RAM etc)
Does this stutter happen with samba and nfs?
Do you see anything interesting in dmesg?
What speed is your network wording at?
Is your network 100% ok, after a stutter what does ifconfig show?

Regards
Ian Dobson

---

### Post by lotharz0r on 2011-08-18
Thanks for your reply!

You are right, it could also be a network problem.
The reason I think it is a server problem is that I have a computer right next to the server, and when I try opening files, browsing folders and such, the client just freezes, but the HDD light on the server is on the whole time until the client un-freezes. I can also hear the disks churning, and when they stop, things imedialty happens on the client.
Based on this, and beacause it does not stutter when I play movies from USB drives, I thought it had to be a server problem. Either the hard drives, the RAID, LVM or filesystem. Maybe the performance of the server iself.


[LIST]
[*]**What do you get with a network performance tool (iperf)?**
[INDENT]With the standard settings I get this result:
> ------------------------------------------------------------
Client connecting to 10.0.0.5, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 10.0.0.12 port 40163 connected with 10.0.0.5 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    779 MBytes    653 Mbits/sec

[/INDENT]
[*]**Whats the performance like reading/writing directly on the server?**
I've tried hdparm -Tt on /dev/md0 and the other arrays.
I get from 111-150 MB / sec read speed

Using DD to write to a mounted LVM volume
>  time sh -c "dd if=/dev/zero of=speedtest bs=8k count=131072"
131072+0 records in
131072+0 records out
1073741824 bytes (1.1 GB) copied, 15.0145 s, 71.5 MB/s

real    2m44.274s
user    0m0.020s
sys     0m6.160s

Using DD to read the same file:
> time sh -c "dd if=speedtest of=/dev/nul bs=8k"
131072+0 records in
131072+0 records out
1073741824 bytes (1.1 GB) copied, 9.66466 s, 111 MB/s

real    0m9.667s
user    0m0.030s
sys     0m1.000s

[*]**Whats the servers hardware config (CPU,RAM etc)**
[INDENT] Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
3GB RAM
Using 1 builtin SATA controller, one Promise Sata 300 TX3 and one Silicon Image SATA SiL 3114
Gigabit Pci Express NIC
Gigabit builtin NIC
Boths NICS have same problem
[/INDENT]
[*]**Does this stutter happen with samba and nfs?**
[INDENT]yes[/INDENT]
[*]**Do you see anything interesting in dmesg?**
[INDENT]no[/INDENT]
[*]**What speed is your network wording at?**
[INDENT]Got gigabit switches. Sync speeds:
Server:
        Speed: 1000Mb/s
        Duplex: Full
Client:
        Speed: 1000Mb/s
        Duplex: Full

[/INDENT]
[*]**Is your network 100% ok, after a stutter what does ifconfig show?**
I have not tried running ifconfig after a stutter.
What should I look for? Drops, errors?
[/LIST]

---

### Post by robgr85 on 2011-08-18
Have You tried to test the speed connection from the client to the server when downloading/uploading single file?  Have You tried to restart Your network switch? Have You tried to connect different one? What are the pings between network stations and server? Do connections by other protocols works right (http, ssh etc)? Do You use some security tools, like SELinux?

Does it happen without the difference in different directories? I've got some problems with browsing dvd's with large amounts of pictures in folders on windows machines. Generating thumbnails hanged windows clients.

Run top on Your server,  then connect with windows client and tell us if the load on the server drasticly increases during working from windows clients or not. run system moniotor on windows client and tell us what takes all of Your CPU/RAM resources.

P.S. You have quite powerfull platform for so simple shares. I would assume that there is some misconfiguration issue on the server, or networking problems.

---

### Post by rubylaser on 2011-08-18
iperf shows decent (not great speeds), but certainly enough to support streaming even Bluray rips.  What happens if you transfer a file from your OS drive, assuming it's on it's own separate drive from all the mdadm arrays.  This should be able to stream without hiccup based on the iperf stats that you provided.  Otherwise, it sounds like a network problem (ethernet cable, nic, switch, the nic, or cable on the HTPC, etc)

I can understand adding hard disks over time, but this really is unnecessarily complex.  You no longer need LVM to grow or shrink an mdadm array, so unless your using LVM snapshots, that layer can be eliminated.  And, the (3) raid5 arrays really could benefit from being combined.  But, I'm guessing the reason you have it this way is you have a bunch of different sized hard drives that you've joined into separate arrays. So, I would run hdparm -tT /dev/mdX against each array and see if one is causing the slowdown.

---

### Post by lotharz0r on 2011-08-18
> **robgr85 said:**
> Have You tried to test the speed connection from the client to the server when downloading/uploading single file?  Have You tried to restart Your network switch? Have You tried to connect different one? What are the pings between network stations and server? Do connections by other protocols works right (http, ssh etc)? Do You use some security tools, like SELinux?

Does it happen without the difference in different directories? I've got some problems with browsing dvd's with large amounts of pictures in folders on windows machines. Generating thumbnails hanged windows clients.

Run top on Your server,  then connect with windows client and tell us if the load on the server drasticly increases during working from windows clients or not. run system moniotor on windows client and tell us what takes all of Your CPU/RAM resources.

P.S. You have quite powerfull platform for so simple shares. I would assume that there is some misconfiguration issue on the server, or networking problems.


I have tried restarting the network switches.
I've got two NetGear 1gbit switch in a technical room, and one in my living room.
I have tried changing cables, but not changing the switch. They are both new, but I could try connecting the HTPC directly to the other switch, or try a long network cable and connect them directly to see if there is a difference.

I will also try the rest of your tips, and post a reply.
I have several times used a laptop that runs top at the server and client at the same time to see if there is any performance issues, but the cpu load never hits the roof on either computer.

SSH works, HTTP works.
SSH is slow when I log in. When I have typed my username and password, the time between I press enter on the password promt and when I get my BASH prompt varies. Sometimes it just hangs for several minutes, sometimes it takes 2 seconds.

The SSH login often hangs when I have opened up screen and I run several screens with different commands and stuff going on at the same time.


I don't use any security protocols or firewalls on the internal network.

---

### Post by lotharz0r on 2011-08-18
> **rubylaser said:**
> iperf shows decent (not great speeds), but certainly enough to support streaming even Bluray rips.  What happens if you transfer a file from your OS drive, assuming it's on it's own separate drive from all the mdadm arrays.  This should be able to stream without hiccup based on the iperf stats that you provided.  Otherwise, it sounds like a network problem (ethernet cable, nic, switch, the nic, or cable on the HTPC, etc)

I can understand adding hard disks over time, but this really is unnecessarily complex.  You no longer need LVM to grow or shrink an mdadm array, so unless your using LVM snapshots, that layer can be eliminated.  And, the (3) raid5 arrays really could benefit from being combined.  But, I'm guessing the reason you have it this way is you have a bunch of different sized hard drives that you've joined into separate arrays. So, I would run hdparm -tT /dev/mdX against each array and see if one is causing the slowdown.

I will try streaming from the OS disk. The OS disk is not part of an LVM or MDADM array.

The reason why I've got the large LVM is because the raid array consists of one array with 4x500GB disks, one with 4x750GB and one with 4x2TB disks.

I have tried running hdparm -tT against each array, all arrays perform from 110MB/s to 150MB/s. Not great speeds, but enough for my use.

The network performance could be slow because of the NetGear switches, or because the HTPC is an Asus EEEbox EB1012. Not the fastest computer around, but good enough for streaming HD media.

I'll try the same test from another computer, and try without the switches.

---

### Post by robgr85 on 2011-08-18
> **lotharz0r said:**
> 
SSH is slow when I log in. When I have typed my username and password, the time between I press enter on the password promt and when I get my BASH prompt varies. Sometimes it just hangs for several minutes, sometimes it takes 2 seconds.


Slow SSH logins are often caused by problems with reverse DNS records (it probably asks external DNS server for Your internal IP, wait for response which can not be served and then go on). You should configure Your local caching DNS properly, or set 

> 
UseDNS no 

In */etc/ssh/sshd_config *file

But it would be probably better to setup local DNS, which might solve Your problem. I'm not 100% sure about that, but if I were You I would give it a try - if there is no massive load on both server or client it is problably network/configuration issue (if all the cables, switches, nics are ok it is software related). Does Your switches allow to get some stats via web interface (are these managed ones)?

---

### Post by lotharz0r on 2011-08-18
> **robgr85 said:**
> Slow SSH logins are often caused by problems with reverse DNS records (it probably asks external DNS server for Your internal IP, wait for response which can not be served and then go on). You should configure Your local caching DNS properly, or set 


In */etc/ssh/sshd_config *file

But it would be probably better to setup local DNS, which might solve Your problem. I'm not 100% sure about that, but if I were You I would give it a try - if there is no massive load on both server or client it is problably network/configuration issue. Does Your switches allow to get some stats via web interface (are these managed ones)?



I forgot to mention it, but I have allready done this.
SSH logins got much faster. The time from when I typed my password until anything happened was very slow before. Now the welcome message appears, but it takes a long time for the bash prompt to appear sometimes. Not allways.

**Other stuff I tried now**
I do have KVM installed on this server.
It has performed extremly bad. So I uninstalled it now.
I noticed that the dnsmasq process was running prior to uninstallation.
This should not be nescessary when I'm not running virtual networks?
I also uninstalled bridge-utils.

I have also stopped apache, mysql and nagios3.

So I'm down to mdadm monitoring, smartmontools, nfs and samba.
I'll try using the HTPC and windows computers now.

---

### Post by lotharz0r on 2011-08-18
I think I found the reason for the SSH login to be slow.
I can see in top and iotop that a process called xauth starts.
Iotop reports that it reads data at about 300k /sec, and it just goes on for about 4-5 minutes before its done.
If I disable X forwarding in putty, SSH login is fast.

So the slow SSH login is unrelated to the file sharing problems.

---

### Post by tehtide on 2011-08-18
If you have software raid are there any errors reported on the raid? What does the output of ```
sudo cat /proc/mdstat
``` look like?

I had a SLOW raid server and it boiled down to a SATA cable going bad.

---

### Post by lotharz0r on 2011-08-23
I've got a failed disk in one of the arrays ATM. Waiting for a new disk to arrive. I am aware of this. The problem did not occur after the disk failed, it was there before as well.

> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md3 : active raid5 sdl1[0] sdk1[3] sdi1[2] sde1[1]
      2197715712 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

md2 : active raid5 sdh1[2] sdg1[1] sdj1[3] sdf1[0]
      1465151808 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

md0 : active raid5 sdc1[3] sdd1[2] sdb1[1]
      5859791424 blocks level 5, 64k chunk, algorithm 2 [4/3] [_UUU]

unused devices: <none>


The md0 array is the newest one. It's got WD20EARS disks (Western Digital Caviar Green 2 TB).
I've read bad stuff about them, and I'm beginning to wonder if they are the source of the problem.

I have been logging the Load Cycle Count that Smartmontools reports, and it increases every hour.

Could a parked read head cause a lag when it has to wake up?

There's a lot of forum posts and articles about this drive and the Load Cycle issue.
The factory default setting is that the read heads is being parked every 8 seconds.
WD has got a tool called WDIDLE to modify this, but WD20EARS is not a officialy supported drive.
Since I've got a lot of data on the drives, I have not tried to run the tool.

Within a year, I've had two of the WD20EARS drives fail before the warranty ran out.

I have tried running hdparm -S 252 on all the WD20EARS drives. I will monitor the Load Cycle Count and see if it stops increasing as fast as before, and if the media playback stops lagging.


The WD20EARS drive is an Advanced Format Drive.
I see that one of the drives is not partitioned correctly.
I followed a guide when I partitioned the drives. The starting sector of the partition had to be dividable by 4. So I chose starting sector 40.
I see now that one of the drives (sdb1) has starting sector 31.
The performance on the drive and on the partition is the same as the other drives when I run hdparm -t, but when I get the replacement drive I'm waiting for, I will fail /dev/sdb1 and repartition it to see if it helps.
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              31      243201  1953263872   fd  Linux raid autodetect

Any thoughts on this?
I know it is possible to realign the partition, but is that safe when it is a Linux raid autodetect partiton?

---

### Post by ian dobson on 2011-08-23
Hi,

hdparm -S 252 won't work on the ears drives.

Pull the drive out of the box, plug into a different box, boot to dos and run the wdidle3 tool to disable the head parking.

Regards
Ian Dobson

---

### Post by lotharz0r on 2011-08-24
Ok. Thanks for your reply.

What about the data on the drives. Is it safe to do this?

---

### Post by lotharz0r on 2011-08-26
Looks like the problems gone now.
No problems with media playback on the HTPC for some days now.

The lagging stopped when I removed the KVM service, libvirt and all that stuff, and configured the HTPC to get all files via NFS with mount option: rsize=8192,wsize=8192,timeo=14,intr

Don't know which was the problem.


Oh. And also, it looks like hdparm -S 252 works on the WD20EARS drives.
I have configured the server to issue this commands to all drive at startup, and when the server is idle for some time and I try running mdadm -D /dev/md0 there is a delay and I can hear the disks spinning up.
/dev/md0 is the array with the WD20EARS drivers.

---

### Post by ian dobson on 2011-08-28
> **lotharz0r said:**
> Looks like the problems gone now.
No problems with media playback on the HTPC for some days now.

The lagging stopped when I removed the KVM service, libvirt and all that stuff, and configured the HTPC to get all files via NFS with mount option: rsize=8192,wsize=8192,timeo=14,intr

Don't know which was the problem.


Oh. And also, it looks like hdparm -S 252 works on the WD20EARS drives.
I have configured the server to issue this commands to all drive at startup, and when the server is idle for some time and I try running mdadm -D /dev/md0 there is a delay and I can hear the disks spinning up.
/dev/md0 is the array with the WD20EARS drivers.

Interesting on my EARS drives hdparm didn't work for me. The head load count continued to rise even after running hdparm. Running wdidle fixed it on my drives.

Regards
Ian Dobson

---

