---
title: "Time to build a server with old hardware."
date: 2020-11-21
forum: Server Platforms
---

### Post by Phil Binner on 2020-11-21
My home/small(very) business system stores all its information on a D-Link NAS.  This is an old piece of kit using SMB1; I think I bought it about 2014 so it doesn't owe me anything.  Release 20 of Ubuntu has discontinued support for SMB1, however, and although I managed a work around in XUbuntu 20.04 it's clunky at best.  Last week I got a laptop back from maintenance and they had re-installed Windows.  It turned out that the latest Windows 10 also has SMB1 turned off, and although it was relatively easy to turn it back on, I would say the writing is on the wall.  Now is probably time to build a server.

I have an old full tower case with one of the last Intel chips before the I series.  I last had it running about a couple of years ago, when it handled either Ubuntu or XUbuntu just fine. 

My problem is that my knowledge of communications protocols is next to non-existent.  Actually putting the thing together and loading the Linux software are things I can handle, but I have the feeling I may get into deep water shortly after that, so I have an initial list of questions:

1.  Is the idea of building and running a server something that a reasonably bright but technically  inept old git should be able to accomplish with help:
2.  Are there people out there who are willing to help me,  because I don't think it's something I would be able to do on my own:
3.  Is the hardware I currently have likely to work as a server, given that demands on it will be low and I will be willing to spend money on an upgrade once it is successful;
4.  Is there something I should be spending money on up-front;
5.  Given that it will be accessed by both Windows and Linux, what communications protocols should I be looking at.

Thanks in advance.

Phil B

---

### Post by TheFu on 2020-11-21
> **Phil Binner said:**
>  

1.  Is the idea of building and running a server something that a reasonably bright but technically  inept old git should be able to accomplish with help:

You can do anything you put your mind at.  But the learning curve can be steep if you want to understand everything. There are pre-built setups designed for specific tasks, however I find they aren't really too secure by default.

> **Phil Binner said:**
>  
2.  Are there people out there who are willing to help me,  because I don't think it's something I would be able to do on my own:

You can ask any questions here that you like, provided they don't tie to illegal activities. If a questions is well-asked, someone will likely answer. Nobody should be typing on your system and you shouldn't allow anyone else to do that, unless you have a written contract, for money, setup.

> **Phil Binner said:**
>  
3.  Is the hardware I currently have likely to work as a server, given that demands on it will be low and I will be willing to spend money on an upgrade once it is successful;

