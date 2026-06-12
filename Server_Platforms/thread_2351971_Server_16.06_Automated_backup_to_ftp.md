---
title: "Server 16.06 Automated backup to ftp"
date: 2017-02-08
forum: Server Platforms
---

### Post by monster-it on 2017-02-08
Hi,

I'm running 16.06 with yetiforce installed on the server. Is there a way to automate a backup of the /var/www/html/yetiforce folder and the database to my ftp server on the same network daily?

Thank you

Alex

---

### Post by howefield on 2017-02-08
Moved to the "*Server Platforms*" forum.

---

### Post by LHammonds on 2017-02-08
I am not familiar with YetiForce but it sounds like you are wanting to copy a file from one Linux server to another?

There are many ways to transfer files between one server and another.

RCP (remote copy)
Mount + RSync
Samba + CP/Rsync
FTP

Depends on how you want to do it or what is available.  If the FTP server is a Windows box, you could setup a folder share and configure an ID/password that you could use to mount from the Linux box using CIFS.

LHammonds

---

### Post by monster-it on 2017-02-08
So the windows server has a share folder on it for ftp which i use for cpanel to backup. 

The ubuntu server needs to backup mysql and the entire yetiforce folder (CRM system) any pointers as i'm new to linux but expanding my "Knowledge".

---

### Post by darkod on 2017-02-08
Share folder or FTP? It's not the same.

You access windows shared folder by \\IP or \\hostname and it works on port tcp/445 while FTP as standard works on tcp/21.

If it's shared folder you can mount it on the linux server and use it as local path.

For ftp you will need little more complex script to connect, upload and disconnect.

---

### Post by LHammonds on 2017-02-08
Ok, looks like yetiforce is your basic web-app with a mysql backend.  This is what you will want to do:

1. Make an rsync copy of your yetiforce folder which is probably somewhere under /var/www/html to a backup location such as /bak
    Example: **rsync -apogHK --delete /var/www/html/ /bak/yeti/**
2. Export your mysql data to a .sql file and place it with your yeti backup (e.g. /bak/mysql-all.sql)
    Example: **mysqldump --skip-lock-tables --all-databases --routines > /bak/yeti/mysql-all.sql**
3. Archive the backup folder into a single file.
    Example: **tar -cpzf /bak/`date +%Y-%m-%d`-yetiforce.tgz /bak/yeti**
4. Mount your windows share and copy the file.
    Example Part 1: **mount -t cifs //WINDOWSSERVER/ShareName /mnt/backup --options nouser,rw,nofail,noatime,noexec,credentials=/etc/cifspw**
    Example Part 2: **cp /bak/`date +%Y-%m-%d`-yetiforce.tgz /mnt/backup/.**

The tutorials in my sig (among other tutorials on my forum) cover such steps and scripts to do things just like this.

NOTE: I just whipped up these examples without testing/validating them 1st but should be a good start.

LHammonds

---

### Post by monster-it on 2017-02-13
Thank you. But this crashed my server. I went to your forum and no joy can't find the thread you were talking about.

---

### Post by LHammonds on 2017-02-13
What crashed your server?  None of those command should crash a server unless you configured your storage (root, /opt, /var, /usr) to all be shared and you ran out of room.  (e.g. running out of space on the root system is very bad).

Also, even though there are many scripts on my site, you will not find a single one you can copy/paste to your server and expect it to work right off the bat.  They are customized to the server.

What I posted above should be 90% of all you need...but you need to make sure you have the space.

```
du -sh /var/www/
```

This command will let you know how large your website folder is (uncompressed).

LHammonds

---

### Post by SeijiSensei on 2017-02-13
Export the backup share in Windows and mount it on the Linux box using CIFS.  Then you can write directly to it.  See this document for details: [https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide), particularly the section titled "Automagically mount SMB shares."

I would only do this if by being "on the same network" means they have private IP addresses and are both behind a router.  CIFS isn't secure enough to be used over the public Internet.

---

### Post by monster-it on 2017-02-13
> **LHammonds said:**
> What crashed your server?  None of those command should crash a server unless you configured your storage (root, /opt, /var, /usr) to all be shared and you ran out of room.  (e.g. running out of space on the root system is very bad).

Also, even though there are many scripts on my site, you will not find a single one you can copy/paste to your server and expect it to work right off the bat.  They are customized to the server.

What I posted above should be 90% of all you need...but you need to make sure you have the space.

```
du -sh /var/www/
```

This command will let you know how large your website folder is (uncompressed).

LHammonds Thank you.
I've had a look and i've got 3.7TB of data and 30TB free so i'm good :)

WIll have a go and report back thank you.

---

