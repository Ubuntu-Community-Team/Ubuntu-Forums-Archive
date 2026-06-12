---
title: "Best Practice: File Server File and Permission Structure"
date: 2014-03-18
forum: Server Platforms
---

### Post by Leegaert on 2014-03-18
Hi,

I've been searching for this all night, so far no luck with google. If this should be a duplicate thread, maybe I've use the wrong keywords, in that case, my apologies.

A couple of months ago, I set up a Ubuntu 12.04 Server. I'm using it mainly as file server. Besides that I have my downloads running on it and a Plex Media Server.
In the beginning it was all fairly simple and I just set up a file structure as I saw while browsing for Samba examples.

I'm using 6 separate 2TB hard drives, each mounted to a mountpoint in /srv.
/srv/movies-a
/srv/movies-b
/srv/download-a
/srv/download-b
/srv/documents
/srv/backup

I used these paths for Samba, NFS and locally (transmission & plex). In the mean time, in my opinion, with permissions and all it's becoming a mess. Since I want to add SFTP as well, I started looking for best practices for a decent structure. I bumped into ACL, which I'll be looking into but I'm still wondering what the "best way" is to structure the file system.
Is it possible/advised to mount these drives to different mountpoints for each protocol? Should I work with symbolic links?
I have some experience with Linux but I'm still no expert in managing the file system.

Any help is very much appreciated!
If there are any questions, I'll try to answer them as well/quickly as possible!

---

### Post by TheFu on 2014-03-18
Forget ACLs.  You can almost certainly do everything necessary through normal userid and groupid controls.

I'm more worried about your backups, honestly. ;)  That is a bunch of data to be lost if even 1 drive failed.

So ... start with a tutorial on UNIX userids and groups and file permissions.  If you can explain the userids, perhaps we can help **AFTER** you've come up to speed with permissions. [https://www.dartmouth.edu/~rc/help/faq/permissions.html](https://www.dartmouth.edu/~rc/help/faq/permissions.html) There are many others. Ubuntu has one too.

Spend 30 minutes in a temp directory creating files and directories with different permissions to see how they work or don't work. Nothing can replace this "training".

---

### Post by Leegaert on 2014-03-18
Hi TheFu,

Thanks for your reply!

I understand your worries regarding the backup but it's a deliberate choice. I don't care about most of the content, I only care about the server config and the documents partially.
That aside, I do have some experience with userids, groups and file permissions. I know my way around the chmod and chown commands.

At the moment, I've got five users in use. Three of them were originally meant solely for Samba (mine, my girlfriend's and one for mediaplayer), I've added these to a group to be used in the samba config, this group is owner of everything I want to share. I've got a separate user which owns all the shared files, which I use to connect through SSH, which executes the torrent client daemon and which is also used to executed a post torrent completion script. Next to that there's the plex, which I've added to the "samba group".

I've configured NFS to only use the /srv/movies-a and /srv/movies-b, there I changed the permissions to 775, all other /srv permissions are set to 770. For the Samba shares, any other restrictions are set in the Samba config file.

I hope I explained it well enough, if you'd have any other questions, please let me know ;)

---

### Post by TheFu on 2014-03-18
Samba permissions are completely unrelated to local/nfs permissions, so let's forget those for now.

Are all the local and NFS users in the same group?  Just force the sticky bit at the group level on all directories to force the group you need.  I would use my own userid, not a "separate user" to own everything.  Running a chown/chmod -R script from cron every 30 minutes should correct any issues.

Why does the media player own anything?

I'd torrent to a different "temp" directory, then move the files over later. That can be automated.
I'd only allow plex to access the media files - not samba or nfs. Easier to manage that way.
For the documents ... normal user/group permissions should work - use the chmod g+ws to maintain the group you want.

So - after all that is done, setup samba to use the existing UNIX group for the documents and backup areas.

I hope that makes sense. If not, then we are probably not sharing enough details each way.

---

### Post by Leegaert on 2014-03-19
> **TheFu said:**
> Samba permissions are completely unrelated to local/nfs permissions, so let's forget those for now.
I think we got off on the wrong foot ;) I'll try to explain better.

Users: user1 / user2 / mp / myadminuser
Group: sambashare

Once Ubuntu Server was installed, first thing I did was configuring Samba. I wanted three users (for example **user1**, **u****ser2** and **mp**). If I'm not mistaken, to give those users access to the file system through Samba, they still need local access as well? That's why I added them to a group **sambashare**. I then changed owner and group to respectively **myadminuser:sambashare** with **770** permission. Further access restriction, for the samba users, are set in the samba config.

For example:
drwxrwx---  2 myadminuser sambashare 4096 Nov 19 20:13 documents

After Samba was set up, I started adding transmission, NFS, Plex... All based on my first "idea". Now I'm experiencing some issues specifying different permission for each protocol per user/group.

> Are all the local and NFS users in the same group?
I don't have any users for NFS, I just gave "everyone" access to the directories I wanted to share.
The only restriction is that only certain (local) IP's have access to the NFS share.

