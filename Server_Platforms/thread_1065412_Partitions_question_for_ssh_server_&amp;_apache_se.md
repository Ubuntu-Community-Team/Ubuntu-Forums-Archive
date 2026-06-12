---
title: "Partitions question for ssh server &amp; apache setup"
date: 2009-02-09
forum: Server Platforms
---

### Post by neilevan814 on 2009-02-09
Okay, I hope I will be clear here.  I want to set up a very minimal use apache server and ssh server on my new desktop computer build.  What I want to attempt to do, since this will also serve a purpose for storing data, music, movie, etc type files, is to have a 2 disk set up of which one will be solely a data store.  My question is if I partition my installation disk to have a separate partition for /home and I reconfigure fstab to point to this as /home, if I need to reinstall ubuntu or upgrade will this set up preserve my ssh server and apache server settings?  Will I have to reconfigure fstab on the reinstalled OS to resume the use of my /home partition then?  I hope this makes sense  because I am not sure, but am trying to get the whole picture.  Thanks in advance for the help!

---

### Post by spiderbatdad on 2009-02-09
basically no. You will need another way to back up your config files, data files, etc...like external media: cd, flash drive, and so on. Most of those files are not in home, but in other parts of the root file system, /etc/apache2, /etc/ssh, /var/www, and so on.

---

### Post by neilevan814 on 2009-02-09
Okay thanks.  I forgot where all those files were on the last system I set up...So what if I made separate partitions for /etc and /var as well can I do this...When I originally install and I set these partitions will the installation use all these partitions for these particular file directories and will it know to upgrade in the same fashion if I initiated an upgrade through synaptic?  I need some enlightening on the whole architecture I think.

---

### Post by hyper_ch on 2009-02-10
server config is in /etc
webpages normally in /var/www
mysql dbs normally in /var/lib/mysql

it will know those partitions if you upgrade through synaptic. But as you said you setup a minimal server, why do you have synaptic on there?

---

### Post by neilevan814 on 2009-02-10
Oh, minimal server, what I meant was very under utilized server.  Basically set up with a dyndns free domain and a port forwarding address to learn on and serve only a few pages to craigslist for things I am selling.  Eventually I will set my system up under ubuntu server, but I need to get my new htpc build done first, so I can retire the old one to a corner for that one sole purpose.

---

