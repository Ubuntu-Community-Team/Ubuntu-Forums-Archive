---
title: "Samba share access problem"
date: 2011-07-27
forum: Server Platforms
---

### Post by boskoslo on 2011-07-27
Little background:
- Ubuntu 10.04 server, GUI desktop later installed
- Software raid-1 consisting of two partitions-> md0
- RAID-1 is automatically mounted through fstab
- Samba service installed

I have problems accessing folder contents over samba share. When I try to open Glasba folder (music), I get this error window:
[IMG]http://www.shrani.si/f/33/9M/ul174WK/screenshot.png[/IMG]

Anyway here is a piece of my fstab configuration and /etc/samba/smb.conf:
FSTAB
```
UUID=4807dcd2-8ddb-4ddd-a54b-1c1686cbed80    /media/Pdtki    ext4    defaults 0 0
```

SMB.CONF
```
[global]
   workgroup = WORKGROUP

####..... bloat..... #####

# Moj share za torrente
[torrenti]
    comment = Torrenti
    path = /media/Torrenti
    browsable = yes
    guest ok = yes
    read only = yes
    create mask = 0700

# Moj share za Glasbo
[glasba]
    comment = Glasba
    path = /media/Pdtki/GLASBA
    browsable = yes
    guest ok = yes
    read only = yes
    create mask = 0700
```

You can see a Torrenti folder. It's interesting that I don't have problems accessing its contents.

So, where is my problem located? :)

---

### Post by Morbius1 on 2011-07-27
A "Failed to mount" is usually a Linux permissions problem so what are the permissions of the shared directory? In order for a guest to gain access it has to be set to 777:
```
 sudo chmod 777 /media/Pdtki/GLASBA
```

---

### Post by boskoslo on 2011-07-27
I issued the following code and it's still the same:
```
bosko@streznik:~$ sudo chmod -R 777 /media/Pdtki/GLASBA/
bosko@streznik:~$ sudo service smbd restart
smbd start/running, process 1803
bosko@streznik:~$ sudo service nmbd restart
nmbd start/running, process 1814

```

Is this what you wanted regarding share permissions?
[IMG]http://www.shrani.si/f/1F/dk/CzIPIb1/screenshot.png[/IMG]

---

### Post by Morbius1 on 2011-07-27
What are the onweshi and permissions on /media/Pdtki/GLASBA?
```
ls -al /media/Pdtki/GLASBA
```

BTW, I would never suggest you do a "chmod -R 777" on anything.

---

### Post by linuchsan on 2011-07-27
@Morbius1 chmod -R 777, but you don't want to do that.

---

### Post by linuchsan on 2011-07-27
Create a group. Add an user on the server and make it a member to this group. Get you directory to be owned by this group (chown and chmod)and set a create mode = 0660 in smb.conf. Add the user with smbpasswd -a username.
Use the user credentials, when login to the share.

---

### Post by Morbius1 on 2011-07-27
That's all fine and dandy but he has the share set up as guest access. I still beleive that this is a Linux permissions issue - I'm betting that /media/Pdtki/GLASBA points to an NTFS partition.

---

### Post by linuchsan on 2011-07-27
That (ntfs) could be the problem ;-)

---

### Post by Morbius1 on 2011-07-27
If this is a permissions issue there is a simple solution. Change the share definition to this:
> [glasba]
    comment = Glasba
    path = /media/Pdtki/GLASBA
    browsable = yes
    guest ok = yes
    read only = yes
[COLOR=Blue]** force user = bosko**[/COLOR]
create mask = 0700If "bosko" has access to /media/Pdtki/GLASBA locally so will the remote user because at that point for that share the remote user is bosko.

---

### Post by boskoslo on 2011-07-27
> **linuchsan said:**
> Create a group. Add an user on the server and make it a member to this group. Get you directory to be owned by this group (chown and chmod)and set a create mode = 0660 in smb.conf. Add the user with smbpasswd -a username.
Use the user credentials, when login to the share.

I want these files to be accessed **without username/password**. (When accessing Torrenti folder from Windows box, I get username/password prompt box, where I can type anything I want -> I don't have problems with Torrenti folder).

Considering other assumptions:
raid-1 array filesystem type is **ext4**, but this software array consists of two **ntfs** partitions of same size (each on its own disk). Could problem be related to this?

```
What are the onweshi and permissions on /media/Pdtki/GLASBA?
```
```
bosko@streznik:~$ ls -al /media/Pdtki/
total 36
drwx------  9 bosko bosko 4096 2011-07-24 19:35 .
drwxr-xr-x  5 root  root  4096 2011-07-24 21:46 ..
drwx------  8 bosko bosko 4096 2011-07-06 21:07 BOBAN
drwx------  2 bosko bosko 4096 2011-07-06 19:25 Downloadi
drwxrwxrwx 12 bosko bosko 4096 2011-07-05 14:29 GLASBA
drwx------ 46 bosko bosko 4096 2011-07-05 15:14 Neinstalirani programi
drwx------  9 bosko bosko 4096 2011-07-06 21:27 SLADJA
drwx------ 62 bosko bosko 4096 2011-07-06 20:55 SLIKE
drwx------  6 bosko bosko 4096 2011-07-05 14:15 STARSI
bosko@streznik:~$ ls -al /media/Pdtki/GLASBA
total 6784
drwxrwxrwx  12 bosko bosko    4096 2011-07-05 14:29 .
drwx------   9 bosko bosko    4096 2011-07-24 19:35 ..
drwxrwxrwx   2 bosko bosko    4096 2011-07-05 14:30 Flk
drwxrwxrwx   4 bosko bosko    4096 2011-07-05 14:29 Komadi brez naslovov
drwxrwxrwx   2 bosko bosko    4096 2011-07-05 14:28 Midi
-rwxrwxrwx   1 bosko bosko 6859878 2009-05-10 22:49 MOV00003.3gp
drwxrwxrwx 219 bosko bosko   24576 2011-07-05 15:03 Narodna muzika
drwxrwxrwx   3 bosko bosko    4096 2011-07-05 14:08 Ostalo od mp3-jev
drwxrwxrwx   2 bosko bosko    4096 2011-07-05 14:08 Radio stanice
drwxrwxrwx  14 bosko bosko    4096 2011-07-05 14:45 Rap
drwxrwxrwx   2 bosko bosko   20480 2011-07-05 14:08 Tekstovi narodnih pesama
drwxrwxrwx  12 bosko bosko    4096 2011-07-05 15:01 Tuje
drwxrwxrwx   2 bosko bosko    4096 2011-07-05 14:06 Zabavna

```

---

### Post by boskoslo on 2011-07-27
I also believe that problem is hiding at filesystem level. Perhaps ext4 partition is not mounted correctly? I used (as you could see in 1st post) default options.

Configuration for Glasba and Torrenti is same at smb.conf...

---

### Post by Morbius1 on 2011-07-27
```
bosko@streznik:~$ ls -al /media/Pdtki/GLASBA
total 6784
drwxrwxrwx  12 bosko bosko    4096 2011-07-05 14:29 .
[COLOR=Blue]**drwx------   9 bosko bosko    4096 2011-07-24 19:35 ..**[/COLOR]
```The whole path to the target shared directory has to allow guest access:
```
sudo chmod 777 /media/Pdtki
```
Or at least:
```
sudo chmod 755 /media/Pdtki
```
No need for a "-R".

BTW, my suggested fix using "force user = bosko" would also have worked.

---

### Post by boskoslo on 2011-07-27
It works now. Ubuntu community rocks! And so does the music at my house! :)

Thank you!

---

