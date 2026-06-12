---
title: "Dropbox for Ubuntu Server?"
date: 2011-01-12
forum: Server Platforms
---

### Post by DanHorniblow on 2011-01-12
I use dropbox to store all of my college work, however dropbox's website and application is blocked on the college network. 

I have my own home web server running ubuntu server 10.10, would it be possible to install dropbox to server and then point a PHP file manager to the directory that is synced by dropbox, so I can access my dropbox files at college via my home server?

---

### Post by vortmax on 2011-01-12
I don't see why not.  Dropbox just reads/writes to it's configured directory, so apache (or anything running on the local system) just sees a directory with files that change from time to time (just like if you changed them on the local system).  Without trying it, the only problems you may run into is with file permissions (Dropbox ownes files as <user>.<user>), but there are ways around that.

---

### Post by DanHorniblow on 2011-01-13
Do you know if dropbox is supported in command-line OS's

---

### Post by ginge6000 on 2011-01-13
[This]("http://www.dropbox.com/downloading?os=lnx") would suggest you can.

---

### Post by DanHorniblow on 2011-01-13
I search dropbox's website for ages looking for a linux server page and never found it lol, I will have a go over the weekend :)

Thanks :)

---

### Post by airtonix on 2011-01-14
dropbox do not provide a server daemon for anyone to use.

if you want to run your own sync server check out sparkleshare.

---

### Post by rubylaser on 2011-01-14
Sure they do, I have dropbox running on my Ubuntu CLI server at home.  Here are directions to install it:)
[http://1000umbrellas.com/2010/04/30/how-to-install-dropbox-on-a-headless-ubuntu-10-04-server]("http://1000umbrellas.com/2010/04/30/how-to-install-dropbox-on-a-headless-ubuntu-10-04-server")

---

### Post by airtonix on 2011-01-15
read what i typed.

That's not a dropbox server daemon. It's just a cli client that is auto started with an init script.

---

### Post by airtonix on 2011-01-15
read what i typed.

That's not a dropbox server daemon. It's just a cli client that is auto started with an init script.

---

### Post by airtonix on 2011-01-15
read what i typed.

That's not a dropbox server daemon. It's just a cli client that is auto started with an init script.

dropbox have no plans to undercut their own profit base by providing a server daemon for your own private syncing requirements.

---

### Post by airtonix on 2011-01-15
read what i typed.

That's not a dropbox server daemon. It's just a cli client that is auto started with an init script.

dropbox have no plans to undercut their own profit base by providing a server daemon for your own private syncing requirements.

---

