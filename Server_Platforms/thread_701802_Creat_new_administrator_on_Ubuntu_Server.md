---
title: "Creat new administrator on Ubuntu Server"
date: 2008-02-19
forum: Server Platforms
---

### Post by damonjablons on 2008-02-19
I just installed a new Ubuntu Server and I can't accomplish what should be the simplest thing.  I want to create a new User and add them to the administrator group.  What's the best way to do this?

Thanks in advance!

by the way, if there's a good wiki or tutorial on ubuntu server stuff, please let me know!

---

### Post by bodhi.zazen on 2008-02-19
Create a new user, add him/her to the admin group (for full access) or modify sudo if you want more limited root access.

I personally find it easiest to manually edit /etc/group, but you may like the command line.

sudo adduser <username> <group>

==========

In terms of a server guide, there are many available. Look at the stickies here.

Also try the ubuntu wiki or external links :

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

	[http://linux.about.com/od/ubusrv_doc/a/ubusrv_doc_idx.htm](http://linux.about.com/od/ubusrv_doc/a/ubusrv_doc_idx.htm)

[http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

[http://doc.gwos.org/index.php/ServerGuide](http://doc.gwos.org/index.php/ServerGuide)

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

