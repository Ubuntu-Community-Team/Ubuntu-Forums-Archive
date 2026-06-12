---
title: "/var/run, /var/lock , /dev/shm"
date: 2011-01-18
forum: Server Platforms
---

### Post by cormu7 on 2011-01-18
Hello,

I just recently started using ubuntu. I recently installed ubuntu and did the partitioning. However, when i type in the "df" command, i get this:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             19222656    386168  17859952   3% /
none                  12358348       296  12358052   1% /dev
none                  12363188       332  12362856   1% /dev/shm
none                  12363188       412  12362776   1% /var/run
none                  12363188         0  12363188   0% /var/lock
none                  12363188         0  12363188   0% /lib/init/rw
/dev/mapper/vg03-usr  96118540   2907748  88328156   4% /usr
/dev/sda7              4804736    165176   4395492   4% /tmp
/dev/sda8              9611492    995480   8127772  11% /var
/dev/mapper/vg01-data
                     2685654296    206864 2549024008   1% /data
/dev/mapper/vg02-home
                      19219156    274940  17967936   2% /home

Under the Filesystem header, i'm not quite sure what "none" indicates, and what exactly do the /dev/shm, /dev/, /var/run/, /var/lock, /lib/init/rw, partitions indicate? Is there something that i did wrong with the partitioning during installation?

your help would greatly be appreciated.

thanks,

cor

---

