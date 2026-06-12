---
title: "apt-get install loop issue"
date: 2015-05-05
forum: Server Platforms
---

### Post by Wayne_Sitton on 2015-05-05
I'm trying to upgrade my server for patches and stuff, but it's in some kind of a dependency loop.  The system is trying to configure a previous linux-server image, but breaks because a newer kernel is installed and running.

I have Ubuntu Server 12.04.5

root@xxxx:~# uname -a
Linux 3.2.0-83-generic #120-Ubuntu SMP Wed Apr 29 15:37:05 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

When I try to upgrade I get

root@xxxx:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-server : Depends: linux-image-server (= 3.2.0.82.96) but 3.2.0.83.97 is installed
                Depends: linux-headers-server (= 3.2.0.82.96) but 3.2.0.83.97 is installed
E: Unmet dependencies. Try using -f.
You have new mail in /var/mail/root
root@xxxx:~# 
root@xxxx:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.2.0-76-generic linux-headers-3.2.0-72 linux-headers-3.2.0-74 linux-headers-3.2.0-80 linux-headers-3.2.0-75 linux-headers-3.2.0-76 linux-headers-3.2.0-77 linux-headers-3.2.0-79 linux-image-3.2.0-79-generic linux-headers-3.2.0-76-generic linux-image-3.2.0-74-generic linux-headers-3.2.0-79-generic linux-image-3.2.0-77-generic linux-headers-3.2.0-74-generic linux-image-3.2.0-72-generic
  linux-headers-3.2.0-77-generic linux-image-3.2.0-80-generic linux-image-3.2.0-75-generic linux-headers-3.2.0-72-generic linux-headers-3.2.0-80-generic linux-headers-3.2.0-75-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-server
The following packages will be upgraded:
  linux-server
1 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,734 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 237, in <module>
    main()
  File "/usr/bin/apt-listchanges", line 48, in main
    debs = apt_listchanges.read_apt_pipeline(config)
  File "/usr/share/apt-listchanges/apt_listchanges.py", line 83, in read_apt_pipeline
    return map(lambda pkg: filenames[pkg], order)
  File "/usr/share/apt-listchanges/apt_listchanges.py", line 83, in <lambda>
    return map(lambda pkg: filenames[pkg], order)
KeyError: 'linux-server'
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.82.96); however:
  Version of linux-image-server on system is 3.2.0.83.97.
 linux-server depends on linux-headers-server (= 3.2.0.82.96); however:
  Version of linux-headers-server on system is 3.2.0.83.97.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@xxxx:~#

---

### Post by TheFu on 2015-05-05
aptitude is smarter about dependences. Try that as a first step. 

Would also be good if you removed all older kernels, including the one that didn't get fully installed and is causing the root issue. I keep 2-3 kernels, no more. There are many reasons for this - mainly to avoid having /boot get full which can lead to nasty issues.

---

### Post by Wayne_Sitton on 2015-05-06
Aptitude resulted in the same issue and error.  I had tried to do an apt-get autoremove to get rid of the old kernels, but the current error prevents me from doing even that.

---

### Post by TheFu on 2015-05-06
Ok - dependency issues like this require dropping to **dpkg**.

**dpkg --list | grep linux-image**

**sudo dpkg --purge --force-all  {list of all kernel packages you need to purge}** - the bad/old/broken ones and any extras while you are at it. Keep 2 known-working kernels.

Then do a **sudo aptitude install -f** - hopefully that will install any kernel you need and complete successfully.  Watch the output - if it doesn't do grub "things", you'll need to manually do that - **sudo update-grub**

Any errors?

Assuming all is well now, go back to the weekly **sudo aptitude update && sudo aptitude dist-upgrade** stuff well all do [weekly as part of system maintenance.]("http://blog.jdpfu.com/linsysmaint")

---

