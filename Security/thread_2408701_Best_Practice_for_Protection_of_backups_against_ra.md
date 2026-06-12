---
title: "Best Practice for Protection of backups against ransomware 2019 ????"
date: 2018-12-21
forum: Security
---

### Post by dazz100 on 2018-12-21
Hi

I have been researching strategies for backup protected from ransomware. There is lots of stuff out there but I haven't found a young solution. I haven't found a single solution that implements what I think I need. I have seen "solutions" that don't offer protection from ransomware. eg. store backups in the cloud. I understand that modern ransomware is targeting the backup system. I think the solution should be multi-layered to make it easier to detect ransomware affected data and more difficult for the ransomware to penetrate the backup system.

The key thing I have not seen in any proposed solution is testing. How can anyone know that any specific strategy works unless it is tested against the current known ransomware. That raises the question of obtaining ransomware for legitimate testing purposes, and how that testing might be done. Below is a multi-faceted strategy that I think will provide protection against ransomware. I am not saying it is impregnable but it should be robust. This strategy focuses on isolating the actual backup HDs from the network, and preventing ransomware infecting the backup machine.

I propose the following protections:
[LIST]

[*]    Use a separate backup machine with a secure Linux OS loaded from a CD/DVD ROM into RAM. Use BIOS settings to periodically reboot to clear any possible infection. Actually shutting down the backup machine when it is not required effectively creates an air-gap that no software can penetrate.

[*]    Use an intermediate Backup HD exposed to the network that reads data from  client machines on the network (rather than being written to). This won't stop data being encrypted on the client machines but using an intermediate HD as a DMZ provides another hurdle for the ransomware.

[*]    Make the actual backup HDs invisible to the network.

[*]    Periodically make a master backup on a USB connected HD as the  restore option of last resort. Making a known good backup, stored off-site eliminates the possibility of total data loss.

[*]    Use pattern analysis to detect encrypted files on the DMZ HD. A exceptions white list would be required to backup normal encrypted files.

[*]    Use intrusion detection to sense if ransomware is trying to find and write to the network exposed DMZ HD.

[*]    Replace common destructive commands with aliases  to add time delays and alerts (emails?) to potentially destructive commands on the backup machines.

[*]    Don't allow remote admin logins to the backup machine. Only local on the machine.

[*]    Make all files on the backup HDs (including the DMZ HD) RW but not X
[/LIST]


All of the above are just ideas. They are not my ideas and maybe they are the wrong ideas. In saying that, I haven't found/seen discussion on a multi-layered defense using a collection of techniques specifically designed to protect the backup behind a DMZ HD.  Is this a good idea?  Is this something that could be added to an existing open source solution like FreeNAS?? Is it already a feature??

So the question is, what is considered current best practice to detect and protect backup data from a ransomware attack in 2019?

---

### Post by 1clue on 2018-12-21
You have the main points I think. While I don't have a good solution for early detection of ransomware, I have a good backup strategy, and my work is stored in git, meaning that it's stored off-site, and it's easy to detect when encryption happens and roll back to the point right before that. Or providing the on-workstation copy is trashed by the encryption, I can always roll back to the off-site copy. If git files are completely encrypted by ransomware you won't be able to commit, so that part is OK.

The key characteristics of backups with respect to malware are, in my opinion:
[LIST=1]
[*](reasonably) automated.
[*]Off-line
[*]Off-site
[*]Time-stamped (not rolling) so that you have N backups, each of which is a copy of your data as of a certain date.
[*]Plan is frequently reviewed for comprehensiveness and coverage of current important data.
[*]Backups are tested for viability of data.
[*]I don't use incremental backups at all.
[/LIST]

My strategy saves stored data exactly as it exists on the production system, so some of your steps don't work for me. My data is stored without compression or encoding of any sort, it's a direct copy (cp -rax) from the live data to the intermediate system backup directory, except for databases and such which get a normal database backup and then those backups are copied. From there it's a network transfer to the backup system. In my experience the most critical time in the entire cycle is right after you know you have a problem, you need to find the latest good backup and get that data back to a fresh system as soon as possible. So my backups are on a SATA drive, there's a stack of drives which are rolled out to another site on a schedule so no two consecutive backups are on the same device or the same storage site.

I've been backing up computers for home and work since the 80s. I've spent a ton of money on floppies, tape drives of various sorts, CD burners, commercial apps and so on. My watershed moment was when I had a drive failure and found out that none of my backups could be restored. I now distrust all commercial backup software and all commercial backup devices. I use the same media that my computers use. I have since had drive failures and data corruption and even malware, and found my approach works pretty well. My backups are not completely automated, they still require that I mount a device and start a script. I manually verify that the script made a good copy and that the critical data is readable.

