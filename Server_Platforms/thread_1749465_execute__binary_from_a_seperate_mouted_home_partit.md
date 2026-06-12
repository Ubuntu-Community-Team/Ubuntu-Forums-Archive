---
title: "execute  binary from a seperate mouted home partition"
date: 2011-05-04
forum: Server Platforms
---

### Post by tatt on 2011-05-04
Evenin...

Running 10.04 server.

ssh only into server.

I am attempting to execute a *.bin from within a home directory.

The said home directory is on a separately mounted partition, the user was setup with the "adduser" command and the home directory specified on the mounted partition. As described below...

> sudo adduser srcds --home /media/shared2/srcds

This successfully created the srcds folder for home.

The fstab entry for the volume is as follows...

> /dev/sda1  /media/shared2  ext3  user  0  0

when i execute the binary when cd'd inside the home directory where the binary is, I get the permission denied error as follows.

> srcds@fileserver:~/srcds$ ./hldsupdatetool.bin
-bash: ./hldsupdatetool.bin: Permission denied

If I add Sudo....

> srcds@fileserver:~/srcds$ sudo ./hldsupdatetool.bin
[sudo] password for srcds: 
sudo: unable to execute ./hldsupdatetool.bin: Permission denied

And my user is in the sudoers list and proved.

If I run as a user in a generic home location. i.e /home/user then this works fine, but my server has very little disk space in this partition so therefore I need to use the mounted disk.

Please advise how I can execute this binary.

Ta!

---

### Post by Lateralis on 2011-05-04
Does the file have execute permissions? 

```

chmod +x hldsupdatetool.bin

```

---

### Post by tatt on 2011-05-04
Hi Lateralis.

Thanks for the prompt reply.

Yes I have chmod(ed) the file.....

> srcds@fileserver:~/srcds$ ls -l
total 3436
-rwxr-xr-x 1 srcds srcds 3513408 2005-09-02 03:27 hldsupdatetool.bin

---

### Post by tatt on 2011-05-05
Can anybody help with this please?

---

### Post by volkswagner on 2011-05-05
Have you tried offering the full path?

/home/username/name.bin

---

