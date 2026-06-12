---
title: "access denied by Kubuntu nfs server"
date: 2019-10-16
forum: Server Platforms
---

### Post by jim-anderson on 2019-10-16
My old disk backup server died and I'm installing a new server (on an older 32-but computer). I have installed Kubuntu 16.04 on the server and everything went well. The machine seems to be running fine and I can connect to it over the local network using ssh, ping, etc. The problem is that the machine is to be used as a server and I cannot mount the file system on the machines. When I try to mount, from another PC, using

```
mount -t nfs herman:/home  /mnt/backup
```

I get:

> mount.nfs: access denied by server while mounting herman:/home

For example, if I try to mount from a PC with IP address 192.168.0.250, I get the above message.

In /etc/hosts.allow on 'herman', i.e. the 32-bit server, I have the lines:

```
portmap: 192.168.0.254
lockd: 192.168.0.254
mountd: 192.168.0.254
rquotad: 192.168.0.254
statd: 192.168.0.254
```

and in /etc/exports, I have:

```
/home       192.168.0.250(rw,no_subtree_check)
```

My hosts.deny file is:

```
ALL: PARANOID
```


I have gone through this process many times, but I have never had access denied when my
hosts.allow and exports file are setup correctly. The definitely look correct to me.

Is there some other reason why access might be deinied?

Any suggestions on debugging this?

Thanks!!

Jim A

---

### Post by wildmanne39 on 2019-10-16
*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

### Post by TheFu on 2019-10-16
What do the log files show on the client and the server?

I would disable tcp-wrappers first to see if that is actually the issue.

Also, using file sharing for backups isn't a great idea with malware/crypto-locker out there now.  Using an ssh-based backup tool (there must be 30 of them) in "pull" mode would prevent many of the failures that file sharing allows.

32-bit Ubuntu is going away.  Depending on the storage requires, there are some relatively cheap GigE and SATA3 capable SBCs which would be fine for backup servers in the $50-$70 price points.  These are like raspberry Pi systems, but with much better I/O capabilities.  Much more power efficient, which can matter to many people, but most importantly, 64-bit.

---

### Post by jim-anderson on 2019-10-16
I did some testing with repeated attempts to mount the servers. I checked the /var/log directory and no log files changed there after my various tests. Should I be looking elsewhere for log files? I found that I can turn on nfs logging with the following command:

rpcdebug -m nfsd all

After running a mount 3 times and checking the changes in the syslog file, the difference were:

> < Oct 16 17:54:54 herman kernel: [265013.767797] nfsd_dispatch: vers 4 proc 0
< Oct 16 17:55:08 herman kernel: [265027.783223] NFSD: laundromat service - starting
< Oct 16 17:55:08 herman kernel: [265027.783227] NFSD: laundromat_main - sleeping for 90 seconds
< Oct 16 17:55:40 herman kernel: [265059.832703] nfsd_dispatch: vers 4 proc 0
< Oct 16 17:56:10 herman kernel: [265090.464924] nfsd_dispatch: vers 4 proc 0

> I would disable tcp-wrappers first to see if that is actually the issue.

I am not sure if TC wrappers is being used. I am reading up on TC wrappers. Thus far, the test described in the article that I read does not work for me because the path the nfsd on my host is unknown to me.

> Also, using file sharing for backups isn't a great idea with  malware/crypto-locker out there now.  Using an ssh-based backup tool  (there must be 30 of them) in "pull" mode would prevent many of the  failures that file sharing allows.

32-bit Ubuntu is going away.  Depending on the storage requires, there  are some relatively cheap GigE and SATA3 capable SBCs which would be  fine for backup servers in the $50-$70 price points.  These are like  raspberry Pi systems, but with much better I/O capabilities.  Much more  power efficient, which can matter to many people, but most importantly,  64-bit.         

I appreciate what you are saying. It looks like betrer performance at less cost and more reliable to boot. I'm not a sys admin guy at all and struggle to keep my network going. Thanks for the suggestion.

---

### Post by TheFu on 2019-10-16
I've never heard of "TC wrappers".  Be careful reading old articles, especially when you don't know what you are doing.  If you don't know, stick with articles specific to the exact Ubuntu release you are using.

I have a few log files with NFS stuff on the NFS server. Look for warnings and errors.
```
egrep -i nfs /var/log/*g
```
Do the same on the client, but manually running a mount command in verbose mode is probably easier/better.

hosts.allow/deny **IS** tcp-wrappers, for some tools.  Since around 2000, most network services have had it built-into their config files.  For example, ssh has it built-in using the sshd_config file.  Most of the world has switched to using the kernel firewall instead.  Having multiple layers isn't a bad thing, but having the kernel block access means fewer resources are used than waiting all the way for the daemon to reject a connection.

Have you tried forcing NFSv3?  NFSv4 changes some things that I'm not competent to address.  Both the server and client need the config setting.  To use NFSv4, looks like a Kerberos server is required.  On the nfs client side, the mount option for NFSv3  is vers=3.

---

### Post by jim-anderson on 2019-10-17
I have run

