---
title: "New Server with 3Ware Raid"
date: 2009-02-03
forum: System76 Support
---

### Post by 76cl76 on 2009-02-03
Greetings,

All around ubuntu newbie. I have successfully stumbled thru Samba, Mounting NAS drives and creating Cron events for backups using rsync. Now I need a little help with the ability to SEE or view the status of my 3Ware Raid5. I made an assumption that it was completely setup and operational as delivered. Sure hope it is.

I did interrupt bootup and indeed, it looks like it is there and working, though when running the battery check, it reported that the battery was "charging". It acted as if I -initiated- the charging, and would not report battery condition until it was charged. I need to return to that interface and check that yet.

But the bigger issue now is that it seems that the command lines that look like would take me to a status window of tw_cli or ./tw_cli doesnt take me anywhere.

Responses are: bash: tw_cli: command not found and bash: ./tw_cli: No such file or directory.

Attempts to install the 3ware 3DM2 browser did not go well either, perhaps because the whole setup is in a different folder ? Unfortunately, I am not familiar with the Linux file layout yet, and to me it looks like there is just a zillion folders, all named "bin" <G>.

Ok, any ideas ? This is one of the last straggling issues before I can set this thing on a 2 week basic test before going into daily service.

thanks !

---

### Post by thomasaaron on 2009-02-03
tw_cli isn't installed by default. It is a third-party package.

Have a look at this. It should get you pointed in the right direction.
[http://knowledge76.com/index.php/3ware_RAID_Managment](http://knowledge76.com/index.php/3ware_RAID_Managment)

---

### Post by jdb on 2009-02-03
> **76cl76 said:**
> Greetings,

All around ubuntu newbie. I have successfully stumbled thru Samba, Mounting NAS drives and creating Cron events for backups using rsync. Now I need a little help with the ability to SEE or view the status of my 3Ware Raid5. I made an assumption that it was completely setup and operational as delivered. Sure hope it is.

I did interrupt bootup and indeed, it looks like it is there and working, though when running the battery check, it reported that the battery was "charging". It acted as if I -initiated- the charging, and would not report battery condition until it was charged. I need to return to that interface and check that yet.

But the bigger issue now is that it seems that the command lines that look like would take me to a status window of tw_cli or ./tw_cli doesnt take me anywhere.

Responses are: bash: tw_cli: command not found and bash: ./tw_cli: No such file or directory.

Attempts to install the 3ware 3DM2 browser did not go well either, perhaps because the whole setup is in a different folder ? Unfortunately, I am not familiar with the Linux file layout yet, and to me it looks like there is just a zillion folders, all named "bin" <G>.

Ok, any ideas ? This is one of the last straggling issues before I can set this thing on a 2 week basic test before going into daily service.

thanks !

Try 

man find

it's a great command.

find / -name tw_cli 2>/dev/null

will find it wherever it is.

The 2>/dev/null redirects standard error to nowhere land and makes the output much more readable.
Try it without that & you'll see what I mean :)

jdb

---

### Post by 76cl76 on 2009-02-03
man find came up empty, so I gave thomasarrons direction a shot.

GOT IT ! Wonderful ! Thanks.

Now on to sendmail so I can get this machine to send me events.

---

