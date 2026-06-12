---
title: "Ubuntu server backup, read for info"
date: 2009-06-03
forum: Server Platforms
---

### Post by iLoVe.cF- on 2009-06-03
Well, im currently at school, wrapping up everything soon, made most clear for next years pupils.
There is a possibility that none of the next years pupils are able to fix my stuff which isnt fixed.

The setup is as:
Servicedesk system:
GLPI project.
mysql
Ubuntu server 8.04
simple hardware setup with no raid, just a plain pc.

I got hardware for external backups which i liked to do!

I got a backup script i got from sourceforge.net for mysql.
[http://sourceforge.net/project/downloading.php?group_id=101066&filename=automysqlbackup.sh.2.5&a=14987825]("http://sourceforge.net/project/downloading.php?group_id=101066&filename=automysqlbackup.sh.2.5&a=14987825")
And it got a feature that it can run a script when the backup procedure is done.

I was thinking about.

cp -R /var/www/ /home/sd/backups/
cp -R /home/sd/backups/ /media/"remote mount point"

I was brainstorming abit, i dont have much time, so i thought of freenas, running iscsi which i have kind of fell in love with.
Does freenas support mirroring 2 drives by software(no hardware/software controller) meaning 1 os drive for freenas and two for the backup itself.
and iscsi over wan....?

Well, provide a simple solution that can be done with rather simple hardware, we have already maxed out our budget for this year.

I just want a little point in what direction thats the smartest.

---

### Post by Pnuts on 2009-06-03
Freenas should be able to do software RAID for you and if you have a spare USB memory stick around, you can run it off of that and use all 3 drives if you want. Assuming the PC boots USB.

No idea about the iscsi though

---

