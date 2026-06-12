---
title: "Recovering a mysql database from a hard disk"
date: 2007-04-24
forum: Server Platforms
---

### Post by siennalizard on 2007-04-24
Dear all,

I've got a crashed upgrade from Edgy to Feisty. Suffice to say that I don't have a running system anymore... I've easily recovered most of my file data, but there are a few non-essential but nice to have MySQL databases on there. Is there a nice way to recover them using a live CD, bearing in mind that I cannot actually run MySQL on the server (at least, with that dataset). Ideally, I'd like to get it out as SQL that I can load on to another server.

Many thanks,
J.

---

### Post by johnleonard on 2007-04-25
If your other server is running MySQL I suggest you copy the database folders and table binaries that are in /var/lib/mysql onto a CD. On the new server copy these into the corresponding directory. If it is running MS SQL I'm not sure this will work

---

### Post by Spiny Norman on 2007-04-25
You could try "tar -cvpzf BackupMysql.tar.tgz mysql/"
Rebuild another lamp server and after commenting out the folder mysql in /var/lib place the file in var/lib run "tar -xvpzf BackupMysql.tar.tgz" That is how I have been doing simple backups on a lamp server for some time now. If you can get to that folder of course!

Note: stop mysql first "/etc/init.d/mysql stop" and make sure you are in #var/lib before you run the first command.

---

