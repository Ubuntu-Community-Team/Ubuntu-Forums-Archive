---
title: "Automatically Backup Machines"
date: 2010-08-29
forum: Server Platforms
---

### Post by baudday on 2010-08-29
I'm looking for way to automatically backup a few machines to my server. Does anyone know a good guide to set this up? I want it to pull the files from the machines at a certain time every week.

---

### Post by spynappels on 2010-08-29
One way to do this is to use rsync and create a cron job to rsync from each client to the backup server.

---

### Post by Lars Noodén on 2010-08-29
> **spynappels said:**
> One way to do this is to use rsync and create a cron job to rsync from each client to the backup server.

And for that you can use keys for authentication, either loading the password in an agent or risking passwordless keys.  In either case, do not allow remote login as root.  Instead make a new account for just the backup and then customize it with sudo, if root access is needed on the client by the server.

Are you backing up the operating system or the data or both?

---

### Post by Lars Noodén on 2010-08-29
If you are doing many machines, especially if they are similar, then [radmind](http://rsug.itd.umich.edu/software/radmind/) is another option.  It uses pieces like SSH and Rsync, and provides a framework for snapshots.

---

### Post by baudday on 2010-08-29
I personally will just be backing up data, but I'd like for other people to have the option of backing up the OS if they'd like. Are there any good guides for setting up some of the stuff mentioned?

---

### Post by Lars Noodén on 2010-08-30
> **baudday said:**
> I personally will just be backing up data, but I'd like for other people to have the option of backing up the OS if they'd like. Are there any good guides for setting up some of the stuff mentioned?

There are some links to [radmind documentation](http://rsug.itd.umich.edu/software/radmind/documentation.html) at the project's web page.  Look around in the search engines for conference presentations, workshops and tutorials.  A lot of universities use it, but if they have too many Microsoft people their pages might be hard to find or taken down.  (Yeah it happens.)

Rsync is universal and even Ubuntu has its own [rsync](https://help.ubuntu.com/community/rsync) documentation and [rsync tutorials](http://ubuntuforums.org/showthread.php?t=639979).  

For fun: [http://olstrans.sourceforge.net/release/OLS2000-rsync/OLS2000-rsync.html](http://olstrans.sourceforge.net/release/OLS2000-rsync/OLS2000-rsync.html)

---

### Post by Lars Noodén on 2010-08-30
> **baudday said:**
> I personally will just be backing up data,

For that it helps, but is not necessary, to have the data partition separate from the rest of the system.  If you set up your machine with  a separate **/home** partition, then you are all set.  If you use databases, web servers or other services that user [b]/var[/url] then have that separate too if you are able.

---

