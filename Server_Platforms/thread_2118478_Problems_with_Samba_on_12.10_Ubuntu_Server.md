---
title: "Problems with Samba on 12.10 Ubuntu Server"
date: 2013-02-21
forum: Server Platforms
---

### Post by grunge09 on 2013-02-21
Fresh install of 12.10 server on a 8gb usb flash drive.  With raid5 setup during that process.  I only did the core server install and samba install.  

I recently got RAID5 (3x2tb drives) setup and mounted via Fstab and formatted ext4.  I can make directories in raid5 drive (I have dubbed /dev/md0 as /storage)

I checked /storage with DF -H /storage and it reads what it should.  

I have added users, created smbpasswords for them. Created directories.

terminal cmds:

useradd -a mediabox

smbpasswd mediabox

sudo groupadd homelan

sudo mkdir /storage/mythtv

sudo chgrp homelan /storage/mythtv

chmod 0755 /storage/mythtv

Modded smb.conf

WORKGROUP = HOMESERVER

Security= user

[mythtv]
  comment = storage for myth tv data
  path = /storage/mythtv
  valid users = @homelan (even tried "mediabox" w/smb service restart)
  writable = yes
  browsable = yes

Save and issue "sudo smbd restart"

Also sudo service smbd restart that restarted a PID

I goto my other ubuntu desktop box and try to map drive

1st I ran sudo mkdir/mnt/mythtv on ubuntu client

sudo mount -t cifs //192.168.0.99/mythtv /mnt/mythtv -o username=mediabox,password=xxxxx

And I get .....

password: (which I enter the server smb root password and I get 

mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

I changed CIFS to SMBFS and get the same error above.  

What am I doing wrong?

Now I have access on the client box I am talking just fine on to a 5u 16 drive RAID Nas running FREENAS 0.68 and can map folders and rsync data to that fine.  On the same gigabit network.  

I did not want to use freenas again as you can not seem to "grow" an array with that,  Mdadm does that fine.  

I had the same pc I am working on now setup as a Samba PDC with 2x2tb raid1 and that was working.  Can't find my notes on the old setup.

---

### Post by Morbius1 on 2013-02-21
I don't see anything wrong with what you posted assuming this is a typo:
> sudo mount -t cifs //192.168.0.99/[COLOR=Blue]**movies**[/COLOR] /mnt/movies -o username=mediabox,password=xxxxx
Did you mean: sudo mount -t cifs //192.168.0.99/[COLOR=Blue][B]myhttv

[/B][COLOR=Black]Which also looks like a typo. Maybe it should have been this:[/COLOR][/COLOR]> [COLOR=Blue][COLOR=Black]sudo mount -t cifs //192.168.0.99[/COLOR][/COLOR]**[COLOR=Blue][B]/[COLOR=Blue][B]mythtv**[/COLOR][/B][/COLOR][/B][COLOR=Blue][COLOR=Black]BTW, you did install the following package on the client, right:
[/COLOR][/COLOR]```
sudo apt-get install cifs-utils
```[COLOR=Blue][COLOR=Black]
[/COLOR][/COLOR]

---

### Post by Morbius1 on 2013-02-21
Well, since I posted you seem to have changed your original post so there's something else wrong. No one in @homelan has write access. Add another step:
```
sudo chmod 0775 /storage/mythtv
```

---

