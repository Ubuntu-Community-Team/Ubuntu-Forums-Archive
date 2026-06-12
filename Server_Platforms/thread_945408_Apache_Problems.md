---
title: "Apache Problems"
date: 2008-10-12
forum: Server Platforms
---

### Post by thidranki on 2008-10-12
I just recently installed and set up the Linux server edition. I installed the LAMP server, FTP server, and SSH server. 

After installation, I rerouted my domain to the IP address of the box and it worked!

However, I started going through the documentation for the ubuntu server, and I installed a few things (like apparmor, ebox, ssl) and then now whenever I try to visit my site, it times out. I tried uninstalling these things that I installed while following the documentation, but to no avail.

However, my ftp server and ssh server still work. Just not the http one.

Do you have any suggestions or idea for how I can get apache2 working again? One thing I noticed is that I get emails to my server's machine (I installed Mutt, but haven't configured it) every hour saying that there was an error with ebox, but I thought I had uninstalled it.

Thanks.

---

### Post by thidranki on 2008-10-12
also, all of my config files are fine, and the site is enabled.

---

### Post by cariboo on 2008-10-12
Just because you uninstalled a program doesn't mean that the configuration files got uninstalled. To complete;y uninstall a program you need to use the purge option with either apt-get or aptitude eg:

```
sudo apt-get purge ebox
```

Also be sure that the daemon is not running:

```
sudo /etc/init.d ebox stop
```

For your apache problem, did something you installed block port 80?

To check you can use netstat:

```
netstat -tulpn
```

or 

```
nmap localhost
```

Jim

---

### Post by thidranki on 2008-10-12
Here are the outputs of the commands.

For purge:
package ebox is not installed, so not removed.

For init.d/ebox stop
"Can't locate EBox/Global.pm in @INC (@INC contains: /etc/perl /user/local/lib/perl/5.8.8 etc...) at /etc/init.d/ebox line 14
BEGIN failed--compilation aborted at /etc/init.d/ebox line 14

for nmap:
...
80/tcp open http
...

still doesn't work

---

