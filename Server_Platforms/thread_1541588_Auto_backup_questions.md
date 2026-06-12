---
title: "Auto backup questions"
date: 2010-07-29
forum: Server Platforms
---

### Post by cwscribner on 2010-07-29
Hi all.

I'm attempting to do an automatic backup of an Ubuntu 9.04 server.  I have the command to do the backup and it works swimmingly.  However, this backup needs to be done weekly and backed up to a shared drive on a Windows 2003 server.  I'm assuming I'd need a shell script to do this but I have no idea where to start.  The process I'm trying to accomplish is as follows...

[LIST=1]
[*]Check to see if the shared drive is mounted
[*]If it is, move on.  If its not, mount it, then move on.
[*]Perform the backup command (tar -blah blah blah)
[*]Exit
[/LIST]

---

### Post by arrrghhh on 2010-07-29
[bash](http://tldp.org/LDP/abs/html/) and [cron](http://www.crontabrocks.org/) sound like what you need.  If those guides don't help, do some googling... there's a ton of information about both out there.

If you get stuck, come back and maybe we can poke you in the right direction :D

---

### Post by cwscribner on 2010-08-03
So I think I've got the bash and cron bit handled.  I can't figure out how to access the share via command line though.  I have a share on the Windows Server 2003 called "linux_backup" which shows on the desktop of the Ubuntu server, but I can't find the share via command line.  Any suggestions?

---

### Post by LightningCrash on 2010-08-03
There is a command called smbmount that may do what you desire.

It is in the package `smbfs`


HOWTO: Mounting SMB/CIFS Shares:
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

### Post by cwscribner on 2010-08-03
Hmmm.  I tried several different renditions of the command but I always get error 13(access denied).  I'm not quite sure how to remedy this.  Here's the command I've tried...

```
smbmount //*server*/*share* /backup -o username=*username*,password=*password*
```

For server I used an IP and also tried a servername.

---

### Post by LightningCrash on 2010-08-03
Are you on a domain?

---

### Post by cwscribner on 2010-08-04
The Windows Server is in a workgroup.  Not sure if workgroup is synonymous with domain...

---

### Post by LightningCrash on 2010-08-04
> **cwscribner said:**
> The Windows Server is in a workgroup.  Not sure if workgroup is synonymous with domain...

Are there any relevant entries in the Windows Event Log on the Windows Server?

---

### Post by cwscribner on 2010-08-24
Never did figure this out.  Just wound up going with an external hard drive attached to each server for the time being.

---

