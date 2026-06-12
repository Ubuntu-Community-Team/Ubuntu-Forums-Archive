---
title: "Mount NAS NFS File shares - Allow full r/w control"
date: 2019-06-23
forum: Server Platforms
---

### Post by tim76 on 2019-06-23
Hey all,

I've been having this problem for quite some time and can't seem to figure out what is going on here... 
I have a NAS with 7 different NFS shares in which 6 different machines connect to do various CRUD operations, but I get all kinds of different problems on each machine with read writes... I've created the following diagram to help illustrate the makeup of my systems:

[IMG]https://tims-personal-stuff.s3-ap-southeast-2.amazonaws.com/nas-setup-v3.png[/IMG]

From the above, the connections are somewhat the same, but take notice that I connect my Windows 10 desktop to my NAS via Mapped network drives, but I also SSH into my media.server box to run CLI commands. 
[TABLE="class: grid, width: 800, align: left"]
[TR]
[TD]**Server**[/TD]
[TD]**media.server**[/TD]
[TD]**SG-1**[/TD]
[TD]**stargate-goauld**[/TD]
[TD]**oracle-time**[/TD]
[TD]**judy-imac**[/TD]
[TD]**judy-mac**[/TD]
[/TR]
[TR]
[TD]**Connection**[/TD]
[TD]FSTAB[/TD]
[TD]Mapped Drives[/TD]
[TD]WebDAV[/TD]
[TD]WebDAV[/TD]
[TD]WebDAV[/TD]
[TD]WebDAV[/TD]
[/TR]
[/TABLE]

When I'm editing development files via VSCode and run various node commands, every time node creates a folder/file, I either cannot edit/remove it or I get access denied and my node app fails. I've been bypassing this over the last year by just changing to the parent directory and chown and chmod the child folder so I can do whatever I want, but am getting tired of that and want to have the NAS and my systems all working well together. Again, to help illustrate what's happening, I've created the below diagram:
[IMG]https://tims-personal-stuff.s3-ap-southeast-2.amazonaws.com/dev-server-mount.png[/IMG]

As stated above, my NAS folder is mounted on startup with the following inside my FSTAB:
```
stargatecommand:/volume1/Dev /home/sga/media/dev     nfs     auto,defaults,nofail    0       0
```

When this mounts, all folders are 777 and the user:group owners vary from:
[LIST]
[*]sga:sga
[*]root:root
[*]1024:users
[*]1027:users
[*]1029:users
[/LIST]