egrep -i nfs /var/log/*g | egrep -v "sleeping|starting|dispatch|unpack" 

and got the following results shown below, but don't know enough about nfs to recognize a problem in the output.

 1 /var/log/auth.log:Oct 13 13:21:00 herman useradd[29572]: new user: name=statd, UID=120, GID=65534, home=/var/lib/nfs, shell=/bin/fals    e
  2 /var/log/boot.log:[^[[0;1;39m INFO ^[[0m] PNFS blkmaping enablement. is not active.^M 
  3 /var/log/boot.log:[^[[0;1;33mDEPEND^[[0m] Dependency failed for pNFS block layout mapping daemon.^M
  4 /var/log/boot.log:         Mounting NFSD configuration filesystem...^M
  5 /var/log/boot.log:[^[[0;32m  OK  ^[[0m] Mounted NFSD configuration filesystem.^M
  6 /var/log/boot.log:         Starting Preprocess NFS configuration...^M
  7 /var/log/boot.log:[^[[0;32m  OK  ^[[0m] Started Preprocess NFS configuration.^M
  8 /var/log/boot.log:[^[[0;32m  OK  ^[[0m] Reached target NFS client services.^M
  9 /var/log/boot.log:         Starting NFSv4 ID-name mapping service...^M
 10 /var/log/boot.log:[^[[0;32m  OK  ^[[0m] Started NFSv4 ID-name mapping service.^M
 11 /var/log/boot.log:         Starting NFS Mount Daemon...^M
 12 /var/log/boot.log:[^[[0;32m  OK  ^[[0m] Started NFS Mount Daemon.^M
 13 /var/log/boot.log:         Starting NFS server and services...^M
 14 /var/log/boot.log:[^[[0;32m  OK  ^[[0m] Started NFS server and services.^M
 15 /var/log/boot.log:         Starting Notify NFS peers of a restart...^M
 16 /var/log/boot.log:         Starting NFS status monitor for NFSv2/3 locking....^M
 17 /var/log/boot.log:[^[[0;32m  OK  ^[[0m] Started Notify NFS peers of a restart.^M
 18 /var/log/boot.log:[^[[0;32m  OK  ^[[0m] Started NFS status monitor for NFSv2/3 locking..^M
 19 /var/log/dpkg.log:2019-10-13 13:20:52 install libnfsidmap2:i386 <none> 0.25-5
 20 /var/log/dpkg.log:2019-10-13 13:20:52 status half-installed libnfsidmap2:i386 0.25-5
 21 /var/log/dpkg.log:2019-10-13 13:20:55 install nfs-common:i386 <none> 1:1.2.8-9ubuntu12.2
 22 /var/log/dpkg.log:2019-10-13 13:20:55 status half-installed nfs-common:i386 1:1.2.8-9ubuntu12.2
 23 /var/log/dpkg.log:2019-10-13 13:20:57 configure libnfsidmap2:i386 0.25-5 <none>
 24 /var/log/dpkg.log:2019-10-13 13:20:57 status half-configured libnfsidmap2:i386 0.25-5
 25 /var/log/dpkg.log:2019-10-13 13:20:57 status installed libnfsidmap2:i386 0.25-5 
 26 /var/log/dpkg.log:2019-10-13 13:20:59 configure nfs-common:i386 1:1.2.8-9ubuntu12.2 <none>
 27 /var/log/dpkg.log:2019-10-13 13:20:59 status half-configured nfs-common:i386 1:1.2.8-9ubuntu12.2
 28 /var/log/dpkg.log:2019-10-13 13:21:01 status installed nfs-common:i386 1:1.2.8-9ubuntu12.2
 29 /var/log/dpkg.log:2019-10-13 14:06:42 install nfs-kernel-server:i386 <none> 1:1.2.8-9ubuntu12.2
 30 /var/log/dpkg.log:2019-10-13 14:06:42 status half-installed nfs-kernel-server:i386 1:1.2.8-9ubuntu12.2
 31 /var/log/dpkg.log:2019-10-13 14:06:43 configure nfs-kernel-server:i386 1:1.2.8-9ubuntu12.2 <none>
 32 /var/log/dpkg.log:2019-10-13 14:06:44 status half-configured nfs-kernel-server:i386 1:1.2.8-9ubuntu12.2
 33 /var/log/dpkg.log:2019-10-13 14:07:10 status installed nfs-kernel-server:i386 1:1.2.8-9ubuntu12.2
 34 /var/log/kern.log:Oct 13 12:47:53 herman kernel: [ 5478.129508] RPC: Registered tcp NFSv4.1 backchannel transport module.
 35 /var/log/kern.log:Oct 13 12:47:53 herman kernel: [ 5478.143140] FS-Cache: Netfs 'nfs' registered for caching
 36 /var/log/kern.log:Oct 13 13:21:04 herman kernel: [ 7469.794980] NFS: Registering the id_resolver key type37 /var/log/kern.log:Oct 13 14:06:44 herman kernel: [10209.379786] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
 38 /var/log/kern.log:Oct 13 14:06:44 herman kernel: [10209.401994] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery direc    tory
 39 /var/log/kern.log:Oct 13 16:18:05 herman kernel: [    4.165750] RPC: Registered tcp NFSv4.1 backchannel transport module.
 40 /var/log/kern.log:Oct 13 16:18:05 herman kernel: [    4.340472] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
 41 /var/log/kern.log:Oct 13 16:18:07 herman kernel: [   11.753588] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery direc    tory
 42 /var/log/kern.log:Oct 13 16:18:08 herman kernel: [   12.995402] FS-Cache: Netfs 'nfs' registered for caching
 43 /var/log/kern.log:Oct 13 16:18:08 herman kernel: [   13.050795] NFS: Registering the id_resolver key type

---

### Post by jim-anderson on 2019-10-17
> there  are some relatively cheap GigE and SATA3 capable SBCs which would  be  fine for backup servers in the $50-$70 price points.  These are  like  raspberry Pi systems, but with much better I/O capabilities.  Much  more  power efficient, which can matter to many people, but most  importantly,  64-bit. 			 		

I am not familiar with the acronym "SBC", but after some searching, I believer "Server Base Computer" is the meaning and a concept which I am familiar with in concept. To me that could mean either software or hardware base servers, but in this case I infer that you are saying there are cheap hardware based solutions that will provide what I need that are cheaper and better than my file sharing solution. Going further, I infer that there are GigE (I found a company webpage for GigE) and SATA3 (I could not find a SATA3 brand or company) units in the $50 to $70 range. I assume these units are stand alone units with eithenet ports. I don't know if this a good assumption since I have not found units like this yet. At first glance, it looks like GigE makes circuit boards, but not standalone units.

BTW, I ran across an article on why object storage solutions are much better than file sharing solutions and I convinced I can do much better than what I am currently doing. I will continue to look for a standalone storage unit with an eithernet port. If I not headed in the right direction, please feel free to interject more.

Jim

---

### Post by TheFu on 2019-10-17
SBC - single board computer. A raspberry pi is an SBC, but there are 20 other vendors making small computers, SBCs, of similar size, but very different capabilities.  A r-pi is the low-end choice.

GigE - 1000 base-TX - gigabit ethernet

SATA3 - a SATA protocol that supports 6 Gigabit transfers.  Basically the fastest SATA connection today and commonly available the last 10 yrs.

Sorry. I'd assumed these were commonly known terms.

I don't know where in the world you are, but AmeriDroid sells lots of SBCs. ROCK64 and Odroid models would be on my initial list to check into.  Amazon often sells the more popular variants.  Really, I'm just trying to solve the old-computer, non-64bit problem. There are many different ways to solve that.  

I do not use SBCs for NFS servers. For my needs, they don't have enough storage capacity, but for other people with minimal storage needs, say 2 HDDs, an SBC might be a reasonable solution.  My main NFS machine with 20+TB connected is using a Pentium G3258 and runs lots and lots of other things on it - calibre, plex server, nextcloud, are just a few things it runs.

Please re-read my post above. There are more suggestions to try.

---

### Post by SeijiSensei on 2019-10-17
What if you try mounting as root with sudo?  Ordinary users cannot mount anything under /mnt.

---

### Post by TheFu on 2019-10-17
> **SeijiSensei said:**
> What if you try mounting as root with sudo?  Ordinary users cannot mount anything under /mnt.

Excellent point.  This is part of the reason why we ask to see the FULL COMMAND and output in the same copy/paste block.  Being obtuse makes trivial answers hard to provide.

"object storage" probably isn't what you think it is.  Stick with a file system.

---

### Post by jim-anderson on 2019-10-29
@ 			 				 					[ 						 							[IMG]https://ubuntuforums.org/customavatars/avatar698195_5.gif[/IMG] 						 					]("https://ubuntuforums.org/member.php?u=698195") 				 				 					 						 	[URL="https://ubuntuforums.org/member.php?u=698195"][B][COLOR=#000000]SeijiSensei

I have been trying to mount with root privilege, but no luck with that
[/COLOR][/B][/URL]

---

### Post by jim-anderson on 2019-10-29
@TheFU

I tried:

> sudo mount -t nfs -o vers=3 IPAddr:/mnt/backup /mnt/backup

and I get the error message:

> mount.nfs: Connection timed out

note that I then pinged the server to verify that I do have a connect with the server and the result was positive, i.e. the connection is good.

---

### Post by SeijiSensei on 2019-10-29
Try adding "-v" to the options to mount to get more debugging information.

What do you see in /var/log/syslog on the server side?

Are you sure you need to use "-o vers=3"?  The version should be auto-negotiated.

---

### Post by TheFu on 2019-10-29
Did you ever disable tcp-wrappers?

---

### Post by jim-anderson on 2019-10-29
@ TheFU

> "object storage" probably isn't what you think it is.  Stick with a file system.

From what I have read about "object storage", it is an excellent idea and I would like to move toward it. I have many large compressed files that I store for backup and which I hopefully will never have to use. It does make sense to use object storage then, I think. Do you agree?

---

### Post by TheFu on 2019-10-29
No. Stay with a file system.

---

