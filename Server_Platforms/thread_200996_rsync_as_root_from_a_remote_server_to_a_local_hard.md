---
title: "rsync as root from a remote server to a local harddisk"
date: 2006-06-21
forum: Server Platforms
---

### Post by horus8 on 2006-06-21
Subject tells what I have to do. Locally I use Ubuntu 6.06, the server is also a Linux system.

1. I have ssh access and I have the root passw. ssh login as root is denied.
2. I have to run a backup of the server. Some of the files and subdirs are only accessible by root.
3. The local harddisk on which I want to save the backups is located on a pc which is part of a local network, connected to the internet via hardware router and broadband (DSL).

The questions:
1. How do I set up this on the server with rsync (no automagic backups, only manual, file attributes should be preserved)
2. How do I address the local harddisk from the server, once I am root on the server? Or is there a way to start rsync locally although I will need root access?

And the biggest problem: Normally a nice RTFM with a hint to the right FM would help. But due to unfortunate circumstances I do not have the time now to read up all this in the manuals because I have to start backups ASAP (or better: day before ASAP!). I can read up all needed stuff afterwards, but noe I need help urgently.

horus

---

### Post by horus8 on 2006-06-21
Hmm, question seems to be too difficult to answer for everybody.:)  Of course I have started reading meanwhile and covered step 1. I can run 
```
rsync -avz horus@remote_server.tld:/ /media/server_backup/
```which transfers dirs and files from the remote server to my local disc into subdir /server_backup/.

Remaining problem: How do I backup all files and subdirs which are only accessible by root? I cannot login to the remote server via rsync as root (permission denied).

Horus

---

### Post by spifbv on 2006-06-21
[QUOTE=horus8]Hmm, question seems to be too difficult to answer for everybody.:)  Of course I have started reading meanwhile and covered step 1. I can run 
```
rsync -avz horus@remote_server.tld:/ /media/server_backup/
```which transfers dirs and files from the remote server to my local disc into subdir /server_backup/.

Remaining problem: How do I backup all files and subdirs which are only accessible by root? I cannot login to the remote server via rsync as root (permission denied).

wobo[/QUOTE]

You should consider that you probably only need to back up important data and configs.  If some or all of your data is only readable by root then some options are:

1) push the rsync from the server back to your local system, with rsync running as root on the server and an unprivileged user on your local system - this will only work if your server can initiate connections back to your local system, which may not be desireable

2) make a temporary copy of the data on the server that is owned by another user, and back it up.  this will only work if you have enough space to make a copy, and of course it may be undesireable to have even a temporary copy that is readable by somebody other than root.

3) enable root login via ssh in /etc/ssh/sshd_config (actually it's enabled by default in Ubuntu's openssh-server package) and run rsync over ssh (using the "-e ssh" option).  this is probably the easiest way.  it's kind of insecure but not any moreso than the default Ubuntu config.

4) use a third party like Strongspace or Amazon S3 for backups - cheap, secure, probably faster than downloading to your local box.  definitely more reliable than keeping things on your own local disk.  you could do both, actually, depending on how much data you have and how much time you want to spend backing it up.

---

### Post by lamego on 2006-06-21
You can run the rsync daemon on the system you want to backup. I found this [article](http://www.freeos.com/articles/4042/) describing it.

---

### Post by horus8 on 2006-06-21
[QUOTE=spifbv]You should consider that you probably only need to back up important data and configs.[/QUOTE]
For a first full backup I need all data. And some of the important config data are only accessible by root.

> 1) push the rsync from the server back to your local system, with rsync running as root on the server and an unprivileged user on your local system - this will only work if your server can initiate connections back to your local system, which may not be desireable
This was the option described in my first message's question #2. Whatever I tried, I cannot get my home system to accept any connection from outside. 
On the router NAT is enabled and I tried to set up all data coming in on port 837 for rsync to be routed to my machine with the IP 192.1682.3. I started a rsync command on the server but my system does not accept the connection or the data can't find the address or whatever. Does not work.
And I haven't found any document describing this kind of setup. There are hundreds of documents telling me what to do for NAT but I have found none which describes HOW I can do it.

> 2) make a temporary copy of the data on the server
Not possible.

