---
title: "[SOLVED] MYSQL connection problem"
date: 2008-11-17
forum: Server Platforms
---

### Post by katana6434 on 2008-11-17
Hi All

I have setup a server at home running Ubuntu Server.  It is running a LAMP config that was working fine before the weekend.  I was away for the weekend and came back to it not working.

I get a connection error with everything that is using (phpmyadmin and torrentflux at the moment).

I restarted mysql

```
sudo /var/init.d/mysql restart
```

This produces this error:
[I]
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)[/I]

I tried to check for the *mysqld.sock* file but i could not find a *mysqld* directory in */var/run*.  Could this be part of the problem?

I have checked some other posts as well and I will admit that I don't really understand what is written in them.

This where I am now stuck as I have no idea even where to begin.  I am a complete newbie at linux and any help would be appreciated.

Thanks in advance

---

### Post by Thirtysixway on 2008-11-17
Try running sudo /etc/init.d/mysql restart

---

### Post by katana6434 on 2008-11-17
> **Thirtysixway said:**
> Try running sudo /etc/init.d/mysql restart

I assume that is what I was supposed to be typing instead of *sudo /var/init.d/mysql restart*.

Anyway, I just typed that and I get:

[I] * Stopping MySQL database server mysqld                                 [ OK ]
 * /etc/init.d/mysql: ERROR: The partition with /var/lib/mysql is too full!
[/I]

Does this mean that the disk is full...
What command do I need to type to check disk usuage?

Thanks for your reply.

---

### Post by Coreigh on 2008-11-17
To check how much disk is available (or used up)

```
sudo df -h /dev/sda1
```

Replace sda1 with the disk and partition your /var/lib is located

see also man pages for df and du


```
sudo du -sch /
```
is more thorough but will take a long time and may not work on a very full disk.
Also it may try to follow network file systems and that is not relavent. There is a switch but I do not know it off the cuff, thats what man pages are for.

---

### Post by Thirtysixway on 2008-11-17
Your harddrive is probably full, delete some stuff and mysql should start up again.

---

### Post by katana6434 on 2008-11-17
> To check how much disk is available (or used up)

Code:

sudo df -h /dev/sda1

OK, I ran that and this is the result:

[I]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G   34G  3.4M 100% /[/I]

Oh dear I'm out of disk space...  I better free some up.

Hmmm, I don't think I installed this very well then...
I have a 500GB Hard Drive that I though I mounted at /home but that doesn't seem to be the case.

I will delete some files then i will look into getting my /home moved to that drive.

---

### Post by cariboo on 2008-11-17
Don't just randomly delete files, you should run:

```
sudo apt-get clean
```

To clean out the archive .deb files as you don't need them once you have installed a package. I normally reserve about 20Gb for / on a home server and have seperate partion for /home, plus a separate 80Gb disk for backups and a 400Gb raid array for data storage. Then back the whole thing up on 2 seperate 500Gb external drives. I hate losing data.

Jim

---

### Post by katana6434 on 2008-11-17
> Don't just randomly delete files, you should run:

Code:

sudo apt-get clean


Thanks for that.  Will give it a try.

I have a 500 GB HD in the server that I was planning on using for the /home mount.  I must have done something wrong in the installation as it didn't work out that way.

I will move the /home mount tomorrow onto this disk.  I might be back asking about that tomorrow.... :)

---

### Post by katana6434 on 2008-11-17
Thanks everyone.... \\:D/

I have deleted a couple of files that I don't need from my home directory and also ran *sudo apt-get clean*.  This has given me about 500mb of free space - enough to get mysql started.

I will sort out the rest of the space tomorrow.

Once again, thanks everyone.  You have all been a great help.

---

