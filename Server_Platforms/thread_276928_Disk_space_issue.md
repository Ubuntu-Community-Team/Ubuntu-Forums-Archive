---
title: "Disk space issue"
date: 2006-10-13
forum: Server Platforms
---

### Post by jose3 on 2006-10-13
Hi guys I suddently ran out of disk space and coudnt startx as well as run FE MySQL I figure out it is disk space due to this:


Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             5,6G  5,5G     0 100% /
varrun                189M  172K  189M   1% /var/run
varlock               189M  4,0K  189M   1% /var/lock
udev                  189M   84K  189M   1% /dev
devshm                189M     0  189M   0% /dev/shm
/dev/sda1             111G   66G   39G  63% /home/HD2
/dev/sdb1             220G   97G  112G  47% /home/HD1
/dev/sdb2             9,7G  953M  8,2G  11% /home/IMAGEN

/dev/hda1 is 100% and I cannot tell why because I have been following the partition space for quite a long time. Weird. 


Any suggestions what should I do in order to free space? Is there any tool that shows the amount of space used in each folder? 
Should I make an image of the disk and restore it on another bigger disk?

Please advice me cause I dont want to go ahead with a clean install again. ](*,) 

Thanks lot guys.

---

### Post by kidders on 2006-10-13
Hi there,

There's probably lots of stuff you can get rid of without too many side-effects. Examples might include the contents of /tmp, old gzipped log files, your package cache, ~/.thumbnails, etc., etc.

Try not to keep your box on for too long with no free disk space ... Linux can react pretty unpredictably, sometimes!

For the future, you might want to take a look at the **du** utility, and see if you can shove something like /var or /usr/local onto another disk/partition, so you don't run out of space again. Solving disk space issues by removing temporary files (as I suggested) is only a temporary fix!

---

### Post by Peepsalot on 2006-10-13
i think "sudo apt-get clean" will free up all those downloaded packages that have accumulated.  Though I haven't tried it ever, so don't blame me if something breaks. ;)

---

### Post by Peepsalot on 2006-10-13
baobab is a graphical disk usage program for gnome.  (looks like it is installed by default)
kdirstat for KDE

---

### Post by dannyboy79 on 2006-10-13
can't you also get rid of stuff in /var? what about /etc/apt/cache. the person who suggested sudo aptitude clean is correct, I have done that before on my  laptop, it cleans out all downloaded .deb's i believe. per the aptitude help: clean- Erase downloaded package files and autoclean- Erase old downloaded package files. so i would try autoclean first and so how much space you get. just noticed that /var/cache/apt/archives has almost .5 gb in it but I don;'t know if you need all those old packages probably is safest using the aptitude autoclean. don't forget about your trash bins! that's something I always forget about!

---

### Post by jose3 on 2006-10-13
I am glad for all the tips you guys have given me. Thanks !!!

I give a try.

---

