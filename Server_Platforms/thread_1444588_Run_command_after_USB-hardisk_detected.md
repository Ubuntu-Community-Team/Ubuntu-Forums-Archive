---
title: "Run command after USB-hardisk detected"
date: 2010-04-01
forum: Server Platforms
---

### Post by Vies1 on 2010-04-01
Hi,

I have server that runs mythbackend and fileserver. I would like to semi automate my second backup (I run one every night, but I need to run one now and then by plugin in external USB). 

I would like to run backup script everytime certain USB-disk is plugged in (detected by ID).

How to make this happen? Any ideas

Vies

---

### Post by cdenley on 2010-04-01
Use udev. What do you mean by "ID"? If you mean UUID, create a rule like this:
```

ACTION=="add", SUBSYSTEM=="block", ID_FS_UUID=="MYUUID", RUN="/path/to/script.sh $env{DEVNAME}"

```
then restart udev
```

sudo /etc/init.d/udev restart

```
Every time there is a partition with the UUID "MYUUID", then "/path/to/script.sh /dev/sdb1" will be run, where /dev/sdb1 is the path to the partition.

Keep in mind that with gnome, by default, that partition will already be mounted.
[https://help.ubuntu.com/community/Mount/USB#Configuring%20Automounting](https://help.ubuntu.com/community/Mount/USB#Configuring%20Automounting)

---

