---
title: "Can't mount Samba share (canonicalize_connect_path failed)"
date: 2010-03-26
forum: Server Platforms
---

### Post by arnofiva on 2010-03-26
Hi,

I am setting up a new Ubuntu Server running Samba. The server appears in the local network and also shows the available shares. However when trying to connect to certain shares, it fails to mount some of the available Shares.

Looking at the Samba log on the server, there are lines like following:

[2010/03/26 15:45:13,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service Shared, path /home/fivaa/Shared

/home is mounted to a separate hard drive, so I am not sure if that is causing any trouble. If I try different paths outside of /home (e.g. /var/local/Shared) everything works fine.

It might be worth mentioning that the Ubuntu server is running inside of Virtualbox and connects to the local network using a network bridge (separate IP). The root directory / points to a 80GB virtual disc and the /home directory points directly to a 1.5TB hard drive, which is registered in VirtualBox as a raw hard drive. Mounting does not work from any other machine in the network, nor from the host or guest OS.

Thanks for any help on this!

---

### Post by M0les on 2010-04-22
I just had this error message.

The problem (for me) was that I wanted a "guest read/write" share, but the path I was sharing was not accessible to the "guest" user (which IIRC is the 'nobody' user). I just did a "chmod a+rx" on one of the path component directories and it all works fine now.

My suggestion for you is to check that all directories on the path you are sharing have read+execute permissions for the user/group you want to access them.

I don't believe that virtualbox will be a factor in the problem.

---

### Post by naaman on 2010-05-03
> **M0les said:**
> I just had this error message.

The problem (for me) was that I wanted a "guest read/write" share, but the path I was sharing was not accessible to the "guest" user (which IIRC is the 'nobody' user). I just did a "chmod a+rx" on one of the path component directories and it all works fine now.

My suggestion for you is to check that all directories on the path you are sharing have read+execute permissions for the user/group you want to access them.

I don't believe that virtualbox will be a factor in the problem.

I would recommend just running the following to get the folders shared underneath your home directory working:
```
naaman@caterham:~$ chmod -R a+x /home/naaman/share
```

It will ensure that your home directory files are not readable, however Samba clients can still enter into the next directory below..

---

### Post by nimrodwebdesign on 2010-11-12
I just had the same error, with some shares that had been working before.

It was due to me renaming the parent directory of the shared directories, which of course meant that it couldn't find them.

After updating the /etc/samba/smb.conf file with the correct path it was fine again.

---

### Post by tealex on 2011-01-05
Note:

/home/name/folder

+x - need for all folders in path

chmod +x /home 
chmod +x /home/name
chmod +x /home/name/folder

---

### Post by ikt on 2011-02-03
> **tealex said:**
> Note:

/home/name/folder

+x - need for all folders in path

chmod +x /home 
chmod +x /home/name
chmod +x /home/name/folder

Thank you that worked!

/cheer

---

