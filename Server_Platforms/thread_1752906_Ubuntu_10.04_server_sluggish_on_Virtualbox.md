---
title: "Ubuntu 10.04 server sluggish on Virtualbox"
date: 2011-05-08
forum: Server Platforms
---

### Post by platz on 2011-05-08
I've recently done some experiments with virtualization on my own hardware,  partially because I have recently set-up a linode with Ubuntu 10.04. I have found that Ubuntu 10.04 server is sluggish when virtualized on Virtualbox, while 9.04 and 11.04 servers are snappy, the latter being the snappiest, which makes sense. What doesn't make sense to me is the sluggish behavior of 10.04. All three servers were installed the same way, etc. I am wondering if there are some unusual requirements 10.04 has for Virtualbox. Has anyone else experienced something similar?

---

### Post by abhay4589 on 2011-05-08
Did you install Guest Edition on Virtual Box?

---

### Post by platz on 2011-05-08
> **abhay4589 said:**
> Did you install Guest Edition on Virtual Box?
I'm not sure guest additions will help with the server, it's primarily gui integration and folder sharing, isn't it? Regardless, I don't have the same trouble with either 11.04 server or 9.04 server, neither with guest additions installed - I don't think guest addition could be the issue.

---

### Post by dtfinch on 2011-05-09
There's a problem with Ubuntu Server defaulting to graphics mode instead of text mode, and then choosing the worst/slowest possible framebuffer driver when running in a vm. The only solution I'm aware of is to add "blacklist vga16fb" to "/etc/modprobe.d/blacklist-framebuffer.conf", which will cause it to fail to switch to the mode on next boot.

[http://screamingadmin.wordpress.com/2010/07/08/vga16fb-and-ubuntu-10-04-server/](http://screamingadmin.wordpress.com/2010/07/08/vga16fb-and-ubuntu-10-04-server/)

---

### Post by platz on 2011-05-09
Thanks, that was the the exact issue I was having. I wonder why 9.04 has the line in /etc/modprobe.d/blacklist-framebuffer.conf, but not 10.04. Anyway, great to know this!

---

