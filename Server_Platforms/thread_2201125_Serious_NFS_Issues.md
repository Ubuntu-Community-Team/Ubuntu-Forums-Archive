---
title: "Serious NFS Issues"
date: 2014-01-22
forum: Server Platforms
---

### Post by jlacroix on 2014-01-22
I decided to switch my environment to NFS, since I'm all-Linux, and decided it would be better than using Samba for everything. Unfortunately, the results have been catastrophic. Before I get started, the server is running a fully up to date (as of last weekend) installation of Server 12.04 LTS.

The major issue that I'm facing is that sometimes umounting NFS on my client computer will completely lock up the server to the point where it's so busy that you can't execute *any* command. No TTY's respond to login requests, so I cannot log in to the server when this occurs, nor can I ssh or enter any command that would shut it down safely. My only recourse is to hold the power button down. Since this is RAID/LVM, I'm especially not a fan of doing this.

The error on the screen repeatedly is this (it shows these errors right after the login prompt):
```
INFO: task nfsd:2499 blocked for more than 120 seconds.
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
INFO: task kworker/u:2:3999 blocked for more than 120 seconds.
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
```

The minor issue that I'm facing is that the user and group shows up as 4294967294 when I mount an NFS share (when it does work). I Googled like crazy and virtually every site I find tells me to edit /etc/idmapd.conf and put in the domain name on each machine. I've done this. It does NOT help. I already checked that the uid and gid is the same on each machine, including the server.

I'm using no_subtree_check, rw, and async options. (I'm trying hard to get the server to shut down right now, so I can post the exact /etc/exports later if needbe).

I am mounting the shares with this command:
```
sudo mount -t nfs4 -o rw pluto:/share/Archive /mnt/Pluto/Archive
```

---

### Post by tgalati4 on 2014-01-23
For the second issue, make sure you have /etc/hosts defined on each machine that needs NFS access.  For the first issue, my guess is that there are pending reads or writes that are preventing the NFS daemon from unmounting the share.  It could be as simple as a terminal window that has landed on a share directory or a Nautilus window with a share directory open.  These use cases are probably better handled by SAMBA.  

NFS is an old framework that is optimized for continuous mounts between clients and servers.  SAMBA is better-suited for spontaneous user mounts and dismounts.

---

### Post by jlacroix on 2014-01-23
> **tgalati4 said:**
> For the second issue, make sure you have /etc/hosts defined on each machine that needs NFS access.  For the first issue, my guess is that there are pending reads or writes that are preventing the NFS daemon from unmounting the share.  It could be as simple as a terminal window that has landed on a share directory or a Nautilus windows with a share directory open.  These use cases are probably better handled by SAMBA.  

NFS is an old framework that is optimized for continuous mounts between clients and servers.  SAMBA is better-suited for spontaneous user mounts and dismounts.
In my case, the server itself wouldn't have problems writing if it's the client that's doing all the writing, would it?

My understanding of Samba (and the reasons I moved away from it) is that NFS is better for an all-Linux environment, and that NFS handles UNIX permissions better than Samba. In my case, I was losing permissions when copying files.

Personally I don't see why NFS wouldn't be a viable choice. When I want to connect to a share, I mount it. When I'm done, I unmount. That doesn't seem to be a use-case that NFS wouldn't be able to handle, especially considering that's exactly what it was designed to do. The only reason I can think of is a problem in my configuration. 

I'm curious what you mean by /etc/hosts though, I have a DNS server (bind) that handles this for me, unless there's something that's also required in /etc/hosts.

