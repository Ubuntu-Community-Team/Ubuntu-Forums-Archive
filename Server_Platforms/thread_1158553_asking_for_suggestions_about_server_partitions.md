---
title: "asking for suggestions about server partitions"
date: 2009-05-13
forum: Server Platforms
---

### Post by chuugokujin on 2009-05-13
Hi,
I have a ”4G mem and 2 x 1TB HD“ server for a small business.
I want to make it file server, web server, database server and email server, and use raid mirror on both HD.
Could anyone give me a suggestion about how to partition it?
(such as put /var and /tmp seperated&#65292; and each 20G, I'd like to see details)
Thanks!

---

### Post by a9k3d on 2009-05-14
I have 2 x 2Tb raid 1 server also. I've tried various setup in the past. This time I used a simple one.
I made a small partition on each (same size on both == 1.5X ram size), and used one for /boot and the other for swap. The rest is raid1 md0 / root. Works great. I use that setup on my production servers also.

One handy thing to do is separate your home and media files from the basic system (so / and /home /bigdata (my name)  on diff partitions). That way if you get sick of Ubuntu and want to try some other distro, you can trash the / (root) parition with a new OS and keep all those tunes you collected.

I don't do that. Instead I split the raid up - one drive becomes the old backup and the other usually get replaced with a bigger drive that is the target for the new OS. Then I copy the backup's datafiles, to the new one, install the 2nd new big one and raid that pair. Many hours later it's all sync'd up.

---

