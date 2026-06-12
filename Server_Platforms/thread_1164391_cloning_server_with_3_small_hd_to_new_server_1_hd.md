---
title: "cloning server with 3 small hd to new server 1 hd"
date: 2009-05-19
forum: Server Platforms
---

### Post by confusedstingray on 2009-05-19
looking to clone a web,ftp,mail server that has 3 small hard drives about 200gig total
running ubuntu 8.04.1 server LTS.
Want to mirror all hd's to 1 hd in a new machine and keep the old server running. while bringing the new one up.
also down the road want to set the 2 servers up for fallover.
any help on the clone would be great the fallover work on later
thanks

---

### Post by mellowd on 2009-05-22
Other people may do it different, but I'd install a fresh server and then copy over the files seperately using rsync or something similar. This will ensure you get a clean copy. Just don't copy /etc/fstab as well of course.

---

### Post by windependence on 2009-05-22
rsync would be my choice as well. You'll get people who tell you your data could get corrupted if you do this hot, but I have never had a problem with it on any of my production servers.

-Tim

---