Now that my server is up, I can post my /etc/exports:
```
/share/Archive 10.10.96.0/255.255.252.0(rw,sync,no_subtree_check) 10.10.97.0/255.255.252.0(rw,sync,no_subtree_check)
/share/Backup 10.10.96.0/255.255.252.0(rw,sync,no_subtree_check) 10.10.97.0/255.255.252.0(rw,sync,no_subtree_check)
/share/Downloads 10.10.96.0/255.255.252.0(rw,sync,no_subtree_check) 10.10.97.0/255.255.252.0(rw,sync,no_subtree_check)
/share/Private 10.10.96.0/255.255.252.0(rw,sync,no_subtree_check) 10.10.97.0/255.255.252.0(rw,sync,no_subtree_check)
/share/Public 10.10.96.0/255.255.252.0(rw,sync,no_subtree_check) 10.10.97.0/255.255.252.0(rw,sync,no_subtree_check)
/share/Videos 10.10.96.0/255.255.252.0(rw,sync,no_subtree_check) 10.10.97.0/255.255.252.0(rw,sync,no_subtree_check)
```

Thanks for the reply!

---

### Post by bab1 on 2014-01-23
> **jlacroix said:**
> In my case, the server itself wouldn't have problems writing if it's the client that's doing all the writing, would it?

My understanding of Samba (and the reasons I moved away from it) is that NFS is better for an all-Linux environment, and that NFS handles UNIX permissions better than Samba. In my case, I was losing permissions when copying files.

Personally I don't see why NFS wouldn't be a viable choice. When I want to connect to a share, I mount it. When I'm done, I unmount. That doesn't seem to be a use-case that NFS wouldn't be able to handle, especially considering that's exactly what it was designed to do. The only reason I can think of is a problem in my configuration. 

I'm curious what you mean by /etc/hosts though, I have a DNS server (bind) that handles this for me, unless there's something that's also required in /etc/hosts.

Now that my server is up, I can post my /etc/exports:
```
/share/Archive 10.10.96.0/255.255.252.0(rw,sync,no_subtree_check) 10.10.97.0/255.255.252.0(rw,sync,no_subtree_check)
/share/Backup 10.10.96.0/255.255.252.0(rw,sync,no_subtree_check) 10.10.97.0/255.255.252.0(rw,sync,no_subtree_check)
/share/Downloads 10.10.96.0/255.255.252.0(rw,sync,no_subtree_check) 10.10.97.0/255.255.252.0(rw,sync,no_subtree_check)
/share/Private 10.10.96.0/255.255.252.0(rw,sync,no_subtree_check) 10.10.97.0/255.255.252.0(rw,sync,no_subtree_check)
/share/Public 10.10.96.0/255.255.252.0(rw,sync,no_subtree_check) 10.10.97.0/255.255.252.0(rw,sync,no_subtree_check)
/share/Videos 10.10.96.0/255.255.252.0(rw,sync,no_subtree_check) 10.10.97.0/255.255.252.0(rw,sync,no_subtree_check)
```

Thanks for the reply!
Try changing the sync to async in the export lines.

---

### Post by jlacroix on 2014-01-23
> **bab1 said:**
> Try changing the sync to async in the export lines.
I thought about that, but isn't that considered dangerous?

---

### Post by tgalati4 on 2014-01-23
Using proper /etc/hosts on your clients and server can help solve some mysterious problems with older frameworks like NFS.  async is only problematic if you dismount a share at random times.  SAMBA gives a pop-up that lets you know if a share is locked or has pending writes.  Not sure if NFS does.  

