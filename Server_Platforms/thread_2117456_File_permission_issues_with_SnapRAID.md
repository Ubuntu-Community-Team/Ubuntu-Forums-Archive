---
title: "File permission issues with SnapRAID"
date: 2013-02-18
forum: Server Platforms
---

### Post by DeadLemon on 2013-02-18
I  presently moved my file server away from ZFS, as it really didn't suit  my needs, it was an epic RAID system, and it has a place in my heart,  but I only store large static files on my home server, and having my  drives spinning 24/7 is rather wastefull, not to mention a large amount  of unnecessary wear and tear

I came across a tutorial by Rubylaser, [Here]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04"), to set up SnapRAID with AUFS for pooling, and it's worked well, and am very pleased, after some Samba tweaks, I'm getting really decent speeds to my arrays

The issue is now, the permissions are all weird, I've, in the past, had a few issues, but rectified them reasonable quickly, but for some reason I'm stumped

I emptied my RAIDZ array to destroy it and move all my files to my new SnapRAID array, but I'm finding that some of the files I've copied back on, via SAMBA, I don't have sufficient privileges to change them again, like deleting a folder I created

Even more frustrating is this is creating havok on my download software, Sabnzbd and transmission, can't move anything onto the array, I keep getting returns that they don't have sufficient privileges
Even Post-processioning done by Sickbeard fails to add files to existing folders because of this
Out of desperation, I've Chmod 777 the download folders, with little to no success, sometimes the torrent takes, most of the time it will error out, same with Sab

I'm stumped now, I'm not sure how to proceed
I saw a post in another forum, about using a command setfacl, but I have no idea how to use it correctly, the attempt to try use it has shown no results of improvement

I'm really out of idea, I hope someone can lend a hend

---

### Post by DeadLemon on 2013-02-21
Bump?

---

### Post by rubylaser on 2013-02-21
Hello :)  Can you post the output of these commands (assuming your array is mounted at /storage)?

```
mount
df -h
ls -la / | grep storage
ls -la /storage
cat /etc/samba/smg.conf
```

