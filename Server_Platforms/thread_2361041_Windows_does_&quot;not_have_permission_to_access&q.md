---
title: "Windows does &quot;not have permission to access&quot; SAMBA share anymore"
date: 2017-05-11
forum: Server Platforms
---

### Post by xrintrahx on 2017-05-11
I'm running Ubuntu 17.04 Server, and I successfully installed SAMBA last week, and was able to access the share from a Windows 7 PC last week to transfer files onto the new drives. Since then, I have updated/upgraded, and installed a few packages, the most important probably being mergerFS, and created and mounted a pool of my drives. I'm not sure what broke SAMBA, but I am now getting the "Windows cannot access \\Server\ShareYou do not have permission to access \\server\Share." error message.  I tried adding the mergerFS pool to SAMBA, but have since commented it out. The only thing in the logs was related to that line:

```
[2017/05/11 09:24:59.394299,  0] ../source3/smbd/service.c:102(set_current_service)
  chdir (/storage) failed, reason: No such file or directory

```

But no errors in the log related to accessing the other 2 share points. And I have since commented out the pool /storage.

Testparm:
```
Load smb config files from smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Share1]"
Processing section "[Share2]"
Loaded services file OK.
Server role: ROLE_STANDALONE

```

Config:
```
# Global parameters
[global]
        server string = %h server (Samba, Ubuntu)
        log file = /var/log/samba/log.%m
        max log size = 1000
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        usershare allow guests = Yes
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        passwd program = /usr/bin/passwd %u
        server role = standalone server
        unix password sync = Yes
        dns proxy = No
        idmap config * : backend = tdb




[printers]
        comment = All Printers
        path = /var/spool/samba
        browseable = No
        printable = Yes
        create mask = 0700




[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers




[Share1]
        path = /mnt/data/disk1/
        create mask = 0777
        directory mask = 0777
        guest ok = Yes
        guest only = Yes
        read only = No




[Share2]
        path = /mnt/data/disk2/
        create mask = 0777
        directory mask = 0777
        guest ok = Yes
        guest only = Yes
        read only = No

```

I do not have login turned on for my windows machine, so I wanted to allow guest access with no login to these files. Just navigate via Windows explorer, and drag and drop. And this was working last week, but something has broken it. Any idea?

---

### Post by wildmanne39 on 2017-05-11
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2017-05-11
Please show us the permissions of those folders:
```
cd /mnt/data
ls -l
```

Linux permissions have to allow correct access for anonymous users too, not just samba permissions. It works on both levels and they are independent.

---

### Post by xrintrahx on 2017-05-11
```


drwxrwxrwx 7 nobody nogroup 4096 May 11 09:16 disk1
drwxrwxrwx 5 nobody nogroup 4096 May  4 16:24 disk2

```


Side question, I couldn't navigate to that directory with my user account. I had to elevate to root. I did this by "sudo su". I know it is recommended not to do this, so is there some other way I should be navigating to these directories? "sudo cd" is not a valid command.

---

### Post by darkod on 2017-05-11
If you needed to become root, that means on some level standard users have no permissions. And they need it, not just the folders shared, but all levels leading to them from /. This is why I would not create mount points for shares in /mnt. Mine are in /data for example.

Try checking permissions and ownership on all levels (become root is necessary):
```
sudo -i
cd /
ls -l
cd /mnt
ls -l
```

The permissions of disk1 and disk2 look ok, lets see above them in mnt and data.

---

