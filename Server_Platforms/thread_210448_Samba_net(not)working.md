---
title: "Samba net(not)working"
date: 2006-07-06
forum: Server Platforms
---

### Post by Sandsound on 2006-07-06
Having some troubles mounting a Samba share.

I have made a folder on my local pc (sudo mkdir /mnt/musik) and have shared a folder on the server (actualy its a whole disk i have shared). I can see and read files from the server when i navigate my way through "netvork servers" useing Nautilus, but when I try to do :
sudo mount -t smbfs //server/musik /mnt/musik

I get :
mount: wrong fs type, bad option, bad superblock on //server/musik,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I have tryed other variations, even those sugested elsewhere in the forum, but it I get the same mount error.

If I do :
smbtree

I get a list that clearly says I have a  \\server\musik

Am I missing something here ?

---

### Post by djdicbob on 2006-07-14
If you are seeing that the resource is availible it may just be username & pass!  The syntax of your command is proper. I use this command instead of yours.  mount -t smbfs = smbmount

> smbmount //servername/sharename /mountdirectory -o username=WINDOZEusername,password=yourWINDOZEpass

You may find this link useful...
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

### Post by Sandsound on 2006-07-15
> **djdicbob said:**
> mount -t smbfs = smbmount

I get this :
bash: smbmount: command not found
?

Thanks for the link thou, will take a look at it.

btw... I have also posted this question on "networking", sorry for double-posting, but I was not shure if this was a "server talk" or "networking" topic.

edit : :oops:  I just found out that I havent installed smbfs on my client :oops:

---