Also, if you are using SABNZBD+ with Sickbeard, have you set it up to chmod 777 your files when it's done? It's on this page [http://ip_address:8080/config/folders/](http://ip_address:8080/config/folders/) under **"Permissions for completed downloads"**

---

### Post by DeadLemon on 2013-02-23
Mount

```

$mount
/dev/sde1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sda on /media/disk1 type ext4 (rw)
/dev/sdb on /media/disk2 type ext4 (rw)
/dev/sdc on /media/disk3 type ext4 (rw)
/dev/sdd on /media/disk4 type ext4 (rw)
none on /vat type aufs (rw,br:/media/disk1=rw:/media/disk2=rw:/media/disk3=rw,sum,create=mfs)
```

```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sde1       224G   47G  166G  22% /
udev            2,9G  4,0K  2,9G   1% /dev
tmpfs           1,2G  2,4M  1,2G   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            2,9G     0  2,9G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sda        1,8T  1,6T  180G  90% /media/disk1
/dev/sdb        1,8T  1,6T  181G  90% /media/disk2
/dev/sdc        1,8T  1,6T  177G  90% /media/disk3
/dev/sdd        1,8T  1,6T  177G  90% /media/disk4
none            5,4T  4,6T  537G  90% /vat
```

```
$ ls -la / | grep vat
drwxrwxrwx  17 root root  4096 Feb 18 23:03 vat

```

```
$ ls -la /vat
total 854612
drwxrwxrwx 17 root   root        4096 Feb 18 23:03 .
drwxr-xr-x 25 root   root        4096 Feb  2 14:58 ..
-rw-------  1 root   root   875084912 Feb 18 23:03 content
drwxr-xr-x  6 warren warren      4096 Feb 16 17:16 download
drwxrwxrwx  2 root   root       16384 Feb 15 21:15 lost+found
drwxrwxrwx  8 root   root        4096 Feb 18 22:53 share

```

```
$ cat /etc/samba/smb.conf
[global]
    ; General server settings
    netbios name = Grinder
    workgroup = WORKGROUP
    announce version = 5.0
#   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

   #Test perameters start
    max xmit = 65535
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=65535 SO_RCVBUF=65535
    read raw = yes
    write raw = yes
    max connections = 65535
    max open files = 65535
   #Test Perameter End

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[Master]
    path = /vat/share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    valid users = nothing

[Andy]
    path = /vat/share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0755
    directory mask = 0755
    valid users = andy

[Johan]
    path = /vat/share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0755
    directory mask = 0755
    valid users = johan

[Download]
    path = /vat/download
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0755
    directory mask = 0755
    valid users = nothing

```

Sab is set to 777, and it's always worked fine before on my ZFS array

---

### Post by rubylaser on 2013-02-23
Your permissions on your downloads folder are 755 not 777 (if /vat/downloads is your folder). I would chmod that folder first.  Also, you'll want to see what user your SAB and Sickbeard processes are using, because currently only root or warren can write to that folder.

```
sudo -i
chmod -R 777 /vat/downloads
ps aux | grep sabnzbd
ps aux | grep sickbeard
```

---

### Post by DeadLemon on 2013-03-25
Sorry for the late replay, been all over the show for the past month, and keep forgetting to reply when I'm home

I managed to come right with the permissions with the "download" folder, but I ended up deleting the "Download" folder and recreating under root, and all is happy with that, with 777 permissions 

But setting 777 to other folders isn't helping, I have my series folder, which Sickbeard maintains for me
Except, older series I was maintaining before the move to snapraid, seem to be working fine, but if I add a new show to Sickbeard, it cannot create the folder in the relevant sub directory, it returns permission denied
If I create the correct folder for it, when it runs it's post-processing script, it can't move the new files into the directory, I also get a permission denied
Telling it to rename my files, also permission denied

Is it possible to add these services to create and edit files under another, like "warren" or root, to avoid these issues?
I'm really confused

I still have to fix the permissions for my torrent client, but I don't use it to much

Edit:
I see that both sickbeard and SABnzbd are running under "warren"
Not sure what to make of that, it was fine before running under a user and not root

---

### Post by rubylaser on 2013-03-25
What do the permissions look like on one of these problem folders?  I use SAB and Sickbeard with no problem on my SnapRAID volume, so I know this can be made to work properly.

---

### Post by DeadLemon on 2013-03-25
I would assume that this is generally a non issue, I'm not sure what I've done, lol

Anyway
```
$ ls -l /
(Omitted the bulk)
drwxrwxrwx  17 root root  4096 Mar 25 19:39 vat

```

```
$ ls -l /vat
total 880120
-rw------- 1 root   root   901210884 Mar 25 18:04 content
drwxrwxrwx 6 warren warren      4096 Feb 23 19:39 download
drwxrwxrwx 2 root   root       16384 Feb 15 21:15 lost+found
drwxrwxrwx 8 root   root        4096 Feb 18 22:53 share

```

```
$ ls -l /vat/share
total 8
drwxrwxrwx  9 nothing nothing 4096 Feb 23 19:42 download
drwxr-xr-x 28 nothing nothing 4096 Feb 17 06:25 My Stuff

```

```
$ ls -l /vat/share/"My Stuff"
total 68
(Omitted)
drwxrwxrwx  14 nothing nothing  4096 Feb 17 02:57 Series

```

Is there a reason that in Putty, the Series folder is highlighted in green and the rest are a blueish text?

```
$ ls -l /vat/share/"My Stuff"/Series
total 16
drwxrwxrwx  11 nothing nothing 4096 Feb 10 23:54 Animated
drwxrwxrwx  80 nothing nothing 4096 Feb 13 21:13 Documentary
drwxrwxrwx  38 nothing nothing 4096 Feb 17 08:12 Reality Shows
drwxrwxrwx 243 nothing nothing 4096 Feb 17 21:03 Series

```

---

### Post by DeadLemon on 2013-04-01
Bump!

---

### Post by rubylaser on 2013-04-01
All of the services you are using can be setup to run under a different user name.  [ainer.org]("http://www.ainer.org/") has good directions to setup all of these services including setting the user names if I recall correctly.

---

### Post by DeadLemon on 2013-04-01
Thanks, I'll give it a look

Any idea why it would do this though? While running my ZFS array, I never ran into this issue

---

### Post by rubylaser on 2013-04-01
Unfortunately, I'm not sure.  I used to run this on a ZFS array before (Openindiana), now I have all of these services on my Ubuntu server on SnapRAID.  Have you looked at the log files to see what the actual errors say?

---

