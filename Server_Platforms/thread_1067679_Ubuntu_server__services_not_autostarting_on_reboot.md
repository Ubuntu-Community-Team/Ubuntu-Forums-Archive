---
title: "Ubuntu server : services not autostarting on reboot"
date: 2009-02-12
forum: Server Platforms
---

### Post by skewbie on 2009-02-12
Hi there

I have an Ubuntu Server 8.10 installation which is being used to host a CMS system. It is a virtual machine on VM ESX Server 3.3 with no display manager.

My problem is that there are a number of services which are not starting on reboot:

apache
sshd
xinetd
nbclient (Netbackup client - dependant on xinetd running)

The rc scripts are in place and I have even modified them from relative paths to absolute just in case but to no avail.

Can anyone help?

Thanks very much in advance.

Steve.

---

### Post by linux_tech on 2009-02-12
For apache restart failure, are there any clues in error log? 

/var/log/httpd/error_log

in terminal try:

```
sudo apachectl configtest
```

to verify the configuration files

---

### Post by RealPSL on 2009-02-12
What happens if you run?```
sudo invoke-rc.d ssh start
``` Does ssh actually start? Try running ```
sudo update-rc.d ssh defaults
``` Does that make ssh start on boot? update-rc.d is the correct way to manipulate the startup scripts.

---

### Post by skewbie on 2009-02-13
Thanks linux_tech. There are no errors in the error log

Here is the output from that command:

root@willow:~# sudo /app/apache22/bin/apachectl configtest
Syntax OK

I am now using a custom built apache and created my own symlinks in /etc/init.d and the various rc*.d dirs but I have just rebooted and again it did not start. Here is some output:

root@willow:~# for d in 0 1 2 3 4 5 6; do ls -l /etc/rc$d.d/*apache-willow; done
lrwxrwxrwx 1 root root 25 2009-02-12 09:06 /etc/rc0.d/K09apache-willow -> /etc/init.d/apache-willow
lrwxrwxrwx 1 root root 25 2009-02-12 09:00 /etc/rc1.d/K09apache-willow -> /etc/init.d/apache-willow
lrwxrwxrwx 1 root root 25 2009-02-12 09:01 /etc/rc2.d/S91apache-willow -> /etc/init.d/apache-willow
lrwxrwxrwx 1 root root 25 2009-02-12 09:05 /etc/rc3.d/S91apache-willow -> /etc/init.d/apache-willow
lrwxrwxrwx 1 root root 25 2009-02-12 09:05 /etc/rc4.d/S91apache-willow -> /etc/init.d/apache-willow
lrwxrwxrwx 1 root root 25 2009-02-12 09:05 /etc/rc5.d/S91apache-willow -> /etc/init.d/apache-willow
lrwxrwxrwx 1 root root 25 2009-02-12 09:06 /etc/rc6.d/K09apache-willow -> /etc/init.d/apache-willow

root@willow:~# who -r
         run-level 3  2009-02-13 08:42                   last=2


With regards to RealPSL's suggestions, I get the following output:

root@willow:~# sudo invoke-rc.d ssh start
 * Starting OpenBSD Secure Shell server sshd    [ OK ]

And:

root@willow:~# sudo update-rc.d ssh defaults
 System startup links for /etc/init.d/ssh already exist.

I ran the same command for xinetd and nbclient with the same output. However, when I run it for apache I get:

root@willow:~# sudo update-rc.d apache-willow defaults
update-rc.d: warning: /etc/init.d/apache-willow missing LSB style header
 System startup links for /etc/init.d/apache-willow already exist.

Not sure where to go from here.

Thanks for your help guys.

Steve.

---

### Post by RealPSL on 2009-02-16
From what you are saying it seems as if all the services start up manually without problems but do not start automatically when the system boots. I think the obvious question at this point is whether the system attempt to run the scripts at all. One problem I have seen in the past is one startup script never returning control so the other scripts can run but I doubt this is your problem since you would not get a login prompt locally. This would show up as everything after a particular script not running at all.

To make sure that the system attempts to run these scripts put a line in one that simply does ```
logger -p local0.warning "This is a test"
```

That will put an entry in /var/log/messages. At least we will know if the script is being run or not.

---

