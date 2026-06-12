---
title: "Samba File server Mac OSX sees files as alias"
date: 2009-03-22
forum: Server Platforms
---

### Post by Almeister9 on 2009-03-22
[RESOLVED]
Hello All,

I have installed Ubuntu 8.10 Server and Samba and it is accessed by 1 Windows XP machine, 4 Mac OSX 10.5 Leopard machines and 4 Mac OSX 10.4 Tiger machines.

The office used to use a OSX 10.5 machine as a server with an external HDD but due to crashing and needing a complete re-install and being unable to use Time machine to retrieve files, we decided to go a dedicated Linux server.

The Linux box has two HDD's, a small one for Ubuntu 8.10, Samba and Pureftpd and a large one for Data.

Since the data was copied across, a problem has materialised.

The majority of the files on the Data drive are InDesign files. All users use version CS.
Quite randomly, when a OSX 10.5 client has an Indesign file open and they save it, It shows up in finder as an alias and cannot be opened. Trying to fix the alias by browsing to the file does not work.
However, If the Windows XP machine browses to the location, it sees the file as normal and can open it, no problem. If the XP machine then saves the file with a different name, then all the OSX clients can again open it.
This is also happening while the file is still opened by the OSX 10.5 clients.
Although it only happens when a OSX 10.5 machine has the file open, none of the mac machines are then able to open the file until it has been opened in XP and saved as a different filename.

I have also noticed that when I browse to the location using XP there is a hidden file stating with "._"

e.g. for a file called sp140_16-17 there will also bew a file called ._sp140_16-17
I have discovered that if I delete this ._ file from XP, the actual file then becomes open able by the macs.

This started happening 4 times a week but in the space of 4 weeks it now happens about 10 times a day.

And now another problem has started happening randomly, when any of the macs tries to open a file (InDesign) by double clicking it in Finder, it makes a copy of itself. The only way to get the actual file to open it is from within InDesign, using the Open File menu and tick the bullet "Open Original"

I originally set this server up using Ubuntu 8.04 LTS Server (4 weeks ago) and have since done a complete wipe and reinstall using 8.10 (last week) which means Samba is the latest version also.

The OS HDD and the DATA HDD have both been formatted with the ext3 file format.
I have setup up the Samba shares as No Authentication using

```
security = share
```

and adding the following to the Samba conf file:
```
[JAJA]
    comment = Ubuntu File Server Share
    path = /mnt/JAJA
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0777
```

when making the directory /mnt/JAJA i did this:
```
chmod 777 /mnt/JAJA
```

and afterward did this
```
chown nobody.nogroup /mnt/share
```

I found in another forum, someone suggest that it was the OSX 10.5 extended attributes that was causing the problem. He gave me some commands to see the extended attributes and to delete them, but the commands gave syntax errors.
He suggested browsing to the folder and typing
```
ls -l@
```
but that gives a syntax error
```
/mnt/JAJA/JAJA_DATA/Trade/SPwip/sp140wip/content$ ls -l@
ls: invalid option -- '@'
Try `ls --help' for more information.
```
followed by
```
xattr -d com.apple.FinderInfo my_sticky_file.indd
```
which also gives an error
```
/mnt/JAJA/JAJA_DATA/Trade/SPwip/sp140wip/content$ xattr -d com.apple.FinderInfo sp140_16-17(RoadshowFeature).indd
-bash: syntax error near unexpected token `('
```

The only constants to this problem are:

1. the alias problem is only caused by OSX10.5
2. Once caused, the problem affects 10.4 & 10.5
3. Windows XP is never affected.
4. Deleting the ._ file always cures the problem.

Is there a way to prevent Mac's from creating these ._ files on the Samba share in the first place, I feel that this would stop the problem occurring.

Any help or even clues to this would be greatly appreciated as it is the bane of my life at the moment.

Cheers AL

---

### Post by Yashiro on 2009-03-23
The file is either a thumbnail or some kind of spotlight metadata.
So perhaps disable those features on the Macs for that share, if possible.