Hackers may get a copy of my data and they may encrypt my system, but they won't trash it and make me lose more than a couple days of data.

---

### Post by dazz100 on 2018-12-21
Hi

I like the git idea, especially if it is stored on-line.  That should be out of reach of any ransomware.

I think it would be really useful to be able to quickly detect a ransomware infection.
One way would be to look at the files to be backed up. Either the number count or an encrypted signature.  Not so easy to do.  See here:  [https://security.stackexchange.com/questions/122497/methods-for-determining-if-a-file-is-encypted]("https://security.stackexchange.com/questions/122497/methods-for-determining-if-a-file-is-encypted")

---

### Post by 1clue on 2018-12-22
Just because it's stored online doesn't make it automatically out of reach of ransomware.

Git has information about the repository stored in the data directory. If the data are encrypted then the git command can't make sense out of it, meaning that the encryption process makes the entire repository useless to you until you pay the ransom, assuming that the attackers will actually unlock the drive for you when you're done. Historically speaking that's a pretty big assumption.

The nature of git is such that any other computer with the same repository checked out is a complete repository, meaning that if your git server (github for example) gets attacked then as long as you have an up-to-date copy on any system anywhere, you have lost nothing important.

That's not to say that someone couldn't write malware to look for git repositories and attack them specifically.

---

### Post by dazz100 on 2018-12-27
Hi
I am looking at using Open Vault Media set up to pull diff backups.  
I think typical ransomware will aim to encrypt the target files quickly.  That should result in a large number of diff backups.  If these files are also encrypted, that would be a red flag.  This points to profiling diffs to look for ransomware signature behaviour.

I need to figure out how to respond to ransomware alarm to suspend backups.  I haven't looked at the OPV user manual so need to start there.

I have anti-virus software running as a first line of defense.  A dedicated backup server running some sort of profiling to detect 

As a second line of defense, I need to harden the backup server.  Pulling files is part of that, as is choosing a dedicated backup dist.  If I also disable any web/remote login of the backup server, this should make it more difficult to break into the backup server.  As above, I need to start by reading the manual.

I will look at using a Raspberry Pi back server with HDs connected via USB.  They are cheap and low powered.  I only have a couple of PCs on the network so a high performance backup server is not required.

---

### Post by TheFu on 2019-01-08
There are as many solutions to this as there are computers and admins.  We all have different skills and different backgrounds and learned different lessons due to prior successes and failures.

* raspberry pi systems have poor network and disk I/O capabilities.  Consider getting something with better I/O capabilities.  An old PC is fine, but if you insist on something new, look for real GigE networking (900+ Mbps) and at least USB3 connections.  Other SBCs can do this like a Pine64+ or Rock64Pro or Odroid-xu4.  I don't own any of these other options.  A Pi v3 cannot.  A $30 intel/AMD CPU + $40 MB + $25 in RAM will blow away all these SBCs.  Look up an APU2 if you want something tiny, low-power (watts), yet very capable - around $150 all in. I own one of these, but use it as a router, not for storage.  There are larger devices for less month, since there is a premium on tiny in the amd64 CPU world.  The encryption capabilities in 64-bit x86 systems is much better than other CPU types. [https://www.jeffgeerling.com/blog/2018/raspberry-pi-3-b-review-and-performance-comparison](https://www.jeffgeerling.com/blog/2018/raspberry-pi-3-b-review-and-performance-comparison)  
* Have a separate backup network. The backup network cannot be accessed from the public network.
* never allow passwords for any network connections. Key-based authentication only.
* "Pull" backups from the clients to the backup server. Use a client/server backup tool like duplicity or rdiff-back. Something that uses ssh to encrypt the network traffic and supports key-based authentication from a specific subnet/IP.  You can make the remote connection only be able to run the backup tool and nothing else. This is part of ssh.
* Have versioned backups. That will provide a way to know if a system has been crypto-locked because the backup will suddenly become huge and take a long time. Depending on the risks for each system, between 60 days and 180 days of versioned backups are retained.
* Storage for the backups should be encrypted.  I use dm-crypt + LUKs.
* Replicate the 1st backup off-sight using rsync over ssh.  Lock the ssh/rsync connection down to just the IPs that should have access.
* In no way, no how, would I place these backups on a computer I didn't own.

I use rdiff-backup and for most of my systems, the daily backups take just 2-4 minutes.  A full backup would require 30-90 minutes.
The last month, I've been consolidating from 20 systems down.  I'm down to 10 systems now with 2 remaining to be retired.

I'm a fan of git for many purposes, like having version controls on /etc/ files.  We use ansible, so our configurations for all systems ARE stored in git (a repo we manage, hold, maintain, and backup).  I don't see how git could be efficient enough to backup large data files or files that constantly change. Git shines for text files, but those aren't typically what our servers hold.

---

### Post by 1clue on 2019-01-08
> **dazz100 said:**
> ...
I will look at using a Raspberry Pi back server with HDs connected via USB.  They are cheap and low powered.  I only have a couple of PCs on the network so a high performance backup server is not required.

If you intend to just prototype your backup server then a pi can do the job. However:

Raspberry pi is insanely slow for any sort of file server or backup task. They have a maximum total bandwidth through the USB controller chip, which includes all networking and all disk storage. So, combined bandwidth is usually 100mbps or less. Moreover, it's CPU-intensive as the chips included don't do much of the work themselves like a better quality nic or sata system would do. When they benchmark networking on a pi, they're usually showing you pure network speed, where the only thing the device is doing is pushing bytes through a network interface. No disk activity, no calculation or encryption. Because any extra activity at all slows down the networking speed. Same for disk speed and whatever else.

To contrast, most wireless networks these days are well past 100mbps and gigabit local networking is common. I use a cable modem and have the minimum contract for Internet speed, and my raspberry pi can't accept or send a file even half as fast as I can get it from the Internet on a regular computer. Any decent file server in an office will be at least one gigabit ethernet card, and the file server will likely be able to get close to wire speed. ***Edit: **Close to wire speed for the network, with simultaneous disk access and processing for whatever apps are running too.*

You may not care much about the speed of the backup, until such time as you actually have to wait for it to finish. My pi is pegged at less than 1/20th of what I consider an acceptable file server transfer rate. Not an exaggeration. 

The raspberry pi is a fantastic device, but only if you're using it for what it was made for: A hobby board. It is an abysmal file server and an equally abysmal router, for exactly the same reason. Nothing on that system was optimized for throughput. They picked some really cheap chips and wired them together so they work, and so an amateur with a soldering iron can invent and still have a decent chance that the board still works. That's the Raspberry Pi's superpower.

There are lots of boards out there specifically designed for file servers, routers and backup devices. Some of them are not too expensive and give you WAY more bang for the buck than a pi can.

---

### Post by 1clue on 2019-01-08
If you're looking at a network appliance for your file server (meaning you are exploring my advice and TheFu's) then there are some things that may help:

