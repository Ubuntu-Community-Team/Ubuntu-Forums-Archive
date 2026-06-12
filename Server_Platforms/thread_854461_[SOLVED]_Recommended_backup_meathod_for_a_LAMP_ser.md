---
title: "[SOLVED] Recommended backup meathod for a LAMP server"
date: 2008-07-09
forum: Server Platforms
---

### Post by theonegod on 2008-07-09
I have seen reference to Bacula and Amanda in posts I have found on this subject but not much else. What would be the currently recommended, free if possible, and hopefully easy to use backup solution for an Ubuntu Server LAMP? 

I want to backup to a NAS and I want to do so in a way that will make restoration as fast and pain free as possible to minimize downtime if a full system restore is needed.

---

### Post by tech9 on 2008-07-09
you could backup the whole server to a zipped file using tar... not sure if that is recommended for servers though...


To backup:
 
```

**tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /**

```
To Restore:
```

[B]tar xvpfz backup.tgz -C /
[/B]
```

---

### Post by theonegod on 2008-07-09
Could anyone verify that this would be a okay method to use on a server? And that there is nothing else they would recommend?

---

### Post by unixbills on 2008-07-09
This is a big subject to try and cover in a few lines.  I am not a Linux backup expert but can give you an opinion.  We use a mix of tar and image utilities.

tar is an archive utility that works well but it is like a copy command.  You would need to put some scripting around it.  It is not a backup utility for the entire box.  It is a great way to make a copy of an entire box in case you missed something and need to get it back.  Our normal manual proceedure is tar.  We tar off the personality of the box.  Just critical files, mysql, web server, and things we need that too much to rebuild.  In a crash we would then do a fresh install from an image and install the packages like mysql and the web server.  Then we extract that tar file over the top to give it back it's old personality on the new box.  Keep in  mind this is still not without issues like every other hosts see's this as a new host id so ssh keys are all invalid etc.  So in my opinion tar is great but it is just a "zip" like tool.  I look at tar as a way to backup specific applications and directories (that are not running when you make the tar file) not a full backup or image utility.  I have all of my user setup and basic package adds scripted.  It takes me about an hour and a half to rebuild a typical server from scratch remotely.  The great part about this technique is it not OS specific.  I upgraded two DB's this morning from 7.10 to 8.04.1 with this method.

There are also packages like "partimaged" that makes an image of a entire partion.

Beyond this you may want to consider image utilities that image the entire system for a bare metal restore.

Everyone needs a backup - someone out here must know more about this subject then me.

Bill

---

### Post by theonegod on 2008-07-09
An image utility would be something I would be very interested in. I was looking at Acronis True Server Echo for Linux but it seemed to have a rather complicated install that included the need for me to mess around with some kernal tools.

Something with a simple install that either has its own web interface or works with webmin would also be nice. And of course easy of restoration of the entire box from a bare metal state is ideal.

---

### Post by cariboo on 2008-07-09
dd works well to make an exact image of your hard, by exact I mean with the empty space included, but it is an exact mirror image of your whole system. For more:

```
man dd
```

It is included in any distrtibution. Partimage is aslo a good alternative, it makes a copy of your partition excluding empty space. Install partimage and then:

```
man partimage
```

Jim

---

### Post by here2serve on 2008-07-13
I'm testing out Mondorescue right now. It's currently burning it's 3rd disk. I'll check back after I restore the system from the disks and let you know how it went.

---

### Post by here2serve on 2008-07-15
Ran Mondoarchive using it's defaults. Restored the system using the defaults.
Now it boots to a busybox prompt. No X but it looks like a of the files are there. No I don't want to fix this borked install. I'm just providing info on what works/doesn't work for me. I need to set up a bare metal intall so our MS only techs can drop in a disk and hit enter with out doing anything else.  

Prompt 
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)

(initranfs)

I going to do a fresh install and try some other options.

---

### Post by theonegod on 2008-07-21
DD and partimage require that I unmount the partition for backup, which I can not do as it is a live web server that must always be up. I think ghost or acronis may be the way I have to go. I just need to look into how to install them.

---

### Post by cdtech on 2008-07-21
I personally use "tar", I find it simple to script and no confusing software install or configurations.

I have mine setup to run a full backup once a week, incremental daily, and a full backup once on the first of every month. I use an external USB drive which is mounted ro during standby.

Restoring from tar is as simple as "tar -zxvpf /backup/full-backup.tar.gz /". You can use text files for which directories or partitions you want and dont want to backup. Using a third party backup solution would mean that you would need to reinstall the software in order to restore your backup I would think.

But to each his own..

Good luck.......

---

### Post by theonegod on 2008-07-21
That sounds like a very nice solution. One question. How do I mount a network share on my NAS so that I can use it as the tar destination? I have never tried to mount a netowrk share and am not sure how to go about it. 

I would like essentially to mount 
\\192.168.1.100\backup\Production
to 
/backup

---

### Post by cdtech on 2008-07-21
Using "fstab" you could mount it as:
```
//192.168.1.100/backup/Production	/backup cifs username=###,password=###	 0 0
```

---

### Post by theonegod on 2008-07-21
Do I just add that line to the bottom of /etc/fstab ?
And once I do this how do I make it live without rebooting?

Also in your code line I noticed you reversed the UNC slashes from \ to / Is that correct? I should use //192.168.1.11/Backup/Production and not \\192.168.1.100\Backup\Production?

---

### Post by cdtech on 2008-07-21
Correct, and issue the command "sudo mount -a" to mount the share....

---

### Post by theonegod on 2008-07-21
Awesome thanks :) that worked and the mount is in place. I will test tar now.

---

### Post by cdtech on 2008-07-21
Good luck..

---

### Post by windependence on 2008-07-22
> **theonegod said:**
> DD and partimage require that I unmount the partition for backup, which I can not do as it is a live web server that must always be up. I think ghost or acronis may be the way I have to go. I just need to look into how to install them.

You can ceratinly dd an image while the machine is running and mounted. I have done this lots of times, in fact this i how one of my clients makes backups. We dd the whole drive to another drive and then pull it.

Some things folks have misconceptions about. dd CAN copy a smaller drive to a larger drive just like ghost, you just have to have the correct command. 

You should be aware that if you back up databases while hot no matter what tools you use, you always run the risk of losing a bit of data. The only way to get a really good backup of a database, is to shut it down first. Taking an SQL dump of it works reasonably well also.

I will say this. All of the times I have dd'ed a database to another drive, I have never had any issues doing it hot. Of course, YMMV.

To dd to an image file:

```
dd if=/dev/sda1 of=/home/user/partition.image bs=4096 conv=notrunc,noerror
```

-Tim

---