For example:
drwxrwx**r**-**x**  2 myadminuser sambashare 4096 Nov 19 20:13 documents

> Just force the sticky bit at the group level on all directories to force the group you need.
What do you mean by this? If I'm not mistaken, the sticky bit is used to deny other users then owner and group the rights to delete or rename files?
(Source: [http://help.ubuntu.com/community/FilePermissions#Sticky_Bit](http://help.ubuntu.com/community/FilePermissions#Sticky_Bit))

> I would use my own userid, not a "separate user" to own everything.
I used a separate user because I use that user to run my transmission daemon as well. It's a user to administrate my server. The other user is solely used to access Samba.
Is that a bad thing? 

> Running a chown/chmod -R script from cron every 30 minutes should correct any issues.
What would i need that script for? For the torrents?

> Why does the media player own anything?
The mediaplayer doesn't own anything. That user is restricted to read only operations in the Samba config. I use it to gain access to the Samba shares on my mede8er.

> 
I'd torrent to a different "temp" directory, then move the files over later. That can be automated.

I already have that in place, but might be for a different reason... Why exactly would you do that?

> 
I'd only allow plex to access the media files - not samba or nfs. Easier to manage that way.

This was my question, **how** do I accomplish this? I want to be able to assign user/group permissions for everything separately.

> 
For the documents ... normal user/group permissions should work - use the chmod g+ws to maintain the group you want.

I didn't know about the **s** option, if I read correctly that is for auto inherited permissions?

> 
So - after all that is done, setup samba to use the existing UNIX group for the documents and backup areas.

What existing group? The sambashare group I made with the three users?

> 
I hope that makes sense. If not, then we are probably not sharing enough details each way.

It does make sense, but as you can see I could use some more details ;)
I hope I didn't exaggerate, I feel like I've been typing an hour at this reply...


Thanks for all the help and tips thus far!!

---

### Post by TheFu on 2014-03-19
Sorry - I should have said the **set-group-ID** or **set-user-ID** flags, not "sticky". My mistake.

I'm having trouble following your groups, users - we need to be using the exact names and groups to prevent confusion. I should have asked for the output from ```
find /srv -maxdepth 2 -ls
``` in the first reply.  Also need the lines from the /etc/group file with any groups you plan to use.

Need the facts.
If you can clearly specify which users need what sort of access to which directories, that will be helpful too - table - not text, please. Also, please use "code" tags so the alignment is correct.

Samba access is not related to the local file ownership. I think that is part of the confusion. samba runs as root. It doesn't care what the local permissions are. 
[https://www.samba.org/samba/docs/using_samba/ch09.html](https://www.samba.org/samba/docs/using_samba/ch09.html) explains Samba permissions. Note how nothing around the user/group on the file system is included?

---

### Post by Leegaert on 2014-03-19
Hi,

I will provide you with the structure once I get home, I cannot access my server a.t.m. Right now, I only have one group in use, I think that's part of  the problem.
I'll make the table with the accesses as well.

I'm still confused about the Samba bit. Quote from that link (which I read while I was setting up Samba as well):
> When client users access a Samba share, they have to pass two levels of restriction. Unix permissions on files and directories apply as usual, and configuration parameters specified in the Samba configuration file apply as well. In other words, a client must first pass Samba's security mechanisms (e.g., authenticating with a valid username and password, passing the check for the valid users parameter and the read only parameter, etc.), as well as the normal Unix file and directory permissions of its Unix-side user, before it can gain read/write access to a share.
Doesn't this mean that the users that I use in Samba need to have the local permissions as well?

I'll get back to you with the other facts you asked for.

---

### Post by TheFu on 2014-03-19
True ... but there is a workaround for samba - the "force user" or "force group" options in the smb.conf.  We don't really have those in local file/dir permissions (except through a mount-bind), so local access needs to be working first.  May not be necessary - I can't tell yet.

I'm trying to stick with 1 question at a time. Too many concurrent questions confuses me. ;)

---

### Post by LHammonds on 2014-03-19
Once you get your permissions figured out, you should create a script file that sets those permissions and schedule it to run in crontab on a regular basis.  If you need to tweak permission settings later on, just edit the permission script.  Running a script on a schedule will help ensure the permissions remain how you expect them to be regardless of how/when/who copies/moves files around.

Example fixperms.sh:
```

#!/bin/bash
LogFile="/var/log/fixperms.log"
Owner="johndoe"
Group="xmen"
echo "`date +%Y-%m-%d_%H:%M:%S` Script start." >> ${LogFile}
echo "Resetting file ownership on all samba files..."
chown -R ${Owner}:${Group} /srv/samba/share/
echo "Resetting directory permissions..."
find /srv/samba/share/ -type d -exec chmod 0755 {} \;
echo "Resetting file permissions..."
find /srv/samba/share/ -type f -exec chmod 0644 {} \;
chmod 0444 /srv/samba/share/readonlyfile.txt
echo "`date +%Y-%m-%d_%H:%M:%S` Script completed." >> ${LogFile}

```

LHammonds

---

### Post by Leegaert on 2014-03-19
Hi again, sorry for overwhelming you ;)

Okay so this is the output from the command:
```

131216    4 drwxr-xr-x  11 root     root         4096 Jan  4 20:03 /srv
     2    4 drwxrwx---   3 myadminuser    smbsh        4096 Dec 22 15:27 /srv/backup
    11   16 drwx------   2 root     root        16384 Dec 20 20:07 /srv/backup/lost+found
     5    8 drwxrwx---   1 myadminuser    smbsh        8192 Dec 11 21:14 /srv/windows-data
  9461   32 drwxrwx---   1 myadminuser    smbsh       32768 Dec 10 17:37 /srv/windows-data/Downloads
    37    0 drwxrwx---   1 myadminuser    smbsh           0 Apr  6  2013 /srv/windows-data/$RECYCLE.BIN
  8352    8 drwxrwx---   1 myadminuser    smbsh        8192 Nov 16 15:00 /srv/windows-data/Desktop
  9441    4 drwxrwx---   1 myadminuser    smbsh        4096 Nov 26 20:44 /srv/windows-data/Documents
  9459    4 drwxrwx---   1 myadminuser    smbsh        4096 Sep 13  2013 /srv/windows-data/Music
  9458    4 drwxrwx---   1 myadminuser    smbsh        4096 Sep 13  2013 /srv/windows-data/Pictures
107755    0 drwxrwx---   1 myadminuser    smbsh           0 Oct  1 22:19 /srv/windows-data/Projects
  9781    4 drwxrwx---   1 myadminuser    smbsh        4096 Jun 12  2013 /srv/windows-data/Shared
    35    4 drwxrwx---   1 myadminuser    smbsh        4096 Dec 10 16:46 /srv/windows-data/System\ Volume\ Information
  9460    4 drwxrwx---   1 myadminuser    smbsh        4096 Oct 10 22:20 /srv/windows-data/Videos
     5    4 drwxrwx---   1 myadminuser    smbsh        4096 Dec 11 21:14 /srv/windows-portable
    37    0 drwxrwx---   1 myadminuser    smbsh           0 Apr  6  2013 /srv/windows-portable/$RECYCLE.BIN
  2830    0 drwxrwx---   1 myadminuser    smbsh           0 Nov  6 21:28 /srv/windows-portable/General
  2902    0 drwxrwx---   1 myadminuser    smbsh           0 Dec 22  2012 /srv/windows-portable/Internet
    94    4 drwxrwx---   1 myadminuser    smbsh        4096 Aug 26  2013 /srv/windows-portable/Media
  2785    4 drwxrwx---   1 myadminuser    smbsh        4096 Dec 22  2012 /srv/windows-portable/Scripts
  2809    4 drwxrwx---   1 myadminuser    smbsh        4096 Dec 22  2012 /srv/windows-portable/Shortcuts
    35    0 drwxrwx---   1 myadminuser    smbsh           0 Dec 10 16:46 /srv/windows-portable/System\ Volume\ Information
     2    4 drwxrwx---   9 myadminuser    smbsh        4096 Mar  8 10:22 /srv/documents
3891201    4 drwxrwx---   2 myadminuser    smbsh        4096 Jan  4 22:35 /srv/documents/user1
85499905    4 drwxrwx---   9 myadminuser    smbsh        4096 Mar  6 20:28 /srv/documents/user2
35962881    4 drwxrwxr-x  58 myadminuser    smbsh        4096 Feb 23 17:49 /srv/documents/pictures
    13    4 -rwxrw----   1 myadminuser    smbsh          96 Mar  8 10:22 /srv/documents/View.xml
117850113    4 drwxrwx---  14 myadminuser    smbsh        4096 Mar 15 00:44 /srv/documents/series
100515841    4 drwxrwx---   4 myadminuser    smbsh        4096 Jan  4 23:07 /srv/documents/documents
    11   16 drwx------   2 root     root        16384 Dec 20 20:05 /srv/documents/lost+found
16670721    4 drwxrwx---  13 myadminuser    smbsh        4096 Mar 16 14:40 /srv/documents/music
     2    4 drwxrwxr-x   4 myadminuser    smbsh        4096 Jan 29 22:29 /srv/movies-a
92536833    4 drwxrwxr-x  28 myadminuser    smbsh        4096 Mar  8 19:52 /srv/movies-a/Movies
119799809    4 drwx------   2 root     root         4096 Dec  1 10:07 /srv/movies-a/lost+found
     5   16 drwxrwx---   1 myadminuser    smbsh       16384 Dec 11 21:15 /srv/windows-os
 71646    0 drwxrwx---   1 myadminuser    smbsh           0 Feb 27  2013 /srv/windows-os/MSOCache
 73349    0 drwxrwx---   1 myadminuser    smbsh           0 Apr  6  2013 /srv/windows-os/$Recycle.Bin
 59891    0 drwxrwx---   1 myadminuser    smbsh           0 Dec 22  2012 /srv/windows-os/AMD
 58901    4 drwxrwx---   1 myadminuser    smbsh        4096 Apr  7  2013 /srv/windows-os/Boot
 58952  376 -rwxrwx---   1 myadminuser    smbsh      383786 Nov 21  2010 /srv/windows-os/bootmgr
 58963    8 -rwxrwx---   1 myadminuser    smbsh        8192 Apr  7  2013 /srv/windows-os/BOOTSECT.BAK
139532    0 lrwxrwxrwx   2 myadminuser    smbsh          60 Jul 14  2009 /srv/windows-os/Documents\ and\ Settings -> /srv/windows-os/Users
 63786    4 drwxrwx---   1 myadminuser    smbsh        4096 Apr 28  2013 /srv/windows-os/drivers
  3660    4 drwxrwx---   1 myadminuser    smbsh        4096 Nov 24 01:10 /srv/windows-os/fastboot
 58976 6290776 -rwxrwx---   1 myadminuser    smbsh    6441754624 Dec 12 21:37 /srv/windows-os/hiberfil.sys
 58983 8387704 -rwxrwx---   1 myadminuser    smbsh    8589008896 Dec 12 21:37 /srv/windows-os/pagefile.sys
 73351    0 drwxrwx---   1 myadminuser    smbsh           0 Jul 14  2009 /srv/windows-os/PerfLogs
 73354   12 drwxrwx---   1 myadminuser    smbsh       12288 Dec 11 20:53 /srv/windows-os/Program\ Files
 85774   20 drwxrwx---   1 myadminuser    smbsh       20480 Dec 11 20:53 /srv/windows-os/Program\ Files\ (x86)
112287    8 drwxrwx---   1 myadminuser    smbsh        8192 Dec 11 20:52 /srv/windows-os/ProgramData
 22087    0 drwxrwx---   1 myadminuser    smbsh           0 Apr  6  2013 /srv/windows-os/Recovery
 15974   16 drwxrwx---   1 myadminuser    smbsh       16384 Dec 11 22:39 /srv/windows-os/System\ Volume\ Information
119943    4 drwxrwx---   1 myadminuser    smbsh        4096 Dec 11 20:51 /srv/windows-os/Users
120384   24 drwxrwx---   1 myadminuser    smbsh       24576 Dec 11 20:34 /srv/windows-os/Windows
     2    4 drwxrwx---  15 myadminuser    smbsh        4096 Mar  8 16:29 /srv/download-a
79953921    4 drwxrwx---   2 myadminuser    smbsh        4096 Mar 19 01:06 /srv/download-a/series_mp4
106168321    4 drwxrwx---   2 myadminuser    smbsh        4096 Mar 19 03:07 /srv/download-a/.downloading
107216897    4 drwxrwx---   7 myadminuser    smbsh        4096 Dec  1 00:41 /srv/download-a/transmission
120324097    4 drwxrwx---   7 myadminuser    smbsh        4096 Mar 12 09:42 /srv/download-a/series_season
70254593    4 drwxrwx---   9 myadminuser    smbsh        4096 Dec  1 00:43 /srv/download-a/music
    11   16 drwx------   2 root     root        16384 Dec 20 20:00 /srv/download-a/lost+found
13893633    4 drwxrwx---   2 myadminuser    smbsh        4096 Feb  9 18:00 /srv/download-a/other
116391937    4 drwxrwx---   4 myadminuser    smbsh        4096 Mar 12 00:23 /srv/download-a/movies
81264641    4 drwxrwx---   4 myadminuser    smbsh        4096 Feb  9 17:59 /srv/download-a/.downloaded
65011713    4 drwxrwx---   5 myadminuser    smbsh        4096 Jan  5 01:32 /srv/download-a/sickbeard
41680897    4 drwxrwx---   4 myadminuser    smbsh        4096 Feb  7 22:23 /srv/download-a/flexget
7077889   20 drwxrwx---   2 myadminuser    smbsh       20480 Mar 19 03:07 /srv/download-a/series
57933825    4 drwxrwx---   2 myadminuser    smbsh        4096 Jan  5 00:14 /srv/download-a/.watching
     5   16 drwxrwxr-x   1 myadminuser    smbsh       16384 Mar 11 19:58 /srv/movies-b
  1874    4 drwxrwxr-x   1 myadminuser    smbsh        4096 Mar  8 17:23 /srv/movies-b/ACTION
    42    4 drwxrwxr-x   1 myadminuser    smbsh        4096 Mar  8 17:25 /srv/movies-b/ANIMATION
  1902    4 drwxrwxr-x   1 myadminuser    smbsh        4096 Jan  4 23:23 /srv/movies-b/COMEDY
  1873    4 drwxrwxr-x   1 myadminuser    smbsh        4096 Mar 11 19:58 /srv/movies-b/COMICS
  1877    4 drwxrwxr-x   1 myadminuser    smbsh        4096 Jan  4 23:23 /srv/movies-b/CRIME
  1869    4 drwxrwxr-x   1 myadminuser    smbsh        4096 Mar  8 17:28 /srv/movies-b/DRAMA
    52    4 drwxrwxr-x   1 myadminuser    smbsh        4096 Mar  8 17:29 /srv/movies-b/EASTERN
  1867    4 drwxrwxr-x   1 myadminuser    smbsh        4096 Jan  4 23:23 /srv/movies-b/HISTORY
  1657    4 drwxrwxr-x   1 myadminuser    smbsh        4096 Mar  8 17:34 /srv/movies-b/QUENTIN\ TARANTINO
  1868    4 drwxrwxr-x   1 myadminuser    smbsh        4096 Mar  8 17:34 /srv/movies-b/SCI-FI
  1875    4 drwxrwxr-x   1 myadminuser    smbsh        4096 Mar  8 17:41 /srv/movies-b/SPORT
  1870    4 drwxrwxr-x   1 myadminuser    smbsh        4096 Mar  8 17:43 /srv/movies-b/THRILLER
    65    1 -rwxrwxr-x   1 myadminuser    smbsh          96 Mar 11 19:58 /srv/movies-b/View.xml
  1936    4 drwxrwxr-x   1 myadminuser    smbsh        4096 Jan  4 23:23 /srv/movies-b/WAR
  1663    4 drwxrwxr-x   1 myadminuser    smbsh        4096 Mar  8 18:14 /srv/movies-b/WESTERN
     2    4 drwxrwx---   3 myadminuser    smbsh        4096 Mar  4 18:26 /srv/download-b
    11   16 drwx------   2 root     root        16384 Dec 15 22:52 /srv/download-b/lost+found


```
So I feel like this output deserves some explication :D

First of all, the (ex) Windows partitions, I converted this desktop from Windows 7 workstation to a Ubuntu Home/File Server. In case I'd ever need one of my old files, I mounted the old partitions and made them available through samba.
Second of all, my movies and my downloads require most space so I took two drives for each of them. For movies I have a drive for seen movies that I'd like to keep and a drive for unseen movies. For downloads I have one drive to be used as short term storage (e.g. single episode torrents) and one for long term storage (e.g. my own uploads). The backup scripts are not yet in place so that one is empty for now. Finally, for the last mountpoint, the name "documents" is not perfectly chosen but this is meant to be a collection of all other things I'd like to share. Eventually each sub directory should be a Samba share. I hope that's clear?

Then the command with "all my users and groups".
```

smbsh:x:2000:user1,user2,plex
debian-transmission:x:118:myadminuser,user1

```
Regarding the groups, I'm open for new ideas...

Now what I want...
```

[TABLE]
[TR]
[TD]User[/TD]
[TD]Directory[/TD]
[TD="align: center"]Local[/TD]
[TD="align: center"]Samba[/TD]
[TD="align: center"]NFS[/TD]
[TD="align: center"]SFTP[/TD]
[/TR]
[TR]
[TD]myadminuser[/TD]
[TD]/srv[/TD]
[TD]rwx[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD]user1[/TD]
[TD]/srv[/TD]
[TD]N/A[/TD]
[TD]rwx[/TD]
[TD]N/A[/TD]
[TD]rw-[/TD]
[/TR]
[TR]
[TD]user2[/TD]
[TD]/srv/movies-a[/TD]
[TD]N/A[/TD]
[TD]r-x[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/movies-b[/TD]
[TD]N/A[/TD]
[TD]r-x[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/documents/series[/TD]
[TD]N/A[/TD]
[TD]r-x[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/documents/pictures[/TD]
[TD]N/A[/TD]
[TD]rwx[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/documents/user1[/TD]
[TD]N/A[/TD]
[TD]rwx[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/documents/music[/TD]
[TD]N/A[/TD]
[TD]r-x[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/documents/documents[/TD]
[TD]N/A[/TD]
[TD]rwx[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD]mediaplayer[/TD]
[TD]/srv/movies-a[/TD]
[TD]N/A[/TD]
[TD]r-x[/TD]
[TD]r-x[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/movies-b[/TD]
[TD]N/A[/TD]
[TD]r-x[/TD]
[TD]r-x[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/documents/series[/TD]
[TD]N/A[/TD]
[TD]r-x[/TD]
[TD]r-x[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/documents/pictures[/TD]
[TD]N/A[/TD]
[TD]r-x[/TD]
[TD]r-x[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/documents/music[/TD]
[TD]N/A[/TD]
[TD]r-x[/TD]
[TD]r-x[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD]plex[/TD]
[TD]/srv/movies-a[/TD]
[TD]r-x[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/movies-b[/TD]
[TD]r-x[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/documents/series[/TD]
[TD]r-x[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/documents/pictures[/TD]
[TD]r-x[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/documents/music[/TD]
[TD]r-x[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD]transmission[/TD]
[TD]/srv/download-a/.downloading[/TD]
[TD]rw-[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/srv/download-a/.downloaded[/TD]
[TD]rw-[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[/TR]
[/TABLE]

```
So, in short, I have the local admin user which I use solely to administer the server through SSH. Then I have my regular user for file access through Samba and SFTP (a.t.m. only meant for me). Then there is my girlfriend who only should have limited access to certain shares and to other she can have full access. Then there is the plex user who only needs to have read and execute permissions locally (I think). I also have my mede8er for which I want a separate user witch read and execute permissions to all the media files (except for downloads ofc.) through both Samba as NFS. And at last I'd like transmission to run as a separate user with read and write access to the folders it writes to.
If possible I'd like the whole thing to be future proof, if I'd ever want to add access through SCP (not likely) then (for example) I'd like to be able to specify the permissions per user.

I hope I'm not asking too much? If you'd have any more questions, please do not hesitate to ask me ;)

---

### Post by Leegaert on 2014-03-19
Hi LHammonds,

Thank you for your input, now I know what TheFu meant with that kinda script.
I'll be surely looking into that (once I've get everything in order as you said)!

Thanks for the example as well!

---

### Post by bab1 on 2014-03-19
> **Leegaert said:**
> Hi LHammonds,

Thank you for your input, now I know what TheFu meant with that kinda script.
I'll be surely looking into that (once I've get everything in order as you said)!

Thanks for the example as well!

If I may, @TheFu is correct.  You do not need any cron jobs and scripts to maintain the proper group inheritance.  Just set the SGID bit  and set the permissions on the directory that ithe root of the share and create the share with force group.  See [here at post #22]("http://ubuntuforums.org/showthread.php?t=2211174&page=3") for complete instructions.  I've set this up countless times over the years.  It always works.

---

### Post by Leegaert on 2014-03-20
Hi bab1,

Thanks for the tip, I tried it out and it worked. But how do I force the exact same permissions everywhere? I want them to be 770 with same owner and same group.

---

### Post by TheFu on 2014-03-20
chgrp -R
chmod -R
chown -R

Be careful.

Also - 770 is probably NOT what you want everywhere from my reading of your needs.  Data files probably need to be 660 or 664.  Directories probably need to be 775 - with the set-groupID set on them all.

Be very careful with this stuff.

---

### Post by Leegaert on 2014-03-20
Hi again,

I'm aware of the recursive option. I meant, how can I make sure that the owner and group and permissions all stay the same when new files are created?
And you're right about the permissions :) I think I'm just going to start over and put a structure on paper first.

I looked into the mount --bind. Would it be a good idea to mount the (e.g.) NFS shares that I want to share to /export/?
For example... /srv/download-a to /export/download-a?

---

### Post by TheFu on 2014-03-20
If you want the owner to be the same - use the same account.
If you want the group to be the same - set-gid on the directory AND have the userid placing files there be in the group.

No - I don't think a mount-bind is a good idea.

This is Linux - there are 50 ways to accomplish a goal. My opinion is just that. My opinion.  Only you can decide how much work you are willing to put into this effort.  It is just media - well most of it. No need to be too complex, IMHO.

---

### Post by bab1 on 2014-03-20
> **Leegaert said:**
> Hi bab1,

Thanks for the tip, I tried it out and it worked. But how do I force the exact same permissions everywhere? I want them to be 770 with same owner and same group.
What do you mean by everywhere?  There is no reason to do this in any part of the file system other than the part that is shared.

The default ext4 permissions are set via umask.  If you are mounting an NTFS then the equivalent to umask is set in the mount command.

Samba can set the permissions when a file or directory is created.  But Samba is again, only used for the shared directories.

Once again -- Where do you want these 770 permissions to be?  What objects are you referring to.  Files could be 660 (they should not be 7 anything unless they are executable.  The directories should be 770 or 775 or 755.  They need the executable bit set so the users can see into the directory and descend into those directories.

---

### Post by bab1 on 2014-03-20
> **Leegaert said:**
> Hi again,

I'm aware of the recursive option. I meant, how can I make sure that the Edit: and group and permissions all stay the same when new files are created?
[COLOR="#0000FF"]Edit:  There is no need to worry about the user ownership.  The group ownership is the important part.  The leading 2 on the permissions ( [/COLOR][COLOR="#FF0000"]2[/COLOR][COLOR="#0000FF"]775) sets the SGID bit and all files and directories below that are created with the same group as the one you set the SGID on.[/COLOR]> 
And you're right about the permissions :) I think I'm just going to start over and put a structure on paper first.


Umask handles this outside of the share.  Inside the share you only need to change these settings in the share definition```
        create mask = 0664
        force directory mode = 2775

```
> 

I looked into the mount --bind. Would it be a good idea to mount the (e.g.) NFS shares that I want to share to /export/?
For example... /srv/download-a to /export/download-a?

Mount bind allows you to mount a directory to another directory (a mount point).  The default mount is use to mount a partition to a mount point.

---

### Post by Leegaert on 2014-03-21
> **TheFu said:**
> If you want the owner to be the same - use the same account.
If you want the group to be the same - set-gid on the directory AND have the userid placing files there be in the group.

No - I don't think a mount-bind is a good idea.

This is Linux - there are 50 ways to accomplish a goal. My opinion is just that. My opinion.  Only you can decide how much work you are willing to put into this effort.  It is just media - well most of it. No need to be too complex, IMHO.
I get what you're saying, the way I want to set it up right now is too complex for what I need. But I'm trying to improve my knowledge of Linux and this setup is a project for me. That's why I want to do it right, I make it complex so I can learn new things. Thank you for the tips you gave me! I will use the set-gid.


> **bab1 said:**
> What do you mean by everywhere? There is no reason to do this in any part of the file system other than the part that is shared.

The default ext4 permissions are set via umask. If you are mounting an NTFS then the equivalent to umask is set in the mount command.

Samba can set the permissions when a file or directory is created. But Samba is again, only used for the shared directories.

Once again -- Where do you want these 770 permissions to be? What objects are you referring to. Files could be 660 (they should not be 7 anything unless they are executable. The directories should be 770 or 775 or 755. They need the executable bit set so the users can see into the directory and descend into those directories.
With everywhere, I didn't target the whole file system but the entire shared structure, in my case /srv.

I was mistaken with the 770 permissions, like you and TheFu said, It'd better with 660/664 for files and 770/775 with the set-gid for directories.


> **bab1 said:**
> [COLOR=#0000FF]Edit: There is no need to worry about the user ownership. The group ownership is the important part. The leading 2 on the permissions ( [/COLOR][COLOR=#FF0000]2[/COLOR][COLOR=#0000FF]775) sets the SGID bit and all files and directories below that are created with the same group as the one you set the SGID on.[/COLOR]
Umask handles this outside of the share. Inside the share you only need to change these settings in the share definition```
        create mask = 0664
        force directory mode = 2775

```


Mount bind allows you to mount a directory to another directory (a mount point). The default mount is use to mount a partition to a mount point.
Just for clarification, the first part is about local file system and the second part is about Samba right?
Let me rephrase that, assuming that "my share" is /srv.
[LIST=1]
[*]I set the directory permissions recursively to 2770 and the file permissions to 2660 on /srv
[*]The umask is meant for the default permissions on the local file system
[*]The create mask and force directory mode enforce the permissions when files/folders are created through Samba
[/LIST]


There are some other things I still don't quite get but I'll keep them specific instead of one general question:
[LIST=1]
[*]**More advanced permissions**
Let's say I have three users (user1, user2, user3). I have a file (file1). The details of the file are as follows:
```
-rw-rw---- 1 user1 user1 288 2014-03-21 13:45 /tmp/ex/file1
```
Is there any way I can give user2 ro access and user3 rw access to this file while user1 maintains its current rights?
[*][B]NFS share
[/B]Is there any way I can make an NFS share without giving "everybody" read permissions (i.e. 664 permissions instead of 660 on my shared folder) without using NIS/LDAP?
[*]**Mount bind**
What is this used for? I read about it in the [Ubuntu NFS documentation]("https://help.ubuntu.com/community/SettingUpNFSHowTo").
[*][B]Partition mounts
As far as my structure goes, I think I'm gonna make some changes.
[/B]For example for movies, now I'm using /srv/movies-a and /srv/movies-b. I'm thinking about changing it like this: /srv/movies and /srv/movies/_seen.
[/LIST]


What I actually wanted to get out of this topic is a set of guidelines/best practices of how to structure that part of the filesystem that you want to share amongst multiple users with different permissions through different methods (Samba, FTP, NFS).
I already learned some things out of this topic, so thank you for that!

---

### Post by TheFu on 2014-03-21
```
-rw-rw---- 1 user1 user1 288 2014-03-21 13:45 /tmp/ex/file1
```

Is there any way I can give user2 ro access and user3 rw access to this file while user1 maintains its current rights?

* create a group with user1 and user3 - grp1
* chgrp grp1 /tmp/ex/file1
* chmod 664 /tmp/ex/file1

In all your permissions planning don't forget the "other" parts.  It isn't like someone on your system isn't approved, right?

NFS - permissions for NFSv3 are based on uid/gid matching between the systems involved. File/directory permissions work exactly the same unless NFS mount options are changed (like read-only mount).
I haven't used NFSv4 - but it might mandate the use of LDAP (NIS is not secure enough for you based on your other comments).

Like with every OS, the more complex we make things, the harder it is to manage those things going forward. Complexity is the enemy of maintainability.

/srv/movies/_seen seems like a good idea, until you hook up any media player with a DB. Then every time files are moved around, the metadata gets lost. It works this way for Plex, XBMC, others ... just sayin'. 

The best practice for file permissions is to place files by required permissions in different directory structures. Think [user], [group], [other] style permissions when you try to create this structure. Simplify.

mount-binds have many interesting uses that are not intuitively obvious.  I've never needed to use this tool anywhere for longer than a few minutes, but that doesn't mean it isn't useful for others in a long term situation.  Still, I'd rather see this tool used over ACLs - the first time you forget about the ACLs is when you need to do something quick, it doesn't work, but you have completely forgotten about the ACLs on the files.  SELinux is another tool that can be used with ACLs to mess with users.  It is about maintainability for me.  

There are places for these tools - at home, I'd do it in test areas until gaining a 100% understanding of the longer-term issues.

---

### Post by bab1 on 2014-03-21
> **Leegaert said:**
> ...

Just for clarification, the first part is about local file system and the second part is about Samba right?

All of this is about the permissions set upon the file system in question.  That is; the "local" mount or "remote mount" of partitions to the file system.  When the system is booted up the mount procedure is in charge of assembling the file system as the user will see and use it.  The first part is configured via the fstab file.  Then other methods.  The data that is on any partition has **no user or group ownership** until it is mounted.  The ownership is determined at mount time.  The EXT2/3/4 style of formatting determines the file ownership internally via the mount point ownership settings.  With other formats you need to explicitly define the ownership at mount time (e.g. NTFS).

To answer your question more directly; yes in a general way.
> 

Let me rephrase that, assuming that "my share" is /srv.
[LIST=1]
[*]I set the directory permissions recursively to 2770 and the file permissions to 2660 on /srv
[*]The umask is meant for the default permissions on the local file system
[*]The create mask and force directory mode enforce the permissions when files/folders are created through Samba
[/LIST]

Yes except for the following:
The umask is applied to **all file or directory objects** that are created in the mounted file system (local or remote)
> 

There are some other things I still don't quite get but I'll keep them specific instead of one general question:

Let's say I have three users (user1, user2, user3). I have a file (file1). The details of the file are as follows:
```
-rw-rw---- 1 user1 user1 288 2014-03-21 13:45 /tmp/ex/file1
```
Is there any way I can give user2 ro access and user3 rw access to this file while user1 maintains its current rights?

Linux permissions have three classes of users (i.e. user, group and others).  You could have ```
user1=owner=rw, user3=group=rw, user2=others=rw
```
It's important to point out that user1 and user3 have the same permissions so you could have this also ```
user2=owner=r, user1 and user3=group=rw 
```...and still have the same abilities to manipulate the file.  The design is incorrect on the second one and it will cause you pain down the road, but it shows you that the owner, group and others defined only by their permissions granted.
> 

**NFS share**
Is there any way I can make an NFS share without giving "everybody" read permissions (i.e. 664 permissions instead of 660 on my shared folder) without using NIS/LDAP?

There are no 'permissions on a share".  Permissions are added at creation time in the context of the environment.  For example, on a Ubuntu host with an ext4 file system all files are created with 666 permissions.  With the umask applied (0002) the end result is a file with 0664 permissions.  If this is the same Ubuntu host with a NTFS file system mounted into the local system and you create a file in the NTFS partition the file is created with 0666 permissions and the directives in the mount point create the umask filter for the end result.  The directives are built into the NTFS-3g driver that Ubuntu uses.

More importantly, you shouldn't worry about what the permission are on newly created files/directories.  Think of the root folder of a share as a locked doorway.  Anything beyond the door is private to those you let in.  If you were to create a directory and set the permissions to 700 (you as the owner) and create files inside that directory with 777 permissions, no user but you could manipulate the files you created because they can't get to the files.
> 
**Mount bind**
What is this used for? I read about it in the [Ubuntu NFS documentation]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

In the NFS share context this is used to place the users directories in the /exports directory (mount a directory to a mount point).  You could just have a the data in the /exports directory.  I keep all my data at /srv and mount via bind the directory where the data is stored to /exports.  
> 

[B]Partition mounts
As far as my structure goes, I think I'm gonna make some changes.
[/B]For example for movies, now I'm using /srv/movies-a and /srv/movies-b. I'm thinking about changing it like this: /srv/movies and /srv/movies/_seen.

I thought that's what XBMC or Plex would do for you.  
> 
What I actually wanted to get out of this topic is a set of guidelines/best practices of how to structure that part of the filesystem that you want to share amongst multiple users with different permissions through different methods (Samba, FTP, NFS).
I already learned some things out of this topic, so thank you for that!
To me the guiding point is to design the most simple structure that I can with the privacy concerns needed for the circumstances.  I have to trust that public shares (group rw access) are insecure by definition.

On the other hand...
Linux does have file/directory ACL's and you can have differing permissions for multiple users on the same file/directory.  I hate them.  They are messy and can lead to complex structures.  But they can help you out if needed.

---

### Post by Leegaert on 2014-03-22
@TheFu,

Hm, I think I was not a big fan of using "the others". But like you said, there isn't anyone unapproved on my system...
I don't think I'll be needing the LDAP so I'll be looking for an alternative there. Maybe a downgrade to v3?

Thanks for all the other tips as well!


@bab1,

Thanks for the detailed explanation, this helps me a lot! I was always worrying about the newly created file/directory permissions, the "locked door" comparison made me understand!


So, I know what to do now, I'm gonna start implementing all of this!
Thanks again for all your time and tips!

---

### Post by TheFu on 2014-03-22
The main issue with NFSv3 is that IP addressing is the only real security.  Anyone can claim an IP on a subnet if there is a physical connection and with that, they can become any userid (even root), unless you limit the remote userids and definitely prevent root.  In a home, this isn't too bad, IMHO.  Even inside a data center, if the servers are on their own LAN, separate from every other network, it can work, but if the internet gets involved with the servers, there are just too many attack vectors to be considered safe.

OTOH, NFSv3 is next to trivial to setup once understood.

Anyway, glad to have helped.  Bab1 is the man when it comes to samba stuff.

---

