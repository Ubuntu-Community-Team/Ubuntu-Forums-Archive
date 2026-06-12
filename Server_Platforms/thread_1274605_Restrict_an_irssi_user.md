---
title: "Restrict an irssi user"
date: 2009-09-24
forum: Server Platforms
---

### Post by virtuoosi on 2009-09-24
Hello,

I've had a headless Ubuntu 9.04 server running for 2 weeks. I am using it to take backups, run rtorrent and host irssi for me and my brother. 

I just created an user for my brother using ```
sudo adduser
```I moved the obligatory irssi config files to his /home on the server, and started a screen & irssi. He is now able to login via Putty tray from a windows machine and do ```
screen -r. 
```I noticed that he could also cd into MY /home, but I fixed that by editing the privileges of my /home.

He cannot sudo, so I guess he can't do any harm, but I would still like to "lock" him to his /home so he couldn't even do 

```
cd /
```How can I accomplish this?

---

### Post by JonRohan on 2009-09-24
Hey, 

What you are after is called a jail. You want to jail and ssh user to their home directory. 

This link ([http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/](http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/)) looks handy but I have not tested it. 

Hope this helps. 

Jon

---

### Post by virtuoosi on 2009-09-26
Thanks, it worked out just the way I wanted. 

:)

---