[SIZE=3][B]
App Services running in Ubuntu[/B][/SIZE]
From the patterns I can see, it looks like when Sonarr/SAB automatically download, create and transfer files, the user:group is set to: [B]1024:users
[/B]When I manully add NZB files to SAB and it creates and moves files, the user:group is: **1024:users**
The above apps all run from the [COLOR=#ff8c00]media.server[/COLOR] ubuntu box

[SIZE=3]**Editing Development files inside Windows**[/SIZE]
For my node/npm applications, when I run `npm i *` from the VSCode terminal **inside Windows**, folders and files are created with [B]1027:users
[/B]When I manually create folders/files from within Windows, folders and files are created with **1027:users**

[SIZE=3]**Editing Development files and SSH'ed into Ubuntu box from Windows**[/SIZE]
For my node/npm applications, when I run `npm i *` from the VSCode terminal **ssh'ed into media.server**, folders and files are created with [B]1024:users
[/B]When I manually create folders/files, from the CLI, they are created with [B]1024:users

[/B][SIZE=3]**Editing Development files from my Macbook Pro**[/SIZE]
For my node/npm applications, when I run `npm i *` from the VSCode terminal, folders and files are created with [B]1026:users
[/B]When I manually create folders/files from within Windows, folders and files are created with [B]1026:users


[/B]Now that I've gone through all of this, below is the user mapping from all my systems:
**Ubuntu**: 1024
**Windows**: 1027
**Synology UI**: 1026
[COLOR=#ff0000]**Unknown**[/COLOR]: 1029

How do I make it so that no matter what system I connect from, each system can create/update/delete other files/folders without me having to run **chown **and **chmod **operations?
And is there a way I can mount/share this in Ubuntu where all files and folder don't need to be 777 and can utilise standard permissions and still be editable across all my systems *(even if I SSH into my [COLOR=#ff8c00]media.server[/COLOR] via Windows or my Macbook when I'm remote)*?

I appreciate this is a BIG post and if you made this far, a very big thank you! I'm also hoping that I've shown due diligence in vetting out as much info as possible to help get some good feedback. 

Thanks all and speak soon!

---

### Post by TheFu on 2019-06-23
TL;DR

Make the userids map 1-for-1.  If the userid is 1000 on Ubuntu and 500 on a Mac, then those are different userids.  Make them the same.  The same applies to groups.  All Unix systems should use NFS and have the correct 1-for-1 mapping.  When I say that I mean the exact uid and gid (the numbers) should be identical on all Unix client machines.

NFS is dumb.  It is the uid/gid numbers that matter.

I don't use webdav. Too many terrible security problems.  Use cifs on Windows and NFS for everything else on the LAN.

When you are outside the LAN, use sftp or sshfs.  There are sftp clients for every networked OS.

root shouldn't have any ability to change anything from a remote system. By default, NFS blocks root userids over NFS.  If the NFS server is a full Linux, there is a way to allow remote root accounts access. I don't do this.


OR


You could put all the different userids into the same group and setup each storage area like you would when working with other people.  [https://ubuntuforums.org/showthread.php?t=2411858&highlight=Working+Together](https://ubuntuforums.org/showthread.php?t=2411858&highlight=Working+Together) has the required steps to that.

---

### Post by TheFu on 2019-06-23
[https://serverfault.com/questions/514118/mapping-uid-and-gid-of-local-user-to-the-mounted-nfs-share](https://serverfault.com/questions/514118/mapping-uid-and-gid-of-local-user-to-the-mounted-nfs-share)
says that nfsv4 includes an id-mapping capability.  I've never used it.  Do cheap NAS boxes support NFSv4?  Anyway, that could be an option.

---

### Post by tim76 on 2019-06-24
Thanks for the replies TheFu! I've started to look at the different options have setup NFSv4 on the NAS device and testing with the my client configs in fstab. Need to look at id-mapping next.

---

### Post by tim76 on 2019-06-24
So I've done some reading based on your input above and found out that even if I get NFSv4 going and get the users on both client and server, due to RPC limitations and AUTH_SYS, NFS will still send a UID/GID over the wire and thus not match correctly. So in a NFS world, the only real option to ensure consistency on the LAN across multiple machines is to do ID syncing - which all articles say basically defeats the purpose of NFSv4 ID mapping. :( 
[https://web.archive.org/web/20170215124557/http://dfusion.com.au/wiki/tiki-index.php?page=Why+NFSv4+UID+mapping+breaks+with+AUTH_UNIX](https://web.archive.org/web/20170215124557/http://dfusion.com.au/wiki/tiki-index.php?page=Why+NFSv4+UID+mapping+breaks+with+AUTH_UNIX)

---

### Post by TheFu on 2019-06-24
I would use **FreeIPA** as my authentication server for all platforms.  FreeIPA needs to run on a separate, dedicated machine/virtual machine.  I've not deployed it at this point. I have used openldap for Linux-only authentication and it was a pain due to the lack of nice interfaces. Basically, everything has to be accomplished by creating an LDIF file to be batch submitted.  I found a how-to guide for FreeIPA on Ubuntu about a month ago. It is on my list of things to try out.  FreeIPA is an authentication solution for all platforms, not just Linux.

I'd pick POSIX uid/gid numbers higher than any currently used, then on each machine setup the LDAP-based authentication and migrate the files over to the new userid/groupid numbers one at a time using a 'find' command.  I've had to do this a few times at smaller companies (LT 100 users).  It was a pain to do in the beginning, but it sure made things easier after that.

If you don't want centralized users management, you can manually setup the userids to match, though on Windows using Samba, I'm unsure of how to get the ownership to map correctly.  Last week I did learn how to make NTFS storage used on both Windows and Unix have proper mapping and support POSIX permissions.  That has been working well enough, but doing it over a network would be much better for 99% of the world.

---

### Post by tim76 on 2019-06-28
So I've gone and changed the UID on my linux machine to match my NAS and updated all the files to use the new ID, but I still can't edit files in the system... 

And the weird thing, my dev folder is also mounting as root:root and my other mounts are mounting as 1000:sga (so it's half right)
```
sga@Media-Server:media$ ls -all
total 12
drwxrwxr-x  5 sga  sga  4096 Apr  8  2018 .
drwxr-xr-x 49 sga  sga  4096 Jun 28 18:12 ..
drwxrwxrwx  2 root  root  4096 Apr  8  2018 dev
drwxrwxrwx  1 1000 sga 24510 Jun 26 13:48 movies-new
drwxrwxrwx  1 1000 sga  5190 Jun 26 21:58 tv-new

```



Here's the fstab entries
```
#Entries NAS Shares
stargatecommand:/volume1/Movies /home/sga/media/movies-new      nfs     auto,defaults,nofail    0       0
stargatecommand:/volume1/TV-Series /home/sga/media/tv-new      nfs      auto,defaults,nofail    0       0
stargatecommand:/volume1/My\040Documents /home/sga/Documents/MyDocuments      nfs      auto,defaults,nofail    0       0
stargatecommand:/volume1/Dev-Server /home/sga/media/dev     nfs     auto,defaults,nofail    0       0
```

Can anyone help me figure out why my /home/sga/media/dev mount is mounting as root:root and the others are 1000:sga when all the entries are exactly the same?

For the purposed of testing other mount options, I've been trying the below... 
I've been trying to mount the drives with a uid=1029, but every time I try, I get incorrect mount option
```
sga@Media-Server:media$ sudo mount -vvv -t nfs -o nfsvers=4,user,uid=1029 stargatecommand:/volume1/Dev-Server /home/sga/media/dev
mount.nfs: timeout set for Fri Jun 28 18:49:41 2019
mount.nfs: trying text-based options 'uid=1029,vers=4,addr=192.168.1.113,clientaddr=192.168.1.114'
mount.nfs: mount(2): Invalid argument
mount.nfs: an incorrect mount option was specified

```

Even if I just try options with just uid, still incorrect mount options
```
sga@Media-Server:media$ sudo mount -vvv -t nfs -o uid=1029 stargatecommand:/volume1/Dev-Server /home/sga/media/dev
mount.nfs: timeout set for Fri Jun 28 18:49:41 2019
mount.nfs: trying text-based options 'uid=1029,vers=4,addr=192.168.1.113,clientaddr=192.168.1.114'
mount.nfs: mount(2): Invalid argument
mount.nfs: an incorrect mount option was specified

```

```
sga@Media-Server:media$ sudo mount -vvv -t nfs -o nfsvers=4,user stargatecommand:/volume1/Dev-Server /home/sga/media/dev
mount.nfs: timeout set for Fri Jun 28 18:57:00 2019
mount.nfs: trying text-based options 'vers=4,addr=192.168.1.113,clientaddr=192.168.1.114'
sga@Media-Server:media$ ls -all
total 8
drwxrwxr-x  5 sga  sga   4096 Jun 28 18:49 .
drwxr-xr-x 49 sga  sga   4096 Jun 28 18:12 ..
drwxrwxrwx  1 root root   346 Jul  6  2018 dev
drwxrwxrwx  1 1000 sga  24510 Jun 26 13:48 movies-new
drwxrwxrwx  1 1000 sga   5190 Jun 26 21:58 tv-new

```
No matter what I try, **ONLY** the dev mount is mounting as **root:root** and I'm baffled by it... from both CLI and in fstab.

---

### Post by TheFu on 2019-06-28
Did you chown the dev/ directory?  
Also, I don't think you get to use uid/gid options with NFS mounts.  Use chown/chgrp. This has to be done ON THE STORAGE machine itself, not from a client.

Is nfsver an allowed option for v4 of NFS?  It is for v2 and v3 only. It is not an option for v4 mounts.
**man -s 5 nfs** will show the available options and warnings about using UDP for GigE or faster networks.

Try this:
```
               server:/export  /mnt  nfs4  sec=krb5                      0 0
```
it assumes you have kerberos setup. If you don't, I think you are limited to v3 of NFS. I find it surprising that specifying ver4 doesn't cause an error in the logs.

---

### Post by tim76 on 2019-06-28
>[COLOR=#000000]Also, I don't think you get to use uid/gid options with NFS mounts. [/COLOR]
Yeah, I actually went and read the man pages for mount and fstab after posting this... sorry for wasting the time on that one! 
Where I got confused was I read a lot of older posts showing people using guid and uid in mount options, so I was giving it a go. 

>[COLOR=#000000]Use chown/chgrp. This has to be done ON THE STORAGE machine itself, not from a client.[/COLOR]
I'll give this a go now.. tried doing it via the UI with simple permission changes but I couldn't alter the main folder, so I'm going SSH into the NAS and give that a go. 

I don't have kerberos setup, that's a last resort if I can't get this local working properly. Immediate fix is to get my Ubuntu server working without perm issues on the box itself and via ssh through windows. 

Thanks for all help mate! It's good to bounce ideas off someone else other than my brain!

---

### Post by tim76 on 2019-06-28
Man! my dev folder took 30 minutes to finish the chown (loads of node_modules) folders everywhere, but I'm happy to show:
```
sga@Media-Server:media$ ls -all
total 8
drwxrwxr-x  5 sga sga    4096 Jun 28 18:49 .
drwxr-xr-x 49 sga sga    4096 Jun 29 09:05 ..
drwxrwxrwx  1 sga users   346 Jul  6  2018 dev
drwxrwxrwx  1 sga users 24510 Jun 26 13:48 movies-new
drwxrwxrwx  1 sga users  5190 Jun 26 21:58 tv-new
```

---

