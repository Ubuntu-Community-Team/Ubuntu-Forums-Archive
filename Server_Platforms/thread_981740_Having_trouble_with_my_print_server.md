---
title: "Having trouble with my print server"
date: 2008-11-14
forum: Server Platforms
---

### Post by xyvian on 2008-11-14
So I recently reinstalled ubuntu 8.04 server after a failing hard drive. During the install process I checked on the "print server" option. After setting up Samba the way I needed it I started on to cups.

I configured my cupsd.conf file to how it was before (I had a backup of it) and then restarted my cups server only to have it spew out an error.

```
bwm@nas:~$ sudo /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd
cupsd: Child exited with status 1!

```

I thought it might be a misconfiguration of my config file so I started slimming it down, as I had some unnecessary stuff in it, but to no avail.

I don't remember what started my looking into it, but in my cupsd.conf it showed "Listen /var/run/cups/cups.sock" however, when I browsed to the cups directory it was empty.

Thinking this was strange I thought I would reinstall cupsys, hoping it would place the cups.sock as I blamed it on the missing file. After inputting the reinstall command I got as follows:

```
bwm@nas:~$ sudo apt-get --reinstall install cupsys
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 9 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up cupsys (1.3.7-1ubuntu3.1) ...
Reloading AppArmor profiles : done.
 * Starting Common Unix Printing System: cupsd
cupsd: Child exited with status 1!
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of cupsys-driver-gutenprint:
 cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5); however:
  Package cupsys is not configured yet.
  Package cups is not installed.
dpkg: error processing cupsys-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 cupsys-driver-gutenprint
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Not exactly sure what I did, but it sure seems like it's broken :lolflag:

I've uploaded my cupsd.conf file, so feel free to take a look at it. I look forward to any responses.

Oh and as a side note, I was on ubuntu 7.10 server before. Has the configuration file changed since then? It appears that I did not save a backup of the .conf file before pasting in my new one (I usually always remember to!).

Thanks,
Brian

---

### Post by xyvian on 2008-11-14
Any ideas at all? :confused:

---

### Post by Thirtysixway on 2008-11-14
try purging it with apt-get purge cupsys and reinstalling it.  This should clear out all of the configuration files for cups and start fresh.

---

### Post by xyvian on 2008-11-14
Aha! Purged it and reinstalled and it appears to work ok now! Thank you, Thirtysixway. Now to configure that stupid printer!

---