Avoid boards with a cheap NIC. The difference in cost between a cheap NIC and a good NIC (in the gigabit range) is really pretty small. If they're using a crappy NIC that means the entire board is likely crappy.

 RealTek is the modern ethernet equivalent of a WinModem. I'm using them as an example because I have a system with 5 of them on it. They have barely enough hardware to do the job, and everything else is in the driver software. They generate a lot more interrupts than a good NIC and they rely on the CPU for throughput.

I have an i7 with 5x RealTek NICs (which I mentioned above) and an 8-core atom with 7x built-in Intel NICs. The atom is faster at networking than the i7. The i7 has a 600w power supply and tends to run with the supply pretty hot. The atom has a 100w supply and according to the monitoring built-in it uses about 30w when running normally, maybe 40w when going flat out. The atom board was built specifically as a network appliance in a server room.

A good NIC handles almost all the networking stack right on the board, and your CPU simply tells it where to go and how high to jump, and the NIC lets the CPU know when it's done or the buffer's full.

My favorite NIC in the gigabit range is an Intel, one that uses the 'igb' Linux driver. It has really good Linux support and lets your CPU work on things that need to be done.

SATA controllers are similar.  A good one will do most of the work itself and leave the CPU alone until it's done.

Another thing: ECC memory. This might be a bit out of your range but if you have real server hardware (some of which is not expensive) then you can get ECC memory on it. If you're building a device which will be on all the time, and you want to just turn it on and forget it, then ECC memory is important. If your home router freaks out once a month or so, that's likely because of a memory error and your router doesn't have ECC memory. A file server/backup device won't need much of it so it will only be a few dollars difference.

So for a file server:
[LIST=1]
[*]Look for a good gigabit NIC built-in.
[*]Look for a good SATA controller built-in.
[*]ECC memory.
[*]If you have a mini-pcie slot then you can add stuff later.
[/LIST]

