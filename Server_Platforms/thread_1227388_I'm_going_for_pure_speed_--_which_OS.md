---
title: "I'm going for pure speed -- which OS?"
date: 2009-07-30
forum: Server Platforms
---

### Post by garfonzo on 2009-07-30
Alright, I'm looking at setting up my home server (private LAN only) for the following purposes:

- file sharing ** Main purpose
- video/audio streaming
- the occasional download -- rare though

I'm trying to get the best speed so that the computers on my network don't have to wait for the system to serve the files, and I don't want video to hiccup as I'm watching it (I rip my DVDs, uncompressed to the server, and want to stream them to any computer).

My question is, what is better: 
Ubuntu 9.04 Server:
   - RAID 0 for disk speed
   - rsync for backup
   - Samba for translations - possible performance issue here?

Windows XP:
   - no Samba (all comps on network are Windows) so possible speed benefit
   - no great way to use rsync (I don't think?)
   - no RAID built into OS (I don't want a RAID card)


I want a good backup systems and WinXP is a bit weak on that, compared to rsync I believe. For each hard drive I have, I have a duplicate which is mirrored via rsync at this point. 

Here is the system that the OS will reside on:

CPU: AMD Athlon 64 X2 5200+ (64 bit)
Motherboard: Two SATA connections, two IDE connections, 2GB Ram (only two slots, perhaps bigger sticks are in order?)
Hard drives:
   500GB X 2
   320GB X 4
   90GB X 1 for the OS
Network adapter: Wired Gigabit to a gigabit router

I'm relatively comfortable with command line and am fine with learning what I don't already know. So usability wise, either OS is ok.

So, what do you think?

---

### Post by Macchi on 2009-07-30
> **garfonzo said:**
> Alright, I'm looking at setting up my home server ...
I'm trying to get the best speed...


Probably you have already heard that GNU/Linux offers a higher performance, much higher reliability, and great flexibility through a wide range of free open source software solutions that can be installed for free without hassle. Ubuntu is definitely a better solution.

---

### Post by garfonzo on 2009-07-30
Thanks for the reply.

> **Macchi said:**
> Probably you have already heard that GNU/Linux offers a higher performance...

Would you say that Ubuntu would more effectively use my computer's hardware or would much of the hardware be unused due to Ubuntu's efficiency and my relatively minimal (compared to enterprise solutions) requirements? Much like a Porche driving through a school zone at 30km/h -- lots of power but who cares if you are only doing 30? Know what I mean?

> **Macchi said:**
> Ubuntu is definitely a better solution.

I'm leaning that way...

Anyone else have some thoughts?

---

### Post by Arup on 2009-07-30
For speed nothing comes close to sidux, its not that easy to install like Ubuntu so do consider that.

---

### Post by Macchi on 2009-07-31
High-performance comes often bundled with diverse trade-offs.
Hypothetically, the best way to use most of the processing power available on a computer system is to directly program it in assembly (i.e. machine language). Obviously this is often neither practical nor flexible enough. If you simply want to create a file server with media streaming for a few users you probably don't need a very high performance system. Most modern low-end office boxes would do the job with a well configured standard linux distro. 

In other words:Your existing hardware and Ubuntu alternate install (AMD) is good for a start. Add more memory or disks later. 

I recommend the Ubuntu alternate install disk so that you can set up software raid for the file system. If you install a complete desktop then all configuration and remote access can be done from a graphical interface in a few minutes. Later you may remove and purge the graphical desktop environment or simply prevent it to start on boot, if you wish to save memory. Who cares later about a few hundred megabytes of disk space for gnome or KDE?

(I should mention that many system administrators would never recommend installing a graphical desktop environment on a server, but believe me, it will save you a lot of time!)  


People can write dozens of books about creating a group server, thus check the Ubuntu documentation (both official and community documents)

---

### Post by lykwydchykyn on 2009-07-31
I'm not sure why you would think samba would have speed issues?  I've never found it to be significantly slower than Windows' smb/cifs implementation.  'Course I've never seen benchmarks, so who knows?

I use Debian stable for my own server.  Personally I'd recommend either that or Ubuntu Hardy Heron (8.04).  Reason being, there's just no good reason to want to update a server every 6-12 months.  With either Ubuntu LTS or Debian stable you have about 2 years between releases.

I'm not an expert on multimedia streaming, but I believe VLC is supposed to be good.  Others here can probably share their experiences.

I've tried using Windows XP as a server before; sometimes it's ok, but I keep finding there are little "gotchas" here and there that can be frustrating.

---

### Post by Macchi on 2009-07-31
Samba is actually a "chatty" and less safe protocol, thus there are risks for several issues if used over slow lines and/or with VPN connections. Never run it unprotected over the internet. On a LAN samba should not have performace issues for small groups. 

For a streaming server I have used Firefly (works with itunes, Mac, Windows, and Linux). I have also read references to gnump3d on streaming servers.

---

### Post by lykwydchykyn on 2009-07-31
> **Macchi said:**
> Samba is actually a "chatty" and less safe protocol, thus there are risks for several issues if used over slow lines and/or with VPN connections. 

Yes, but I guess I'm wondering why the OP would expect it to be slower than the Microsoft implementation of the same protocol.  Both are very chatty if you leave netbios name resolution running, though it can be disabled to help a little.

There are better file sharing protocols, but they're all more complicated to set up on windows clients.

---

### Post by go2dell on 2009-07-31
If you really want the absolute fastest server, Gentoo is your baby.

If you want to retain your sanity and avoid days and weeks of compiling absolutely everything on the system all the time, Ubuntu is great.  For your purposes, it will have more speed than you will ever use.

I would highly recommend against using RAID 0 on your server, however, unless you have another dedicated backup server to backup your server.  You never know when a disk controller or drive gremlin will pop up to bite you.  Unless your hard drive controller is remarkably slow -- as in ATA66 or slower -- you'll likely not see a difference in speed anyway.  Ext3 is fairly remarkable at managing to recover data (ask me how I know ;) ) but it's a hassle you don't want to experience if you can avoid it.

---

### Post by garfonzo on 2009-07-31
> **lykwydchykyn said:**
> Yes, but I guess I'm wondering why the OP would expect it to be slower than the Microsoft implementation of the same protocol...

I created a thread about a server's bottleneck over [here ]("http://ubuntuforums.org/showthread.php?t=1221588")and the second reply hinted that Samba *could* pose speed issues if not set up correctly. From that I assumed that one could setup Samba and have it 'work' but not at its optimal. That was my rational for mentioning the speed issue there.

> **Macchi said:**
> I recommend the Ubuntu alternate install disk so that you can set up software raid for the file system.
With a RAID 5 setup, would the performance increase be worth the effort? If I were to RAID 5 two of my 320 GB drives, and then rsync those two discs to my other two 320 drives, I would have a performance increase and a backup process. Or am I mixing apples and oranges?

> **go2dell said:**
> I would highly recommend against using RAID 0 on your server...Totally agree.

---

### Post by lykwydchykyn on 2009-07-31
> **garfonzo said:**
> I created a thread about a server's bottleneck over [here ]("http://ubuntuforums.org/showthread.php?t=1221588")and the second reply hinted that Samba *could* pose speed issues if not set up correctly. From that I assumed that one could setup Samba and have it 'work' but not at its optimal. That was my rational for mentioning the speed issue there.

Fair enough, but I wouldn't put much stock in an offhand comment like that.  Some people say "samba" when they mean the smb/cifs protocol.  Both Samba and Windows file sharing implement the smb/cifs protocol.  There are faster PROTOCOLS for sharing data, but I'm not aware that one IMPLEMENTATION is faster than another.  

You know what I'm saying?
> 
With a RAID 5 setup, would the performance increase be worth the effort? If I were to RAID 5 two of my 320 GB drives, and then rsync those two discs to my other two 320 drives, I would have a performance increase and a backup process. Or am I mixing apples and oranges?

RAID is not backup.  It's redundancy in case of hardware failure.    And you need at least 3 disks to do a RAID 5.  Your only RAID option for redundancy with 2 disks is RAID 1 (disk mirroring).

---

### Post by garfonzo on 2009-07-31
@lykwydchykyn

Ya, I know what you're saying. Thanks for the input re the various protocols. I've never ventured into RAID territory, so the idea of setting one up is intriguing, but, as you point out, I'd need another drive. And ya, I knew that RAID is not a backup solution. I really like rsync for backups. 

Thanks for the great info.

---

