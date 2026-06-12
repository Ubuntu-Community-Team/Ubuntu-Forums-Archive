---
title: "Can not get root access to windows share"
date: 2014-02-09
forum: Server Platforms
---

### Post by einar3 on 2014-02-09
Hi, I have googled the internett and asked at askubuntu.com but still no result.. :(

I stared with following the ubuntu wiki guid on how to conenct to a windows share...
I can mount, but only with read permission..

My windows share permissions: Administrator and Everyone.

I'm using my admin username and password in the fstab entry.


So this is what i have done:

1: ```
sudo apt-get install cifs-utils
sudo mkdir /media/ussenterprise
```
edited the fstab: ```
[COLOR=#333333]//servername/sharename  /media/windowsshare  cifs  guest,uid=1000,iocharset=utf8  0  0[/COLOR]
```[COLOR=#333333]

With this i can mount with read permission...

2: After asked on askubuntu.com

I did this:

[/COLOR]
fstab:```
 [FONT=Ubuntu Mono]//servername/sharename  /media/ussenterprise  cifs  username=msusername,password=mspassword,umask=002,uid=1000,gid=1000,iocharset=utf8,sec=ntlm  0  0[/FONT]
```
```
[FONT=Ubuntu Mono]sudo umount /media/ussenterprise[/FONT]
sudo chmod 755 /media/ussenterprise
sudo chown einar:einar /media/ussenterprise
[COLOR=#222222][FONT=Verdana]sudo mount -a[/FONT][/COLOR]
```
[COLOR=#333333]When i try to mount i get: [/COLOR][COLOR=#444444][FONT=UbuntuRegular]mount error(22): Invalid argument Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

Any ideas why any of this dont work?[/FONT][/COLOR]

---

### Post by volkswagner on 2014-02-10
I think you want to change

```
username=msusername
```
to
```
user=msusername
```

I believe that is the invalid argument.

---

### Post by brokenhachi on 2014-02-11
username=msuser is valid.

my mounts for reference..

/etc/fstab
```
//SERVER/SHARE/ /MOUNTPOINT cifs credentials=/etc/samba/creds,uid=UNIXUSER,gid=users 0 0
```

/etc/samba/creds
```

username=MSUSER(**administrative rights**)
password=MSUSERPASS

```

I have root access to the share with the above. I think the issue is you need to get admin priv with the msusername, not the unix side. For reference though my mountpoint looks like this:

```

drwxr-xr-x   2 username users     0 Nov 13 11:56 share1
drwxr-xr-x   2 username users  8192 Jan  2 11:21 share2
drwxr-xr-x   2 username users 49152 Jan 31 09:52 share3

```

---

### Post by einar3 on 2014-02-11
Thanks for the replys :)
I changed my fstab to:
```
//server/share/utorrent  /media/ussenterprise/utorrent  cifs  username=msAdminUser,password=mspassword,uid=1000,gid=1000 0  0
```

This might have worked, but not 100%
The output of ls -l /mountpoint

```
drwxr-xr-x 0 einar einar          0 Nov 10 08:02 The.Ultimate.Fighter.S17
-rwxr-xr-x 0 einar einar 1773348317 Nov 14 11:23 The.Ultimate.Fighter.S18
```

When i fire up Transmission, and starting downloading to /mountpoint i get permissions denined...

---

### Post by brokenhachi on 2014-02-12
can you try doing the ms authentication via /etc/samba/creds? Also, is transmission running as einar:einar? Can you copy to and delete files from the share through nautilus?

---

