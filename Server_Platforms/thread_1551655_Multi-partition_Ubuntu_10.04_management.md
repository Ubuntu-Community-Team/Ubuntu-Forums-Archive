---
title: "Multi-partition Ubuntu 10.04 management"
date: 2010-08-12
forum: Server Platforms
---

### Post by fred2028 on 2010-08-12
I have 2 partitions, 1 for OS and 1 for data. The OS 1 is going to be imaged with every Ubuntu OS update so that this image can be taken from the testing server to the live server. However, the data must stay on the live server, so the imaging it will not erase the data. Therefore, I divided the live server into 2 partitions: OS and data.

I want to be able to save all of my customizations and data on the live server to the data partition. This includes (but is definitely not limited to) MySQL databases, Apache configurations, my /var/www/ folder, etc. How would I go about doing this? As in how do I set MySQL/Apache/etc. to save their configuration files on the data partition? Or is there a totally better way to achieve what I want?

Thanks!

---

### Post by lukeiamyourfather on 2010-08-12
One way is to manually go change all of the configuration files for each software to point to the other partition. Another is to setup symbolic links in place of directories where data would normally be stored and point them to the other partition.

---

