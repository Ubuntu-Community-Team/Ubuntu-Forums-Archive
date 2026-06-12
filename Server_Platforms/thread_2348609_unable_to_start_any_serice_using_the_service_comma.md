---
title: "unable to start any serice using the service command or /etc/init.d/"
date: 2017-01-05
forum: Server Platforms
---

### Post by kailashms on 2017-01-05
Hi All,

I need your assistance in finding a solution.

I have Ubuntu 16.04 VM and I have update it recently.
After the update, I am not able to restart the service manually

[EMAIL="root@kailash"]root@kailash[/EMAIL] :~# /etc/init.d/ssh restart
ssh stop/waiting
start: Job failed to start

I even tried to restart using the /etc/init.d/ssh restart.
But was not able to do so.

I need to reboot the vm if any of the service is stopped as I cannot start it manually.


[   12.841683] init: Error while reading from descriptor: Broken pipe
/bin/sh: 0: Can't open /proc/self/fd/9
[   12.852104] init: Error while reading from descriptor: Broken pipe
[   12.883521] init: Error while reading from descriptor: Broken pipe

Cloud-init v. 0.7.8 running 'modules:final' at Tue, 03 Jan 2017 11:02:09 +0000. Up 13.17 seconds.
Cloud-init v. 0.7.8 finished at Tue, 03 Jan 2017 11:02:09 +0000. Datasource DataSourceAzureNet [seed=/dev/sr0].  Up 13.26 seconds

[11703.442915] systemd-logind[2088]: Failed to start user service, ignoring: Unknown unit: [EMAIL="user@999.service"]user@999.service[/EMAIL]
       


Please go through them and let me know if you can provide any assistance on it.

---

### Post by SeijiSensei on 2017-01-05
16.04 and later use systemd. To start a service use
```
sudo systemctl start servicename
```
Read the man page for systemctl for details.

---

### Post by tzachie on 2017-01-09
@[**[COLOR=#000000]kailashms[/COLOR]**]("https://ubuntuforums.org/member.php?u=2055025") Command is fine also

tzachie@Ubuntu1604:~$ uname -a
Linux Ubuntu1604 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
tzachie@Ubuntu1604:~$ sudo /etc/init.d/ssh restart
[ ok ] Restarting ssh (via systemctl): ssh.service.
tzachie@Ubuntu1604:~$

---

### Post by kailashms on 2017-01-11
Hi All,
It is not related to a single service, I am facing issues with other services to like nfs etc.
I need to restart the vm in order to get the service back up.
let me know if there is any other way to resolve this

---

### Post by darkod on 2017-01-11
Was this an upgrade from previous version or clean install of 16.04? You said you did an update but by update I consider just updating the packages, not upgrading the OS version. So, which one is it?

If it was upgrade of the OS version it might not have completed correctly, so starting/stopping services manually might be affected... Anything in the logs? Have you checked?

---

### Post by geeksmith on 2017-01-11
The command 'sudo journalctl -xe' may give you some hints about why the services can't be controlled.

Also try 'sudo apt-get dist-upgrade' and 'sudo apt-get -f install' -- they may reveal a problem with missing dependencies or packages not properly installed.

---

