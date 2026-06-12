---
title: "Remote backup my Server to an .img file"
date: 2015-01-21
forum: Server Platforms
---

### Post by guldberg72 on 2015-01-21
Hello Everybody. i have the following setup at home Router <-> Raspberry Pi (has an ext. hdd so the backup should be stored here) <-> Ubuntu server Lamp stack.
i was wondering how can get my server to make a backup of apache, php, mysql and my /var/www/ folder. 

it should be a automatic job my server performs every week and and then just overwrite the old backup. is that possible ? and how ? 
i have been using clonezilla until now but i think it is annoying to boot my server up on a live usb, to perform the backup so i really want it to be an automatic process :D

i would prefer the backup as an .img file but i am open to suggestions :D

---

### Post by TheFu on 2015-01-21
You can name your backup files anything you like, but it is extremely unwise to create an image of any running database. Corruption is possible.

Making an image backup of a running system really isn't smart, but you can do whatever you like at the risk of a corrupted backup.

Also, having 1 backup is not nearly enough.  What happens if you machine gets hacked and you don't notice for a month?  Or a file becomes corrupted somehow and you don't notice for 2 weeks?  Incremental backups will provide time to notice and recover. Incremental backups are highly network and storage efficient these days. I've been keeping 60-120 days of backups, depending on the nature of the system and whether it is internet facing or not.

Regardless - there are many, many, many threads here about backing up servers and desktops recently. Take a look in the server subforum for those discussions with pros/cons.  You'll want to handle mysql dumps before doing backups. Ensure the mysql dumps are in a file area within your backup.

The debian administrator website has lots of backup examples, which are nice to learn about.

Provided there isn't a GUI, all of these methods can be scripted and added to a crontab.

---

