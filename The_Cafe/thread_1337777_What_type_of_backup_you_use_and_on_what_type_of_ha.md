---
title: "What type of backup you use and on what type of hardware?"
date: 2009-11-25
forum: The Cafe
---

### Post by Nimless on 2009-11-25
As thread name suggests,what kind of backup are you using ? ( If you are backupping your data of course :P )

Are you using r-sync...tar...bakula? and where you backup to? usb disk/flash drive? Nas? Another Computer? Online server ?

I have a second disk attached to my "main" computer and backup stuff using a r-sync cron job to that disk , but thinking about upgrading my "backup infrastructure" :D

---

### Post by juancarlospaco on 2009-11-25
On Desktop: 
Ubuntu's Time Machine: Back In time
U1 Cloud: ODF Docs encrypted

On Server:
ETCKeeper
Rsync
Bacula

---

### Post by jrusso2 on 2009-11-25
I do a differential back up of any data to my server.

---

### Post by CharlesA on 2009-11-25
I just rsync my data to an external drive.

---

### Post by gn2 on 2009-11-25
Grsync to an NSLU2

---

### Post by cariboo on 2009-11-25
Grsync daily to server, rsync weekly sever to exteranl

---

### Post by dragos240 on 2009-11-25
Well. For small things, I use dropbox. Otherwise, I don't really backup. Nothing of value.

---

### Post by beercz on 2009-11-25
Automated [rsnapshot]("http://rsnapshot.org") backup to a backup server every day.  Server runs it as a cron job to automatically backup my laptop.

Works like a charm!

---

