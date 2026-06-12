---
title: "SAMBA and permissions - Best practice?"
date: 2012-12-04
forum: Server Platforms
---

### Post by MadsRC on 2012-12-04
I'm currently installed 12.04 on my server, and configured it with snapRAID and mhddfs.

I have, besides my system disk, 1 parity and 2 data disks. The data disks are mounted as /mnt/disk0x and parity as /mnt/parity.

The 2 data disk's are pooled using mhddfs into /mnt/virtual.

In virtual I have 6 shares:
[LIST]
[*]Movies
[*]TV_Shows
[*]Pictures
[*]Music
[*]Data
[*]webserver_backup
[/LIST]

Those shares are configured like this in smb.conf:
```
[Share name]
read list = @users
write list = mrc, nhc
comment = Some comment
path =  /mnt/virtual/share
browsable = yes
guest ok = no
read only = no
create mask = 0755
force user = mrc
force group = users
```

My system has 4 users:
[LIST]
[*]mrc - shell & home
[*]nhc - No shell, no home
[*]livingroom01 - no shell, no home
[*]bedroom01 - no shell, no home
[/LIST]

Every file in my shares have 0755 and are owned by mrc and users group.

Now, my question is, with the above setup, only mrc and nhc can read/write and Users group can only read (Which i don't understand, cause all 4 users are in Users, and the file permissions should only allow mrc to write? But I guess smb.conf write list overrides that?)

But is that the best way to make user secure shares? or should I force the over of files to be "nobody" or something like that?

---

### Post by Rakeshvijayan on 2012-12-04
[smitha]
comment = /home/smitha
path = /home/smitha/share
guest ok = no
browseable = yes
valid users = smitha
write list = smitha
read list = smitha
create mask = 0777

[general]
comment = /home/general
path = /home/general/share
guest ok = no
browseable = yes
valid users = general
write list = general
read list = general
create mask = 0777

This is my server setup , for 9 users ,they have their own directories .you must look on the path for directories .basically I dont under stand your requirement .hope fully this may help you .

---

