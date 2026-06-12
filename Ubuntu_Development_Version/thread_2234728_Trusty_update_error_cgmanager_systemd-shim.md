---
title: "Trusty update error cgmanager systemd-shim"
date: 2014-07-16
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-07-16
I got in an unresolvable situation with today's updates involving cgmanager and systemd-shim.

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get install -f
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up cgmanager (0.26-0ubuntu5) ...
Failed to issue method call: Unit cgmanager.service failed to load: No such file or directory. See system logs and 'systemctl status cgmanager.service' for details.
invoke-rc.d: initscript cgmanager, action "start" failed.
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: error processing package cgmanager (--configure):
 subprocess installed post-installation script returned error exit status 6
dpkg: dependency problems prevent configuration of systemd-shim:
 systemd-shim depends on cgmanager; however:
  Package cgmanager is not configured yet.

dpkg: error processing package systemd-shim (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cgmanager
 systemd-shim
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Wondering if I should just wait it out or is there a way to correct this? They seem to conflict with each other.
I tried removing them one at a time and it wanted to take whole system with it, so I gave it the big  "NO".

---

### Post by Cavsfan on 2014-07-16
```
cavsfan@cavsfan-MS-7529:~$ systemctl status cgmanager.service
cgmanager.service
   Loaded: [COLOR=#ff0000]error[/COLOR] (Reason: No such file or directory)
   Active: inactive (dead)
```

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy cgmanager
cgmanager:
  Installed: 0.26-0ubuntu5
  Candidate: 0.26-0ubuntu5
  Version table:
 *** 0.26-0ubuntu5 [COLOR=#ff0000]0[/COLOR]
        500 http://us.archive.ubuntu.com/ubuntu/ utopic/main amd64 Packages
        100 /var/lib/dpkg/status

```

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy systemd-shim
systemd-shim:
  Installed: 6-3ubuntu1
  Candidate: 6-3ubuntu1
  Version table:
 *** 6-3ubuntu1 [COLOR=#ff0000]0[/COLOR]
        500 http://us.archive.ubuntu.com/ubuntu/ utopic/main amd64 Packages
        100 /var/lib/dpkg/status

```

I guess they are installed but not configured.

---

### Post by Cavsfan on 2014-07-16
Well, that was simple. I just booted up with upstart (normal) and not systemd and both files fixed themselves.

---

### Post by Elfy on 2014-07-16
/me hasn't got that far yet - but I've had similar issues each time nvidia-prime updates

---

### Post by P-I H on 2014-07-16
I got the same problem. I will not change to upstart yet. I will wait and see.

---

### Post by Cavsfan on 2014-07-16
> **Elfy said:**
> /me hasn't got that far yet - but I've had similar issues each time nvidia-prime updates

Do you mean you haven't gotten those 2 files in updates?

> **P-I H said:**
> I got the same problem. I will not change to upstart yet. I will wait and see.

Aw c'mon all it took was a reboot into upstart, get the updates, reboot back into systemd.
Although I did go to all the trouble of installing my grub on Utopic and making /etc/grub.d/10_linux executable so I could get to linux-headers-3.15.0-6-generic if need be.

But I didn't have to boot in to the older kernel just normal with upstart. Then I reinstalled my grub on Mint 17 because I like the ability to use multiple colors.

[[IMG]http://www.zimagez.com/miniature/20140629115939.jpg[/IMG]]("http://www.zimagez.com/zimage/20140629115939.php")

---

### Post by Cavsfan on 2014-07-16
But I'm back in Utopic with systemd after getting that error fixed. ;)

---

### Post by Elfy on 2014-07-16
> Do you mean you haven't gotten those 2 files in updates?No. I mean I'm in a half-installed/configured state as well and that I also get the same thing each time there is an nvidia-prime update :)

---

### Post by zika on 2014-07-16
From my experience with SystemD error like```
invoke-rc.d: initscript cgmanager, action "start" failed.
```is always reason to go to clean upstart boot and let application that is not completely upgraded to SystemD behavior present itself to system properly... There is a whole bunch of very important applications/services that are still not ready for SystemD in very important part and that is upgrading properly their files and configurations. But, once one get grasp of these glitches everything is cool. It seems that this upgrade caught me while on the job and while home-machine was in upstart so I've missed adrenaline rush...;) Event trysty Trusty can provide some of it, nice.

---

### Post by sammiev on 2014-07-16
Took the update about 10 hours a go and had no issues on reboot.
All Intel here.

---

### Post by Cavsfan on 2014-07-16
> **Elfy said:**
> No. I mean I'm in a half-installed/configured state as well and that I also get the same thing each time there is an nvidia-prime update :)

That's what I thought just not sure.

> **zika said:**
> From my experience with SystemD error like```
invoke-rc.d: initscript cgmanager, action "start" failed.
```is always reason to go to clean upstart boot and let application that is not completely upgraded to SystemD behaviour present itself to system properly... There is a whole bunch of very important applications7services that are still not ready for SystemD in very important part and that is upgrading properly their files and configurations. But, once one get grasp of these glitches everything is cool.

+1 I don't have a problem using upstart getting updates and then going back to systemd. I am just glad I can choose from the menu and don't have to edit the line at boot time.

---

### Post by Cavsfan on 2014-07-16
> **sammiev said:**
> Took the update about 10 hours a go and had no issues on reboot.
All Intel here.

With upstart or systemd?

---

### Post by sammiev on 2014-07-16
sam@sam-L650:~$ systemctl status cgmanager.service
Failed to get D-Bus connection: No connection to service manager.
sam@sam-L650:~$ apt-cache policy cgmanager
cgmanager:
  Installed: 0.26-0ubuntu5
  Candidate: 0.26-0ubuntu5
  Version table:
 *** 0.26-0ubuntu5 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages
        100 /var/lib/dpkg/status
sam@sam-L650:~$ apt-cache policy systemd-shim
systemd-shim:
  Installed: 6-3ubuntu1
  Candidate: 6-3ubuntu1
  Version table:
 *** 6-3ubuntu1 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages
        100 /var/lib/dpkg/status
sam@sam-L650:~$

---

### Post by zika on 2014-07-16
> **Cavsfan said:**
> I am just glad I can choose from the menu and don't have to edit the line at boot time.To each his own.

---

### Post by Cavsfan on 2014-07-17
> **sammiev said:**
> sam@sam-L650:~$ systemctl status cgmanager.service
Failed to get D-Bus connection: No connection to service manager.
sam@sam-L650:~$ apt-cache policy cgmanager
cgmanager:
  Installed: 0.26-0ubuntu5
  Candidate: 0.26-0ubuntu5
  Version table:
 *** 0.26-0ubuntu5 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages
        100 /var/lib/dpkg/status
sam@sam-L650:~$ apt-cache policy systemd-shim
systemd-shim:
  Installed: 6-3ubuntu1
  Candidate: 6-3ubuntu1
  Version table:
 *** 6-3ubuntu1 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages
        100 /var/lib/dpkg/status
sam@sam-L650:~$

That is exactly if not close to what I had. Did you try getting the update through upstart. Worked for me.

---

### Post by sammiev on 2014-07-17
> **Cavsfan said:**
> That is exactly if not close to what I had. Did you try getting the update through upstart. Worked for me.

upstart

---

### Post by Cavsfan on 2014-07-18
I got another big problem when cgmanager needed updating a while ago. It's wouldn't update using systemd so I booted with upstart and the update finished smoothly but when I rebooted it would not boot into either systemd or upstart. I had to boot into kernel 3.16.0-3-generic and that's where I am.
This is the bug if anyone else has this same issue [https://bugs.launchpad.net/ubuntu/+source/cgmanager/+bug/1344196](https://bugs.launchpad.net/ubuntu/+source/cgmanager/+bug/1344196)

---

### Post by Elfy on 2014-07-18
pitti did request that bugs with systemd be tagged systemd-boot I've tagged this one

as far as the recent cgmanager update goes - worked fine here

---

### Post by Cavsfan on 2014-07-18
> **Elfy said:**
> pitti did request that bugs with systemd be tagged systemd-boot I've tagged this one

as far as the recent cgmanager update goes - worked fine here

I noticed you updated it - thanks! I'll keep that in mind. I just updated it too with this: I am able to boot with the latest kernel using upstart but it fails to boot with systemd.

So I guess for the time being I'll use upstart.

---

### Post by sammiev on 2014-07-18
todays update worked good here - using upstart

---

### Post by Cavsfan on 2014-07-18
> **sammiev said:**
> todays update worked good here - using upstart

You probably don't want to use systemd for a while. It's broken here. If it is on your system as well add yourself to that bug a few posts back.

---

### Post by Cavsfan on 2014-07-24
The bug I reported is duplicate of this bug: [https://bugs.launchpad.net/ubuntu/+source/cgmanager/+bug/1343802](https://bugs.launchpad.net/ubuntu/+source/cgmanager/+bug/1343802)
Apparently someone else got to it before me that day.

It says that systemd 208 fixes the problem.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy systemd
systemd:
  Installed: 204-14ubuntu2
  Candidate: 204-14ubuntu2

```

I enabled Pre-Release updates utopic-proposed and with SPM got the updates for just these packages and then disabled Pre-Release updates:

```
libpam-systemd (version 204-14ubuntu2) will be upgraded to version 208-6ubuntu2
libsystemd-daemon0 (version 204-14ubuntu2) will be upgraded to version 208-6ubuntu2
libsystemd-journal0 (version 204-14ubuntu2) will be upgraded to version 208-6ubuntu2
libsystemd-login0 (version 204-14ubuntu2) will be upgraded to version 208-6ubuntu2
systemd (version 204-14ubuntu2) will be upgraded to version 208-6ubuntu2

```

I'll reboot and see if systemd is working again.

---

### Post by Cavsfan on 2014-07-24
That fixed systemd for me. I rebooted and everything looks good. It was a little slow coming up but I expect that was just an initial response.

---

