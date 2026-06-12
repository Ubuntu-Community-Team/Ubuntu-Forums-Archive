---
title: "symlinks and apache"
date: 2010-04-06
forum: Server Platforms
---

### Post by luftadler on 2010-04-06
Hi all


My apache server don't want to start by itself on boot

I've removed the links from symlinks

**sudo update-rc.d **[B]-f apache2 remove

[/B]and set them to defaults
**sudo update-rc.d **[B]-f apache2 defaults
[/B]
nothing works... i have to start it mannualy

any ideas about this isue Regards,
Cristian

---

### Post by cdenley on 2010-04-06
When you start it manually, are you prompted for a password for an SSL certificate?

---

### Post by luftadler on 2010-04-09
> **cdenley said:**
> When you start it manually, are you prompted for a password for an SSL certificate?

No, is starting normally 

```
sudo /etc/init.d/apache2 start
* Starting web server apache2                                           [ OK ] 
```now I've tried to change the run level 

```
ls -l /etc/rc2.d/*apache2
```... the problem is the same

---

### Post by cdenley on 2010-04-09
```

sudo update-rc.d -f apache2 remove
sudo update-rc.d apache2 start 91 2 3 4 5 . stop 09 0 1 6 .
ls -l /etc/rc2.d/S91apache2

```

---

### Post by luftadler on 2010-04-09
```
$ sudo update-rc.d -f apache2 remove
 Removing any system startup links for /etc/init.d/apache2 ...
   /etc/rc0.d/K09apache2
   /etc/rc1.d/K09apache2
   /etc/rc2.d/S91apache2
   /etc/rc3.d/S91apache2
   /etc/rc4.d/S91apache2
   /etc/rc5.d/S91apache2
   /etc/rc6.d/K09apache2

$ sudo update-rc.d apache2 start 91 2 3 4 5 . stop 09 0 1 6 .
 Adding system startup for /etc/init.d/apache2 ...
   /etc/rc0.d/K09apache2 -> ../init.d/apache2
   /etc/rc1.d/K09apache2 -> ../init.d/apache2
   /etc/rc6.d/K09apache2 -> ../init.d/apache2
   /etc/rc2.d/S91apache2 -> ../init.d/apache2
   /etc/rc3.d/S91apache2 -> ../init.d/apache2
   /etc/rc4.d/S91apache2 -> ../init.d/apache2
   /etc/rc5.d/S91apache2 -> ../init.d/apache2

$ sudo ls -l /etc/rc2.d/S91apache2
lrwxrwxrwx 1 root root 17 2010-04-09 15:09 /etc/rc2.d/S91apache2 -> ../init.d/apache2
```:confused:

the problem is the same. \\

---

### Post by cdenley on 2010-04-09
How is your network configured? On a server, it should be configured with /etc/network/interfaces. If you use the NetworkManager applet, which I think is the default for a desktop install, then you may not have a network configured when apache attempts to start.

You can test this by adding this line to /etc/init.d/apache2
```

#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          apache2
# Required-Start:    $local_fs $remote_fs $network $syslog
# Required-Stop:     $local_fs $remote_fs $network $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start/stop apache2 web server
### END INIT INFO
#
# apache2               This init.d script is used to start apache2.
#                       It basically just calls apache2ctl.

ENV="env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin"
**ifconfig>/apache.txt**

```
Then reboot, and check the output that was generated
```

cat /apache.txt

```

---

### Post by luftadler on 2010-04-09
I think is another problem ... 
also, the postgesql server is not starting at boot

and network works...
:-(

---

### Post by cdenley on 2010-04-09
> **luftadler said:**
> I think is another problem ... 
also, the postgesql server is not starting at boot

and network works...
:-(

The network works when the init scripts are run, or the network works after you login? Your network not being up when init scripts are running would explain both your problems.
```

cat /etc/network/interfaces

```

---

### Post by luftadler on 2010-04-09
first, i have no output under **/etc/init.d/ **after reboot, no **apache.txt** was generated
secod, this is the output of [B]cat /etc/network/interfaces

[/B]```
uto lo
iface lo inet loopback
```but I don'u undestand what is all about
:(

---

### Post by cdenley on 2010-04-09
> **luftadler said:**
> first, i have no output under **/etc/init.d/ **after reboot, no **apache.txt** was generated
secod, this is the output of [B]cat /etc/network/interfaces

[/B]```
uto lo
iface lo inet loopback
```but I don'u undestand what is all about
:(

Did you add the line to /etc/init.d/apache2 which I suggested, which would pipe the output of "ifconfig" to the file /apache.txt, which you can then check after the system finished booting with the command "cat /apache.txt"? If that is all that is in /etc/network/interfaces, then your network interfaces are not configured in that file, and may not be configured when your servers attempt to start.
[https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)

---