Or run a cron job every 10s to remove any ._ files.

---

### Post by Almeister9 on 2009-03-24
We have now discovered that when InDesign files are moved from one folder to another (regardless of whether they have had there "._" files deleted or not), alot of the images in the InDesign files lose there linking information and need to be re-linked.

It seems as if when these InDesign Files are stored on the Samba Share, the important data contained within it is being damaged somehow.

At this point I should add that I have mounted the DATA HDD by placing this entry in /etc/fstab
```
/dev/sdb1 /mnt/JAJA ext3 defaults 0 0
```

---

### Post by Yashiro on 2009-03-24
It probably doesn't record the full paths correctly. This is not that surprising.

You would benefit from moving to a GUI based subversion system.
So people can 'check out' files then upload them when done.

This is preferable to a free for all Samba folder.

---

### Post by Almeister9 on 2009-03-24
Unfortunately, A "free for all" is exactly what is required.

The server used to be one of the OSX 10.5 machines and the office requires absolute ease of access, which, as far as I can tell, Samba should be able to deliver, and most of the time it is.

---

### Post by Yashiro on 2009-03-24
It's not really samba at fault though. It's the way the mac/adobe soft is saving the files. :)

---

### Post by Almeister9 on 2009-03-24
With the help of someone over at howtoforge/forums, we have now worked out what is causing this to happen.

The problem is extended attributes that is being saved with the file and it is a problem caused by Leopard 10.5.6

specifically this extended attribute:

```
com.apple.FinderInfo
```

extended attributes can be viewed with this command ls -l@

if the attribute is removed using:

```
xattr -d com.apple.FinderInfo filename.indd
```

then the problem goes away.

All we need to do now is work out how to stop the Leopard machines from writing these extended attributes to the Samba Share.

---

### Post by Yashiro on 2009-03-24
If it's Spotlight search/indexing metadata you should be able to disable it.

---

### Post by Almeister9 on 2009-03-24
From what I've read, you cannot easily disable Spotlight search/indexing metadata.

I don't think that this is the culprit anyway as Tiger 10.4 has the same Spotlight as Leopard 10.5 and Tiger does not create the extended attributes that are causing the problem namely:

com.apple.FinderInfo

only Leopard is doing this.

We need to find a way to either prevent Leopard from writing this extended attribute,
or cause the Samba server to prevent Leopard from being able to write this extended attribute.

I am very grateful for your suggestions on this though.

---

### Post by Yashiro on 2009-03-25
I guess if the server is in constant use running a delete on the files, or the otherfix, every few seconds (cron) would work until you find a better method. 

It is a generic Leopard quirk as you say. My iMac dumps all that rubbish on my share too. I just run a chown all, rm  ._* script every now and then. The Mac doesn't get used much though and it's never been an issue. I have read about similar problems to yours in the past though.

```
#!/bin/bash
cd /home/myname/Public/Uploads
pwd
sudo chown myname:mygroup *.*
rm ._*
rm .DS_Store
```

2 minute job. Never needed anything better myself.

---

### Post by Almeister9 on 2009-03-25
Again thanx for your suggestions,

Unfortunately, this is not the only problem that appears to be caused by the Leopard machines in the office.

When ever .indd files are moved from one folder to another on the Samba Share, most of the image links are broken and need to be re-linked, every time a file is moved by Leopard.

Also a spate of files copying themselves when you try to open them and opening the copy instead.

I have since turned my attentions to InDesign itself and found on the Adobe support site that InDesign CS2 and earlier are Incompatible with Leopard. We have purchase one copy of InDeisgn CS4 and Photoshop CS4 and are using it in a test environment to see if this fixes the problems.

Thanks again for your patience and help.
I am going now, to drown myself in a bucket of water.

---

### Post by Almeister9 on 2009-11-23
Im sorry for not getting back sooner.

Upgrading all machines to CS4 fixed ALL the problems.:popcorn:

---