You might look for a 2-core Atom c3000 board. c3000 is a group of Intel Atom chips designed specifically for small communications servers. Routers and file servers, for example. Various boards will have a different complement of devices. [https://ark.intel.com/products/series/97941/Intel-Atom-Processor-C-Series](https://ark.intel.com/products/series/97941/Intel-Atom-Processor-C-Series)

My atom is a c2000 series, which is older. The c3000 has better virtualization support and allows you to donate a NIC to a specific VM for example. That's likely more features than you want, but if you were thinking of several small systems on your network you could easily combine the hardware and make a mini KVM/QEMU server.

---

### Post by dazz100 on 2019-01-09
Hi
All looks like good advice to me.  I hadn't considered the Atom, mainly because I didn't know about it.  
I am away from home until Feb so I will start looking at an Atom based solution then.

Thanks for your time/effort.

---

### Post by 1clue on 2019-01-09
Food for thought then: The Intel Atom uses x86_64 instruction set, so a normal Linux distribution will work. Atom is significantly faster than arm processors. It was designed for tablets and "lightweight" laptops or even home systems.

The mainstream atom is pretty slow, but still faster than arm. They tend to have 2 cores. But Intel has made several variants for different purposes, and has done much work to reduce the power requirements in a server room or network panel. There are now high performance Atoms able to handle multiple 10 GBPS NICs, they have 16 cores and real SATA ports.

When I was looking for a router box I started thinking about a pi, and then based on advice from others I soon saw the error of that line of thought. I was looking for an alternative to a SOHO wireless router. People pointed out netgate devices and many others (none of which would do very well for a backup storage device so I won't link them) and I started looking around there, and finally started looking at the c2000 Atom chips. c3000 was not available yet.

I have used SuperMicro products at work, so when I saw what they had for C2000 systems I really didn't look anywhere else. I was a huge SuperMicro fan before I started shopping for my router hardware. I also spent significantly more than you're likely to want to spend, but what I got is pretty sweet. My board is focused on networking but there are other c2000 and c3000 chips which would be perfect for NAS or backup. Some of them have as many as 12 SATA ports, including sata3. Mine has 4 sata2 and 2 sata3 ports.

If I were looking for something like what you're describing, I would aim for an 8-16 core c3000 system with 2 or more gigabit NICs and heavy on the SATA ports. I would put it into a box with lots of room for hard drives, and one removable sata3 housing. I have one on the system I use for backups, you can insert a 3.5" SATA drive as though it were a tape cartridge.

Backups which stay attached to a computer are not backups. Backups are a record of what your system looked like at a certain point in time, as far as data goes. You should have several backups. I use 4 sets. Each time I use the next disk in the series and, if necessary, I delete the oldest backup from the disk I'm using in order to make room.

I also have a long-term backup (first of the month) that doesn't get deleted. When the drive fills up I put that one in a fire safe and stick in a new drive.

---

### Post by 1clue on 2019-01-09
Before you freak out about the price of an 8-16 core c3000 system, this system would also be able to be a VM host, allowing not just a very good file server but also a number of other  things as well, whatever you need for a home or small office. The C3000 series can use 256 GB RAM if you go with ecc memory, and your board supports it.

The Atom is a system-on-a-chip the same as ARM. So not only is there a processor, there is some other devices like the network interface or sata stuff. Mine has encryption and compression hardware acceleration, tagged as QuickAssist or QAT.

The arguments I'm making for all this are:
[LIST=1]
[*]In order to make a decent backup system or NAS device, you need to buy a power supply, a case, drives, etc. Probably you need the same class of all that that you would use here.
[*]Virtualization utilizes the same hardware to implement several servers.
[*]A home or small office usually makes heavy use of one thing at a time, surrounded by long idle times for whatever service you're using.
[*]Virtualization allows you to have better performance for all your services because when you're heavily using your backup, for example, you are likely not heavily using some other service you might want.
[*]The c3000 series allowing more complete isolation of hardware devices for a specific VM would let you safely have, for example, a really good firewall/router as one of your VMs, and maybe IDS/IPS (intrusion detection/prevention systems) or a VPN.
[*]A backup system is architecturally almost the same as a NAS. You could make your device and implement a NAS with a removable cartridge like I said, then keep interesting data on that system, as well as an online copy of your most recent backup, and still take the real backup to a different location to provide protection from theft or fire or ransomware or whatever else.
[*]IMO an 8-core atom could do all that stuff very nicely. But it will cost you more than you had intended.
[/LIST]

---

### Post by pending... on 2019-01-11
If I had something of this kind to manage, I'd probably work also on processes check. Unless a ransomware were able to get root, it would run from userland. At least, That's what I read about the discovered ones. A routine in bash script that checks any process running from userland (ps x | grep -v grep | grep -E '/home/|/var/tmp/|/tmp/|/dev/shm/') and kills it as soon as it's detected (and even checks and remove its contrab entry, etc.) before popping-up a warning could add a small layer of security, I think.

---

### Post by TheFu on 2019-01-11
This is why system monitoring is important.  Lots of different methods for that from logwatch, IDS/IPS, alarming and performance data capture.  

But it all starts with versioned backups.

---

