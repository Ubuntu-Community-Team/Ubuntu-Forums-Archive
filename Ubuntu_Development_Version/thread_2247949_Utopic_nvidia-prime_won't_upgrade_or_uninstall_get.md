---
title: "Utopic nvidia-prime won't upgrade or uninstall gets an error"
date: 2014-10-11
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-10-11
Today I'm getting this error when updating the system and it will not go away.

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get upgrade
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  nvidia-prime
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/11.4 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 280128 files and directories currently installed.)
Preparing to unpack .../nvidia-prime_0.6.7_amd64.deb ...
Failed to issue method call: Unit nvidia-prime.service not loaded.
invoke-rc.d: initscript nvidia-prime, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 5
dpkg: trying script from the new package instead ...
Failed to issue method call: Unit nvidia-prime.service not loaded.
invoke-rc.d: initscript nvidia-prime, action "stop" failed.
dpkg: error processing archive /var/cache/apt/archives/nvidia-prime_0.6.7_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 5
Failed to issue method call: Unit nvidia-prime.service failed to load: No such file or directory.
invoke-rc.d: initscript nvidia-prime, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-prime_0.6.7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I can't uninstall it or upgrade it either one.

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get purge nvidia-prime
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-prime*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 104 kB disk space will be freed.
Do you want to continue? [Y/n] Y
dpkg: error processing package nvidia-prime (--purge):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 nvidia-prime
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It doesn't seem to prevent the system from booting up. I couldn't find the appropriate bug to report this against.

---

### Post by Cavsfan on 2014-10-11
I already tried all of these to no avail:
```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get check
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
```

---

### Post by Elfy on 2014-10-11
I did have an issue earlier in the cycle where nvidia* wouldn't upgrade properly when I'd booted with systemd - had to reboot without - then finish.

---

### Post by mc4man on 2014-10-11
Saw this when I had a 14.10 install last week (couldn't remove nvidia-prime
See 2 reports, probably the same issue (one is status 5, the other status 6, no matter really
[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1363871](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1363871)
[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1380053](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1380053)

---

### Post by zika on 2014-10-11
What```
sudo systemctl list-units --type=target --all
sudo systemctl list-units --type=service --all
```gives?
You could pipe those through```
grep nvidia
```just for being sure that You not show any private info. But whole list could be a bit more informative, still.
Justa a thought: Go to runlevel 1 and try to perform upgrade or (better) with```
init=/bin/bash
```in kernel boot line boot machine and try upgrade.
Disclaimer: No promises and no insurance from me... ;)

---

### Post by Cavsfan on 2014-10-11
Thanks for the helpful posts! But I was able to do like Elfy said and boot with Upstart instead of Systemd.
The update never even hiccuped  this time.

That's the first time I've used Upstart or even needed to in quite a while.

Thanks for the help! :)

---

### Post by zika on 2014-10-11
> **Cavsfan said:**
> Thanks for the helpful posts! But I was able to do like Elfy said and boot with Upstart instead of Systemd.
The update never even hiccuped  this time.
That's the first time I've used Upstart or even needed to in quite a while.
Thanks for the help! :)If I've had Nvidia and my machine at present state (without UPstart, since I've removed it and installed systemv-systemd) I would have to revert to a bigger hammer... ;)

---

### Post by Cavsfan on 2014-10-11
> **zika said:**
> If I've had Nvidia and my machine at present state (without UPstart, since I've removed it and installed systemv-systemd) I would have to revert to a bigger hammer... ;)

LoL :lol: indeed you would need a bigger hammer. I guess it's good you don't have Nvidia drivers then.

I booted in Utopic Mate with Upstart and the same updates went flawlessly this time.

I like Mate, it's like a step in the past - there is no option for Unity. Is any one else testing/trying it out?

---

### Post by SpUpUz on 2014-10-17
i have similar problem after upgrade how do i start without systemd??
look at the problems i have