> 3) enable root login via ssh in /etc/ssh/sshd_config
That's what I tried but there seems to be another file where the root login via ssh is denied. If I try to 'ssh [email]root@my_server.tld[/email]' I am asked for the root password but I always get 'permission denied'.

> 4) use a third party like Strongspace or Amazon S3 for backups 
Hmm, that should be my very last straw. If I wanted a payed 3rd party backup I could as well ask the hoster of the server to do it.

I have read so many different documents about this during the last 24 hours, I may be blocked from rational thinking by now.

Me thinks, the easiest way should be if I could get the access from the remote server to my local disc to work. From the previous admin I already have a user 'backup' on the server who has an entry for a sudo command to rsync everything to that former admin's local machine. So all I need to do is changing the address of that sudo entry to my machine's address -- if only I could get the connection to work.

The other scenario is making root access via ssh work.

But I do not have any idea about both.

Horus

---

### Post by horus8 on 2006-06-21
[QUOTE=lamego]You can run the rsync daemon on the system you want to backup. I found this [article](http://www.freeos.com/articles/4042/) describing it.[/QUOTE]
This looks like agood idea. But on first glimpse I already found some small but essential stones in my way:
1. It says to put the user password in the /etc/rsyncd.secrets. Is this password in clear text or is it to be encrypted? If encrypted, how do I do this?
2. It says to give the hostsallow IP which I can't because my local IP changes from day to day.
etc.

As I said, I was thrown into cold water before I had the chance to learn to swim. If I had the time I'd set up a server on one of my machines, buy a SAG book and start to learn (which is what I'll be doing in my vacation in September anyway). But right now I do not have the time. The server is the server of a free community site and I am very anxious not to mess anything up. Of course, running this site as a community site means also that I cannot just go out and hire an experienced server admin to do all this.

Horus

---

### Post by MJN on 2006-06-22
[SIZE=2]Another option which I don't think has been covered (apologies if I somehow missed it) is to take advantage of the seemingly-little-known ability for SSHD to disallow root logins yet still allow specific commands to be run as root whilst logged in as a non-root user.
 
It basically requires the **permit-root-login no** option to be changed to **permit-root-login forced-commands-only** in the remote server's SSHD config file and then for you to enable your rsync command to be permitted by associating it with a public/private key pair - the same key pair that you will need to use to login in the first place (which will also allow automated backups, if required, without storing a cleartext password).
 
This probably sounds complicated, and indeed it will do so particularly as you've only just started learning about rsync and to extend its capability like this requires further public/private key creation and some additional SSHD configuration. However, like everything else there are many guides to walk you through it e.g. [/SIZE][_[SIZE=2][COLOR=#0000ff]http://lts2www.epfl.ch/~jost/rsync.html[/COLOR][/SIZE]_]("http://lts2www.epfl.ch/~jost/rsync.html")[SIZE=2] and [/SIZE][_[SIZE=2][COLOR=#0000ff]http://www.jdmz.net/ssh/[/COLOR][/SIZE]_]("http://www.jdmz.net/ssh/")[SIZE=2] (the former is a rewrite of the latter however it may help your understanding to read two interpretations of the same steps).[/SIZE]
[SIZE=2]
Mathew
[/SIZE]

---

### Post by horus8 on 2006-06-22
Thanks all for your input, I appreciate your help! I will spend another day reading HowTos and Fine Manuals and will come back again with the results. In the end I may (hopefully) be able to write a step-by-step "RFARSIRA for Dummies" (rsync from a remote server including root access for dummies). :D 

Horus

---

### Post by MJN on 2006-06-22
Best of luck, however if there's one thing we don't need it's YARHT (Yet Another Rsync HowTo!)! There're dozens of them out there! (Still, I suppose one more won't hurt!) ;)
 
Mathew

---

### Post by horus8 on 2006-06-22
[QUOTE=MJN]Best of luck, however if there's one thing we don't need it's YARHT (Yet Another Rsync HowTo!)! [/QUOTE]
As you can see in my case, that one I may be writing is not there yet. :) 
Besides, I'll write it in German, so none of you will be bothered to read it anyway. :mrgreen: 

Horus

---

