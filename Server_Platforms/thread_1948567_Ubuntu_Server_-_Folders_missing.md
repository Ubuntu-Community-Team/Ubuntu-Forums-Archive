---
title: "Ubuntu Server - Folders missing"
date: 2012-03-28
forum: Server Platforms
---

### Post by darknoobie on 2012-03-28
Good morning, I recently got a job as a network admin. We have some really old storage/web servers. They keep crashing and it results to data loss on a monthly basis. The company currently cannot afford to purchase thousands of dollars of Microsoft licenses. I proposed a ubuntu storage server. They like the cost \\:D/ , but they did not like the idea that if I left the next IT possibly wouldn't know how to maintain it. The server currently runs samba and openssh. I installed webmin and wrote a maintenance tutorial for anyone who will need to maintain it in the future. 
I have two 2TB hard drives. One mounted on /data and the other on /backup. 

cron job:
30 0 * * * sudo rsync -av /data /backup 

When I got to work in the morning I saw that rsync had ran successfully. I powered the server down and set it into the server closet. I powered it on and opened a ssh from my workstation.

This is what I get:
```
administrator@storage:/data$ ls
lost+found  
administrator@storage:/data$ cd /backup
administrator@storage:/backup$ ls
lost+found
administrator@storage:/backup$

```

df command:
```
administrator@storage:/$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            476982272   1427096 451325800   1% /
udev                   1824504        12   1824492   1% /dev
tmpfs                   733320      1356    731964   1% /run
none                      5120         0      5120   0% /run/lock
none                   1833300         0   1833300   0% /run/shm
/dev/sdb1            1922859824  11650376 1813533776   1% /data
/dev/sdc1            1922859824    200028 1824984124   1% /backup
```

blkid command:

```
administrator@storage:/$ sudo blkid
/dev/sda1: UUID="4d46e2fc-bbd3-40c0-afcc-ad570a1d4447" TYPE="ext4"
/dev/sda5: UUID="a0ed4cc6-26eb-46c2-bd78-5ffbcb19bcfb" TYPE="swap"
/dev/sdb1: UUID="476dbe8f-9dfa-418c-9f97-604f2ccd2453" TYPE="ext4"
/dev/sdc1: LABEL="Backup" UUID="ef8c5944-b8c7-49c3-9188-d175101bec98" TYPE="ext4"
```

fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4d46e2fc-bbd3-40c0-afcc-ad570a1d4447 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a0ed4cc6-26eb-46c2-bd78-5ffbcb19bcfb none            swap    sw              0       0
UUID=476dbe8f-9dfa-418c-9f97-604f2ccd2453 /data ext4 defaults 0 0
UUID=ef8c5944-b8c7-49c3-9188-d175101bec98 /backup ext4 defaults 0 0

```

I cant seem to find out why that happened.

---

### Post by collisionystm on 2012-03-28
post your rsync command please

---

### Post by collisionystm on 2012-03-28
Also, may I suggest you look at Zentyal? It to is based on 10.04 LTS. It has a nice proprietary web gui, a lot of features and very easy ldap function. It is free to use but also has the option of paid support and training. Its what I use. I am also the lone ranger system admin for over 100 people and 8 sites. I have everyone running on Zentyal from the main office here and each individual site has a Dell desktop running Ubuntu 10.04 Server and OpenVPN to link us all together.

---

### Post by collisionystm on 2012-03-28
Should you ever decide to use Ubuntu/Zentyal whatever has your domain controller, here is the .reg file I have found to be the best so far. It is needed to join Win7 and Server 2008 to a Samba domain.

---

### Post by papibe on 2012-03-28
Hi darknoobie

Congratulations on the new job ):P

'sudo' is an interactive command, so it won't work on cron. If you need to run a script as root, I'd suggest you to create a crontab specifically for root. That is as simple as:
```
sudo crontab -e
```
Paste the rsync command you are using, and you should be ready to go.

Now, If I were you, I would run the rsync command on a script:
```
30 0 * * *   /path/to/script.sh
```
and script.sh would be:
```
#!/bin/bash
/usr/bin/rsync -a --log-file=/path/to/logfile.txt /data /backup
```
This is my personal preference for a few of reasons:
[LIST]
[*]cron is a limited environment so I avoid scripting on it.
[*]I use full paths because even I'm using bash, sometimes it does not inherit all of the 'regular' paths.
[*]In case you need to add complexity to the script, you have the full bash functionality to write it on.
[/LIST]
Note that I remove the verbose option since no one will see it. Instead, I would log the output to a file that can be later analysed if needed.
 
I hope that helps, and let us know how it goes.
Regards.

---

### Post by darknoobie on 2012-03-28
I got the crontab setup now and tested a rsync. It worked great. But Im still a little worried on why my files are missing from /data. I had the following folders:
co_data
engineering
documentcontrol

Now there gone. The rsync went through last night and this morning when I came into the office and checked it and it was synced correctly using cron. Both the /backup and /data had the same information. I powered the server down and moved it to the closet. When I powered on the computer all the data was gone and I was left with Lost+found folders in each.

---

### Post by CharlesA on 2012-03-28
> **collisionystm said:**
> Also, may I suggest you look at Zentyal? It to is based on 10.04 LTS. It has a nice proprietary web gui, a lot of features and very easy ldap function. It is free to use but also has the option of paid support and training. Its what I use. I am also the lone ranger system admin for over 100 people and 8 sites. I have everyone running on Zentyal from the main office here and each individual site has a Dell desktop running Ubuntu 10.04 Server and OpenVPN to link us all together.
+1.

Run fsck on the drives in question.

---

### Post by darknoobie on 2012-03-28
Does my configuration look good? Did I mount everything properly? Iv'e always setup Ubuntu this way and I hate to put it into work and next day its all gone. I added a few dummy folders and files, synced and reboot the server. Everything is there. Im going to continue testing it before I deploy it. :(

---

### Post by CharlesA on 2012-03-28
The mount looks good, I'd still run fsck on the drive and see what it says.

Oh and run this too:

```
df -h
```

---

### Post by darknoobie on 2012-03-28
Thank you so much fro all the help. just one more thing... is there any way to log just the errors on rsync?

---

