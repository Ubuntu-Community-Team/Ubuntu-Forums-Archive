---
title: "Samba and permissions?"
date: 2009-09-06
forum: Server Platforms
---

### Post by DejitaruJin on 2009-09-06
I've got an Ubuntu 8.04 file server, running Samba. It's only for me, and I use it to store things like my MP3 collection and my Documents folder (shared amongst three systems). The problem is, it has permissions issues, caused by the fact that permissions are involved at all.

Basically, I just want some way to make it so absolutely anyone who makes it onto my network and is able to connect to the server owns the files for as long as they're using them. Add, delete, modify, *anything*, without a single exception. I also want to make sure that files moved from another system to the server are granted the same features (as right now, things copied from my laptop belong to "nobody" in "nogroup").

What's the easiest way to go about doing that?

---

### Post by Whiffle on 2009-09-06
Set the security in smb.conf to what I have below, and set the filesystem permissions to whatever folder you're sharing to 777 

```

[global]
security = share
guest account = nameofaccountyouwanttoownthefiles

[nameofyourshare]
browseable = yes
read only = no
guest ok = yes


```

I didn't put all the options in there, just the ones that need changing.  I think thats all of them...

---

### Post by jamesrfla on 2009-09-06
If you want a GUI interface to manage it install this. ```
sudo apt-get install system-config-samba
```

---

### Post by DejitaruJin on 2009-09-06
That much does explain why new files belong to "nobody" (the guest account name), but all those settings are just as I have them. On the server, every file and every folder is set to mode 777, and the same applies to the folders they're mounted in on the desktop. Still, I get errors if I try to do something like change MP3 tags on a song.

---

### Post by swerdna on 2009-09-07
Try this alternative:
in [global] put:
```
security = user
map to guest = bad user
```
then make a share like this:
```
[share_name]
path = /path_to/shared_directory
read only = no
force user = anthony
guest ok = yes
```
Anthony is some linux user you create on the Ubuntu machine, maybe you, whatever, any Linux user.
Chown the share to owner=anthony and chmod it to permissions drwxr-x--- with these commands:
```
sudo chown -R anthony:anthony /path_to/shared_directory 
sudo chmod -R 750 /path_to/shared_directory
```

The share will be writeable by all network users. The user anthony is an artifice that makes the internal gymnastics of the share work in the name of anthony, but the external network appearance is that any connecting user can manipulate/create/edit the contents as the owner.

FFI see share #4 in this tutorial:
[HowTo Configure a Professional File Server on a SOHO LAN]("http://ubuntu.swerdna.org/ubusambaserver.html")

---

