---
title: "Please help! Somehow moved root directory! Can't boot server"
date: 2011-11-20
forum: Server Platforms
---

### Post by ServerIssues on 2011-11-20
Hello everyone, 

Thanks so much for reading. I using Ubuntu 10.04 LTS Server edition to run a file server for my lab. I  was trying to install matlab and had the folder /mathworks_downloads/MathworksDownloads/ and I wanted the contents of MathworksDownloads to be moved up one level since I had copied that folder from somewhere else. I tried to use the command:

$/mathworks_downloads/MathworksDownloads/ sudo mv * ../

but I think I either had a space between the .. and the /, so maybe I did sudo mv *.. / or perhaps I somehow typed sudo mv /* .. I'm really not sure what I did. 

The result is that somehow I moved the root directory to who knows where. I couldn't use the command line anymore, because there were no directories to cd to or look into. I restarted and I am not able to boot into the machine. I tried to use the live CD to see if my data was still okay, but I couldn't find any of the right folders. 

About my server configuration: I'm very new to all of this, so my apologies if something doesn't make sense. I have three drives, sda(250GB), sdb(2TB), sdc (2TB). I created md0 and md1 so I could make sdb and sdc raid partitions. I had sdb0 and sdc0 as swap which pointed to part of sda0 and sdb1 and sdc1 as the file system, mount point was /-root and I pointed that somehow to sda1. I had sda1 as bootable. I really hope that makes sense. I thought everything made sense a few months ago I created it, but my documentation is terrible and now I don't remember. 

Any help/advice you might have would be greatly appreciated. I'm new to ubuntu and very new to the command line interface for the server edition. 

Thanks so much!
Ann

---

### Post by ServerIssues on 2011-11-20
Hey everyone, 

I didn't realize that I could use any ubuntu live cd so I used one with a gui and found my files. The raided drives seem to be intact and all the folders that used to be in root are now in the mathworks downloads folder. I had a symbolic link to the 2TB raided hard drives on in root, that link is broken, but I'm hoping to restore it when I copy the folders back to their rightful place. My plan is 1) try to backup whatever I can now, 2) Copy the root folders and links back to root. 3) Shutdown, remove the raided drives from the server, 4) see if the server reboots. 5) if so, put the raided drives back in an hope for the best. 

Will update this thread if it works. 

Thanks, 
Ann

---

### Post by LinuxFan999 on 2011-11-20
> **ServerIssues said:**
> Hello everyone, 

Thanks so much for reading. I using Ubuntu 10.04 LTS Server edition to run a file server for my lab. I  was trying to install matlab and had the folder /mathworks_downloads/MathworksDownloads/ and I wanted the contents of MathworksDownloads to be moved up one level since I had copied that folder from somewhere else. I tried to use the command:

$/mathworks_downloads/MathworksDownloads/ sudo mv * ../

but I think I either had a space between the .. and the /, so maybe I did sudo mv *.. / or perhaps I somehow typed sudo mv /* .. I'm really not sure what I did. 

The result is that somehow I moved the root directory to who knows where. I couldn't use the command line anymore, because there were no directories to cd to or look into. I restarted and I am not able to boot into the machine. I tried to use the live CD to see if my data was still okay, but I couldn't find any of the right folders. 

About my server configuration: I'm very new to all of this, so my apologies if something doesn't make sense. I have three drives, sda(250GB), sdb(2TB), sdc (2TB). I created md0 and md1 so I could make sdb and sdc raid partitions. I had sdb0 and sdc0 as swap which pointed to part of sda0 and sdb1 and sdc1 as the file system, mount point was /-root and I pointed that somehow to sda1. I had sda1 as bootable. I really hope that makes sense. I thought everything made sense a few months ago I created it, but my documentation is terrible and now I don't remember. 

Any help/advice you might have would be greatly appreciated. I'm new to ubuntu and very new to the command line interface for the server edition. 

Thanks so much!
Ann
You broke your Ubuntu install, soon the only option is to reinstall Ubuntu.
When you are done, type this:
```
sudo apt-get install ubuntu-desktop
```
Then, it will be easier to move directories around.

EDIT: sorry for my post being late.

---

### Post by oldos2er on 2011-11-21
Moved to Server Platforms.

---

### Post by Jonathan L on 2011-11-21
Hi Ann

Sounds like you're having an education!

> 

[LIST]
[*]raided drives seem to be intact
[*]all the folders that used to be in root are now in the mathworks downloads folder.
[*]I had a symbolic link to the 2TB raided hard drives on in root, that link is broken, but I'm hoping to restore it when I copy the folders back to their rightful place.
[/LIST]


Those sound good.  There's no reason to think you can't unpick what you did.  From your description, that the root directory things are now in the matworks folder, I think you did
```
mv /* ..
```
And .. would have been /mathworks_downloads


> 
My plan is 1) try to backup whatever I can now, 2) Copy the root folders and links back to root. 3) Shutdown, remove the raided drives from the server, 4) see if the server reboots. 5) if so, put the raided drives back in an hope for the best. 

it's a good plan.

To help you, here's a list of the root directory of a 10.04 server.
```
drwxr-xr-x  2 root root  4096 2010-12-28 06:39 bin
drwxr-xr-x  3 root root  4096 2010-12-28 06:40 boot
drwxr-xr-x 11 root root 12880 2011-08-18 19:26 dev
drwxr-xr-x 93 root root  4096 2011-11-21 12:09 etc
drwxr-xr-x 11 root root  4096 2011-11-19 12:36 home
lrwxrwxrwx  1 root root    30 2010-12-28 06:34 initrd.img -> boot/initrd.img-_2.6.32-311-ec2_
lrwxrwxrwx  1 root root    37 2010-12-28 06:34 initrd.img.old -> boot/initrd.img-_2.6.32-27-generic-pae_
drwxr-xr-x 18 root root 12288 2011-08-18 19:43 lib
drwx------  2 root root 16384 2010-12-28 06:28 lost+found
drwxr-xr-x  2 root root  4096 2010-12-28 06:28 media
drwxr-xr-x  2 root root  4096 2010-04-23 10:11 mnt
drwxr-xr-x  2 root root  4096 2010-12-28 06:28 opt
dr-xr-xr-x 78 root root     0 2011-08-18 19:26 proc
drwx------  3 root root  4096 2011-08-18 18:41 root
drwxr-xr-x  2 root root  4096 2010-12-28 06:40 sbin
drwxr-xr-x  2 root root  4096 2009-12-05 21:55 selinux
drwxr-xr-x  3 root root  4096 2011-08-18 18:43 srv
drwxr-xr-x 13 root root     0 2011-08-18 19:26 sys
drwxrwxrwt  4 root root  4096 2011-11-21 16:52 tmp
drwxr-xr-x 10 root root  4096 2010-12-28 06:28 usr
drwxr-xr-x 15 root root  4096 2011-08-18 18:42 var
lrwxrwxrwx  1 root root    27 2010-12-28 06:34 vmlinuz -> boot/vmlinuz-_2.6.32-311-ec2_
lrwxrwxrwx  1 root root    34 2010-12-28 06:34 vmlinuz.old -> boot/vmlinuz-_2.6.32-27-generic-pae_
```

(The underlined parts are likely to be different on your computer.)

If you need something else looked up, please let us know.

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by ServerIssues on 2011-12-29
Hi Everyone, 

Thanks for your help. I had to wait till the semester finished so I actually had time to work on this again, but I was able to successfully copy all the files back and the server is back to it's original state. Thanks again. 

Ann

---

