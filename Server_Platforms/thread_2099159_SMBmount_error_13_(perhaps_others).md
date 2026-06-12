---
title: "SMBmount error 13 (perhaps others)"
date: 2012-12-28
forum: Server Platforms
---

### Post by JaredKat on 2012-12-28
Hello to all. 

I currently run about 19 rackmount machines on Ubuntu Server 12.04 LTS. Right now, I have several servers that I would like to share the same NAS location, to keep all the files on a nice, large storage server set up in RAID 5 across 6 hard drives. 

On the server, I have Samba installed, and working just fine, it seems. I followed [this tutorial]("http://www.youtube.com/watch?v=-5Z_-3EBIHE"). I managed to install WebMin, and used that to configure Samba. Right now, the shares are all accessable on windows clients with each share completely public (the guest user being nobody:nogroup with read and write permissions)

What I need to do is mount the share //192.168.1.150/severs into a location in the home directory, where my particular daemon stores it's files at /home/service/daemon/ and I need the directory /home/service/daemon/servers/ directory mounted to //192.168.1.150/servers. 

I have been using the command "smbmount //192.168.1.150/servers /home/service/daemon/servers" and I have been getting "mount error (13) permission denied" when mounting as a non-root user, and when I mount the location as root, the user "service", which the daemon runs as, does not have access to the mounted directory. 

My samba server has the user service in the valid users, possible users and read-write users. 

What here am I missing? from any Windows computer, I can go to the network tab, go into the share, and red, and write files, directories, and the such, and from Ubuntu, as long as I am root, I can go read, write and make directories. 

I have not tested from Ubuntu Desktop, as I currently only have the servers running ubuntu (I am not fond of giving up dreamweaver) 

Any help is appreciated. These servers, I am hoping to roll out into production soon. Thank you.

---

### Post by JaredKat on 2012-12-28
Okay, I loaded up a Live CD of Ubuntu Desktop 12.04, and I was able to get to the samba server's share and write a file without password, so I am unsure of what is going wrong with how I am doing it in ubuntu server. Probably me not using the right command

Let me know, thank you.

---