Old hardware will often have funny faults and failures.  New stuff that is 10x-30x faster isn't very expensive.  For example, I built a Ryzen 2600 system a few years ago for about $400.  There have been a few times since then that similar systems could have been built for less than $250.  Most 2014 laptops are crap and you'd be better off getting a $300 Core i5 off ebay.  I did that 2 yrs ago - $305 shipped with 8G of RAM, 1TB HDD, and i5-8250U (That's over 7000 passmarks).  The Ryzen 2600 is over 13,000 passmarks for reference. If you have a little more cash, the new Ryzen 5 5600 has over 20K passmarks for $300, but I'm looking forward to the R-2600 and R-3600 price drops myself.  

Why so much CPU?  So different services can be virtualized. This makes upgrading each service much easier and disconnected from other services which are likely to need conflicting libraries.

> **Phil Binner said:**
>  
4.  Is there something I should be spending money on up-front;

You haven't said what you want in a "server".  There are thousands of possibilities. Which do you want?

> **Phil Binner said:**
>  
5.  Given that it will be accessed by both Windows and Linux, what communications protocols should I be looking at.


Start with ssh.  That provides ssh, scp, sftp, x2go, rsync, rdiff-backup, a minimal VPN, a SOCKS proxy and a few other capabilities just with 1 service enabled.
You need to decide what you want this "server" to provide.  
Do you want access from anywhere in the world or just inside the LAN? 
How much do you care about security?

Many of the protocols you hear in Windows just aren't needed and don't work well. This is a chance to switch to better protocols, which greater access and greater security.

[LIST]
[*][https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign) has some ideas for what you might want.
[*][https://medium.com/better-programming/how-i-started-self-hosting-df17f0919d64](https://medium.com/better-programming/how-i-started-self-hosting-df17f0919d64) a crazy guy self-hosting using cheap raspberry pi computers.  I wouldn't do this except for the smallest needs. Any x86 computer will blow away any Raspberry-pi on the compute capabilities. Plus, people don't think their r-pi servers will be hacked.  Had someone here report a hack to their v1 r-pi a few days ago. Any computer can be hacked.
[*]Some other things you might want to self-host: [https://github.com/awesome-selfhosted/awesome-selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted)
[/LIST]

I self-host a few things:
[LIST]
[*]VPN (required to access most internal servers)
[*]email (most people don't want to do this)
[*]communications, shared calendaring, shared addressbook
[*]Storage via NFS (NFS is how Unix systems share storage)
[*]Nextcloud (private and shared storage with lots of interesting addons like photos, music, tasks, GPS tracking, video/audio conferencing)
[*]Wallabag (read-it-later clone)
[*]Calibre ebooks
[*]Plex DLNA (photos, videos, media)
[*]Desktops (can be accessed from anywhere in the world, securely)
[*]Multiple websites for different business and hobby needs
[/LIST]
And don't forget that you need excellent, automatic, daily, backups. If you don't have 3 copies, in at least 2 physically different locations, then you don't have backups at all.  Also, if you haven't tested a full restore onto completely different hardware, then you don't have backups.  Businesses die because they don't have proper, tested, backups.

If you plan to have any remote access at all into the LAN, setup ssh using ssh-keys, block all passwords for authentication. Do that as your first step.

You'll notice that I didn't mention samba or Windows.  Windows has some great ssh, scp, sftp programs - Filezilla and WinSCP come to mind.  Win10 has a subsystem that supports ssh natively, so you can do most things from/to Windows that are so very easy on Linux dekstops.  Accessing sftp from any Linux desktop is as easy as using any file manager with sftp:// for the URL. If you setup ssh-keys, then you won't get hassled for login credentials for that access.  ssh is the only tool I know which is both more convenient AND more secure.

So - what services do you need/want on your "server?"

---

### Post by SeijiSensei on 2020-11-21
Sounds like you're basically interested in building a server to share files, not run mail or web or DNS services.

If so, I suggest installing a desktop version of Ubuntu, then adding the Samba and nfs-kernel-server packages. Use Samba to share files with Windows machines. Use NFS for Linux and MacOS clients.

```

sudo apt install samba nfs-kernel-server

```

On Ubuntu clients, you'll need nfs-common.

You can serve up the same directories via either protocol. I do that on my server here so I can see the shared directories on the rare occasions I use Windows.

---

### Post by Phil Binner on 2020-11-21
What I want is basically what  SeijiSensei has suggested.  I have a media machine that uses video and music, and several windows and one XUbuntu machine that share files.  All that is currently supplied by the NAS.  It's just that the NAS is old and D-Link are not offering any downloads to update the software.  In addition secure remote access would be usefull.  My options seem to be to buy a more modern NAS and continue as before, or build a server.  Since I have an old computer in a full tower case I do not use, I thought loading Ubuntu-Server on it would serve 3 functions, solve my current problems, provide much wider options for the future, and increase my knowledge.  The last of those is tempting.  

What I have done so far is to fire up the old computer to see what state it is in.  Unfortunately that fell at the first hurdle.  The power comes on for about 2 seconds then cuts off.  Since there are no motherboard beeps it seems to be a power supply problem to me, but it could be the motherboard.  If I want to go forward with that I can look for a second hand motherboard/processor on ebay, and a new power supply.  If I do that I'll look at the Ryzens; they tend to be cheaper for the power.  That shouldn't set me back too much.

Alternativly I can put a couple of 3tb drives in the XUbuntu machine I'm using and follow  SeijiSensei's suggestion.  That will mean that my server is also a desktop machine, but i'm assuming that that won't cause too much problem with the low demand I'm putting on it.

Thanks to both of you.  Any further comments will be welcome.  For now I'll sleep on it and decide in the morning.

---

### Post by TheFu on 2020-11-21
Be very careful using 3TB/5TB/6TB HDDs.  Those "odd" sizes have a less than great history of higher failures.
4TB, 8TB and larger seem to all have much better reliability.

If you are really hurting for cheap storage, consider buying used Enterprise HDDs - the WD-Gold (or Hitachi 310) line 4TB can be found mid-life with ZERO bad sectors for under $40.  These things are built for lots of vibration in datacenter environments - probably get 10+ yrs of total life for 50% less than new consumer HDD costs which often fail in 3-5 yrs.

+1 for NFS. My LAN uses NFS for almost all storage access. It provides native Unix access and permissions - basically, network storage acts just like local storage and the client machines don't know the difference.

I love Nextcloud - it provides storage and selective sync to clients for pretty much any platform. Just be certain to have a VPN to get access over the internet.  With Nextcloud, there are some great addons.

---

### Post by Phil Binner on 2020-11-22
I have decided to do both things, getting my feet wet slowly.  The first thing I have done is run "sudo apt install samba nfs-kernel-server" as  SeijiSensei suggested, so that is done.  I now need to work out how to share the folders I have currently, before adding more storage.  I have an article or two to read today, as well as starting to look for hardware.  

The reason I thought about 2 3tb drives is that I already have one originally intended for backups.  I don't want to get into failures while I'm still trying to work out what's going on, so I will take that advice seriously.

Thanks for your help so far.  More on the next step will be appreciated.

---

### Post by TheFu on 2020-11-22
If you search for "ubuntu nfs" you'll find a how-to guide, probably at help.ubuntu.com.
Because that guide has to address almost every possible situation, it is much, much, longer than necessary.

NFS tips:
[LIST]
[*]Make storage locations the same locally and over NFS. This will prevent confusion that will happen based on which machine you happen to be on.
[*]Use NFS for all Unix-like OSes.
[*]NFS is server -to- server sharing.  Not user -to- server like CIFS/Samba.  User credentials have nothing to do with NFS connections.
[*]Make all uid/gid numbers that will be accessed using NFS (as returned by the 'id' command) the same on all the systems. userid 1000 needs to match on all the systems.  Any groups or shared groups gid needs to match on all systems too. On Apple platforms, userids begin with 500. On all Linux platforms, they begin numbering at 1000.  That means if you have the same user (a human) on both apple and Linux, then one or the other platforms will need to change the uid to match the other.  If you have 5 apples and 1 Linux, I'd change the Linux one. IF you have 1 apple and 5 Linux, I'd change the apple.  In theory, there is a mapping solution for this. I've never seen it work.  In businesses, we use LDAP for all logins so all the uid/gid are centrally managed and this is a non-issue.
[*] usernames and groupnames mean nothing. It is all about the numbers.  1000 on the client --> 1000 on the server.
[*]On the server-side, there is 1 line in the /etc/exports for each "exported" file system.  
[*]On the client-side, there is 1 line in the /etc/fstab for each "NFS" file system. 
[*]After changing the /etc/exports file, restart the server-side NFS service to the config changes are reloaded/seen.
[*]Client-side changes should automatically be seen, but if they aren't, you can tell systemd to **sudo systemctl daemon-reload**
[*]The sudo or root accounts from clients don't have superuser privileges on NFS storage by default.
[/LIST]

So, with all that in mind, here is a single NFS on the server in /etc/exports:
```
/TV     regulus(rw,async,root_squash) romulus(rw,root_squash,async) hadar(rw,root_squash,async) posc(rw,async,root_squash) osmc(rw,async,root_squash) pi3(rw,async,root_squash)

```
That's 1 line. Spacing is critical. Note were there are and aren't spaces. It matters.  I share only with specific systems on this subnet. If you want to share on the entire subnet (dangerous), you can use CIDR notation instead:
```
/TV     192.168.1.0/24(rw,async,root_squash)
```
Anyone on your subnet, including guests, can mount.  Often, you'll see other settings in online examples. With NFSv4, which Ubuntu has used for a decade, those other tuning numbers are automatically determined, so not useful except under really odd situations.  Don't forget that sometimes you want a read-only export.  I export Music as read-only to prevent accidental deletions from clients or overzealous media center software.

On the client side, besides using the /etc/fstab, you can use autofs.  That's how I do it for a number of reasons.  As with all mount points, the directory must already exist **sudo mkdir /TV**. But for now, just use the fstab.  
```
istar:/TV   /TV  nfs    proto=tcp,noauto     0     2
```

istar is my NFS server. An IP address can be used, if you prefer.
**sudo mount -a** will mount/remount everything in the fstab.  
```
mount |grep TV
``` will show that it is or isn't mounted. So will the **df** command.
```
$ df -Th
Filesystem                        Type  Size  Used Avail Use% Mounted on
...
istar:/TV                         **nfs4**  294G  102G  193G  35% /TV

```
Because my setup is using autofs, I'm not 100% certain how to get the mount live.  With autofs, storage is only mounted when specifically requested.  **ls /TV/** is sufficient or any command that accessed anything under /TV/ will mount it.  When that mount hasn't been used for a few minutes, it will be removed by autofs.  This is convenient for storage that isn't always available so any connection errors don't cause problems for clients.

So, if you have the userid mapping already handled, you can see were adding NFS is pretty trivial.  2 lines, restart the NFS daemon, and mount. It is 45 seconds, maximum time, once.  No screwing around with credentials after that, unless you want to get much more security.  If you do, NFSv4 supports encrypted connections and Kerberos for server-to-server authentication. Settings those up **is** harder. The encryption is considered secure enough to use over the internet.

If I missed something important, hopefully someone else will post a correction.

---

### Post by SeijiSensei on 2020-11-22
I found the NFS guide way too lengthy and complex for simple applications. So I posted this in recent thread as an alternative: [https://ubuntuforums.org/showthread.php?t=2453841&p=14001094&viewfull=1#post14001094](https://ubuntuforums.org/showthread.php?t=2453841&p=14001094&viewfull=1#post14001094)

---

### Post by TheFu on 2020-11-22
I've had problems using the systemd-automount stuff.  It doesn't work as expected. x-systemd.automount is the config option in the fstab. I tested it for a few months. It never auto-dismounted, IME.

OTOH, autofs is solid and always works as expected once the initial learning curve is done.

---

### Post by SeijiSensei on 2020-11-22
I don't care about dismounting so I haven't seen this issue. The only time I dismount file systems is when rebooting.

---

### Post by TheFu on 2020-11-22
> **SeijiSensei said:**
> I don't care about dismounting so I haven't seen this issue. The only time I dismount file systems is when rebooting.

I use autofs with USB devices, so the lack of u-mount is a problem.  Also, it is nice to not worry about rebooting the NFS server system when that is necessary. Locking up 10 NFS client machines can ruin a day.  The fix for that is to use "soft" mounts, but those have repercussions.  I miss the "Spongy" mounts that amd (auto-mount-daemon) provided in the 1990s.  Perhaps that option still exists and I've missed it? It isn't in the mount.nfs manpage.

---

### Post by Phil Binner on 2020-11-23
Thanks guys.  I obviously have a bit of reading to do before the next move.

One question comes up straight away though.  If NFS is server to server sharing, why do I need it.  I'm sorry if this seems a naive question, but please remember I'm at the very bottom of the learning curve.  We will never have more than one server, and we have no Apple machines, just Linux and Windows.  Unfortunately Windows is essential for the business activities until Word and Excell can run on Ubuntu, so I presume I will need Samba.  

Unfortunately I am just moving into an intense period of business activity, so the time I have spare to follow this thread will be limited for a while.  Perhaps a week.  I will keep watching it, however, and I may be able to reply occasionally.  If I do not then please do not assume I've given up or gone away. I am grateful for the help.  What I will not be able to do for a while is try out any of the suggestions you make.

Thanks.

---

### Post by slickymaster on 2020-11-23
*Thread moved to **Server Platforms**.*

---

### Post by Doug S on 2020-11-23
> **Phil Binner said:**
> One question comes up straight away though.  If NFS is server to server sharing, why do I need it. We will never have more than one server, and we have no Apple machines, just Linux and Windows.  Unfortunately Windows is essential for the business activities until Word and Excell can run on Ubuntu, so I presume I will need Samba.You don't. I only use samba. I use rsync for linux to linux, typicially for bulk backups or whatever.

---

### Post by DuckHook on 2020-11-23
> **Phil Binner said:**
> &#8230;If NFS is server to server sharing, why do I need it.  I'm sorry if this seems a naive question, but please remember I'm at the very bottom of the learning curve.  We will never have more than one server&#8230;
As if you needed any more input. But FWIW, here are my two bits:

NFS is not just server to server. It also works better as a server to client connection, provided both ends are Linux. This is because NFS, being native to Linux, preserves file attributes and permissions properly.

While it is clear that you need Samba, you may wish to consider NFS not only for its better Linux behaviour but because it adds flexibility. Relying on just one server is risky. I have a series of cheap servers&#8212;and I mean *cheap*&#8212;one of which is used for daily mirroring of my main server, another to mirror as well but only periodically through manual instigation (both are old repositioned HW with the only added cost being new HDDs). These mirrored servers are a breeze to set up and maintain because they run NFS, whereas I would hate to configure them in Samba. I find this to be a big plus. The only minus is having to learn something new.

---

### Post by TheFu on 2020-11-23
> **Phil Binner said:**
> Thanks guys.  I obviously have a bit of reading to do before the next move.

One question comes up straight away though.  If NFS is server to server sharing, why do I need it.

server-to-server just means that individual credentials aren't needed.  The different computers are connected regardless of the logged in user.

Sorry I used confusing terms.

There are pros and cons for NFS and Samba.  Mainly, NFS behaves like native storage. Same permissions, same access, same capabilities.  If you don't really understand those capabilities, then you'll never miss them. 

OTOH, if you do not know those things, what difference does it make?

NFS is much easier to setup. There really aren't many options to control NFS. It just works.  Updates to the code through patches doesn't break NFS, at least it never has in my experience.  It just works and it is fast.

Then there's samba/SMB.  Check these forums for people having issues with samba.  People sometimes choose to stay with something they've heard about from Windows instead of using the native Unix methods.  Unix people are smart. They tend to make the easiest, solid, solution, that is possible.  Stuff that doesn't do those things dies off quickly. NFS has been around 40 yrs - perhaps more - because it works.

---

### Post by Phil Binner on 2020-11-23
What I am getting from this is that I should have NFS because it is solid and reliable and will provide a good platform for whatever else I do.  On the other hand, this will not enable me to do without Samba, because whatever else happens I will need Samba for the Windows machines to connect..

So, trying to integrate what everyone has said so far, how about this for an interim plan:

    Use my existing XUbuntu machine as a server. leave the 20.04 implementation but add the additional routines to make this possible.  To this end I have already followed advice from Sijisensi and run the command "sudo apt install samba nfs-kernel-server".  It appeared to work, but by itself it has so far not made any difference. I guess that is what I should expect.

    Set up NFS.  I presume this will require  a similar terminal command to activate.

    Publish files to the new server by editing /etc/exports.  I will need some interpretation of the /TV command, but I think I can see what it is doing.

    Access these files on another Linux machine by editing /etc/fstab

     Set up Samba on the server and get the windows machines talking to it.

     Populate the server with 2 4tb hard drives and format them as a raid system.  Integrate them into the network.

     Build a dedicated server and populate it with mirror disks to act as the permanent server.  Migrate the configuration and hard drives to it.

     Re-build my XUbuntu box as a work station.

I have laid it out like this for 2 reasons:  firstly because I want to get into this as gently as possible, and secondly because I hope you guys out there who know will free to tell me what I am doing wrong.  At least this seems to be generating some interest.

Thank you yet again.

Phil B

---

### Post by TheFu on 2020-11-23
I think you have a good grasp. You didn't mention checking the 'id' command for each userid involved. If there's only 1 user and they are all Linux systems, then it should just work. But if you have 5 different userids and each was added to different workstations or in different order, then some more clean-up will likely be required.

/TV is just a directory.  It is the directory that I export on the NFS server and I mount the NFS onto /TV on the client machine.  Change that to whatever directory you want to export on your NFS server.

Do you really need RAID?  Solid, daily, automatic, backups are much more important. After those are working, then deal with RAID (High Availability) if you like.

---

### Post by Phil Binner on 2020-11-24
What about getting started. How do I install NFS in the first place.  I guess it's something like "sudo apt-get install nfs-server"

---

### Post by CelticWarrior on 2020-11-24
The package name is "nfs-kernel-server".

---

### Post by Phil Binner on 2020-11-24
Ah, so it's already there.  The next job is to publish the drive then.  I'll consider that over the next few days and try to get the office work out of the way.

Thanks.

---

### Post by TheFu on 2020-11-24
> **Phil Binner said:**
> What about getting started. How do I install NFS in the first place.  I guess it's something like "sudo apt-get install nfs-server"

SeijiSensei posted a link with a short guide that gets to the point above. Please take a look at it.

---

### Post by Phil Binner on 2020-11-24
Looking at SeijiSensei's command

"/home     192.168.100.0/24(rw,async,no_root_squash,insecure,no_subtree_check,fsid=0)"

and Fu's command

"/TV     regulus(rw,async,root_squash) romulus(rw,root_squash,async) hadar(rw,root_squash,async) posc(rw,async,root_squash) osmc(rw,async,root_squash) pi3(rw,async,root_squash)"

I am reading that SeijiSensei is publishing the home folder for anyone on the network, while Fu is publishing the folder TV for specific users - regulus, romulus, etc.  

Am I reading that correctly?  If so, where does the ip address point to, and what is the significance of  /24

What I want is for all machines to have access, but based on user rights. My first stab at this command would be 

"/Home     firstuser(rw,async,no_root_squash,insecure,no_subtree_check,fsid=0)"

How does this look.

---

### Post by Phil Binner on 2020-11-24
Sorry if this is dragging on.  I'm only getting a few minutes a day on this at the moment, but I'm trying to keep it moving.

---

### Post by TheFu on 2020-11-24
> I am reading that SeijiSensei is publishing the home folder for anyone on the network, while Fu is publishing the folder TV for specific users - regulus, romulus, etc.


Specific Computers.  Users aren't involved at this level.  Remember, it is system-to-system, not user-to-system. NFS doesn't care about users. It cares about uids and normal Unix permissions. That's the plus.  Local and remote storage follow the same rules, except that local root isn't root on NFS storage, just local storage.  Unless you use the no_root_squash option (which is poor security).

/24 is known as CIDR notation.  A /24 (slash 24) network is the same as having a netmask of 255.255.255.0. It is just shorter.

User permissions are handled using normal, standard, Unix permissions.  chmod, chgrp.

This is for the /etc/exports file on the NFS server:
```
"/some-shared-directory ubuntu-client-hostname(rw,async,no_root_squash,insecure,no_subtree_check,fsid=0)"
```
I fixed 
[LIST]
[*]the shared directory. I can almost assure you that you do not want to share /Home or /home/. Those are advance capatilities and require much more understanding of users, HOME directories, and ramifications for snaps.
[*]the extra space
[*]hostname
[*]don't  need _insecure,no_subtree_check,fsid=0_ options
[/LIST]
So - either put in the IP address of your client machines or ubuntu-client-hostname (assuming you have a properly managed network with DNS).  

The exports file has to be setup before the fstab can be known.

---

### Post by Phil Binner on 2020-11-24
Saying I have a properly managed network with DNS may be stretching it.  I have a router supplied by the ISP and a couple of extension routers hanging off it.  The various desktop computers are hard wired with Cat 7 cable, and phones/tablets use wifi.  The business consists of 2 partners, me and my wife.  My understanding is that the ISP's router handles the DNS, and the extension routers are set up as slaves.  I believe IPA's are dynamically assigned.

So I think you are saying:

Find or create /etc/export.  Then add the line:

/myfolder     firstmedion(rw,root_squash,async)

Run the command, sudo systemctl start nfs-kernel-server  

Then I have a server running and have to connect to it by editing fstab in firstmedion

What is the difference between root_squash and no_root_squash.  Does  root_squash meen I need to present more information when connecting from firstmedion.

Looking at the link SeijiSensei provided, he said I need fsid.  How come I can do without it.

Sorry if I'm still being naive, but this is all new.

Thanks.

---

### Post by TheFu on 2020-11-24
The nfs server must have a static IP.  The clients need to know how to locate the server. It cannot jump around.  That is what an internal DNS server does. If you don't have one of those, then you must use the IP address.

root_squash determines whether the root account on a client has root-level file control to the NFS files. All these things are documented in the exports manpage.  Manpages are on your system ad cover all the options.

A well-managed network is one where all systems can find each other using names. Normally, this is accomplished using DNS. There are other methods, but only DNS works on all platforms. External DNS doesn't help to resolve systems on your LAN.  Servers all have static IPs.

If all your nfs clients cannot ping  firstmedion using that name, then you must use the IP address.

fsid is for special nfs needs that your setup will not have.  It takes 60 seconds to try with and without the setting. I've never needed it in 30 yrs.

After you edit the fstab, you need to mount the storage.  **sudo mount -a** will mount everything configured in the fstab. It is safe to run that with some file systems already mounted.

BOB'S OUR UNCLE.

---

### Post by Phil Binner on 2020-11-25
Everything on my system has a name, so that's one hurdle.  I should be able to go into the router management and make the IP static.  So I should be ready.  

With luck I'll get time to do this today.  Otherwise it will be the weekend.

Thanks.

---

### Post by Phil Binner on 2020-11-25
So far I have

1  Put an additional hard drive into the machine I am using as a server.  Formatted it as FAT and called it Vol10

2   Edited /etc/exports to add the line         "/Vol10     firstmedion(rw,root_squash,async)"

3   in the terminal run the command        "sudo systemctl start nfs-kernel-server"

4   open the rooter and find the IPA for the server.  Make it permanent.

5   Go to firstmedion and edit fstab to add the line   "/Vol10   (serverIPA)/24(rw,async,root_squash)

6   Restart firstmedion

The result is that firstmedion will not boot.  It goes into emergency mode and offers Advanced options or System setup, but neither offer me any way of reversing the fstab change.

This is not an immense tradgedy.  firstmedion is only an old laptop with a duff battery that has to stay plugged into the mains, and I have no more invested in it's setup than loading the DVD.

What did I do wrong though.

Thanks.    Phil B

---

### Post by TheFu on 2020-11-25
Don't use FAT.  use ext4.
Local storage must be mounted using the fstab before it can be shared by either nfs or samba.  
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)  This is assumed, basic, knowledge. The "Examples" section in that link has both NFS and local file system mount examples.

Don't use fat or ntfs or any other non-natve linux file system.

IPA = Beer?  Definitely seek that.

---

### Post by Phil Binner on 2020-11-26
Do you drink this stuff called American IPA, or is that just how they market it in the UK.  Good stuff; I enjoy the extra hoppyness, but I always think American India Pale Ale must be Sioux or Appache.

Thanks.  I have a trip now but I'll get to that when I get back.

---

### Post by TheFu on 2020-11-26
> **Phil Binner said:**
> Do you drink this stuff called American IPA, or is that just how they market it in the UK.  Good stuff; I enjoy the extra hoppyness, but I always think American India Pale Ale must be Sioux or Appache.

Thanks.  I have a trip now but I'll get to that when I get back.

OT:

We just call it "IPA" - not my favorite. I prefer Bochs, because that is what we drank at University. 
[https://www.shiner.com/beer/bock](https://www.shiner.com/beer/bock)  

Never heard of "American India Pale Ale". Looked it up.  I'm not much of a drinker - perhaps 4 beers in a month. Right now, there's some Blue Moon wheat in the fridge. I haven't been to a liquor store in over a year, so getting anything that isn't mass marketed is impossible. Grocery stores here tend to have lots of bad American beers because the majority of Americans think Miller or Bud (American) are fine beers. ;( They've not been to the Czech Republic for the real Budweiser which isn't bad, just not my choice if I'm picking.

Oddly, my LUG (Linux Users Group), is called "ALE" - ale.org. A few of the members are brewers. There are long discussions about brewing at some meetings plus post-meeting happens at a local (local to the meeting location) pub.  My sub-group in the LUG has been meeting 100% virtual since March, but the other groups have gone back to physical meetings.

---

### Post by Phil Binner on 2020-11-28
Interesting you call a pub a pub.  We call them pubs, but most American films call them bars.  We also have bars, but they are not the same as pubs.  Not sure if I could actually describe the difference.  You certainly wouldn't get a bar in a village, so I suppose that's one difference.  Plus a bar is altogether more trendy.

I suspected American IPA was a British marketing term.  Now I know.

Anyway, back to work.  I have formatted the new disk as Ext4, so lets see what happens now.

---

### Post by Phil Binner on 2020-11-28
Formatting the hard drive as FAT does not seem to have been the problem.  Unfortunately a couple of other things have gone wrong also, so I have had to go back to the start.  So far I have:

Loaded XUbuntu 18.04 onto an I5 desktop machine.  This machine is called Bigbin-XUbuntu.
Installed a hard drive and formatted it as Ext4 named Vol10
in a terminal, run the command    sudo apt install samba nfs-kernal-server
Loaded Ubuntu 18.04 onto an I5 laptop.  This machine is called firstmedion
In Bigbin-XUbuntu, edited /etc/exports to add the line       /Vol10      firstmedion(rw,async,root_squash)
Logged onto the router to find that the IP address of Bigbin-Xubuntu is 192.168.1.168.  Make that address fixed.
In a terminal run the command     sudo systemctl start nfs-kernel-server 
In firstmedion, edit /etc/fstab  to add the line     /Vol10    192.168.1.168/24(rw,async,root_squash)
re-boot firstmedion

firstmedion will not reboot properly.  The first two lines of the error screen reads:

/dev/sda2:   clean,  179554/15597568 files,  3308911/62383360 blocks
emergency mode.

Entering my password gets to the command prompt, but I am not able to edit /etc/fstab  to comment out the line I added.

Interestingly, when I ran the command   sudo systemctl start nfs-kernel-server in Bigbin-Xubuntu nothing happened.  It just went back to the command prompt.

---

### Post by TheFu on 2020-11-28
> **Phil Binner said:**
> Interesting you call a pub a pub.  We call them pubs, but most American films call them bars.  We also have bars, but they are not the same as pubs.  Not sure if I could actually describe the difference.  You certainly wouldn't get a bar in a village, so I suppose that's one difference.  Plus a bar is altogether more trendy.

I suspected American IPA was a British marketing term.  Now I know.

Anyway, back to work.  I have formatted the new disk as Ext4, so lets see what happens now.

OT: A pub is more low-key, laid back, where families can come.  Bars usually don't allow anyone under 21 inside, have loud music constantly. Every state has different laws, but I think allowing kids inside would be the main legal difference.  Pubs would have a food menu, but still feature alcohol much more than a restaurant with a liquor license.

Some of this is my best guess/opinion based on living in 12 states and going inside many bars and pubs. Important research, as you can understand. ;)  People from different parts of the country will probably have different ideas.

We also have Sports Bars with 20-50 TVs with almost every conceivable sport playing.

Because I live way outside any town, pubs and bars aren't really convenient even without COVID.

ext4 will make lots of things easier for Linux - and faster.

---

### Post by Phil Binner on 2020-11-28
I have ext4.  The client still won't boot.

The thing that stops the client booting is the line

/Vol10   192.168.1.168(rw,async,root_squash)     in fstab.   I have loaded Ubuntu twice now, and it initially boots OK, then fails to boot when that line is added.

---

### Post by TheFu on 2020-11-28
Ok ... let me pass on 20+ yrs of a Unix admin knowledge, much of it not specific to getting NFS working, but to help avoid issues later.

> **Phil Binner said:**
> Formatting the hard drive as FAT does not seem to have been the problem.  Unfortunately a couple of other things have gone wrong also, so I have had to go back to the start.  So far I have:

FAT is always to be avoided, unless there isn't any other choice. Don't use non-Linux file systems with Linux/Unix services. Sometimes there are ways to make things work, but often basic things do not. This is mainly because Unix expects Unix permissions, owners, groups, ACLs, and xattrs to be supported.  Avoid NTFS too, for the same reason.  Also, both of those are 30% slower than the Unix file systems for a number of reasons.

> **Phil Binner said:**
> Loaded XUbuntu 18.04 onto an I5 desktop machine.  This machine is called Bigbin-XUbuntu.

Do not use mixed case in hostname. bigbin-xubuntu would be fine.  Sure, it should work and it might most of the time, but every script, written by every programmer, on every team has to take extra steps to ensure comparisons work correctly. hostnames and DNS names are all supposed to be case-insensitive, but there isn't any way to enforce Joey - programmer just learning php - to do that.  Avoid this issue.

> **Phil Binner said:**
> Installed a hard drive and formatted it as Ext4 named Vol10
"names" are unclear. What exactly do you mean?  Also, file systems shouldn't be put directly onto hard drives. There should be a partition table, then a partition created, then a file system, ext4, would be placed onto that partition.  Never put a file system directly onto a non-partitioned drive.  BTW, the tools will allow this, but it is a really, really, really, really, bad idea.  People tend to do it when they are setting up RAID systems. There are reasons never to do it for RAID configs too.  Always partition HDDs. Always.  
Multiple partitions are possible.  So, the partition can have a "LABEL" - is that what you mean by "name"?  It matters  if the LABEL is used in the mounting configuration or not.  For ext4, internal storage, we usually would use the UUID for the partition in the mount, but if you are careful to always have a unique LABEL, that can be used instead. If you didn't LABEL it during the format creation, I think you can add a label later. I'd use **gparted** for that.  For simple storage setups, gparted is my go-to tool. Unfortunately, it doesn't support more advanced storage management, just simple partitioning, simple formatting, simple labels and partition bits.

> **Phil Binner said:**
> 
in a terminal, run the command    sudo apt install samba nfs-kernal-server
I'd have to check if that was sufficient. The link above from Sensei has the commands to run.  You can also check the Ubuntu Server Guide for the distro/release you are running. There will be a how-to for samba and a how-to for NFS in the Ubuntu Server Guide.  Server stuff is in the Server guide.  Desktop stuff is in the Desktop Guide.

> **Phil Binner said:**
> 
Loaded Ubuntu 18.04 onto an I5 laptop.  This machine is called firstmedion
Why using 18.04?  If you don't have a specific reason, today it is probably best to start with 20.04. Both have 5 yr support periods, but 18.04 has already used 2 yrs of that 5.  I like to avoid having to reinstall a fresh OS every few years.  4-5 yrs is long enough to get good use from an install, but not so long as to make me afraid to migrate to newer.  For me, it is about avoiding hassles for as long as possible.  My NFS and Plex server runs 16.04.  When I move it to the next release in the next few months, it will be 20.04, probably.

> **Phil Binner said:**
> 
In Bigbin-XUbuntu, edited /etc/exports to add the line       /Vol10      firstmedion(rw,async,root_squash)
Ok, but you didn't mount /Vol10 in bigbin-xubuntu's fstab. Can't export storage that isn't mounted on the NFS server.

**Mount the partition using the fstab on bigbin-xubuntu.**  Look at the existing fstab lines. You need something like that, but with slight changes.  The UUID will be different. Use **blkid** to find the correct UUID.  The last number on the line needs to be a 1 for non-OS, internal storage. This tells it to run the fsck from time to time during boot. I think the default is every 30 or 60 days, but I don't recall exactly. The file system configuration controls how often. That is something for another day.
After the fstab is done, use **sudo mount -a** to mount it. That looks through the fstab and if there are any new lines for storage that hasn't been already mounted, it mounts each.
Search for "ubuntu fstab" for a how-to guide.  On bigbin-xubuntu, mounting Vol10 on to /Vol10 is just like mounting any other local storage.

> **Phil Binner said:**
> 
Logged onto the router to find that the IP address of Bigbin-Xubuntu is 192.168.1.168.  Make that address fixed.

DHCP has a range of addresses in your router.  Static IPs need to be outside that range. Fix that.  I use .1 - .100 for LAN static IPs. I use .101 - .200 for VPN IPs and I use .201-.250 for DHCP guests.  All my portable devices use DHCP, but with DHCP reservations so they effectively get static IPs .... in the .1-.100 range.  My LAN DNS server knows about these systems, by-name.

> **Phil Binner said:**
> 
In a terminal run the command     sudo systemctl start nfs-kernel-server 
But you haven't mounted the storage to be shared?  edit the fstab, run **sudo mount -a** to mount it.
After you start the nfs daemon, you need to tell it to read the modified exports file - **sudo exportfs -a**.

> **Phil Binner said:**
> 
In firstmedion, edit /etc/fstab  to add the line     /Vol10    192.168.1.168/24(rw,async,root_squash)
re-boot firstmedion
That isn't a correct fstab entry.  

On first glance, it looks like an *exports* file line.  You are getting confused between the fstab and exports.  They are very different.

192.168.1.168/24 is probably incorrect even in an exports file. You if you want to export to the entire subnet, use 
192.168.1.0/24.  _But this doesn't go into the fstab!_ It won't work there.

When you look at the existing fstab lines, yours needs to look like that both on the NFS server and on the NFS client.  
On the NFS server, the new ext4 partition needs to be mounted just like the other ext4 partitions inside there.
On the NFS client, the new NFS needs to point to the NFS server (by name or IP) with the exported directory name and the 'type' column needs to say 'nfs'.  This is normal for client/server architecture.

[LIST]
[*]/etc/fstab is how storage (local and nfs and cifs and ... lots of other types) is mounted to the local machine.
[*]/etc/exports is read by the nfs-server to know which available storage to be shared via NFS to the machines listed.
[/LIST]

The format of the nfs-client machine /etc/fstab is this: 
```
example.hostname.com:/srv /opt/example nfs timeo=14,proto=tcp,intr,rw,async
```
So you should use something like this:
```
bigbin-xubuntu:/Vol10  /Vol10  nfs timeo=14,proto=tcp,intr,rw,async
```
The /Vol10 directory must pre-exist. This is called a "Mount Point", but it is really just an empty directory for a storage device (local or remote) to be hooked into some other, existing, file system, that is already mounted.
I use /d/D1 and /d/D2 and /d/D3 for my storage stuff.  Because I use enterprise-LVM to manage storage, I don't want to post the 'df' output since that can be confusing since it uses different device names.

> **Phil Binner said:**
> 
firstmedion will not reboot properly.  The first two lines of the error screen reads:

/dev/sda2:   clean,  179554/15597568 files,  3308911/62383360 blocks
emergency mode.

Entering my password gets to the command prompt, but I am not able to edit /etc/fstab  to comment out the line I added.

Of course they won't.  The NFS server was told to share storage that hasn't been mounted.
As for the command prompt, I bet it is a trivial thing that you aren't seeing.
A prompt with a '$' means that is a normal userid.
A prompt with a '#' means that is a root prompt.
```
tf@regulus:/etc$ 
```
[LIST]
[*]tf is my username.
[*]regulus is the hostname.
[*]/etc is the current working directory. This is exactly like on Windows.
[*]$ says - I'm not root.
[/LIST]
It turns out that prompt is exactly the information that scp, rsync, sftp need for transferring files TO/FROM systems. It is brilliant that I can **select** it into a command with 1 left dbl-mouse click, then paste it using a center mouse click in any window I have open. Freakin' amazing.

Anyway, I don't have enough information to provide the correct fstab line for either machine.  Run **blkid** on the machine with the new partition (formatted to ext4) and then we can do the fstab.  BTW, your system has reference manuals on it about all this stuff in the form of manpages.  **man fstab** and **man exports**.

> **Phil Binner said:**
> 
Interestingly, when I ran the command   sudo systemctl start nfs-kernel-server in Bigbin-Xubuntu nothing happened.  It just went back to the command prompt.
Unix has a philosophy - if it did what you asked, don't return anything. Be silent on success. However, complain loudly on failure.

I fear we/you have made this 100x harder than it needed to be.  

BTW, usernames should be all lower-case too for the same reason as hostnames should be all lower-case plus there are historical reasons from back when Unix terminals didn't support lower-case at all.  Doing things a certain way to avoid future problems is one of those things Unix admins learn over years of practice.

And 1 more experience thing - never edit a config file and remove the last empty line.  Always have 1 empty line at the bottom of every config file.  This is another historical thing.  An end-of-line character isn't the same as an end-of-file character. Some programmers use the EoL to know that a record has been read. If they get to an EoF instead, then that last record/setting won't be seen.  Again, Joey may not have been told this and his personal habit is to always leave 1 or more empty lines at the bottom of files, so it never impacts him. There is still some code that was written in 1970 being used on Unix systems today, so this issue still comes up from time to time.  fstab?  exports?  Got an extra line at the end?

Unix admins have always been expected to be power-users of the OS as a minimal entry point. This makes is hard for people forced to learn everything at once.

Hope I didn't ramble too much.

---

### Post by SeijiSensei on 2020-11-28
> **Phil Binner said:**
> The thing that stops the client booting is the line

/Vol10   192.168.1.168(rw,async,root_squash)     in fstab.   I have loaded Ubuntu twice now, and it initially boots OK, then fails to boot when that line is added.
As TheFu says, you're mixing up the entries in the file /etc/exports on the server (which look like the line above), and the entries in /etc/fstab which have a different syntax.

I always use no_root_squash which lets me mount the exported shares to directories owned by root. Then I let the ordinary authentication systems on the client determine access to the exported shares. In this model, both the server and clients have to have the same user and group IDs in /etc/passwd. In my example above, if I create a mount point as root, then mount the share to it, each user can access his or her directory on the server as long as the IDs match.

To see what might be going wrong, mount the remote NFS filesystem manually with the "mount" command and use the "-v" switch to get verbose results.

```
sudo mount -v server:/share /mnt/point
```

---

### Post by Phil Binner on 2020-11-28
Thank you.  I'm aware this must be difficult for you, talking to someone who knows absolutely nothing.  A lot of problems for people like me arise from philosophy and arcane language.  By philosophy I mean the set of ideas a particular system is based on.  Once you understand them it's difficult to imagine that someone else doesn't.  And as to arcane language, by that I mean that when someone is familiar with the language of their specialty it is easy to forget that in their subset of language words tend to take on additional meaning that they do not necessarily have outside.  And documentation can be very difficult to read, because when people are about to write documentation they tend to ask themselves "what would I like to find here?", rather than "who is going to read this and what would they like to find here?".

That last post is incredibly useful.  Some of it I understand, and some I don't.  Ill go through it again and address things one at a time as they have been presented.

First thing - FAT.  I used FAT because I format disks using the Gnome Disk utility.  It says NTFS is for Windows, Ext4 is for Linux, and FAT is for any system.  Because this server needs to be available for Windows and Linux machines I used FAT.  I was thinking about Windows machines reading it directly, as if it was a removable hard drive that can be connected to either system.  Obviously that is not the case.  It will be permanently mounted inside an Ubuntu server.  I will not make that mistake again.

Second, I loaded XUbuntu 18.04 onto an I5 desktop machine. This machine is called Bigbin-Xubuntu.  Is there any way to change that name without re-installing.  I’d like to get the little problems out of the way, so if I have to re-install I will.  This is all in the sandbox.

Third, I formatted the hard drive as Ext4.  What I actually did was to use the Gnome Disks utility to  remove all partitions from the hard drive then add a new partition.  I called that partition Vol10 and said the format was Ext4.  I did not do an aggressive format.  This disk was originally a boot disk in a windows system, so the partition table would have been created by the windows installer.  Should I have been more fundamental.

Fourth, I got the  command “sudo apt install samba nfs-kernal-server” from SeijiSensei’s post.  I will have to address samba later, but for now I just want to get NFS working.  Would I be best with just “sudo apt install  nfs-kernal-server”.

Fifth, I loaded Ubuntu 18.04 onto the client.  The client is essentially temporary, but in it’s temporary use it may require access to the D-Link NAS, which is SMB1.  I don’t want to have to configure Samba for this purpose.  I’ll address that problem later.

Sixth,  I think I am now getting to where the real problem is.  I have looked up the mount command and it’s clear I need to understand  lots more things before I understand that.  Also, the command seems to be different in fstab than at the command prompt.  On the other hand, if I double click the Vol10 icon on the desktop it get’s mounted, without asking for anything else.  Do I need anything more than   “/Vol10”  in fstab.

I think that’s the next problem I have to solve, so for now I’m going to leave it at that.  Think I can see why the client machine was refusing to beet, however, so I may not be too far away.

Thanks again.  I do hope you’re not getting too frustrated.

Have a good day.

---

### Post by TheFu on 2020-11-28
> **Phil Binner said:**
>  
That last post is incredibly useful.  Some of it I understand, and some I don't.  Ill go through it again and address things one at a time as they have been presented.

First thing - FAT. 

You've got the understanding for FAT. File systems are all about where they will physically be connected.  Maybe want to skip using Gnome-Disks.  That program has a fairly dumb interface in the Gnone team attempt to over-simplify stuff. It has bugs and lies.

> **Phil Binner said:**
>  Second, I loaded XUbuntu 18.04 onto an I5 desktop machine. This machine is called Bigbin-Xubuntu.  Is there any way to change that name without re-installing.  I’d like to get the little problems out of the way, so if I have to re-install I will.  This is all in the sandbox.
Yes, changing the hostname isn't hard - basically 3 things ... plus any were you've pointed to the hostname in config files and from other systems.  Again, in theory, case shouldn't matter ... until it does.  

Make your life easier now by using all lower-case everywhere.  Most things on Unix are case sensitive - files, directories, programs, options for programs ... but hostnames and FQDN shouldn't matter.

> **Phil Binner said:**
>  Third, I formatted the hard drive as Ext4.  What I actually did was to use the Gnome Disks utility to  remove all partitions from the hard drive then add a new partition.  I called that partition Vol10 and said the format was Ext4.  I did not do an aggressive format.  This disk was originally a boot disk in a windows system, so the partition table would have been created by the windows installer.  Should I have been more fundamental.
That should be fine.

> **Phil Binner said:**
>  Fourth, I got the  command “sudo apt install samba nfs-kernal-server” from SeijiSensei’s post.  I will have to address samba later, but for now I just want to get NFS working.  Would I be best with just “sudo apt install  nfs-kernal-server”.
Installing 1, 5, 50 things on the same *sudo apt install .... * command is fine, assuming the system has been maintained.  A link for later: [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

> **Phil Binner said:**
>  Fifth, I loaded Ubuntu 18.04 onto the client.  The client is essentially temporary, but in it’s temporary use it may require access to the D-Link NAS, which is SMB1.  I don’t want to have to configure Samba for this purpose.  I’ll address that problem later.
Not an issue, provided you understood the remaining support period.  Accessing SMB1 shares will need some non-default settings.  Look through Morbius1's posts here for that. Every time I think I understand, there's a new-to-me caveat, so I've decided it is best to avoid helping with Samba connections. I've only been using samba since around 1995 and only had an issue this last summer that took a few weeks to figure out. Never had issues before, but I don't have any SMB1 stuff.

> **Phil Binner said:**
>  Sixth,  I think I am now getting to where the real problem is.  I have looked up the mount command and it’s clear I need to understand  lots more things before I understand that.  Also, the command seems to be different in fstab than at the command prompt.  On the other hand, if I double click the Vol10 icon on the desktop it get’s mounted, without asking for anything else.  Do I need anything more than   “/Vol10”  in fstab.
Yes.  You must specify the "device".  That is either using the UUID or the LABEL or directly using the device file (this last one is dangerous, since device files move around).
To get the UUID, run **blkid** command and trace the storage you call "/Vol10" back to a UUID. That should be used in the 1 fstab line on the server system.  1 line is all that is needed in each computer fstab.

> **Phil Binner said:**
>  I think that’s the next problem I have to solve, so for now I’m going to leave it at that.  Think I can see why the client machine was refusing to beet, however, so I may not be too far away.
"beet?"
You've never been more than 10 lines total away.  3 in config files (server fstab, server experts, client fstab) and perhaps 5-7 commands to be run between the two systems.

> **Phil Binner said:**
>  Thanks again.  I do hope you’re not getting too frustrated.

Have a good day.

One more "mentoring" tidbit.  When you edit system files, the safest way for almost all of them is to use **sudoedit /etc/fstab**.  There are a few exceptions, like to modify the sudoers and the passwd file - those both have special commands just for each which do some extra validation and attempt to prevent bogus configurations in those specific files. sudoedit supports using any editor you like. That is controlled by the EDITOR environment variable. Save this for later too. ;)

---

### Post by Phil Binner on 2020-11-28
Ive taken a couple of steps forward, but not totally successful.  I've followed up on the last set of instructions and read up on changing the host name and the structure of fstab.  Consequently the computer is now called bigbin-xubuntu, and stays that way after re-boot.  The command in fstab is now 

UUID=cf560714-4c5b-47d9-9765-08638b617ff4  /Vol10  ext4   rw,async  0  0

Unfortunately since I set this Vol10 no longer has an icon on my desktop, and does not seem to be available for me to use.  It's the middle of the night now, though, so I'm off to bed.

Sweet dreams

---

### Post by TheFu on 2020-11-28
> **Phil Binner said:**
> Ive taken a couple of steps forward, but not totally successful.  I've followed up on the last set of instructions and read up on changing the host name and the structure of fstab.  Consequently the computer is now called bigbin-xubuntu, and stays that way after re-boot.  The command in fstab is now 

UUID=cf560714-4c5b-47d9-9765-08638b617ff4  /Vol10  ext4   rw,async  0  0

Unfortunately since I set this Vol10 no longer has an icon on my desktop, and does not seem to be available for me to use.  It's the middle of the night now, though, so I'm off to bed.

Sweet dreams

Cool that you changed the hostname, but I would have done that in a week or two. ;)  A quick win is sometimes needed, so I understand the reason you wanted to do it sooner than later.

When you mount storage in the fstab, it is available.  Just make a shortcut/bookmark to that location in your file manager. You can also use **symbolic links**. Wikipedia has an explanation.  Hard-links are less useful than symlinks (aka soft-links aka symbolic links).  Symlinks can cross file systems.  Hard-links cannot.  Symlinks work over NFS too, BTW. ;)

You can check that it is mounted a few different ways. Some commands:
```
df -Th
mount
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

In a terminal, just **cd /Vol10**   what's there?  

BTW, assuming the UUID is correct, then this is probably the fstab line you want:
```
UUID=cf560714-4c5b-47d9-9765-08638b617ff4     /Vol10      ext4      noatime,errors=remount-ro    0     2 
```
What this does is tell the systemd-mount program to run fsck automatically from time to time, but even if that doesn't work, then you still want the file system mounted as read-only if that is possible.  Not having the file system keep track of the access times (noatime) will speed things up slightly and for SSD storage, it will drastically drop the writes.  

Every file/directory has 3 time related fields.
[LIST=1]
[*]Creation time (ctime)
[*]Modification time (mtime)
[*]Access time (atime)
[/LIST]
Knowing when a file was created and last modified is important.  Just because some random program read/accessed a file, that isn't really noteworthy.

Now that you have the storage mounted under /Vol10, you probably want to change the owner from root:root, to whatever your username:groupname are.  **sudo chown -R $USER:$USER** /Vol10 will do that and you'll be able to add files, directories and manage that storage however you like going forward since you are the owner. This is a 1-time chown command.  This is all native Unix file and directory permissions. These work over NFS exactly the same way, unlike CIFS which behaves differently whether you are remote or local.

Life is good.

If you have 5 other userids that need to only read the files, that is easy to setup.  If you have 3 other userids that need read-write to specific directories, that is possible, but you'll need to learn Unix permissions.  Here's a post about that:
[https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp](https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp)  These things are also 1-time setup things for each directory where a team needs to work together on the same files.  With Unix permissions, you'll get it and have it the rest of your life.  Since this is the way that permissions work on all popular OSes, except 1 (cough), this knowledge is useful everywhere - phones, tablets, TV devices, computers.

BTW, when Unix people are forced onto Windows, they have similar struggles. Things that appear the same are not implemented in the same way deep in the OS. Only about 20% are the same with Windows and all the Unix-based OSes.  

Ever wondered why websites are partially case sensitive in the URL?  The domainname is not (like a hostname), but everything else is?  That's because they run on Unix systems where file structures are case-sensitive.

You may notice I've been adding a few new Unix ideas with each post. There are many little things that Unix has had for 40 yrs that Windows either doesn't support or that just aren't used in Windows.

More football to watch.

Tomorrow, the client fstab with NFS inside?

---

### Post by Phil Binner on 2020-11-29
Why "remount-ro".  I always want read/write access to this volume.  Is there something I'm missing here.

---

### Post by Phil Binner on 2020-11-29
Just noticed I'm now Frothy Coffee.  Actually, not sure these beans are roasted yet.

Anyway, Vol 10 is mounted and I have a link on the desktop.

On the client side I have installed nfs-common.   I have edited the fstab with the line:

192.168.1.168/Vol10    /Vol10     nfs   proto-tcp,noauto   0   2

Unfortunately Vol10 is not getting mounted.  I have searched for it in Files, and tried to CD into it in the terminal.  No such file or directory.

So where do I go next.

---

### Post by TheFu on 2020-11-29
> **Phil Binner said:**
> Why "remount-ro".  I always want read/write access to this volume.  Is there something I'm missing here.

The option is "errors=remount-ro" - so if there is an error, then try to mount it as read-only.  That's handy if a file system has been corrupted for some reason.  At least then you can update a new backup set of the data, though it would be best to have daily, automatic, versioned, backups already.

BTW, these options are documented in the manpages.  With mounts, the manpages to check are for the fstab, mount and specific mount command like mount.ext3 or mount.xfs or mount.nfs4 or mount.vfat or mount.cifs or mount.ext4 manpages. Lots of useful information.  Not all file systems support each option, so beware. Sometimes mount programs get reworked, so options are in the main 'mount' manpage.

The main mount manpage has this:
```
       errors={continue|remount-ro|panic}
              Define  the  behavior when an error is encountered.
              (Either ignore errors and just mark the  filesystem
              erroneous  and  continue, or remount the filesystem
              read-only, or panic  and  halt  the  system.)   The
              default  is  set  in the filesystem superblock, and
              can be changed using tune2fs(8).
```

If there are file system errors and you force a continue, it is highly likely that choice will create more and more and more file system errors. The only thing worse than no data is bad data, yes?

---

### Post by TheFu on 2020-11-29
> **Phil Binner said:**
> Just noticed I'm now Frothy Coffee.  Actually, not sure these beans are roasted yet.

Anyway, Vol 10 is mounted and I have a link on the desktop.

On the client side I have installed nfs-common.   I have edited the fstab with the line:

192.168.1.168/Vol10    /Vol10     nfs   proto-tcp,noauto   0   2

Unfortunately Vol10 is not getting mounted.  I have searched for it in Files, and tried to CD into it in the terminal.  No such file or directory.

So where do I go next.

Dude, that's incorrect.  Details matter to computers.
```
 192.168.1.168/Vol10 /Vol10 nfs proto-tcp,noauto 0 2
```
My example was:
```
bigbin-xubuntu:/Vol10  /Vol10  nfs timeo=14,proto=tcp,intr,rw,async
```
So - what is different in your line and mine? Details matter. Guess I'm not trustworthy?

---

### Post by SeijiSensei on 2020-11-29
I wouldn't bother with "proto=tcp" in the /etc/fstab entry.  I've used the default UDP on all my servers, and they work just fine. It also has slightly better performance than using TCP which requires the client to send an upstream "acknowledgement" packet to the server in response to every packet it sends.  UDP just blasts the data out over the network.  If you were connecting from a remote location where connectivity might be spotty, you would use TCP.  (Many services like HTTP and email use TCP for this reason.) But for connections over your own local network, UDP is fine.

I'd start with just using "defaults" in the options section like this:

```
192.168.1.168/Vol10 /Vol10 nfs defaults 0 2
```

---

### Post by TheFu on 2020-11-29
```
192.168.1.168/Vol10 /Vol10 nfs defaults 0 2
```
is incorrect. Missing a ":"

The last 2 numbers are dubious as well.  Backups and running fsck?  Those need to happen on the NFS server via the local device mount, not over NFS. I doubt fsck works over nfs at all. I doubt any harm will come from having them and I use those from time to time too.  But the more I think about it, perhaps the "reasonable defaults" provided by systemd.mount for NFS are fine.  I actually don't use fstab to mount NFS stuff.  

As for TCP - for 100 base-tx **and faster** connections, it has been recommended for a long time. NFSv4 requires TCP.
> All versions of NFS can use Transmission Control Protocol (TCP) running over an IP network, with NFSv4 requiring it. NFSv2 and NFSv3 can use the User Datagram Protocol (UDP) running over an IP network to provide a stateless network connection between the client and server. 
...
NFSv4 has no interaction with portmapper, rpc.mountd, rpc.lockd, and rpc.statd, since they have been rolled into the kernel. NFSv4 listens on the well known TCP port 2049
....
UDP can be used for compatibility purposes as needed, but is not recommended for wide usage. 

NFSv4 has been production ready for 15 yrs. We really should use it.
Additionally, NFSv4 brings some other desirable capabilities.
But yes, NFSv3 and UDP will still work on solid connections.
The mount options used by any mount type can be seen with just a plain 'mount' command.

---

### Post by Phil Binner on 2020-11-30
OK guys, It's clear the two of you have differences in approach.  There are no trust issues; I'm certain either of you would have smashed this in minutes if you were sitting here in front of it rather than operating me by remote. Making choices in these areas is way above my pay grade.

What I have done in the server machine is to mount Vol10.  I know it is successfully mounted.  I think I have also started nfs-kernal-server, but I do not have confirmation of that.

On the client side I have installed nfs-common, and I have edited fstab to add the line    "bigbin-xubuntu:/Vol10  /Vol10  nfs timeo=14,proto=tcp,intr,rw,async  0  2".  I've also tried it as     "192.168.1.168:/Vol10  /Vol10  nfs timeo=14,proto=tcp,intr,rw,async  0  2",  restarting each time.  From reading your posts it seems that you both think that that should work.

I have also tried running the command sudo systemctl start nfs-common,   in case the problem is that nfs is not running on the client.  This failes with the message  "Failed to start nfs-common.service: Unit nfs-common.service is masked."

So far the client cannot see Vol10, and doesn't have it mounted.

---

### Post by Phil Binner on 2020-11-30
For sake of completeness I also tried editing the client fstab so the line reads  "bigbin-xubuntu:/Vol10 /Vol10 nfs defaults 0 2"

There is now a Vol10 in the file structure which I can cd into, but it is empty - i.e. it does not contain a directory called newdir, which it would if it was seeing Vol10 on the server. 

From this I deduce one of two things:

1.   This is not the Vol10 on the Server, but one that has been created on the local machine.
2.   I need an account to access it.

It is not asking me for any account detailos,  and opening the volume shows it to be empty.

---

### Post by LHammonds on 2020-11-30
For mount points, I like to create an "offline.txt" file in there so that when the mount is successful, you do NOT see the text file.  But if you do, you know the mount is "offline" hehehe.

LHammonds

---

### Post by TheFu on 2020-11-30
I wrote a too-long reply then, just prior to posting, closed the browser. Ouch.
I'll try to be more concise, for my personal sanity.

Check real storage mounts on any system using 
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
Most of that command is options to prevent non-storage stuff from being displayed. We only care about real storage.

Check nfs exports on the nfs-server using.
```
showmount -e
```

If you change anything in the /etc/exports file, you need to restart the nfs-server, do that with
```
sudo service nfs-server restart
```
We all forget to do that sometimes. To get the current status, use
```
sudo service nfs-server status
```
Log files and errors can be checked in many different ways, but **journalctl  -xe ** is usually the easiest.

If you change an /etc/fstab line, you'll need to un-mount the file system, then mount it again. It works for all storage, local or NFS.
```
sudo umount /Vol10
sudo mount -a
```

NFS will not ask you for credentials to mount anything. It isn't an end-user mount system. It is computer-to-computer.

LHammonds has a good tip with the empty file so you'll know if the mount happened. It is easy to programmatically check in a script as well.
SeijiSensei has good ideas too.  The differences are from our different experiences and different work environments.
All of us have lots and lots of experience and long histories here trying to help people. None of us has all the answers. We all make mistakes.  The first time we each setup NFS, you can bet we struggled a little too.

With Unix, there is almost always 50-500 different ways to accomplish the same thing. The days of 1-right-answer seldom exist on Unix systems.

On the NFS server, you'll probably want to make your userid the owner of /Vol10 and any subdirectories after it is mounted there. This will carry over to NFS clients with that userid as the owner. My _NFS tips_ above tried to explain the relationship between the userids on each system. If there are issues - like different names are seen on different systems, then you'll want to post the 'id' command output for each userid on each client system.  With only 1 client system, there won't be issues.

---

### Post by SeijiSensei on 2020-11-30
Try to mount the share manually with 
```
sudo mount -v bigbin-xubuntu:/Vol10 /Vol10
```
The "-v" switch means "verbose." You may see where the problem lies.

Sorry I missed the absent colon in my earlier post.

---

### Post by Phil Binner on 2020-12-02
A hearty thank you to all.  

Just prior to getting these posts I tried an experiment turning both machines off and then only turning the client on.  The file Vol10 was still there in the files list.  But now hen I try to restart the server it goes into emergency mode.  I typed journalctl -xb,  but there was pages of output.  I think I need to get to the fstab file to comment out my last entry.  I can get to the root command prompt and cd  into ect  -  root@bigbin-xubuntu:/etc#  but attempting to edit fstab results in 
"unable to init server: could not connect; connection refused".

Unfortunately I have to leave this for now.  If all goes well I will have a short spell tomorrow afternoon and a whole day at it on Friday.  There is a journal file I kept on this machine that I should have saved elsewhere but didn't, so I hope I'm going to be able to get back in.

---

### Post by Phil Binner on 2020-12-02
Couple more things. 

First, I don't understand "offline text file". I would presume write a text file in the shared directory so it's obvious if it's loaded, but then you'd see it if its mounted and not if it isn't.  This sounds a good idea, but can I have a bit more detail please.

Second, if i cant't get back into the server I'll have to start again.  Not such a big deal, this is the sandbox.  Things that have happened mean that this machine is destined te become a full time server, rather than a workstation with server modules added.  Would now be a good time to do it.  If I install Ubuntu server will the rest of the setup be very different.  I intend to do this eventually, but it will only be now if I have to re-install the software anyway.

---

### Post by TheFu on 2020-12-02
Ubuntu Server doesn't have a GUI. That makes it more stable. GPU drivers have always sucked a bit on Linux - more so recently.

If you have another workstation and can ssh into the server system using it, which is how Unix admins have worked for 40+ yrs, great.

---

### Post by LHammonds on 2020-12-03
> **Phil Binner said:**
> First, I don't understand "offline text file". I would presume write a text file in the shared directory so it's obvious if it's loaded, but then you'd see it if its mounted and not if it isn't.  This sounds a good idea, but can I have a bit more detail please.

Assuming /Vol10 is your mount point and the mount point NOT mounted, run these commands:

```
sudo echo "This file is used to tell if the mount is active or not" > /Vol10/offline.txt
sudo chown root:root /Vol10/offline.txt
sudo chmod 0444 /Vol10/offline.txt
```

When you type "ls /Vol10" and see "/Vol10/offline.txt" then you know it is not mounted.
After you issue the mount command, do the list again and if you no longer see the offline text file, then the mount worked.
If at any point after the volume is mounted that you ever see the offline file, that will be a clear indicator that it is dismounted (besides the fact that your files are gone...but at least this will let you know it is dismounted rather than deleted).

It seems you plan to have it mounted all the time so something like this will help let you know if it stops working.

Most of the mounts I have used were always temporary so I wrote a script to toggle it on or off.  When run, the script would check if the offline file is there...if so, I mounted the share.  If not, I dismounted the share...which effectively acted like a toggle without me specifying if it should be mounted or not.

LHammonds

---

### Post by Phil Binner on 2020-12-03
Offline text is going to be usefull.  Thanks.

---

### Post by Phil Binner on 2020-12-03
The machine that is now my server used to be the main Linux workstation. At the beginning of this I bought a decent second hand motherboard and I7 processor.  I just havent had time to put it in it's case.  With a bit of luck, and assuming I can work out the f-panel connections without a manual, I should have a new workstation by the end of tomorrow. 

It sounds as if there are other questions to answer if I go fully into the server route, however, so in the interest of "one thing at once" I'll hold off that for now.

How will I go about getting into bigbin-xubuntu without re-installing everything.  It's currently stuck at the root command prompt in emergency mode.

---

### Post by TheFu on 2020-12-03
If you have root, then you own the box and can do anything. Undo whatever you did to break it.

If you don't know what you did to break it, but think it is related to some userid settings, just move those settings somewhere else.
```
mv ~/.config ~/.config-old
```
logout, login again. Simple.

If you don't know which settings you modified to break it, just create a new userid with a new HOME directory, being careful to get the groups just like they were for the other userid that you broke, especially the sudo and adm groups.  There are two different commands for creating a new userid. I never remember which does everything (creating a HOME, copying in skel files, etc.) and which is low-level  useradd or adduser.  I always have to check the manpage.  These commands are ubuntu only, I think. Other distros have slightly different versions, so read the manpage ... or use the GUI admin tool, if you have one.  Double-check the groups.

If you don't know how to accomplish these things - [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good beginner-level book.

---

### Post by hk42 on 2020-12-03
Thanks all for this very informative topic.

---

### Post by Phil Binner on 2020-12-08
Hello again

I seem to have gone a long way to get back to where I was a week ago.  Basically, I failed to get control of bigbin-xubuntu, so I rebuilt it as a work station.  That is what it was always destined to be anyway.

I built a new machine to be the server.  This is still an XUbuntu machine.  It is called serverbot, and it now contains the disk with the partition Vol10.  On serverbot I:

ran "sudo apt install nfs-kernel-server"
ran "sudo systemctl start nfs-kernel-server"
edited fstab with the line "UUID=cf560714-4c5b-47d9-9765-08638b617ff4    /Vol10    ext4   noatime,errors=remount-ro    0     2"
edited exports with the line "/Vol10  bigbin-xubuntu(rw,root_squash,async)"

Following this I went to the client. There I:

ran "sudo apt install nfs-common"
edited fstab with the line "192.168.1.91:/Vol10 Vol10 nfs defaults 0 2"

Again, Vol10 exists in the File System browser, but it is empty.  Browsing the network makes Serverbot visible, but the only thing in it is the print share.

Should I being doing something to start nfs-common,  I tried

sudo systemctl start nfs-common

but this command failed.

---

### Post by SeijiSensei on 2020-12-08
nfs-common just provides the infrastructure needed to run NFS.

What do you see with
```
sudo mount -v 192.168.1.91:/Vol10 /Vol10
```

---

### Post by TheFu on 2020-12-08
On the client .... 
edited fstab with the line 
```
192.168.1.91:/Vol10 Vol10 nfs defaults 0 2
```
is incorrect. A **/Vol10** is missing.  Details matter. Computers do what we tell them.

If you insist on staying with what you have AND , 192.168.1.91 is the correct NFS-server static IP, 
```
192.168.1.91:/Vol10   /Vol10    nfs     defaults 0 2
```
would be the client-side fstab.

In post #7 above, I provided a number of correct lines, and attempted to be clear as to where those lines and commands needed to happen. 

Also, if you did a fresh install, the UUID could have changed, so you'll need to check that. There are commands above, which try to explain what they are for and how they check stuff, you can/should run.  When you build a car engine, do you wait until after the final wash+wax job to try the key and turn the engine over?  I hope not.  That makes for confusion and lots of rework. It makes troubleshooting 1 tiny issue into troubleshooting every step, hoping nobody missed anything else along the way.

Do a little, check it.
Do a little more, check it.
Do a little more, check that.

SeijiSensei's command:
```
sudo mount -v 192.168.1.91:/Vol10 /Vol10
```
will validate everything upto the client-side fstab line.

---

### Post by Phil Binner on 2020-12-08
Thank you for persisting.  I missed out a "/"  in my post, but  I checked fstab and the  "/" is there in the real thing.  I'm sorry if I'm misinterpreting instructions, but three forms were given originally and that is the one which seemed nearest.  I'll try the others again tomorrow.  Unfortunately the journal file I was keeping on the first version was one of the things I lost.  That was strange, because I copied it into Vol10 using the cp command, and then checked the driectory of Vol10 before physically moving the disk to the new machine, but the file was not there after re-mount.

192.168.1.91 is the fixed address of the server.

I did check the UUID for the new server.

sudo mount   -v   192.168.1.91:/Vol10    /Vol10  returns

mount.nfs: timeout set for Tue Dec  8 22:20:10 2020
mount.nfs: trying text-based options 'vers=4.2,addr=192.168.1.91,clientaddr=192.168.1.168'
mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting 192.168.1.91:/Vol10

---

### Post by TheFu on 2020-12-08
Whenever posting configs, aren't you just copy/pasting everything?

Did the client IP address change? 
Does your LAN DNS know about that change?
If not, then inside the /etc/exports file, don't use the hostname, use the static IP for the client.

There are lots of moving parts in this setup.  Because the first thing I do with any new install is force a specific, static, IP and update the LAN DNS, those things don't enter my mind, but they are necessary to have a "well-managed" network.  IMHO.

It would be helpful if you used 'code tags', like we've been using.

---

### Post by Phil Binner on 2020-12-08
I usually copy and paste, but I'm switching between machines on 3 different desks.  I set the server to a fixed IP - 192.168.1.91.  This is what it had been allocated; I just set it to fixed.  The client is not fixed, but I checked the name.  One of tomorrows tasks could be to fix the client's IP and use that.

I'm not familiar with "code tags".  I just looked them up and was presented with information on ctags and etags commands.  But as usual, no conceptual context to make sense of it, just that thay are a kind of text editor accross "Unix like systems".  If it is simple and you can explain a little more I will try to use them.

Did the output from "sudo mount -v 192.168.1.91:/Vol10 /Vol10"  help at all.

---

### Post by SeijiSensei on 2020-12-08
> **Phil Binner said:**
> Did the output from "sudo mount -v 192.168.1.91:/Vol10 /Vol10"  help at all.

Let's see the /etc/exports file from the server.

"Code tags" are a feature of most forum software. If you embed text within [noparse]```

```[/noparse] tags, it will display like this
```
Text inside code tags
```

For instance entering the text

[noparse]```
sudo mount -v 192.168.1.91:/Vol10 /Vol10
```[/noparse]

displays as
```
sudo mount -v 192.168.1.91:/Vol10 /Vol10
```

---

### Post by TheFu on 2020-12-08
There are 2 reasons for code tags n these forums:
* to show terminal commands + output clearly; fixed width fonts are used.
* to retain spacing from the terminal - columns line up - makes output readable for us who are used to seeing it that way.

I'm sorry I wasn't clear.

If you want to use machine names in NFS, then each machine needs to be able to ping the other using the name. If in doubt, use the IP address instead. These are network protocols.

---

### Post by Phil Binner on 2020-12-09
Positive progress today.  I now have a server, serverbot, with Vol10 mounted and shared, and I have two clients, firstmedion and bigbin-xubuntu, that have read write access.

Lines in /etc/exports was 

```
/Vol10  192.168.1.168(rw,root_squash,async)
/Vol10  192.168.1.83(rw,root_squash,async)
```

I need to save this as a test to see if I understood about code tags.

---

### Post by Phil Binner on 2020-12-09
Obviously I did not understand about code tags.  Nevermind.

I would be very grateful if one of you would explain exactly what I should do and when I should do it (e.g. in a post? in a terminal? etc.).  I will then comply.  Clearly what I did in the previous post was nor what you meant.  What I had been hoping would happen was that the forum would detect [code]....[code]

Arcane language has always been difficult.

---

### Post by TheFu on 2020-12-09
BBcode .... and code tags.  I think you are missing the '/' in the 2nd tag.  
[https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

There is an open and a close.  It works just like the "bold-tags" or "quote-tags" ... just with 'code' replacing the 'b' or the 'quote' letters.

But it seems you've finally gotten NFS working!  Next is to use Unix permissions, if you have any issues.

---

### Post by QIII on 2020-12-09
@Phil Binner --

I corrected the code tags in your post.  Please use the edit button to view the change made.

---

### Post by Phil Binner on 2020-12-09
I believe my recent problems have bee DNS based, and relevant to the very simple router supplied by my ISP.  The problem was solved by using the IP address in the exports file, rather than the device name.  Strangely, ping worked for bigbin-xubuntu from serverbot when using either the IP or the name, but it only worked in exports using the IP,

I live in an old limestone farmhouse, with two foot thick walls.  The local limestone is also riddled with quartz, which further restricts wireless.  My response to that is to have two subsidiary routers hard wired as slaves, so I get coverage around the house.  I've spent today unravelling the connections, and giving everything I'm going to want to have network access a fixed IP address.

I still have one probably unrelated problem, in that my next step was to be a volume test.  I have a 3tb hard drive that is not used, I removed the old windows partition from that and created a single partition using GParted.  The new partition, Vol01,  is 2.73 Tb.  I have treated this partition in the same way as I treated Vol10, and consequently it appears to be mounted, but it is not accessible.  It is in fstab with the UUID I got by running blkid at the terminal, and when I run 

```
sudo mount -v /Vol01
```

I get

```
mount: /Vol01: /dev/sdb1 already mounted on /Vol01
```.

but I can't copy anything into it.

I'm obviously going to have to mess with this for a while.  The disk may be faulty, though I would expect error messages in that case, or perhaps there are things I need to know about big partitions.

One last thing;  I do not intend to use this disk in a live system.  I took note about odd sized disks earlier.  I am using this because I have it and I want to run a volume test.

Thanks for getting me this far.

---

### Post by Phil Binner on 2020-12-09
Got it about the code tags.  Thanks

---

### Post by QIII on 2020-12-09
A quick way to do code tags is to use the "#" button above the text entry box.  Either: Click it, put your cursor between the code tags that appear and type or paste your text; or type or paste your text, highlight it and then click the button.

Cheers!

---

### Post by TheFu on 2020-12-09
> **Phil Binner said:**
>  
<snip>
The new partition, Vol01,  is 2.73 Tb.  I have treated this partition in the same way as I treated Vol10, and consequently it appears to be mounted, but it is not accessible.  It is in fstab with the UUID I got by running blkid at the terminal, and when I run 

```
sudo mount -v /Vol01
```

I get

```
mount: /Vol01: /dev/sdb1 already mounted on /Vol01
```.

but I can't copy anything into it.

I'm obviously going to have to mess with this for a while.  The disk may be faulty, though I would expect error messages in that case, or perhaps there are things I need to know about big partitions.

One last thing;  I do not intend to use this disk in a live system.  I took note about odd sized disks earlier.  I am using this because I have it and I want to run a volume test.

Thanks for getting me this far.

[LIST]
[*]Prove the mount happened:  [B]df -Th |grep Vol
[/B][*]Which file system type is being used? **df -Th |grep Vol**
[*]Show the Unix permissions for the mounted storage top. After mounting is proven, **ls -al /Vol01**
[/LIST]

Please.

Remember when I mentioned Unix permissions being important? Well, they are.  Hopefully, NTFS isn't being used. NTFS, FAT32, and other non-native file systems don't support Unix permissions.  Really large HDDs need to use GPT, not MS-DOS partition tables.

---

### Post by Phil Binner on 2020-12-09
```
df -Th |grep Vol
/dev/sda1      ext4      143G   61M  136G   1% /Vol10
/dev/sdb1      ext4      2.7T   73M  2.6T   1% /Vol01
```

```
ls -al /Vol01
total 24
drwxr-xr-x  3 root root  4096 Dec  8 14:43 .
drwxr-xr-x 22 root root  4096 Dec  8 17:33 ..
drwx------  2 root root 16384 Dec  8 14:43 lost+found
```


What does that tell me.

---

### Post by TheFu on 2020-12-09
```
drwxr-xr-x  3 root root  4096 Dec  8 14:43 .
```
says that root is the owner and the only userid that can create files there.
Because it truly is mounted AND because you formatted using ext4, the fix is easy. Make your userid the owner.  This is probably something you want to do with the other mount too.

```
sudo chown -R phil:phil  /Vol10  /Vol01
```

Use explainshell.com to learn what that command means or just read the manpages. Every command has a manpage on Uinx systems, well, almost every command.

To learn and understand Unix permissions, [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) is a place to start. But to really learn them, it is best to create 3 temporary userids, 3+ groups, mix and match which users are in each group. Next, create some directories and files somewhere under /tmp/ and spend 45 minutes practicing with every possible combination of own, groups, and permissions.  I wasted about 6 months hunting and pecking before I sat down and learned permissions. That was about 27 yrs ago. Every popular OS uses the Unix permissions model, except 1. Unfortunately, because that 1 has 90+% market share, 10 yr old kids aren't taught this stuff.

---

### Post by Phil Binner on 2020-12-09
I finally have a network.  I'll spend a while trying out the permissions, following the reading and finishing my documentation before coming back to get the Windows machines connected.

If you ever get fed up with your American colleagues boring you with how to make American beer, come and ask me and I'll bore you with how to make English beer, along with all the history about how IPA came to be, etc, etc.

I don't know how you put up with me.  Thank you.

---

### Post by TheFu on 2020-12-09
> **Phil Binner said:**
> I finally have a network.  I'll spend a while trying out the permissions, following the reading and finishing my documentation before coming back to get the Windows machines connected.

If you ever get fed up with your American colleagues boring you with how to make American beer, come and ask me and I'll bore you with how to make English beer, along with all the history about how IPA came to be, etc, etc.

I don't know how you put up with me.  Thank you.

Glad you got it working. Nobody is born knowing this stuff.

---

### Post by LHammonds on 2020-12-09
> **TheFu said:**
> Nobody is born knowing this stuff.Except for T-800 and T-1000 models.  (Terminator movie reference)

---

### Post by Phil Binner on 2020-12-14
Now I have NFS working I would like to get to the next phase, which is to get the windows machines connected.  My understanding is that the only way to do this is with Samba, but it would be great if that is not true.

Where do I go next.

---

### Post by Phil Binner on 2020-12-14
That was ridiculously easy.  Ubuntu documentation has a very simple  seminar on the subject.  Here

```
https://ubuntu.com/tutorials/install-and-configure-samba#1-overview
```

What I did was to install Samba and edit smb.conf to add the lines:

```
[Vol01]
   Comment = Vol01 on Samba
   path = /Vol01
   read only = no
   browsable = yes
```

Then set up the user and opened the firewall and restarted.

I had to map a network drive in windows and there it all was.

---

### Post by Phil Binner on 2020-12-14
What I will need next is a good backup system, then I can go live.  Currently I just copy my network files to a couple of removable hard drives, but I think I want better than that now, probably daily/weekly/monthly.

Any suggestions as to a good system.

Thanks.

---

### Post by TheFu on 2020-12-14
If multiple userids are involved, you'll need to plan for capturing permissions, ACLs, xattrs AND the data as each change over time.  There are modern backup solutions and their are old-school backup solutions that follow the methods from 1970. Only 2 that I know will capture everything needed, not just the data as it changes over time. All the others fail in that way or are extremely inefficient.  For a single user, desktop, setup, permissions aren't nearly so important, so lots of advice you might see for "simple backup tools" handles just the files, but little else. 

On multi-user systems or servers, the metadata about files and directories are absolutely critical.  We need to capture the data (50%) and the metadata (50% owner, group, permissions, ACLs, xattrs) as each file changes over time. Attempting to restore without the correct metadata won't end well. For system files, it will lead to a system that won't boot - really the best case would be an non-secure system that shouldn't be trusted.

Do some reading about the different types of backups available, how much time and storage you can allocate for backups, and consider how important a 1-click restore is.  You'll find there are lots and lots of trade-offs. If you have 50x the storage of the original for backups and 2-5 hours a day where the system can be down, then imaged backups can be used.  Most people do not have that amount of storage or that amount of time that a server can be unavailable.  Trade-offs.

Assuming you have multiple users and perhaps 1.3x the amount of storage as the source files being backed up, there are really only 2 choices. Duplicity and rdiff-backup.  These are very different sorts of tools. 

Duplicity works in the 1970 way .... weekly "full" backups and daily incrementals. To restore, first restore the last "full" backup, then all the incremental backups to get to the date recovered. Running a full backup every week or every other week or even every month, will take lots of downtime, unless some enterprise storage management with snapshot capabilities was used, like LVM or ZFS.  However, using LVM is **not** something for a beginner.

rdiff-backup works in a more modern way.  Nightly mirrors with compressed differences for changes between the current and last backup version. The differences in metadata are also captured and versioned for every file and directory even if the contents of those files doesn't change.  About 90% of the time, when picking which backup set we want to restore, the most recent (last night) is the one used.  rdiff-backup's most recent backup looks like a mirror - as though rsync had been used, so we can use rdiff-backup as the restore tool or rsync or cp or any tool that can copy the files (assuming the permissions allow that). If we need 1 file, a directory structure or the entire backup set restored, we can easily.  OTOH, if we had a corrupted DB and nobody noticed that issue until weeks later, **rdiff-backup -r 25 days** will restore whatever is in the backup set from 25 days ago - or we can limit it to a directory structure or single file. The way that times can be specified are many - X days ago, Y backups ago, or an exact time following the DBMS standard timespec.  The problem with this reverse, compressed, differential, backup set method is that intermediate backup sets cannot be removed, but the last one(s) can. In fact, after my daily backups finish, I have rdiff-backup remove any backup sets older than XXX days ago. That results in a rolling XXX days of retained versions.  [https://www.tecmint.com/rdiff-backup-remote-incremental-backup-for-linux/](https://www.tecmint.com/rdiff-backup-remote-incremental-backup-for-linux/) is an old how-to. Don't worry about the dependencies. APT will handle those as needed for your system.

BTW, almost all efficient backup tools on Unix will be based on rsync. Both duplicity and rdiff-backup are. Lots of people just use rsync or rsync+hardlinks to provide versioning.  I used rsync and a number of rsync+hardlink techniques for years before I was burned by changes to the file metadata in an important system.One last thing. Some solutions appear to recommend having 2 or 3 backup tools. IMHO, if you need more than 1 tool to accomplish this goal, perhaps you picked the wrong solution. Every tool has caveats. Learning those subtle caveats for each tool, especially when new to Linux, will be difficult to remember, assuming they can be understood.

All these tools are network capable, so people like me have a network backup server and we "pull" backups from the different client systems on our network. "Pull" uses ssh connections and it much more secure than "push" from the client systems.  "Pull" backups address problems with crypto-malware, among some other issues.  "Push" or local backups can be compromised by crypto-locker malware. Setting up secure, networked, "pull" backups requires a good understanding of Unix users, permissions, and ssh. [https://www.tecmint.com/rdiff-backup-remote-incremental-backup-for-linux/](https://www.tecmint.com/rdiff-backup-remote-incremental-backup-for-linux/) - no need for other repos or to use any PPA these days.

[LIST]
[*]Restoring backups: [https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[*]A Script: [https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[*]aljames2 script w/ LVM snapshots: [https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233](https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233)
[/LIST]

You'll also see that most people don't backup the entire system with all the bits. That used to be how we all did things because a restore was the easiest way to get back to a working system.  Since the Linux installers have become so friendly and UEFI became common, many of us begin our restore process by doing a fresh, minimal, install. This handles the partitioning, boot, UEFI vs Legacy BIOS, encryption or no encryption with the ability to change underlying storage and completely replace the hardware in a way that restoring an OS running from another system doesn't.  Linux isn't nearly so picky about moving a HDD from 1 computer to another. I've done that a few times with only minor problems to be addressed, but for someone really new to Linux, those minor problems could easily cause days of a non-working system. OTOH, a fresh, minimal, install is 15 minutes to a working system.  Then we just need to make that minimal system into "our" system with the next steps as outlined in those links above.

Do some reading.  Look at some different options. Only you can pick which of the non-perfect solutions you'll put up with for the next 2-5000 months.  For me, the best trade-off is rdiff-backup with 90-180 days of versioned backup sets. Most of the time, 60 days of versioned backups uses just 20% more storage than the source files, so if you have 100G in the backup, to have 60 days of versioned backups would use about 120G. Seems like a pretty easy choice.  Plus, daily backups require less than 5 minutes after the first mirror job completes. Obviously, that first mirror will take as long to finish as copying all the files requires. Usually, that time is limited by storage write performance.  If the backup storage is tight, begin with just 30 days of versioned backups and see how much storage is used.

As for automation, use cron for that.  If you simply drop a script into /etc/cron.daily/ the backups will happen daily, sometime, thanks to anacron.  Anacron guarantees a script will run sometime during a day, if the system is powered on.  If you are like me and want more control over the exact time backups happen on each system, then using the /etc/crontab file directly will provide start time control for the script to the minute resolution. Scripts run from anacron or /etc/crontab run with root permissions. That is required for all backups that are more than getting a single user's HOME directory.

GUI programs cannot be run via crontabs/anacron, which means there is no choice except to create a script to control the backups.  Google "beginning bash scripting guide" to get started with that.  There are a few hundred bash script examples on your computer already and millions of examples online.

One last thing. Some solutions appear to recommend having 2 or 3 backup tools. IMHO, if you need more than 1 tool to accomplish this goal, perhaps you picked the wrong solution. Every tool has caveats. Learning those subtle caveats for each tool, especially when new to Linux, will be difficult to remember, assuming they can be understood.  Keep everything as simple as possible, but not so simple as to fail to accomplish the task at hand.

If you want to try out/use a rsync+hardlink solution, that wheel has been invented for a few decades.  rsnapshot is the name and it is in the ubuntu repos, just like duplicity and rdiff-backup are in the repos.
[https://ubuntu.com/server/docs/tools-rsnapshot](https://ubuntu.com/server/docs/tools-rsnapshot)
[https://help.ubuntu.com/community/DuplicityBackupHowto](https://help.ubuntu.com/community/DuplicityBackupHowto) - that guide spends way too much time with a dead protocol, plain FTP. Nobody, anywhere, should be using plain FTP in 2020.  Nobody.  Duplicity supports plenty of secure transfer methods. Use one of those instead - sftp, scp, rsync, one of those.

It is probably time to end this thread. Please create another for backup questions, but include a link to this one as background information.  That way, people who don't know NFS, but have great ideas about backups will be likely to respond with their expertise. Getting lots of points of view would only help you to make the best possible decision.

---

### Post by SeijiSensei on 2020-12-14
I posted my home-grown backup script that sucks down specific content from three remote sites and stores them on a 4 TB removable drive. It keeps a specified number of days of backups in dated directories ("/201213/")and archives one backup per month. Maybe it will give you some clues.

[https://ubuntuforums.org/showthread.php?t=2452278&p=13994172&viewfull=1#post13994172](https://ubuntuforums.org/showthread.php?t=2452278&p=13994172&viewfull=1#post13994172)

(The remotes are on [Linode]("https://www.linode.com/"), and a snapshot of each machine is taken there every night.  The last two nights' data, and data from a week ago, are available. You can take manual snapshots as well.)

---

### Post by Phil Binner on 2020-12-14
Thanks to all.  That's for tomorrow now.  I'll end this and start again.

---