### Post by xrintrahx on 2017-05-11
```

drwxr-xr-x   2 root   root     4096 May  5 15:15 bin
drwxr-xr-x   3 root   root     4096 May 10 19:22 boot
drwxr-xr-x  20 root   root     4120 May 11 10:12 dev
drwxr-xr-x  98 root   root     4096 May 11 10:11 etc
drwxr-xr-x   4 root   root     4096 May  7 16:31 home
lrwxrwxrwx   1 root   root       33 May  4 10:13 initrd.img -> boot/initrd.img-4.10.0-20-generic
lrwxrwxrwx   1 root   root       33 May  4 09:27 initrd.img.old -> boot/initrd.img-4.10.0-19-generic
drwxr-xr-x  23 root   root     4096 May  4 15:13 lib
drwxr-xr-x   2 root   root     4096 May  4 09:27 lib64
drwx------   2 root   root    16384 May  4 09:27 lost+found
drwxr-xr-x   3 root   root     4096 May  4 09:27 media
drwxr--r--   6 root   root     4096 May 11 09:13 mnt
drwxr-xr-x   2 root   root     4096 Apr 11 23:06 opt
drwxr-xr-x   3 root   root     4096 May  7 16:31 path
dr-xr-xr-x 189 root   root        0 May 11 10:12 proc
drwx------   6 root   root     4096 May 11 09:16 root
drwxr-xr-x  26 root   root      980 May 11 15:31 run
drwxr-xr-x   2 root   root    12288 May 11 10:11 sbin
drwxr-xr-x   2 root   root     4096 Apr  6 04:32 snap
drwxr-xr-x   2 root   root     4096 Apr 11 23:06 srv
drwxrwxrwx   7 nobody nogroup  4096 May 11 09:16 storage
dr-xr-xr-x  13 root   root        0 May 11 10:12 sys
drwxrwxrwt   9 root   root     4096 May 11 15:17 tmp
drwxr-xr-x  10 root   root     4096 May  4 09:27 usr
drwxr-xr-x  14 root   root     4096 May  4 15:59 var
lrwxrwxrwx   1 root   root       30 May  4 10:13 vmlinuz -> boot/vmlinuz-4.10.0-20-generic
lrwxrwxrwx   1 root   root       30 May  4 09:27 vmlinuz.old -> boot/vmlinuz-4.10.0-19-generic
...
...
drwxr--r-x 4 root root 4096 May 11 09:16 data
drwxr-xr-x 5 root root 4096 May 11 09:14 mass
drwxr--r-- 3 root root 4096 May  4 15:35 parity
drwxr--r-- 2 root root 4096 May  5 13:13 usb

```

I can change the mount point. I was following this: [https://zackreed.me/setting-up-snapraid-on-ubuntu/](https://zackreed.me/setting-up-snapraid-on-ubuntu/)

---

### Post by darkod on 2017-05-11
Hmmm, /mnt somehow lost the x bit for other users. That means they can't "look inside" the folder which  is probably preventing it to work. Notice how all folders in / (except lost+found and root) have r-x at the end of the permissions, but mnt has r--. If it doesn't have the x other users can't open it.

Try just setting the x for other users. The data folder inside it already has it, so it should be sufficient to set it on mnt only.
```
sudo chmod o+x /mnt
```

Test the shares after that.

---

### Post by SeijiSensei on 2017-05-11
> **darkod said:**
> 
```
sudo chmod o+x /mnt
```
Test the shares after that.

I would recommend 
```
sudo chmod og+x /mnt
```
since there are no group permissions either.  

I just ran a little test to see if using "o+x" also changes the group permissions (since if all are permitted, then group members should be, too), but it did not.  I needed to use "og+x" to change them both.

---

### Post by xrintrahx on 2017-05-11
Hey, thanks, that did the trick. I appreciate it. So based on what you know of my system, do you have any advice or recommendations? Should I move the mount points out of /mnt/?

---

### Post by darkod on 2017-05-11
I saw about the group too, but since both user and group are root, and user already had x, I didn't suggest adding it for group too. You are right, I too understand you would need to use go+x to add for both group and others. Because others is not all, to change for all you would use a+x.

About your question for the mount points and moving them, I don't have time to go through your snapraid setup, so you have to check if maybe changing mount points will have other implications. If it mounts just like normal partition, you could easily change your mount point to something like /data. But again, that is not really necessary since you got it working... It's your choice basically. I can't be sure if mount point change will have implications on the snapraid.

Also, if you don't need further help, please mark the thread as solved. You can do that in Thread Tools above the first post.

---