```
spupuz@spupuz-EP35C-DS3R:/etc/systemd/system$ sudo aptitude -f install
The following partially installed packages will be configured:
  indicator-network ofono powerd qtdeclarative5-ubuntu-telephony0.1 telepathy-ofono telephony-service 
  ubuntu-system-settings unity8 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up ofono (1.12.bzr6880+14.10.20141010-0ubuntu1) ...
Failed to issue method call: Unit ofono.service failed to load: No such file or directory.
invoke-rc.d: initscript ofono, action "start" failed.
dpkg: error processing package ofono (--configure):
 subprocess installed post-installation script returned error exit status 6
dpkg: dependency problems prevent configuration of telepathy-ofono:
 telepathy-ofono depends on ofono; however:
  Package ofono is not configured yet.

dpkg: error processing package telepathy-ofono (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of telephony-service:
 telephony-service depends on telepathy-ofono; however:
  Package telepathy-ofono is not configured yet.

dpkg: error processing package telephony-service (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtdeclarative5-ubuntu-telephony0.1:i386:
 qtdeclarative5-ubuntu-telephony0.1:i386 depends on telepathy-ofono; however:
  Package telepathy-ofono is not configured yet.
 qtdeclarative5-ubuntu-telephony0.1:i386 depends on telephony-service (>= 0.1+14.10.20141007.1-0ubuntu1); however:
  No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                            No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                         No apport report written because MaxReports is reached already
                                                          No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         Package telephony-service is not configured yet.

dpkg: error processing package qtdeclarative5-ubuntu-telephony0.1:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity8:
 unity8 depends on qtdeclarative5-ubuntu-telephony0.1; however:
  Package qtdeclarative5-ubuntu-telephony0.1:i386 is not configured yet.

dpkg: error processing package unity8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-network:
 indicator-network depends on ofono; however:
  Package ofono is not configured yet.
 indicator-network depends on unity8 (>= 8.00+14.10.20140806); however:
  Package unity8 is not configured yet.

dpkg: error processing package indicator-network (--configure):
 dependency problems - leaving unconfigured
Setting up powerd (0.16+14.10.20141007-0ubuntu1) ...
Failed to issue method call: Unit powerd.service failed to load: No such file or directory.
invoke-rc.d: initscript powerd, action "start" failed.
dpkg: error processing package powerd (--configure):
 subprocess installed post-installation script returned error exit status 6
dpkg: dependency problems prevent configuration of ubuntu-system-settings:
 ubuntu-system-settings depends on indicator-network (>= 0.5.0+13.10.20130918); however:
  Package indicator-network is not configured yet.

dpkg: error processing package ubuntu-system-settings (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
               Errors were encountered while processing:
 ofono
 telepathy-ofono
 telephony-service
 qtdeclarative5-ubuntu-telephony0.1:i386
 unity8
 indicator-network
 powerd
 ubuntu-system-settings
E: Sub-process /usr/bin/dpkg returned an error code (1)
Failed to perform requested operation on package.  Trying to recover:
Setting up ofono (1.12.bzr6880+14.10.20141010-0ubuntu1) ...
Failed to issue method call: Unit ofono.service failed to load: No such file or directory.
invoke-rc.d: initscript ofono, action "start" failed.
dpkg: error processing package ofono (--configure):
 subprocess installed post-installation script returned error exit status 6
Setting up powerd (0.16+14.10.20141007-0ubuntu1) ...
Failed to issue method call: Unit powerd.service failed to load: No such file or directory.
invoke-rc.d: initscript powerd, action "start" failed.
dpkg: error processing package powerd (--configure):
 subprocess installed post-installation script returned error exit status 6
dpkg: dependency problems prevent configuration of telepathy-ofono:
 telepathy-ofono depends on ofono; however:
  Package ofono is not configured yet.

dpkg: error processing package telepathy-ofono (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-network:
 indicator-network depends on ofono; however:
  Package ofono is not configured yet.

dpkg: error processing package indicator-network (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-system-settings:
 ubuntu-system-settings depends on indicator-network (>= 0.5.0+13.10.20130918); however:
  Package indicator-network is not configured yet.

dpkg: error processing package ubuntu-system-settings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtdeclarative5-ubuntu-telephony0.1:i386:
 qtdeclarative5-ubuntu-telephony0.1:i386 depends on telepathy-ofono; however:
  Package telepathy-ofono is not configured yet.

dpkg: error processing package qtdeclarative5-ubuntu-telephony0.1:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of telephony-service:
 telephony-service depends on telepathy-ofono; however:
  Package telepathy-ofono is not configured yet.

dpkg: error processing package telephony-service (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity8:
 unity8 depends on qtdeclarative5-ubuntu-telephony0.1; however:
  Package qtdeclarative5-ubuntu-telephony0.1:i386 is not configured yet.

dpkg: error processing package unity8 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ofono
 powerd
 telepathy-ofono
 indicator-network
 ubuntu-system-settings
 qtdeclarative5-ubuntu-telephony0.1:i386
 telephony-service
 unity8

```

