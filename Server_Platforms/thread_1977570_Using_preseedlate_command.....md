---
title: "Using preseed/late_command...."
date: 2012-05-10
forum: Server Platforms
---

### Post by ragtag on 2012-05-10
I'm setting up an automatic install of Ubuntu 12.04, using preseed. Everything installs fine, without any questions, but I can't quite figure out how to use the late_command at the end of the preseed file.

What I want to do is wget a shell script and run that.

I tried:
```
d-i preseed/late_command string chroot /target;cd /;/usr/bin/wget http://ubuntu/12.04/postinst/files.tar.gz;/bin/tar -zxvf files.tar.gz;/bin/sh files/post.sh;touch /root/test;   
```

But it just hung at the very end of the installation. The installation was functional, but the script had not run at all.

Is the newly installed file system mounted under /target? And what's the environment like at this point in the install. What would be the correct way to do this?

---

### Post by rgcosma on 2012-05-10
Hi - a working script would look like this:
```
d-i preseed/late_command string \
in-target wget -O /tmp/files.tar.gz [http://ubuntu/12.04/postinst/files.tar.gz](http://ubuntu/12.04/postinst/files.tar.gz) ; \
in-target tar zxf /tmp/files.tar.gz -C /tmp/ ; \
in-target /bin/sh /tmp/files/post.sh ; \
in-target touch /root/test
```

---

