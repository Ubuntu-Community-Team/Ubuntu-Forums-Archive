---
title: "Web Server Backup Advice"
date: 2010-07-26
forum: Server Platforms
---

### Post by danbishop on 2010-07-26
I have an Ubuntu web server configured and running just the way I like it.

I want to be able to back it up. There are hundreds of guides on this, but none of them seem to quite do what I want.

Firstly, I want a system I can just forget about until I need to restore.

Secondly, it must back up not only all mysql databases, but also all files in /home and /var/www AS WELL AS all my configuration AND installed packages...

That's to say I want to be able to quickly restore the whole server in the event of major hardware failure. The server has several extra packages installed from the main repo and lots of configration that's been done in /etc so I want all this to remain intact.

Finally, the option to automatically store the backup remotely as well as locally would be nice.

Is there any all-in-one solution for this? Or will I have to write scripts to do every individual bit :(

What does anyone else use for web server backups? Is there anything with a nice web-based frontend maybe?

I'm really lost with all the different options I've come across and would be so grateful for any advice from anyone who's had experience in this. Sorry for such a long post and thanks in advance!!! :D

---

### Post by Ryan Dwyer on 2010-07-26
I would just script it.

Use mysqldump to export your MySQL databases.
Use dpkg -l to export a list of installed software
Use an archive/compression tool to create a compressed backup of the files you want.

Then you can FTP or SCP it all to another machine.

I'd also do restoration manually.

---

### Post by danbishop on 2010-07-26
Thanks Ryan, I guess you're right, I'll give this a try and test restoring it to another machine.

---

### Post by Sporkman on 2010-07-27
I've scripted my webserver setup. It's very handy to have a VM to develop this on (I use Virtualbox), which you can save a snapshot of the base OS install. You can then develop the script & test the installation through repeated snapshot-restores.

---

### Post by richardjh on 2010-07-27
I looked at using MondoRescue to image the whole server before, it works well and if you have time it is worth checking out.

However I now have a script that mysqldumps databases, backs up subversion repositories, copies crontabs and config files, gets installed packages using dpkg and tars up my /var/www/ folder and /var/log folder and dumps all of that into a folder in my home directory called ~/backup/.

It used to then continue by rsyncing my home folder to a remote server but that has since changed and the remote server now pulls a backup using BackupPC. 

This makes it trivial to restore individual files through a web interface as well as being able to rebuild my machine using the install CD and my backup in a little over an hour.

BackupPC is very good and also worth checking out.

---

