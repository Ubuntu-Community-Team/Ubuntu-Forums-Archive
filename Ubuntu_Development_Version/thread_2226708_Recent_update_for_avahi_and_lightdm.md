---
title: "Recent update for avahi and lightdm"
date: 2014-05-28
forum: Ubuntu Development Version
---

### Post by Elfy on 2014-05-28
Amongst a bunch of updates I just got - avahi-utils/-daemon and lightdm were nestling furtively amongst them.

That went well ... 

Errors were encountered while processing:
 avahi-daemon
 [s]libnss-mdns:amd64[/s] you can forget that - unless you go wandering around in recovery mode without thinking :p
 lightdm
 avahi-utils

---

### Post by Cavsfan on 2014-05-28
My Utopic is broken too with today's updates.

Errors were encountered while processing
lightdm
avahi-daemon
avahi-utils
bluez
bluez-alsa:amd64
bluez-gstreamer
E: sub-process /usr/bin/dpkg returned an error code (1)

I tried everything and no bueno so far.

---

### Post by Rustan on 2014-05-28
I have the exact same problem

---

### Post by Cavsfan on 2014-05-28
I'm going to just give it some time and see what happens. It'll probably iron itself out; it usually does.

I made some notes. One important command to get the filesystem writeable is **sudo mount -n -o remount,rw /** after getting network enabled.

We shall see. ;)

---

### Post by mc4man on 2014-05-28
The issue seems to be with bluez & maybe  bluez-alsa - 
```
Setting up bluez (4.101-0ubuntu15) ...
insserv: Service dbus has to be enabled to start service bluetooth
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package bluez (--configure):
 subprocess installed post-installation script returned error exit status 1

```

Probably will be fixed shortly, resolved here by non standard method
(the dependency of unity-control-center on various indicators  was a bit of an over reaction to a somewhat obsure bug so previously had rebuilt u-c-c without those deps for trusty, just used those & then got rid of bluez & company

---

### Post by Sworddragon on 2014-05-28
I have just now made a dist-upgrade on my laptop and after booting it gets stuck at:

```
keys:
 * Stopping Mount filesystems on boot
```

Some lines before there is an error:

```
[   30.135306] Bluetooth: Can't get version to change to load ram patch err
[   30.153063] Bluetooth: Loading patch file failed
```

I'm able to switch between console 1 and console 7 but can't login at console 1. Also on my desktop system a todays dist-upgrade has caused the new package of sysv-rc to make some problems with insserv which hasn't appeared on my laptop. I have forced them in a hackish way to succeed but I think I will delay the boot now a little.

Has somebody else noticed any of these issues or get even stuck on booting too? As soon as I know what has caused the issue I will fix my laptop with Knoppix (and just in case I'm anyways making every day a half-automatic backup on my desktop system).

---

### Post by Rustan on 2014-05-28
same problem here
[http://ubuntuforums.org/showthread.php?t=2226708](http://ubuntuforums.org/showthread.php?t=2226708)

---

### Post by cariboo on 2014-05-28
Merged to similar threads.

---

### Post by Sworddragon on 2014-05-28
> **cariboo907 said:**
> Merged to similar threads.

Hm, yes, the insserv problem is the same. The question now is if it is related to the booting problem (as my laptop hasn't encountered the insserv problem).

---

### Post by sammiev on 2014-05-28
Took this update about 7 hrs ago... The fun begins! :)

---

### Post by oldos2er on 2014-05-28
> **Sworddragon said:**
> Has somebody else noticed any of these issues or get even stuck on booting too? 

I haven't noticed any issues, but I don't use lightdm (or any dm, for that matter), nor bluetooth.

---

### Post by Rustan on 2014-05-28
me for awhile helped add to the kernel command line:

init=/lib/systemd/systemd

system is loaded and working

---

### Post by installshield on 2014-05-29
> **Rustan said:**
> me for awhile helped add to the kernel command line:

init=/lib/systemd/systemd

system is loaded and working

Where do I put that in the grub commands?:guitar:

---

### Post by installshield on 2014-05-29
nevermind figured it out :D

---

### Post by Elfy on 2014-05-29
Was nothing to do with bluez here.

This morning's updates fixed it though.

---

### Post by ventrical on 2014-05-29
After  a large update /and reboot/ Ubuntu Plymouth start screen will just roll, roll. Can't use ctrl+alt+F1. Recovery from GRuB menu gives limited options.  It will boot from recovery to safe graphics mode but then you can't shut down unless hard shutdown. This will happen on 3.13.x-x and 3.15.x-x kernels respectively so not a kernel issue.

 In recovery mode it will usually lock up with :

Starting AppArmour:

and other errors.

Anyone else?

---

### Post by mdurham on 2014-05-29
Anyone else?
Yep, me too

---

### Post by plucky on 2014-05-29
Xubuntu 14.10 same problem.
Ctrl+Sysrq+REISUB will reboot.

---

### Post by cariboo on 2014-05-29
Merged some more similar threads.

---

### Post by slickymaster on 2014-05-29
> **ventrical said:**
> After  a large update /and reboot/ Ubuntu Plymouth start screen will just roll, roll. Can't use ctrl+alt+F1. Recovery from GRuB menu gives limited options.  It will boot from recovery to safe graphics mode but then you can't shut down unless hard shutdown. This will happen on 3.13.x-x and 3.15.x-x kernels respectively so not a kernel issue.

 In recovery mode it will usually lock up with :

Starting AppArmour:

and other errors.

Anyone else?

lol

That's almost what I'm facing. The difference being that my box was able to start AppArmour but it stopped 4 services after it and freeze at ```
Starting cups-browsed - Bonjour remote printer browsing deamon
```.

---

### Post by kansasnoob on 2014-05-29
> **mdurham said:**
> Anyone else?
Yep, me too

Me three .............. errm 4, errm 5 ......................

Yep she's borked :lolflag:

---

### Post by slickymaster on 2014-05-29
Replacing upstart with systemd is a viable workaround.

When booting using grub just edit the line **GRUB_CMDLINE_LINUX_DEFAULT** and append _init=/lib/systemd/systemd_ so it will read like this:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet init=/lib/systemd/systemd"
```Reload grub```
update-grub
```and reboot.

Note that we're not removing upstart. We're still keeping upstart around but making permanent booting with systemd.

---

### Post by slickymaster on 2014-05-29
Please disregard my last post. Even though I was able to boot and load the system it resulted in a kernel panic situation. ](*,)

---

### Post by zika on 2014-05-29
I do not have UU at hand at this moment.
This sounds much like (avahi) that initramfs did not work (or that some of You are trying to use kernels that did not get initramfs updated (default is that it is updated only for the newest kernel (that can be changed in /etc/initramfs-tools/update-initramfs.conf)))...
Beware: If I'm not right (not rare occasion) You should not contaminate working kernels by updating initramfs... ;)

---

### Post by bapoumba on 2014-05-29
Got that 2 hour ago on the ubuntu-devel list from Martin Pitt:
> Hello all,

this morning we found that current utopic du jour would hang at boot.
The cause has been identified, and we found a relatively simple
solution which restores booting, which is in sysv-rc 2.88dsf-41ubuntu15.

If you are in a situation where your machine does not boot any more,
the least intrusive workaround ironically is to boot with systemd:
Press "shift" during boot to get to the grub menu, press "e" on the
Ubuntu line, and append this to the "linux" line":

  init=/lib/systemd/systemd

Then press Ctrl-X to boot.

Should that fail for any reason, the alternative workaround is to boot
into rescue mode, mount the root partition R/W, get a shell, and run

  touch /etc/init.d/.legacy-bootordering

then reboot. After getting the fixed sysv-rc, you should remove that
file again.

For those who are interested in the details: We recently switched
Ubuntu's "old" upstart/sysvinit policy to what Debian currently uses.
Debian dropped support for the old statically numbered init.d script
links in /etc/rc*.d/ and moved to insserv and startpar long ago. We
finally did that transition as well to avoid an ever-growing delta in
Ubuntu and packages slowly becoming incompatible with the old way.

But it happens that some of our upstart jobs are "tasks" which appear
as "stopped" after they did their thing. init.d scripts which depend
on these will never start as startpar assumes that the depending
upstart job is "running". So we need to find out how to keep upstart's
"task" job semantics and make that work with startpar, but this isn't
something which we want to or can do "under the gun". Hence the above
sysv-rc upload disables startpar again for now.

Sorry for that blunder and for the inconvenience!

Martin

---

### Post by zika on 2014-05-29
I hope You will not deem inappropriate if I say that this situation led me to faster boot: [http://ubuntuforums.org/showthread.php?t=2224798&p=13036197#post13036197](http://ubuntuforums.org/showthread.php?t=2224798&p=13036197#post13036197) ... ;)

---

### Post by eusonlito on 2014-05-29
> **slickymaster said:**
> Replacing upstart with systemd is a viable workaround.

When booting using grub just edit the line **GRUB_CMDLINE_LINUX_DEFAULT** and append _init=/lib/systemd/systemd_ so it will read like this:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet init=/lib/systemd/systemd"
```Reload grub```
update-grub
```and reboot.

Note that we're not removing upstart. We're still keeping upstart around but making permanent booting with systemd.

I have solved my boot problem with this fix. Related: [http://ubuntuforums.org/showthread.php?t=2226828&p=13036241](http://ubuntuforums.org/showthread.php?t=2226828&p=13036241)

---

### Post by slickymaster on 2014-05-29
> **slickymaster said:**
> Please disregard my last post. Even though I was able to boot and load the system it resulted in a kernel panic situation. ](*,)

As it turned out the kernel panic wasn't at all related to the replacing upstart with systemd.

---

### Post by philinux on 2014-05-29
Me used chroot to update system from 14.04 install on disk 1.

---

### Post by Vanishing on 2014-05-29
I'm getting this for this morning's update:
> root@ubuntu:/var/cache/apt/archives# sudo apt-get -f install
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 112 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Can not write log (Is /dev/pts mounted?) - openpty (2: No such file or directory)
Setting up procps (1:3.3.9-1ubuntu4) ...
invoke-rc.d: -----------------------------------------------------
invoke-rc.d: WARNING: 'invoke-rc.d procps start' called
invoke-rc.d: during shutdown sequence.
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: -----------------------------------------------------
update-rc.d: error: unable to read /etc/init.d/procps-instance
dpkg: error processing package procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package udev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg: dependency problems prevent configuration of systemd:
 systemd depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package systemd (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg: dependency problems prevent configuration of libpam-systemd:amd64:
 libpam-systemd:amd64 depends on systemd (= 204-10ubuntu8); however:
  Package systemd is not configured yet.

dpkg: error processing package libpam-systemd:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of ppp:
 ppp depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package ppp (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 procps
 udev
 systemd
 libpam-systemd:amd64
 ppp
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Cavsfan on 2014-05-29
> **Elfy said:**
> Was nothing to do with bluez here.

This morning's updates fixed it though.

I'm good to go too with today's updates. I did go through recovery mode, enabled network before dropping to root shell and mounted the file system as rw. 
Then **sudo apt-get update && sudo apt-get upgrade** and all looked normal and went well.
I then booted normally and got the new kernel.

```
cavsfan@cavsfan-MS-7529:~$ uname -a
Linux cavsfan-MS-7529 3.15.0-4-generic #8-Ubuntu SMP Wed May 28 14:33:19 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

That was fun! :lolflag:

---

### Post by Vanishing on 2014-05-29
I think I see somewhere /etc/init.d/procps is being changed to /etc/init.d/procps-instance, but I can't find procps-instance in the deb file..

---

### Post by Sworddragon on 2014-05-29
Sadly my internet went down over night otherwise I would have telled you that deleting /etc/init.d/.depend.* solves the issue too as a workaround (but now you have already another workaround).

---

### Post by ventrical on 2014-05-29
> **bapoumba said:**
> Got that 2 hour ago on the ubuntu-devel list from Martin Pitt:


This:

> 

init=/lib/systemd/systemd

Then press Ctrl-X to boot.



did not work but, I was able to boot into the 3.13.x-x kernel on the GRuB menu in recovery ansd was able to udpate with the fix. All appears to be working now.

---

### Post by DogMatix on 2014-05-29
Yesterdays update screwed my Lubuntu UU too. I was already using 'init=/lib/systemd/systemd' though!
Upgrade problems seemed to be bluez and lightdm. '2 not fully installed packages' Wouldn't boot to lightdm. 
I got to a command line, but I had lost wireless.

Reinstalled, fresh today from daily and all is good now.

---

### Post by sammiev on 2014-05-29
When I heard an update was out I just used the info from post 4 by Cavsfan and took the update. All is good now.

---

### Post by Cavsfan on 2014-05-31
> **sammiev said:**
> When I heard an update was out I just used the info from post 4 by Cavsfan and took the update. All is good now.

I actually helped someone? Ermahgerd! Glad to be of help and glad you got your system back like I did. :)

---

