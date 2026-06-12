---
title: "Connecting to Network Attached Storage (NAS)"
date: 2011-07-26
forum: Server Platforms
---

### Post by MAFoElffen on 2011-07-26
I had started a thread in General Help on this... But in a week,  there was 0 replies.  Maybe that was the wrong place to post that.  I closed that thread and am asking here, where it might be more appropriate.  Anyways:

Re: Ubuntu 11.04

Okay, this one is just weird.

I added a standalone NAS(Snap! Server) to my network.  For those that know me....  I have a bit of experience (between installed and attached  drives, over 20 drives on just one of my servers . I have no troubles sharing / connecting when it's physically attached to a Linux, Unix or Windows machine (server or desktop)...  But-- this is  the first time I've installed a standalone NAS in my network.

I know, the first question I would ask someone else would be: Is it the rights and privileges on the NAS... No, it is not.  Firewall problem- no.  Please see below...
 
 I can connect to the web server services of the NAS via any browser using the same data as above...  I can connect to the ftp services of the NAS.
 
 My desktop (main box) can connect correctly to the NAS if I do a Places > "Connect to  Serverr" using the same data in the 2 attached pic's manually.  If I  connect this way, I do have a desktop icon and have rw previledges...    The connect via windows share / samba looks like this:
```

smb://mafoelffen@192.168.2.107/maferr-snap/ Snap

```Connecting with rw access and having an icon on the gnome desktop and showing up in the nautilus menu...

Someone would see that and say what is the problem?  Well, this is where it starts getting weird on me!

I can sort of mount the NAS manually from my main box (11.04) from the command line if I:
```

sudo mount -t smbfs //192.168.2.107/maferr-snap /Snap -o credentials=/home/mafoelffen/.smbpasswd

```I can sort of mount it through fstab via:
```

//192.168.2.107/maferr-snap   /Snap       smbfs        credentials=/home/mafoelffen/.smbpasswd 0 0

```What do I mean by "sort of"?  Well, there are no errors during the connect, but is only partially mounting(?).  I will explain:

After doing either of the above, It doesn't show up on the gnome desktop as mounted like my other disk  mounts & real "server shares" or as a folder in Places.  I can see and read the files in that  NAS via the /Snap directory through a terminal to /Snap or nautilus if I  go to filesystem > /Snap.... Problem is when I check permissions on  that folder from that machine, it says the owner and permissions are  root(?)  Even though it says it is root, it will let root read  , but not write... 

So the question is: 
"How to get this working and appearing as other shares, with normal access and rw rights?"  My goal is to have my desktop autoconnect to this NAS...

---

### Post by JKyleOKC on 2011-07-26
You're mounting it to /Snap, but in order to automatically show up in Places it needs to be mounted to /media/Snap instead. Only the systems mounted under /media are automatically added to Places.

If you want the NAS to show up with you as its owner, you will need to add a couple of lines to smb.conf to force that situation. I'm no longer using Samba for much of anything so have forgotten the exact syntax, but it's covered in most all of the Samba how-to files...

---

### Post by MAFoElffen on 2011-07-26
> **JKyleOKC said:**
> You're mounting it to /Snap, but in order to automatically show up in Places it needs to be mounted to /media/Snap instead. Only the systems mounted under /media are automatically added to Places.

If you want the NAS to show up with you as its owner, you will need to add a couple of lines to smb.conf to force that situation. I'm no longer using Samba for much of anything so have forgotten the exact syntax, but it's covered in most all of the Samba how-to files...
> **UNIX NFS Networks**
The Snap Server supports version 2.0 and 3.0 of the NFS protocol. The Snap Server preserves the case of file names but is case insensitive when comparing file names. Therefore, the server cannot have two files with the same name.

For example, a file saved as &#8220;FOOD&#8221;, another saved as &#8220;Food&#8221;, and a third saved as &#8220;food&#8221; are considered the same file to the server.

A network share on a Snap Server is equivalent to an exported file system on an NFS server. NFS users can mount Snap Server shares and access their content directly or mount a subdirectory of a share. They can use dynamic mounting (with auto-mount) or static mounting (with automatic remount when the server restarts after being shut down). To perform a static mount, you must be logged into your UNIX system as root. Mount a Snap Server exported file system with the following commands:
```

mount snap_server:/share_name/mnt /local_dir

```where snap_server is the Snap Server name or IP address, share_name is the name of the
exported file system, mnt is a subdirectory of the share (not required), and local_dir is the
local directory to which the file system is mounted. Note the space inserted after the mount name. Below are two examples of a mount:
```

mount snap30286:/share1/mnt /workdir
or
mount 192.168.1.1:/share1/mnt /workdir

```The Snap Server uses mount points (network shares) to control access. Files and directories (folders) accessible through the mount point have the access rights of the network share combined with any file and folder security. 
You can configure Snap Server users and grant them rights for selected network shares. (Snap Server user names, such as root and GUEST, are not case-sensitive.) You can then associate user accounts from one or more UNIX systems to a Snap Server user.

To configure NFS users first click Users on the Security menu and then click New to create
a new, local user. Select the user you created and then click NFS. On the NFS Settings for User page, click New. On the New NFS Settings for User page, enter the user ID (UID), IP address, and Address Mask. Click OK to apply your changes. 
Which is also configured on the NAS... to use it, the only thing I haven't add to options on the connecting machine is the uid=1000...

EDIT- No, Adding uid=100 made no change.

---

### Post by bakegoodz on 2011-07-26
You need to set permissions when you mount or use the fstab. [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) I think the umask one is most important. example umask=002 setup full permissions for specified or implicit uid and gid. Personally I find all tedious. I just use Gnome mount. I think it is pretty brain dead that Gnome doesn't make its mounted network drives in folder easily accessible to the terminal and applications. I just use the following command while in /home/user folder: ln -vs .gvfs network Then all the Gnome mounted network drives show up in /home/usr/network

---

### Post by MAFoElffen on 2011-07-26
> **bakegoodz said:**
> You need to set permissions when you mount or use the fstab. [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) I think the umask one is most important. example umask=002 setup full permissions for specified or implicit uid and gid. Personally I find all tedious. I just use Gnome mount. I think it is pretty brain dead that Gnome doesn't make its mounted network drives in folder easily accessible to the terminal and applications. I just use the following command while in /home/user folder: ln -vs .gvfs network Then all the Gnome mounted network drives show up in /home/usr/network
Well, here's the present fstab entry... and still the same.
```

//192.168.2.107/maferr-snap   /media/Snap  smbfs  credentials=/home/mafoelffen/.smbpasswd,uid=1000,gid=1001,umask=006 0 0

```You're right... Connecting manually through gnome is a lot easier... But now it's a challenge.

Well this didn't work either...
```

//192.168.2.107/maferr-snap   /media/Snap  smbfs  defaults,user,credentials=/home/mafoelffen/.smbpasswd,uid=1000,gid=1001 0 0

```

---

### Post by bakegoodz on 2011-07-27
When you connect with Gnome, can you Write to the NAS?

---

### Post by JKyleOKC on 2011-07-27
Your fstab entries all show the system type as "smbfs" but the documentation bit you posted says that the NAS is "equivalent to" an NFS file system (whatever that may mean). Have you tried setting its type to "nfs" instead of "smbfs"?

---

### Post by Morbius1 on 2011-07-27
And what does this do:
```
 //192.168.2.107/maferr-snap   /media/Snap  cifs credentials=/home/mafoelffen/.smbpasswd,uid=1000,file_mode=0777,dir_mode=0777,nounix 0 0
```That's probably as close as I can get to how a "gvfs-mount smb://192.168.2.107/maferr-snap" mount does it ( i.e., Connect to Server ) except I added a 777 dir_mode and file_mode to make it accessible to everyone just to hedge my bet :wink:

BTW smbfs is gone - cifs replaced it. May not make any difference depending on how old the samba version is on the NAS but .........

---

### Post by MAFoElffen on 2011-07-28
> **bakegoodz said:**
> When you connect with Gnome, can you Write to the NAS?
Yes it does.

---

### Post by MAFoElffen on 2011-07-28
> **JKyleOKC said:**
> Your fstab entries all show the system type as "smbfs" but the documentation bit you posted says that the NAS is "equivalent to" an NFS file system (whatever that may mean). Have you tried setting its type to "nfs" instead of "smbfs"?
I've tried smbfs, cifs and using the nfs mount line in it's docs...

---

### Post by MAFoElffen on 2011-07-28
> **Morbius1 said:**
> And what does this do:
```
 //192.168.2.107/maferr-snap   /media/Snap  cifs credentials=/home/mafoelffen/.smbpasswd,uid=1000,file_mode=0777,dir_mode=0777,nounix 0 0
```That's probably as close as I can get to how a "gvfs-mount smb://192.168.2.107/maferr-snap" mount does it ( i.e., Connect to Server ) except I added a 777 dir_mode and file_mode to make it accessible to everyone just to hedge my bet :wink:

BTW smbfs is gone - cifs replaced it. May not make any difference depending on how old the samba version is on the NAS but .........
I was hopeful... Same thing, mounts with no errors... Folder shows on desktop. Can display and read files (there's a text file I have in a folder there.  Can open that file. Editor will not let me save edits.

I tried cifs, just in case.  This is a Quantum Snap!Server, probably circa 2002-2003.  Not really sure wwhat version of GuardianOS it's running or what exact model it is.  The person who gave it told me it was a Snap1000, but is doesn't "look" exactly like the docs.

---

### Post by MAFoElffen on 2011-07-28
But again connecting through gnome I have full read and write.  See attached.  I have noticed connected that way, the folder on the desktop's icon is "different"... like a nework folder.  Where as all the times I've tried to mount w/ fstab it displays as a mounted local folder.

I tried using an "_netdev" fstab option to see if I had to wait to verify the network device was ready first... made no change either.

---

### Post by Morbius1 on 2011-07-28
> there's a text file I have in a folder there.  Can open that file. Editor will not let me save edits.text file as in *.txt or text file as in an OpenOffice or Word document. The reason I ask is because there is an option that has to be added for one to save any of the Office documents that disables a characteristic of these files: **nobrl**

If it's just a plain text document it won't do anything.
[COLOR=Blue]
**EDIT:**[/COLOR]  Just did something out of the box and did a search on this forum and found this: [http://ubuntuforums.org/showthread.php?p=8721020](http://ubuntuforums.org/showthread.php?p=8721020)

In that topic two more options were used successfully: noserverino,noperm

On the bright side mount.cifs only has 3 or 4 more options available so when you have them all listed you'd think it would have to work :)

---

### Post by koenn on 2011-07-28
I'll throw in 5 cents :

"NAS" is simply a dedicated server with a filesharing protocol : CIFS (smb, SAMBA) and/or NFS. It works essentially the same as a general purpose computer with those protocols (except that the general purpose OS tools are missing). So you can approach this problem is if it was an ordinary NFS or CIFS issue.

If  you're using linux and want to use NAS, NFS would probably be your first choice, it's actually designed to add network storage to unix/linux systems (cifs is windows file sharing, and supported on linux for interoperability reasons mainly)


Don't rule out permissions. It's not uncommon for a NAS system to provide read access by default but expect you to configure users and assign rights in order to get write access. That you have a user account that can log on to the management web ui does not automatically mean this account has (write) access to the files

Read-only access on a linux/unix-like system sometimes is an indication of disk or filesystem trouble : the system could be configured to set its filesystems readonly to avoid file corruption if one or more disks  are faulty or in similar cases where filesystem errors might occur.That will result in read-only access no matter what permissions are set. 
You may want to look that up in the docs.

---

### Post by MAFoElffen on 2011-07-29
> **Morbius1 said:**
> text file as in *.txt or text file as in an OpenOffice or Word document. The reason I ask is because there is an option that has to be added for one to save any of the Office documents that disables a characteristic of these files: **nobrl**

If it's just a plain text document it won't do anything.
[COLOR=Blue]
**EDIT:**[/COLOR]  Just did something out of the box and did a search on this forum and found this: [http://ubuntuforums.org/showthread.php?p=8721020](http://ubuntuforums.org/showthread.php?p=8721020)

In that topic two more options were used successfully: noserverino,noperm

On the bright side mount.cifs only has 3 or 4 more options available so when you have them all listed you'd think it would have to work :)
Just plain text I figured a plain text file editing from Gedit is about as basic as it gets. Except maybe VIM or EMACS...).

"noserverino"... well that one didn't work and additionally added a white line/shadow/border around all the gnome panels, bars and menus.

---

### Post by MAFoElffen on 2011-07-29
> **koenn said:**
> I'll throw in 5 cents :

"NAS" is simply a dedicated server with a filesharing protocol : CIFS (smb, SAMBA) and/or NFS. It works essentially the same as a general purpose computer with those protocols (except that the general purpose OS tools are missing). So you can approach this problem is if it was an ordinary NFS or CIFS issue.

If  you're using linux and want to use NAS, NFS would probably be your first choice, it's actually designed to add network storage to unix/linux systems (cifs is windows file sharing, and supported on linux for interoperability reasons mainly)


Don't rule out permissions. It's not uncommon for a NAS system to provide read access by default but expect you to configure users and assign rights in order to get write access. That you have a user account that can log on to the management web ui does not automatically mean this account has (write) access to the files

Read-only access on a linux/unix-like system sometimes is an indication of disk or filesystem trouble : the system could be configured to set its filesystems readonly to avoid file corruption if one or more disks  are faulty or in similar cases where filesystem errors might occur.That will result in read-only access no matter what permissions are set. 
You may want to look that up in the docs.
The disks test out fine.  Yes, this is just a very basic file server with remote access/administration, running a basic scaled down UNIX OS geared for basic administration.

I have NT services configured with Workgroup intead of Domain (I have Samba configured on 2 servers with no instance of an NT server.)  I have NT SMB's enabled.  Connecting gnome  is SMB right?  Connect maunally via gnone server connect and I have no problems / full rw.  I have default access to the NAS as rw, with the users and groups setting and inheriting righst and privileges.  

My account has full access, rights and priviledges.  I do have some setting to go back over and recheck on the NFS config, but I know the NT type settings are good.

I guess I could connect via a Windows session and confirm that.  I think it was capscrew and morbeus1 that helped me with my samba.conf on my servers about 2-3 years ago... and had not problems with that since.

Lately?  Well just trying different options and see what happens.  I think "morbeus1" gave me an insight into this... one of the links had a --verbose option to expand connection debugging mesaages.  Right at present this was a bit frustrating by connecting with no error messages, but failing on rights somehow. At least an error message would give me some direction on what is happening.  

Will try that tomorrow.  Last night was a long one/running on 2 hours sleep.

EDIT- I take that back > NFS config is good...

---

### Post by Morbius1 on 2011-07-29
This is a rather curious situation and just to recap for new viewers of this topic:

MAFoElffen can access the NAS as a cifs resource just fine and without issues by using "Places > Connect to  Server" which essentially performs the following operation:
```
 gvfs-mount smb://192.168.2.107/maferr-snap
```It does have the unfortunate byproduct of creating a mount point in a hidden ".gvfs" mount point in his home directory however which is the result of using a fuse based utility. But that isn't the issue here.

The issue here is what set of options are necessary to recreate the same client accessibility using the traditional mount.cifs method used in fstab.

---

### Post by MAFoElffen on 2011-07-29
> **MAFoElffen said:**
> 
Will try that tomorrow.  Last night was a long one/running on 2 hours sleep.

EDIT- I take that back > [COLOR=Red]NFS config is good[/COLOR]...
Maybe not so good... (Used --verbose on the command line.) )NFS manual mount excepts the username, asks for password and then fails on the connect.

But using "smbclient", sees the shares on the NAS and connects manually...
```

mafoelffen@maf-ubuntu-01:~$ smbclient -L //192.168.2.107/maferr-snape -U mafoelffen
Enter mafoelffen's password: 
Domain=[WORKGROUP] OS=[UNKNOWN] Server=[UNKNOWN]

    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       
    ADMIN$          Disk      
    RPC$            Disk      
    WebRoot$        Disk      
    Java$           Disk      
    maferr-snap     Disk      
Domain=[WORKGROUP] OS=[UNKNOWN] Server=[UNKNOWN]

    Server               Comment
    ---------            -------
    SNAP47875            Snap! Server 192.168.2.107 
    MAF-UBUNTU-01        maf-ubuntu-01 server (Samba, Ubuntu)

    Workgroup            Master
    ---------            -------
    WORKGROUP            MAF-UBUNTU-01
mafoelffen@maf-ubuntu-01:~$ smbclient -L //192.168.2.107 -U mafoelffenEnter mafoelffen's password: 
Domain=[WORKGROUP] OS=[UNKNOWN] Server=[UNKNOWN]

    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       
    ADMIN$          Disk      
    RPC$            Disk      
    WebRoot$        Disk      
    Java$           Disk      
    maferr-snap     Disk      
Domain=[WORKGROUP] OS=[UNKNOWN] Server=[UNKNOWN]

    Server               Comment
    ---------            -------
    SNAP47875            Snap! Server 192.168.2.107 
    MAF-UBUNTU-01        maf-ubuntu-01 server (Samba, Ubuntu)

    Workgroup            Master
    ---------            -------
    WORKGROUP            MAF-UBUNTU-01
mafoelffen@maf-ubuntu-01:~$ smbclient //192.168.2.107/maferr-snap -U mafoelffen
Enter mafoelffen's password: 
Domain=[WORKGROUP] OS=[UNKNOWN] Server=[UNKNOWN]
smb: \> 
smb: \> listconnect
0:    server=192.168.2.107, share=maferr-snap
smb: \> quit
mafoelffen@maf-ubuntu-01:~$ 

```

---

### Post by MAFoElffen on 2011-07-29
> **Morbius1 said:**
> This is a rather curious situation and just to recap for new viewers of this topic:

MAFoElffen can access the NAS as a cifs resource just fine and without issues by using "Places > Connect to  Server" which essentially performs the following operation:
```
 gvfs-mount smb://192.168.2.107/maferr-snap
```It does have the unfortunate byproduct of creating a mount point in a hidden ".gvfs" mount point in his home directory however which is the result of using a fuse based utility. But that isn't the issue here.

The issue here is what set of options are necessary to recreate the same client accessibility using the traditional mount.cifs method used in fstab.
Right-  Because (@Morbius1)... 
```
 gvfs-mount smb://192.168.2.107/maferr-snap
```
That worked perfect as a command line replicating mounting it manually through gnome with the correct access, rights and permissions.

Partial hooray... On the right track.

---

### Post by MAFoElffen on 2011-07-29
Lastest Line and it's results:
```

mafoelffen@maf-ubuntu-01:~$ sudo mount -t cifs //192.168.2.107/maferr-snap /media/Snap -o credentials=/home/mafoelffen/.smbpasswd,rw,uid=1000,,iocharset=utf8,file_mode=0777,dir_mode=0777 --verbose
mount.cifs kernel mount options: ip=192.168.2.107,unc=\\192.168.2.107\maferr-snap,credentials=/home/mafoelffen/.smbpasswd,,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000,ver=1,user=mafoelffen,pass=********
mafoelffen@maf-ubuntu-01:~$ sudo umount /media/Snap
mafoelffen@maf-ubuntu-01:~$ 

```And it's the same error as before > read-only... no write.

---

### Post by MAFoElffen on 2011-07-29
**[Bug #34813 - gedit fails to save files over smbfs/cifs]("https://bugs.launchpad.net/gedit/+bug/34813?comments=all")**

Maybe I ought to test this with something else...

EDIT-->  Found this Bug Report and workaround:[Bug #406466, 2.6.31 - Can't see files in CIFS-mounted directories]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406466")

By this time I was really reaching... a description had it "showing owned by root and..." which is sort of similar, but the work-around worked, on a mount...

Current Mount line and results:
> 
mafoelffen@maf-ubuntu-01:~$ sudo mount -t cifs //192.168.2.107/maferr-snap /media/Snap -o credentials=/home/mafoelffen/.smbpasswd,rw,uid=1000,,iocharset=utf8,nobrl,file_nounix,mode=0777,dir_mode=0777 --verbose

mount.cifs kernel mount options: ip=192.168.2.107,unc=\\192.168.2.107\maferr-snap,credentials=/home/mafoelffen/.smbpasswd,,iocharset=utf8,nobrl,[COLOR=Red]file_nounix,mode=0777,[/COLOR]dir_mode=0777,uid=1000,ver=1,user=mafoelffen,pass=********
mafoelffen@maf-ubuntu-01:~$ 
Showed up on desktop with the same icon as Morbius1'es commmand line and the manual gnome connect... and had rw access, rights and previledges...

EDIT2- Wasn't unitl I tried carry over all the options to the fstab and see if it worked.  It didn't.  In fact. I don't know-
It shouldn't have worked in the commandline as a mount <> I notice I had a typo in the options of the mount, where what should have been "nounix,file_mode=077", wound up as "file_nounix,mode=0777"... but worked finw from the commandline. fstab must not be as forgiving!!! Not working yet, but I see hope somehwere here.  Maybe now it's a matter of playing with the file_mode?

---

### Post by Morbius1 on 2011-07-30
So if I clean up that mount command a bit this works?
> sudo mount -t cifs //192.168.2.107/maferr-snap /media/Snap -o  credentials=/home/mafoelffen/.smbpasswd,rw,uid=1000,iocharset=utf8,nobrl,nounix,file_mode=0777,dir_mode=0777 --verboseThe only difference between this and posts #11 & #13 was the addition of "iocharset=utf8" ?

But the corresponding fstab entry does not work?
> //192.168.2.107/maferr-snap /media/Snap cifs credentials=/home/mafoelffen/.smbpasswd,rw,uid=1000,iocharset=utf8,nobrl,nounix,file_mode=0777,dir_mode=0777 0 0

---

### Post by MAFoElffen on 2011-07-30
> **Morbius1 said:**
> So if I clean up that mount command a bit this works?
> 
Quote:
                                                 sudo mount -t cifs //192.168.2.107/maferr-snap /media/Snap -o   credentials=/home/mafoelffen/.smbpasswd,rw,uid=1000,iocharset=utf8,nobrl,nounix   ,file_mode=0777,dir_mode=0777 --verbose                      
The only difference between this and posts #11 & #13 was the addition of "iocharset=utf8" ?

But the corresponding fstab entry does not work?
[quote]
//192.168.2.107/maferr-snap /media/Snap cifs  credentials=/home/mafoelffen/.smbpasswd,rw,uid=1000,iocharset=utf8,nobrl,nounix   ,file_mode=0777,dir_mode=0777 0 0                      
[/QUOTE]
Neither... ](*,)

What I posted "somehow" did as I said, but has not worked since.  It was false hope.

This again, is on the frustrating side... I think I'm on the right track > trying different mount options > unitl I get something to work > to try as an fstab entry... At least faster.  Besides, a few of the fstab entries I tried before, would lock the machime and I had to edit the fstab "externally" to recover and continue.

Seems like that bug report, what was working for them was
> 
nounix,noserverino,file_mode=0777,dir_mode=0777,username=myuserID,password=mypassword
Which in itself is not working here.

What is curious about that Bug Report, is that the last status was "Confirmed" but that they "Will not Fix." They left it. abandoned it... Did not peruse it as they were in a different version by then > Not that the new version fixed anything. Oh well.

---

### Post by Morbius1 on 2011-07-30
Then I don't understand post #21.

---

### Post by MAFoElffen on 2011-07-30
> **Morbius1 said:**
> Then I don't understand post #21.
I see we're both online now... I editted post 23 to clarify  on that.  

I had edited post 21, to say it shouldn't have worked (when I later found the typo's) and it hasn't worked since.  

It did work once... and I cut and pasted the terminal display of it and output... but still > It was false hope.

This is getting to be humbling.

---

### Post by Morbius1 on 2011-07-30
> Besides, a few of the fstab entries I tried before, would lock the  machime and I had to edit the fstab "externally" to recover and  continue.In the hopes that I may actually be of some use to you, there is no need to reboot you know. You can change fstab and then issue the following command to run the new line:

```
sudo mount -a
```It will also give you error messages if something is wrong which you would not see during a boot.
[COLOR=Blue]**EDIT**[/COLOR]: just make sure you unmount the remote share first if it mounted successfully before you make changes to fstab and run the "sudo mount -a".

---

### Post by MAFoElffen on 2011-07-30
Sidebar-- 
I'm going to pick up another dual proc server mobo this afternoon to upgrade one of my servers... I need a "success" today in "something" to get my head back in perspective.

---

### Post by michiedo on 2011-08-02
I'm having the very same problem with another hardware (iomega home network drive) .
If I mount it with gnome everything is ok, mounting via CLI or fstab I get only read access.
I run Ubuntu 11.04, I've also tried some "live" distribution (knoppix ? puppy ? don't remember ) to no avail.
I'll follow this thread.

---

### Post by MAFoElffen on 2011-08-02
I'm back on trying this with no luck yet... So far no luck in fstab via smbfs, cifs or nfs.

On smbfs and cifs I get a connect, but read only.

On NFS, I get a server connect failure.

On Ubuntu's NFS instructions, it's clear that the install/config is mostly on the server side, if I was installing and configuring a server to provides those server services... But what about the client-side?  

Client side of cifs and smbfs is via smbfs client services.  I think the client-side of NFS connect problem is related to my client-side package installation, which I'll reinstall and reconfigure to see if I can get that going... If it does, then I'll stop trying to connect via smbfs and cifs.

---

### Post by MAFoElffen on 2011-08-08
Okay--> Still no love on this.  Very frustrating.

Since the smbfs and cifs mounts "are" connecting, even though they are not connecting with the correct privileges, that is making correcting that a very big challenge!!!  I'm not getting any errors that would direct me in a direction to track down.

I'm thinking that if I can somehow turn on logging on the NAS, that I could "see" what is being recognized as the command to mount it and how it interprets that...

That might help with the NFS issues it's getting also.  Still curious why connecting SMB is no problems!

Another thing I haven't done yet, is to check and update the firmware/OS on the NAS.  I think there was 2 major updates on it's OS with many interim maintenance releases... since it was new 8 years ago.

---

