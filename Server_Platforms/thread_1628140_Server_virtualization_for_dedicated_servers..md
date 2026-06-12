---
title: "Server virtualization for dedicated servers."
date: 2010-11-22
forum: Server Platforms
---

### Post by artheus on 2010-11-22
Hey,

I've got a small web hosting service, for some of my friends. Where I want my friends to be able to have dedicated virtual servers just for a simple LAMP and ftp-server.

I've got quite limited hardware.

AMD Athlon II (Dual core)
4 GB 1333 MHz DDR3 RAM
100 Mbit Fiber-lan ( Dynamic IP )

What I would want to know is how to create the virtual servers in an truly optimal way. Should I use KVM or VirtualBox?
How can I make the request to mydomain.org go to one of the virtual servers and the request to anotherdomain.com go to another virtual server?
Maybe there are better ways of solving my problem?

If the virtual server is the best solution.
* How much memory should be sufficient for a simple LAMP/FTP-server?
* What would be the most optimal settings for my limited hardware capacity?

Any help or suggestions are welcome!

Thanks,
Artheus

---

### Post by SeijiSensei on 2010-11-22
Virtual servers are probably not what you want to use.  Each virtual machine would be running in its own memory space; for Ubuntu server you'd need at least 256M per server, with 512M preferred.  

You're much better off using named virtual hosting with the Apache web server.  Give each person an account on the box with a directory into which to place their website files.  Create individual databases in MySQL for each user as well.  Any good FTP server can be configured to use "chroot" to let each person log into her home directory and upload/download from there, but not wander around the entire filesystem.  Then create separate <VirtualHost> containers in Apache for each site.  I usually create separate files defining each site and place them all in /etc/apache2/sites-enabled.  You can follow the 000-default file in that directory as an example.

This is how hosting providers handle multiple users. Using separate VMs is overkill and a waste of system resources.

---

