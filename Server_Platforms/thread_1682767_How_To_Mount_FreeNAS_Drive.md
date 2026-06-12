---
title: "How To Mount FreeNAS Drive"
date: 2011-02-06
forum: Server Platforms
---

### Post by coey on 2011-02-06
I am very new to Ubuntu and have been having trouble mounting my FreeNAS drive. I installed Ubuntu 10.10 on partition sda2. I wanted to keep FreeNAS completely separate from here, so I used Virtualbox to host FreeNAS as a guest o/s on a second hdd, sdb1 mounted at /media/NAS-Data. I can access the NAS from all computers except my Ubuntu box. I have CIFS/SMB and NFS (among other) services enabled on FreeNAS.

I would like to run a program that needs access my music. I followed many of the "How To's" on the forum, but am not sure if they didn't work or if my setup is different and can't work the way that has been described. My last effort was to mount the file system using NFS, but I get a timed out error.

When I run showmount -e 192.168.0.44, result is /mnt/cNb-NAS-data 192.168.0.0. I've tried many variations to mount, but none have worked.

For all I know, again I'm very new to Ubuntu, the file system is already considered mounted (/media/NAS-Data), and I just need to find the correct path to access my data. This is probably obvious, but when I navigate to NAS-Data, it has the Virtualbox NAS.vdi file.

Was hoping someone might be able to either help me get the correct path name or mounting instructions in order to view these files from Ubuntu.

Thank you in advance and sorry to ramble on...

---

### Post by arrrghhh on 2011-02-06
Hrm, I guess I'm confused.  So the SAMBA shares work to other machines, have you tried any NFS to any other clients?  Sounds like you've tested the smb client, but not the nfs client.

Post your /etc/exports - I have a feeling it's not properly configured, assuming I am understanding your setup correctly.

FreeNAS is a guest OS on your Ubuntu 10.10 Server, correct?  You can also use file sharing between the guest & host OS using virtual box.  I would think either method would work, so it really depends on what you prefer.

---

### Post by coey on 2011-02-06
Arrrghhh,

Believe it or not, I am probably more confused than you...

Yes I can access shares via samba on Windows and Mac machines. I'm embarrassed to say, I am not quite sure how to test NFS-I thought NFS was a linux specific protocol and this is the only machine running Ubuntu. My /etc/exports is as follows:

#
/mnt/cNb-NAS-data    192.168.0.0/24(rw,no_root_squash,async)

I tried many variations for this, but this is the last one saved. I just saw your last statement and maybe I posted to wrong forum. I am running Ubuntu (Maverick) desktop. Virtual box is installed, with FreeNAS running as a guest OS on 2nd hdd.

What I am trying to do is have my music player point to my music folder on the NAS drive, so all I really need is a path to my music folder on the NAS share, I don't care how its done, I just thought that I would need to mount the share to do this.

Thank you for the help.

---

### Post by arrrghhh on 2011-02-06
> **coey said:**
> Arrrghhh,

Believe it or not, I am probably more confused than you...

Yes I can access shares via samba on Windows and Mac machines. I'm embarrassed to say, I am not quite sure how to test NFS-I thought NFS was a linux specific protocol and this is the only machine running Ubuntu. My /etc/exports is as follows:

#
/mnt/cNb-NAS-data    192.168.0.0/24(rw,no_root_squash,async)

I tried many variations for this, but this is the last one saved. I just saw your last statement and maybe I posted to wrong forum. I am running Ubuntu (Maverick) desktop. Virtual box is installed, with FreeNAS running as a guest OS on 2nd hdd.

What I am trying to do is have my music player point to my music folder on the NAS drive, so all I really need is a path to my music folder on the NAS share, I don't care how its done, I just thought that I would need to mount the share to do this.

Thank you for the help.

Ha, yes this is the "Server Platforms" section, but no worries.

Is this the correct path?```
/mnt/cNb-NAS-data
```I thought you said it was mounted at ```
/media/NAS-Data
```But with your setup, sharing it between the guest and host are probably easiest.  [Here's](http://www.virtualbox.org/manual/ch04.html) the doc on the Guest Additions, and how to use shared folders.

---

### Post by coey on 2011-02-06
Thank you, I will try this. This may have been my confusion, but my second hard drive is mounted in /media/NAS-Data per disk utility, but in FreeNAS, the mount is /mnt/cNb-NAS-Data.

Thanks again.

---

### Post by coey on 2011-02-13
Thank you for all the help. I was able to get my NAS drive mounted with the help of installing the Guest Additions and the following post:

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

### Post by elico on 2011-02-14
mounted as nfs or samba?

to mount nfs you dont use the **/etc/exports** files
you use the command line mount or fstab file.

---