---

### Post by SpUpUz on 2014-10-17
> **Cavsfan said:**
> LoL :lol: indeed you would need a bigger hammer. I guess it's good you don't have Nvidia drivers then.

I booted in Utopic Mate with Upstart and the same updates went flawlessly this time.

I like Mate, it's like a step in the past - there is no option for Unity. Is any one else testing/trying it out?

how do i boot with upstart?

---

### Post by Elfy on 2014-10-18
If you've not _specifically_ edited grub (either at boot or by editing /etc/default/grub) then you will be booting with upstart. 

You can only boot with systemd by making changes.

---

### Post by ventrical on 2014-10-18
> **SpUpUz said:**
> how do i boot with upstart?

Read this first..

[http://askubuntu.com/questions/420917/how-can-i-replace-upstart-with-systemd](http://askubuntu.com/questions/420917/how-can-i-replace-upstart-with-systemd)

Regards..

---

### Post by ventrical on 2014-10-18
> **SpUpUz said:**
> how do i boot with upstart?

Could you please copy n' paste content of /etc/default/grub

Thanks.

---

### Post by Cavsfan on 2014-10-18
> **SpUpUz said:**
> how do i boot with upstart?

Do you have a default grub? It uses upstart as default. You have to edit the line or make a custom grub entry to use systemd in Utopic.

Edit: guess I was a little late.

---

### Post by Cavsfan on 2014-10-18
If you _do_ have a default grub menu and want to add the ability to boot with systemd check this out.
This would put the systemd boot line at the top and the normal Utopic boot line will use upstart which is and will always be default.

[http://ubuntuforums.org/showthread.php?t=2224798&page=6&p=13059146#post13059146](http://ubuntuforums.org/showthread.php?t=2224798&page=6&p=13059146#post13059146)

---

### Post by zika on 2014-10-18
> **Cavsfan said:**
> If you _do_ have a default grub menu and want to add the ability to boot with systemd check this out.
This would put the systemd boot line at the top and the normal Utopic boot line will use upstart which is and **will always be default**.
[http://ubuntuforums.org/showthread.php?t=2224798&page=6&p=13059146#post13059146](http://ubuntuforums.org/showthread.php?t=2224798&page=6&p=13059146#post13059146)I sincerely do hope that it won't be **always**... We are so close to 15.04 testing... ;)

---

### Post by Cavsfan on 2014-10-19
> **Cavsfan said:**
> If you _do_ have a default grub menu and want to add the ability to boot with systemd check this out.
This would put the systemd boot line at the top and the normal Utopic boot line will use upstart which is and will always be default.

[http://ubuntuforums.org/showthread.php?t=2224798&page=6&p=13059146#post13059146](http://ubuntuforums.org/showthread.php?t=2224798&page=6&p=13059146#post13059146)

> **zika said:**
> I sincerely do hope that it won't be **always**... We are so close to 15.04 testing... ;)

I really just meant it will be the default for 14.10.

---

### Post by teknotus on 2014-10-27
I mostly solved this by creating systemd configurations for the things that were broken. 

ofono.service config I got from a fedora 20 rpm

```
[Unit]
Description=Telephony service
After=syslog.target

[Service]
Type=dbus
BusName=org.ofono
ExecStart=/usr/sbin/ofonod -n
StandardError=null

[Install]
WantedBy=multi-user.target
```

I made my own urfkill.service based on the upstart config. It seems to work.

```
[Unit]
Description=killswitch manager
Requires=systemd-udevd.service
After=systemd-udevd.service

[Service]
Restart=always
ExecStart=/usr/lib/x86_64-linux-gnu/urfkill/urfkilld

```

I also made one for powerd.service, but powerd dumps core on startup when launched manually on my machine for unknown reasons so I commented out some things, and made it run /bin/true instead so that it passes tests of successfully running.

```
[Unit]
Description=Power daemon to monitor and control system power state

[Service]
Type=dbus
BusName=com.canonical.powerd
#Restart=always
Restart=no
Environment="ANDROID_ROOT=/system"
#ExecStart=/usr/bin/powerd
ExecStart=/bin/true

```

---

