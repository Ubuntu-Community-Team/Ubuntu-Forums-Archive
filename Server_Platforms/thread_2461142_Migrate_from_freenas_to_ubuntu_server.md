---
title: "Migrate from freenas to ubuntu server"
date: 2021-04-25
forum: Server Platforms
---

### Post by linre-90 on 2021-04-25
Hello everybody, i'm first time poster long time reader!:p I'm quite new for nas/server stuff so sorry for stupid questions beforehand...:(

So i have old computer running freenas **Version:**   FreeNAS-11.3-U5. I use it to store media files images, videos and music. It uses mainly samba shares.

_Computers/NAS specs_ are following: 
[LIST]
[*]Amd phenom x3 720 phenom (pretty old) 
[*]8 gb of ram (this is one reason to use ubuntu) 
[*]some cheap nvidia card (I honestly forget:D it is only because pc did not boot without graphics card) 
[*]2x 1000gb hard drives (zfs) 
[*]500gb boot ssd (os) 
[/LIST]


So i will move from freenas to ubuntu server...

The freenas has single pool with those 2 drives. They are mirrored and using zfs. OS is installed on seperate ssd. I have single pool with multiple sub-folders and ACL configured for 3 different users. 

I mainly use this to store files, coding projects etc. Recently i have been in need for some isolated dev/test environments. So my idea was to use it as server. Mainly behave like nas but option to spin up virtual machine that can act like VPS server for example. These VM would be quite small and do not require much computing power. For example to develop some docker app i would spin up VM with nginx and docker then push containers to that and test and experiment. Sometimes maybe python, lamp, databases or node or whatever. No need for ui, terminal access is fine. I don't need to code in there just to run applications and experiments.  I can propably survive with that stuff but the NAS side is little bit confusing for me now..

[SIZE=3]**So now to the questions...**[/SIZE]

[INDENT] 1.Those two 1000gb drives are at raid-1 (mirrored) what happens when i import these to ubuntu server?
[/INDENT]

[LIST=|INDENT=2]
[*]Does the mirroring be the same in ubuntu server or do i need to configure it again somehow? 
[*]Do i have to import one, format another and then mirror the disk containing data or will ubuntu figure out they are mirrored? 
[/LIST]
[INDENT]
2.  Is ACL only freenas and not disk related?
[/INDENT]

[LIST]
[*=1]I assume that all ACL configuration will be lost and i need to do it again in ubuntu server samba configuration? 
[/LIST]
[INDENT]
[/INDENT]
[INDENT]3. I assume S.M.A.R.T checks need to be configured again?

4. I should propably allocate space in 500gb os drive for VM to use?

5. Ubuntu has proper fzs support and importing works fine?

6. My current structure (in pool) is not ideal it is: Pool -> folders (user specific ACL) -> some data
[/INDENT]

[LIST]
[*=1]How this effects to mounting? Can i do -> /pool/folder(user specific)/data 
[*=1]Or do i have to split it to multiple pools like pool(user)/folders/data 
[/LIST]
[INDENT]
[/INDENT]
[INDENT]7. Maybe just copy all data to external source format everything and start again? (would be reaaaaaaaaally long project with these file sizes)
[/INDENT]


I have searched internet a lot and found many good examples and points but the things i just listed are little hazy for me and i don't know the answer... 
[INDENT]

[/INDENT]

---

### Post by TheFu on 2021-04-25
If you can't afford to lose the data, then make a backup first.

I've never used any home NAS, so I can't answer the other questions with authority about transferring.

Using ACLs on storage is asking for a mess. Just use normal Unix permissions. Both are stored in the file systems, but where the issue will probably arrive is that userids will almost certainly be different unless you go out of your way to ensure they do not change for the owner and groups used on disk.

Why use Samba? Can't NFS be used or setup a streaming server like Plex, MiniDLNA, or one of the 5 other projects?
I would expect ZFS across different OSes to be nearly completely compatible, but check the versions on both platforms.

Copying 1TB is nothing. Just a few hours.

---

### Post by linre-90 on 2021-04-25
The Smb is for windows machine and because of that ACL are set...  Nas is accessed from multiple os like ubuntu, android and windows. Occasionally by ps4... 

About those plex and others, i thought those only share media files like music and images. Can they be used for text/code files also?

---

### Post by TheFu on 2021-04-25
> **linre-90 said:**
> The Smb is for windows machine and because of that ACL are set...  Nas is accessed from multiple os like ubuntu, android and windows. Occasionally by ps4... 

About those plex and others, i thought those only share media files like music and images. Can they be used for text/code files also?

If you want to share text and code, use **git** or something like Nextcloud/Seafile/Owncloud.  For ebooks/pdfs, I use calibre.  Most NAS systems have a 1-click install for those.  Running a git server took me about 5 minutes to figure out. Read 1 page in _Pro GIT_ to understand it.

Samba is the least good option for file sharing of 20 other choices.

You read text files on a PS4?

I will admit these things:
[LIST]
[*]My **nextcloud** server accesses most of the files and data off an NFS server.
[*]My **Calibre** server accesses most of the files and data off an NFS server.
[*]My **Plex**, **jellyfin**, **Kodi** and **mpd** servers access most of the files and data off an NFS server.
[*]NFS is faster and provides native Unix permission controls.  POSIX permissions, going without is a hardship.
[/LIST]

My git and wallabag servers don't use NFS, just local storage.

---

### Post by linre-90 on 2021-04-25
No not reading text files with ps4. In fact i think, i lastly accessed nas with playsation when it was still running omv. It had dlna... 

Anyway ubuntu + nextcloud + calibre seems pretty interesting combo. Have to dig into that more. 

But regardless of path i'm gonna go probably the best way is to pull data to external source and start from scratch...

---

### Post by TheFu on 2021-04-25
And samba isn't always bad.  Sometimes it is the least bad choice. 

The only trick is for different shares to be created if you need different permissions. Then put users into the necessary groups by which shares they need to access. No need for ACLs that way. On Unix, ACLs are not in-your-face, so we don't really notice them, but they can override normal POSIX permissions, which is what all Unix systems use.

I was testing some samba stuff this morning for performance and got 113 MB/sec transferring a 1.9G file. I think the disk buffers hid the true speed disk-to-disk, so I ran the test going forwards and backwards ... only got about 72 MBps (570 Mbps) that way - HDD to HDD over the network. That's much more realistic for the storage involved.

If you don't need to transcode any media, then calibre and nextcloud and some DLNA server can run from a raspberry Pi v3 or newer.  A v4 Pi has real USB3 support and GigE NIC, so it could be a network backup server. That's always needed.  RAID never replaces backups, even ZFS RAID-whatever.

---

### Post by linre-90 on 2021-04-25
True, i have raided the disks mainly because the other disk is much older and will fail at some point, sooner or later. Anyway i also have backups from the most important stuff in complete separate drive outside system. 

I also found about something named proxmox that actually seems pretty interesting too and it might be very good match for my use case.  Or i could buy pie for experiments and keep nas just a nas.  Or make pie my new nas and play with old pc....

Have to do some thinking....

---

### Post by LHammonds on 2021-04-26
Proxmox is nice.  That's about all I can contribute to this conversation. :)

LHammonds

---

### Post by TheFu on 2021-04-26
> **linre-90 said:**
> True, i have raided the disks mainly because the other disk is much older and will fail at some point, sooner or later. Anyway i also have backups from the most important stuff in complete separate drive outside system. 

I also found about something named proxmox that actually seems pretty interesting too and it might be very good match for my use case.  Or i could buy pie for experiments and keep nas just a nas.  Or make pie my new nas and play with old pc....

Have to do some thinking....

Good on RAID and backups. 

I used proxmox around 2010 for a few weeks.  It takes over the system completely, so don't expect to run a desktop on it, except inside a virtual machine which would be accessed from another machine over the network.  Proxmox is interesting. For a small business that plans to have a few physical VM servers and wants them to be clustered, Proxmox is probably the easiest solution.  We can roll our own using ZFS or sheepdog with KVM or if we aren't tied to Ubuntu Server, RHEL and those flavors have **oVirt**.  I use a simple **virt-manager** setup with **libvirt** and KVM on LVM storage. LVM or ZFS bring enterprise storage volume management to all types of Linux systems. Both are rock solid.  LVM is purely volume management, whereas ZFS is both volume management AND a file system.  If I were starting new today, I'd skip LVM completely and use ZFS.

---

### Post by linre-90 on 2021-04-26
> **TheFu said:**
> Good on RAID and backups. 

I used proxmox around 2010 for a few weeks.  It takes over the system completely, so don't expect to run a desktop on it, except inside a virtual machine which would be accessed from another machine over the network.  Proxmox is interesting. For a small business that plans to have a few physical VM servers and wants them to be clustered, Proxmox is probably the easiest solution.  We can roll our own using ZFS or sheepdog with KVM or if we aren't tied to Ubuntu Server, RHEL and those flavors have **oVirt**.  I use a simple **virt-manager** setup with **libvirt** and KVM on LVM storage. LVM or ZFS bring enterprise storage volume management to all types of Linux systems. Both are rock solid.  LVM is purely volume management, whereas ZFS is both volume management AND a file system.  If I were starting new today, I'd skip LVM completely and use ZFS.


Interesting stuff... I desided to build entirely new server when gpu and cpu prices are somewhat reasonable. This 12 years old beaten machine starts to be end of it's life cycle. Noticed today when i was connecting kb and monitor that it smells little bit like burned capacitor, so i don't think it has much time left. I will inspect hell out of virtualization and start putting together suitable machine to satisfy my nas and VM thirst...

And to answer some questions i asked in the first post.
[LIST]
[*]As freenas states in documentation "ACL stands for Access Control List, which designates access control entries for users and administrators on _FreeNAS systems_, specifically for Windows SMB shares." So i think it does not impact impact pool/drive  importing in ubuntu. But it migth be good idea to remove ACL to reduce risk, how ever i might be wrong! Please correct me.
[*]Smart checks can be handled with smartmontools
[*]Ubuntu supports zfs. If not 100% happy with old structure back up data and configure pool again.
[/LIST]

[B]However i don't know how the mirroring behaves when importing i assume ubuntu zfs can catch it? My understanding is that mirroring configuration lives inside pool -> it is available when pool is imported or mounted? 

So if somebody knows please leave answer for future reference and correct me if i'm wrong...[/B]

---

### Post by TheFu on 2021-04-26
> **linre-90 said:**
>  
Ubuntu supports zfs. If not 100% happy with old structure back up data and configure pool again.


There are differences in zfs versions. Don't assume they are all he same. Also, zfs is for data storage, not OS or booting.  Dragons be in there.  Maybe ubuntu will have great boot support for zfs in 22.04. In 20.04, it isn't ready.

---

### Post by linre-90 on 2021-04-26
Great addition!

I meant data drives and zfs version is important especially if pool is imported. Sorry for my bad expression...

> [COLOR=#000000]*"Ubuntu supports zfs. If not 100% happy with old structure back up data and configure pool again."*[/COLOR]

[COLOR=#000000]What i meant with that last sentence that it is good to evaluate if the old pool is worth importing in the first place.
My pool is so small and simple that i think it is better to create completely new structure in ubuntu, fix old design inconsistency in folder structure and then feed data back to drives from back up...

Of course with bigger systems this would not work or it would be really tedious. [/COLOR]

---

### Post by linre-90 on 2021-04-27
Ok so i did complete the migration (have to do lot of things still try nextcloud, smart reports, vm's etc.), i thought to write not so detailed description what i did in case somebody else stumbles here. I did not want to put anything too detailed cause i'm not specialist and think it depends setup to setup what to do. 

Anyway my data is in place and everything seem to be working. Turns out pc was just full of dust and cat hair that is what probably caused smells.. First it is **important to check zfs version**, i did not do it because i went with what ever attitude... If ubuntu is on lower zfs version you cannot do this. I suspect that it is also good to unmount drives from freenas before installing ubuntu server (i did not do this and was receiving errors for this, luckily there is easy prefix for this that can be added to command)....


[LIST=1]
[*]First i checked that backups were functional and safe. Backup also freenas config file!
[*]Created ubuntu boot usb for server version 21.04. I tried to use 20.04 but i could not get it to install. It crashed multiple times at that point were you input profile. There were quite lot of discussions in world wide web about the same behavior from other users. The 21.04 installed without problems but note it is smarter to use lts versions. I also checked that all disks were showing up correctly.
[*]After that it booted, i added ssh (so i don't have to work from the floor) and static ip, checked everything was up to date and installed zfsutils.
[*]Import pool but _first check that it can be recognized by ubuntu! _Pay attention at this point this is the point when you can deside where you wanna mount it.  I did let zfs to pick place, i think it defaults to /YOUR_POOL_NAME/YOUR_DATASETS.
[*]No errors everything went great, yippee!  How ever it is good to always double check. I did see when running zpool status pool configuration with two discs that are in mirror. So the one question that i had is now answered,_ raid config is stored inside pool at least in freenas and i think it is zfs thing, really smart feature_.
[*]Then i went to browsing inside my server found the pools and of course access denied! i also created quick smb share just to check everything, again incorrect password etc.
[*]Oh boy i wrestled with this, did try a lot stuff. Eventually i realized that i cannot even access those folders from terminal and that waked me up. So i did have to give myself permission to these disks. I found that little weird, i did a lot stuff already with these, i though i must have permissions. Turns out i don't. So grant permissions and everything did work.
[*]After that i created test smb server for everything and i did have access to all datasets without issues in permission. So this leaves me to believe that acl was just freenas smb share thing (but we will see if errors rise) of course _not sure ask this from somebody more wise than me._
[/LIST]


[B]Positive impacts:
[/B]
My transfer speed from server to local computer went to 6x compared to freenas. I must have had some error in freenas configuration or some compatibly issue or my hardware is just too old to properly run freenas. I have had problems in the past when this pc was my daily driver it works great with some ubuntu releases and not at all with others. Another positive side is that i now have 6.5gb ram still to use with everything fun and cpu supports hardware vm's! I'm excited like kid in candy store!\\:D/ _I want to emphasize that i probably had error in my freenas configuration it is not realistic to expect these kind of speed improvements!_


[B]Few perhaps usefull personal observations:
[/B]
[LIST]
[*]Pick server solution for your needs. If requirement is just nas go for nas os like freenas, open media vault or unraid. I think they are easier to set up, stable and probably contain way less gotchas and provide lot of stuff out of box.
[*]Evaluate hardware tier and check system req. (freenas ram: 8gb + 1gb/tb for zfs, ubuntu server ram: 1gb + if using zfs 1gb/tb, open media vault 1gb ram).
[*]If newbie like me do search before hand
[*]Check compatibly
[*]Backup, backup, backup!
[*]Don't just copy paste every command found in the web, inspect them
[*]With this ubuntu server route, server admin who is probably you must maintain and setup everything so be prepared for lot of learning
[/LIST]


**Good search terms on google (i don't put links they end up not working):**
[LIST]
[*]zpool import
[*]Aaron Toponce install-zfs-on-debian-gnulinux
[*]Openzfs
[*]Ubuntu forum
[*]Ubuntu server documentation
[/LIST]

[B]Disclaimer:

[/B]These steps worked for me they might not work for someone else! Everything depends on how your stuff has been set up! Please read the full thread!

---

### Post by linre-90 on 2021-04-29
[B]Small permission update


[/B]After poking around and investigating my wonderful successful importing, i found that there comes some permission setups with importing pool. I did not see any ACL permissions and the type is off but somehow there were unix permissions with old users that existed in freenas. 

I am very bad with permissions, i always configure them wrong and end up using trial and error. I need to study those more. Anyway it might be good idea to simplify permissions before importing and mounting unless 100% sure what is set and happening. I wonder if there were some permission conflicts that caused my bad speed with freenas....:-k

---

### Post by TheFu on 2021-04-29
All Unix file systems have Unix POSIX permissions as part of the file system storage.  The uid and gid numbers - type 'id' command - to see them - those numbers are what determine the owner and group for each file system object.  chown and chgrp are used to modify those. Only root/sudo can use chown.  The "owner" can change the group, but only within groups the owner is a member. The owner can change the permissions bits too - 700 or use the letters, if you like.
u = user
g = group
o = is any id that isn't either the user or the group. Sometimes this is called INCORRECTLY "world" or "everybody" - which is wrong.
Then
r = read
w = write
x = eXecute
So, **chmod 770 {file}** = **chmod ug+rwx,o= {file}**
Which would you rather type.  The numbers become memories over time. Sometimes using the letters is shorter/easier.
Sometimes I'll use **chmod 770 {directory}** followed by **chmod g+s {directory}** - that uses the setgid flag.

Unix permissions have been elegant and relatively simple the last 40+ yrs.

Every popular OS except one uses Unix permissions, so learning them isn't a waste of your time.
Google "ubuntu permissions" for a tutorial.  That's fine for an overview, but until you sit down with 3 userids, inside 3 different terminals, with 2 different groups, all mixed and match, and start creating directories and files then chmod and chown each using every possible permission and owner/group combination from 700 to 007, you'll never really "get" permissions.  But once you do, the light bulb will go off and you'll have that understanding the rest of your life.

The overview tutorial is about 15 minutes.
The trial and error, hands-on, work is about 30 minutes.  So in 45 minutes, you could know 90% of Unix permissions, which is most used.  That last 10% is for things like setuid-bits, setgid-bits and the sticky-bit.  The first and last are seldom used and really should be avoided.  The setgid flag is extremely useful when groups of userids need to work together, edit the same files, etc.

45 minutes.  Do it ASAP.

CIFS and SAMBA don't care about Unix permissions, BTW. OTOH, NFS does use full POSIX permissions with just a few caveats. Root from a client machine does not have root privileges. Only root on the NFS-server has root.

---

### Post by TheFu on 2021-04-29
I'm a little shocked that someone using ZFS doesn't fully understand Unix permissions.  That freaks me out a bit.

---

### Post by linre-90 on 2021-04-29
> **TheFu said:**
> I'm a little shocked that someone using ZFS doesn't fully understand Unix permissions.  That freaks me out a bit.

I'm aware of those those basics and try to set everything best i can. I try to set always only minimum amount of rights and this sometimes drives me to confusion why something is not working as expected. But i need more practice.

---

### Post by LHammonds on 2021-04-29
Make sure ACL permissions are not messing with you which are not normally visible unless you use the ACL utilities.

```
getfacl filename
```

The ACL utilities are not installed on Ubuntu Server by default so you might need to install them if the command is not found.

```
sudo apt install acl
```

LHammonds

---

### Post by linre-90 on 2021-05-14
I finally came to an end with my migration. I did had to face my old permission s***... :( But managed to solve them and learned a lot. I ended up using docker quite heavily, it fits my needs perfectly and it is "lighter" than separate VM. 

Anyway I wanted to pay my respects for LHammonds and especially for TheFu.Thanks for both of you for pointing great stuff! 

Keep up the good work!

---