NFS is a viable choice if you work in a laboratory and you have a desktop workstation that is crunching data and a server that is used for backup and sharing with other linux/unix computers in a lab.  These mounts are continuous and typically established once and kept permanent.  [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

So although you insist that NFS is supposed to handle your use case, it is an older framework designed for permanent mounts.  There is [autofs]("https://help.ubuntu.com/community/AutomaticallyMountNFSSharesWithoutAutofsHowto") that will get NFS to act more like SAMBA with spontaneous mounts, but I don't have experience with it.  Others will have to weigh in.

---

### Post by jlacroix on 2014-01-23
> **tgalati4 said:**
> Using proper /etc/hosts on your clients and server can help solve some mysterious problems with older frameworks like NFS.  async is only problematic if you dismount a share at random times.  SAMBA gives a pop-up that lets you know if a share is locked or has pending writes.  Not sure if NFS does.  

NFS is a viable choice if you work in a laboratory and you have a desktop workstation that is crunching data and a server that is used for backup and sharing with other linux/unix computers in a lab.  These mounts are continuous and typically established once and kept permanent.  [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

So although you insist that NFS is supposed to handle your use case, it is an older framework designed for permanent mounts.  There is [autofs]("https://help.ubuntu.com/community/AutomaticallyMountNFSSharesWithoutAutofsHowto") that will get NFS to act more like SAMBA with spontaneous mounts, but I don't have experience with it.  Others will have to weigh in.
I'll have to respectfully disagree wit you on this. At my job we have 50 Linux servers and 80-ish Linux desktop computers, and everyone mounts/unmounts NFS shares and has never seen an issue before. I, however, am having issues on my home server, so based on this I can only imagine it's something specific to me. Further, last I checked, Samba doesn't handle UNIX permissions well, therefore I can only see it viable for mixed-environments. NFS may be old, but I don't see a better option.

Now, politics aside, is there any recommendations for me to troubleshoot what in my configuration might be causing the issue? I've been Googling for hours and have come up empty. I'll try async to see if that helps, but the only other thing I can think of is a kernel bug with my chipset (Intel Atom).

---

### Post by bab1 on 2014-01-23
> **jlacroix said:**
> I thought about that, but isn't that considered dangerous?

I try and overlook all the BS that's out there.  The sync option is really safe but takes a lot of resources as it constantly syncs the buffers to the disks.  When you dismount the drive as is done in shut down it can take some time.  I believe async is the default on NFSv3.  The risk is when the system is ungracefully shut down (power outage or ...).  What file system format are you using?  EXT4 or ...

I use NFSv4 with async now.  I tried sync and had problems with my home servers.  I don't have a gazillion $$$ to spend on RAM and CPU to cover the overhead for my hobby machines.  I do BACKUP however, so I don't see the risk.  I've had no problems on 3 machines for the last 2 years.

It's really a test anyway.  Try it and see what happens.  Then you can make a decision.  Read the man pages for info on sync vs async.

---

### Post by jlacroix on 2014-01-24
> **bab1 said:**
> I try and overlook all the BS that's out there.  The sync option is really safe but takes a lot of resources as it constantly syncs the buffers to the disks.  When you dismount the drive as is done in shut down it can take some time.  I believe async is the default on NFSv3.  The risk is when the system is ungracefully shut down (power outage or ...).  What file system format are you using?  EXT4 or ...

I use NFSv4 with async now.  I tried sync and had problems with my home servers.  I don't have a gazillion $$$ to spend on RAM and CPU to cover the overhead for my hobby machines.  I do BACKUP however, so I don't see the risk.  I've had no problems on 3 machines for the last 2 years.

It's really a test anyway.  Try it and see what happens.  Then you can make a decision.  Read the man pages for info on sync vs async.
I had a really busy night and wasn't able to test it much, but I did test it with the async option just once and it did work (mount and unmount) so that's a start at least. I'll test further this weekend.

I know for sure I'm still having the problem where the mounted folders show as 4294967294 in Thunar, despite the uid and gid matching on both my laptop and server. Perhaps this is normal - though I thought that if the uid/gid matched it would show the right username.

I'll test further and see what happens.

Thanks!

---

### Post by bab1 on 2014-01-24
> **jlacroix said:**
> I had a really busy night and wasn't able to test it much, but I did test it with the async option just once and it did work (mount and unmount) so that's a start at least. I'll test further this weekend.

I know for sure I'm still having the problem where the mounted folders show as 4294967294 in Thunar, despite the uid and gid matching on both my laptop and server. Perhaps this is normal - though I thought that if the uid/gid matched it would show the right username.

I'll test further and see what happens.

Thanks!
I'll bet you have more than one problem.  Deal with the sync/async issue first and then we can look into the other issues.

---

### Post by SeijiSensei on 2014-01-24
I don't see "no_root_squash" among the options in the definitions in /etc/exports.  If you try and mount a share as root without no_root_squash enabled on the server, it will not use root's UID 0 but the "nobody" UID.  From "man /etc/exports":
> Very often, it is not desirable that the root  user  on  a  client  machine  is  also treated  as  root  when accessing files on the NFS server. To this end, uid 0 is normally mapped to a different id: the so-called anonymous or nobody uid. This mode of operation (called  &#8216;root  squashing&#8217;)  is  the  default,  and can be turned off with no_root_squash.

Since the anonymous user has, at best, only read permissions to mounted filesystems, you'll have problems with writing files to the mounted share.  So just change /etc/exports to include "no_root_squash" among the options for any share you'll want to mount as root on the client.

---

### Post by jlacroix on 2014-01-25
> **SeijiSensei said:**
> I don't see "no_root_squash" among the options in the definitions in /etc/exports.  If you try and mount a share as root without no_root_squash enabled on the server, it will not use root's UID 0 but the "nobody" UID.  From "man /etc/exports":


Since the anonymous user has, at best, only read permissions to mounted filesystems, you'll have problems with writing files to the mounted share.  So just change /etc/exports to include "no_root_squash" among the options for any share you'll want to mount as root on the client.
Thanks, I'll try that next. I just had it lock up again today. This time, it happened when I tried to use Clonezilla to save a hard disk image over NFS.

---

### Post by bab1 on 2014-01-25
> **jlacroix said:**
> ...I just had it lock up again today. This time, it happened when I tried to use Clonezilla to save a hard disk image over NFS.
Did you try the async option on the /etc/exports listings?  I have a setup just like you (i.e 12.04 and NSFv4).  Reading from my install notes I also see this:
> 
If directories and files on the client are owned by uid/gid 4294967294:4294967294) then you need to set in /etc/default/nfs-common:

NEED_IDMAPD=yes

The above is from [here]("https://help.ubuntu.com/community/NFSv4Howto") and although it states that it applies to "Ubuntu 11.10 or earlier" I have found that Ubuntu 12.04 also needs this fix.  I have used this setting on my Ubuntu 12.04, non  KERBROS NFSv4 installs.

I think all you need is to set the exports to async and edit the /etc/default/nfs-common appropriately.  I don't think "no_root_squash" has anything to do with your problems.

---

### Post by SeijiSensei on 2014-01-26
> **bab1 said:**
> I don't think "no_root_squash" has anything to do with your problems.

Well the OP is trying to mount the share as root with sudo:

> sudo mount -t nfs4 -o rw pluto:/share/Archive /mnt/Pluto/Archive

so his identity will be "squashed" by the server.

---

### Post by bab1 on 2014-01-26
> **SeijiSensei said:**
> Well the OP is trying to mount the share as root with sudo:```
sudo mount -t nfs4 -o rw pluto:/share/Archive /mnt/Pluto/Archive 
```

The OP is *running the mount command as root * not setting the ownership as root.
> 
...so his identity will be "squashed" by the server.

I'm not saying it's wise to allow root.  I'm saying that this is not the cause of the OP's errors.

---

### Post by jlacroix on 2014-01-26
I appreciate all of the replies you guys. It might be fixed. I'm not certain if one or more of the suggestions here fixed it or if I've been lucky lately, but nfs hasn't locked up the server since the last time I posted about it. Further, the permissions are showing properly now so that's fixed at least. I'll consider this solved for now unless it locks up again.

Thanks all!

---

### Post by bab1 on 2014-01-26
> **jlacroix said:**
> I appreciate all of the replies you guys. It might be fixed. I'm not certain if one or more of the suggestions here fixed it or if I've been lucky lately, but nfs hasn't locked up the server since the last time I posted about it. Further, the permissions are showing properly now so that's fixed at least. I'll consider this solved for now unless it locks up again.

Thanks all!
For future readers tell us what fixes you did apply, even if you don't know what actually fixed your problems.

---

### Post by jlacroix on 2014-01-26
I added the async and no_root_squash options to /etc/exports. I also added NEED_IDMAPD=yes to /etc/default/nfs-common. I restarted the both portmap and nfs-kernel-server after.

---

