---
title: "gProFTPd and Sharing Drive"
date: 2008-02-10
forum: Server Platforms
---

### Post by DevgruSeal on 2008-02-10
I have Samba setup so I can map a shared folder to a network drive on my XP machine. I did that so I can control what is seen easily on the network, and I want to use FTP to share the rest of the hard-drive, so I can login to FTP and have complete FTP access to my hard-drive. (I also need it to be LAN exclusive).

I did this with FileZilla when I was using XP Home while setting up my new computer, but I have begun my migration to linux on my old machine.

I'm using ProFTPd and the GUI for it, gproftpd. I'm fairly new to setting it up, linux-style, but I'd prefer to stick to setting this up with the GUI for now.

I tried creating a user (Call it LinuxBox for now) in the Users section of gproftpd, group to 'root', and setting its home folder to /media/sdb4/, but when I attempt to login, I get a 530 Unable to set Anonymous privileges; 530 Login Incorrect.

---

