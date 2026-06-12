---
title: "Holding back certain packages from automatically updating"
date: 2005-05-02
forum: Repositories &amp; Backports
---

### Post by superhac007 on 2005-05-02
Does anyone know how to hold back packages from being upgraded when issusing the apt-get upgrade.

I would like to issue that simple command instead of manually looking at what packages are going to be updated and then manualling installing them.  

What I am tring to prevent is my wine packages from being updated.  I am using an older version that seems to be more stable then the latest.

Thanks!

---

### Post by Juergen on 2005-05-02
You might want to read this:
[http://www.ubuntulinux.org/wiki/PinningHowto](http://www.ubuntulinux.org/wiki/PinningHowto)

It's easier with Synaptic. 
Just mark the package, open the package-menu and choose 'lock version'

---

### Post by mendicant on 2005-05-02
% sudo aptitude hold <package-name>

or, in the aptitude curses interface, use the '=' key.

You should probably use aptitude in preference to apt-get:
[http://lists.debian.org/debian-user/2004/04/msg11344.html](http://lists.debian.org/debian-user/2004/04/msg11344.html)

---

### Post by superhac007 on 2005-05-02
Okay I tried the the /etc/apt/preferences and kept getting the following error:

E: Invalid record in the preferences file, no Package header

here was my /etc/apt/preferences file:

Package: wine
Pin: version 0.0.20041201-1

Package: libwine
Pin: version 0.0.20041201-1

I was able to lock the packages in Synaptic.  But I would prefer to lock the file from apt.

I also messed around with aptitude.  Got that working with the hold parameter.  I also read the link provided for aptitude.  Sounds like a good program.

When I tried to do a dist-upgrade with aptitude it came back with the following:

--------------------------------------------
The following NEW packages will be automatically installed:
  linux-image-2.6.10-5-386 linux-restricted-modules-2.6.10-5-386
The following packages have been kept back:
  libwine libxvidcore4 wine
The following NEW packages will be installed:
  linux-386 linux-image-2.6.10-5-386 linux-image-386
  linux-restricted-modules-2.6.10-5-386 linux-restricted-modules-386
  portmap
0 packages upgraded, 6 newly installed, 0 to remove and 3 not upgraded.
--------------------------------------------------------------------------

I am running a 686 kernel.  apt-get does not show these packages with the dist-upgrade parameter.  Why is there a difference with aptitude?

Thanks for all your help!

---

### Post by mendicant on 2005-05-02
I suspect you may have some old dependency on some -386 package somewhere.  Can you try:

% aptitude -s --show-deps dist-upgrade

That should show you why things are being automatically installed.  It won't tell you about linux-386 and all the stuff under 'NEW packages will be installed'.  To discover why those might be installed, try (under bash):

% aptitude search ~Dlinux.*386 | sort | uniq

which searches for things which depend on those packages.  In my stock sources.list, this only non kernel one is sl-modem-daemon and linux-headers-386.  Perhaps you have others?
If any non-kernel thing has an 'i' at the front (instead of a 'p'), that is what is causing those things to be installed.

portmap has a longer list, and you can do the same thing.

---

### Post by superhac007 on 2005-05-02
[QUOTE=mendicant]I suspect you may have some old dependency on some -386 package somewhere.  Can you try:

% aptitude -s --show-deps dist-upgrade

That should show you why things are being automatically installed.  It won't tell you about linux-386 and all the stuff under 'NEW packages will be installed'.  To discover why those might be installed, try (under bash):

% aptitude search ~Dlinux.*386 | sort | uniq

which searches for things which depend on those packages.  In my stock sources.list, this only non kernel one is sl-modem-daemon and linux-headers-386.  Perhaps you have others?
If any non-kernel thing has an 'i' at the front (instead of a 'p'), that is what is causing those things to be installed.

portmap has a longer list, and you can do the same thing.[/QUOTE]

Heres what I got with aptitude -s --show-deps dist-upgrade:
----------------------------------------------------
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
The following NEW packages will be automatically installed:

  linux-image-2.6.10-5-386 (D: linux-image-386, D: linux-restricted-modules-2.6.10-5-386)
  linux-restricted-modules-2.6.10-5-386 (D: linux-restricted-modules-386)
The following packages have been kept back:
  libwine libxvidcore4 wine
The following NEW packages will be installed:
  linux-386 linux-image-2.6.10-5-386 linux-image-386
  linux-restricted-modules-2.6.10-5-386 linux-restricted-modules-386
  portmap
0 packages upgraded, 6 newly installed, 0 to remove and 3 not upgraded.
Need to get 20.5MB of archives. After unpacking 59.6MB will be used.
-------------------------------------------------------------------------------

Then I did the aptitude search ~Dlinux.*386 | sort | uniq and got:
-------------------------------------------------------------------------------
p   linux-headers-386               - Linux kernel headers on 386
p   sl-modem-daemon                 - SmartLink software modem daemon
pi  linux-386                       - Complete Linux kernel on 386.
pi  linux-image-386                 - Linux kernel image on 386.
pi  linux-restricted-modules-2.6.10 - Non-free Linux 2.6.10 modules on 386
pi  linux-restricted-modules-386    - Restricted Linux modules on 386.
-----------------------------------------------------------------------------------------

From what I can tell I don't have any references to the 386 kernel image only 686.  Thanks again.

---

### Post by mendicant on 2005-05-02
Yeah, doesn't seem like there's anything.  Does apt-get dist-upgrade still say nothing needs to be upgraded?  You can always try doing:

% aptitude purge "linux.*386"
% # check that they are not marked for installation:
% aptitude search "~Dlinux.*386"
% aptitude dist-upgrade

---

### Post by superhac007 on 2005-05-03
[QUOTE=mendicant]Yeah, doesn't seem like there's anything.  Does apt-get dist-upgrade still say nothing needs to be upgraded?  You can always try doing:

% aptitude purge "linux.*386"
% # check that they are not marked for installation:
% aptitude search "~Dlinux.*386"
% aptitude dist-upgrade[/QUOTE]

Same thing. I did the purge and I still got the 386 kernel modules are going to be installed.

-------------------------------------------------------------------------------------------------------
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
The following NEW packages will be automatically installed:
  linux-image-2.6.10-5-386 linux-restricted-modules-2.6.10-5-386
The following packages have been kept back:
  libwine libxvidcore4 wine
The following NEW packages will be installed:
  linux-386 linux-image-2.6.10-5-386 linux-image-386
  linux-restricted-modules-2.6.10-5-386 linux-restricted-modules-386
  portmap
-------------------------------------------------------------------------------------------------------

Heres apt-get dist-upgrade:
-------------------------------------------------------------------------------------------------------
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  libxvidcore4
The following packages will be upgraded:
  libwine wine
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 12.8MB of archives.
--------------------------------------------------------------------------------------------------------


Does aptitude use the same package database as synaptic and apt?  Both of those don't show those kernel packages are going to be installed while issuing a dist-upgrade.  I also know for a fact that I removed all reference to anything kernel i386 when I changed to the i686.  

What do the "p" & "i" mean in the output from aptitude when looking for dependencies?

Thanks again for your continued help!

---

### Post by mendicant on 2005-05-03
They all should use the same package database--they're all just frontends for dpkg, essentially (via libapt-pkg-libc6.3-5).  The p and i stuff means purge and install.  'pi' means it is currently purged, and marked for installation.  A single 'p' means it is purged (not installed) and a single 'i' means it is currently installed.

After you did the purge, did you see 'pi', or just 'p'?  All the linux.*386 should have just a lone 'p'.  This is pretty puzzling.  Perhaps the portmap package that it is also trying to install indicates something.  Can you try:

% aptitude search ~Dportmap

Also, what's the output of:

% aptitude -s install heartbeat ## the -s means simulate, so nothing gets installed--I just chose heartbeat because you probably don't have it

In particular, does it try to install the linux.*386 packages?

FYI, I just tried this on my machine:

```

% aptitude purge "linux.*386"
% aptitude search "linux.*386"
p   linux-386                       - Complete Linux kernel on 386.
p   linux-headers-2.6.10-5-386      - Linux kernel headers 2.6.10 on 386
p   linux-headers-2.6.11-1-386      - Linux kernel headers 2.6.11 on 386
p   linux-headers-386               - Linux kernel headers on 386
p   linux-image-2.6.10-5-386        - Linux kernel image for version 2.6.10 on
p   linux-image-2.6.11-1-386        - Linux kernel image for version 2.6.11 on
p   linux-image-386                 - Linux kernel image on 386.
p   linux-restricted-modules-2.6.10 - Non-free Linux 2.6.10 modules on 386
p   linux-restricted-modules-386    - Restricted Linux modules on 386.

```
% aptitude -s dist-upgrade

and it shows nothing to be upgraded, which is exactly what apt-get shows.  One last thing to try would be to accept what it is trying to do, then call aptitude purge:

% aptitude dist-upgrade
## ...  install away
% aptitude -s purge "linux.*386" portmap ## this should reveal what is causing the problem, because it will want to remove whatever is causing the problem.
% # on the other hand, if it works:
% aptitude purge "linux.*386" portmap
% aptitude dist-upgrade ## to see if it still tries to do it

I'm not sure what else to say here, though.  You've definitely come across something puzzling.

---

### Post by superhac007 on 2005-05-03
Okay heres my output from "aptitude -s install heartbeat":
```

Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
The following NEW packages will be automatically installed:
  libnet1 libpils0 libsnmp-base libsnmp5 libstonith0
The following packages have been kept back:
  libwine libxvidcore4 wine
The following NEW packages will be installed:
  heartbeat libnet1 libpils0 libsnmp-base libsnmp5 libstonith0
0 packages upgraded, 6 newly installed, 0 to remove and 3 not upgraded.
Need to get 3191kB of archives. After unpacking 7258kB will be used.

```

As you can see it doesn't try to install the 386 packages.  I dont remember if the output was just "p" before the purge.

Heres my  aptitude search "linux.*386" again:
```

pi  linux-386                                                 - Complete Linux kernel on 386.
p   linux-headers-2.6.10-5-386                                - Linux kernel headers 2.6.10 on 386
p   linux-headers-2.6.11-1-386                                - Linux kernel headers 2.6.11 on 386
p   linux-headers-386                                         - Linux kernel headers on 386
v   linux-image-2.6-386                                       -
c   linux-image-2.6.10-4-386                                  - Linux kernel image for version 2.6.10 on 386.
pi  linux-image-2.6.10-5-386                                  - Linux kernel image for version 2.6.10 on 386.
p   linux-image-2.6.11-1-386                                  - Linux kernel image for version 2.6.11 on 386.
c   linux-image-2.6.8.1-3-386                                 - Linux kernel image for version 2.6.8.1 on 386.
pi  linux-image-386                                           - Linux kernel image on 386.
v   linux-restricted-modules-2.6-386                          -
pi  linux-restricted-modules-2.6.10-5-386                     - Non-free Linux 2.6.10 modules on 386
c   linux-restricted-modules-2.6.8.1-3-386                    - Non-free Linux 2.6.8.1 modules on 386
pi  linux-restricted-modules-386                              - Restricted Linux modules on 386.

```

The 386 packages are marked purged, but to be installed.. I just dont get it.

I did the dist-upgrade heres the aptitude search "linux.*386" result: 

```

root@jkhjkh:/boot/grub # aptitude search "linux.*386"
i   linux-386                                                 - Complete Linux kernel on 386.
p   linux-headers-2.6.10-5-386                                - Linux kernel headers 2.6.10 on 386
p   linux-headers-2.6.11-1-386                                - Linux kernel headers 2.6.11 on 386
p   linux-headers-386                                         - Linux kernel headers on 386
v   linux-image-2.6-386                                       -
c   linux-image-2.6.10-4-386                                  - Linux kernel image for version 2.6.10 on 386.
i A linux-image-2.6.10-5-386                                  - Linux kernel image for version 2.6.10 on 386.
p   linux-image-2.6.11-1-386                                  - Linux kernel image for version 2.6.11 on 386.
c   linux-image-2.6.8.1-3-386                                 - Linux kernel image for version 2.6.8.1 on 386.
i A linux-image-386                                           - Linux kernel image on 386.
v   linux-restricted-modules-2.6-386                          -
i A linux-restricted-modules-2.6.10-5-386                     - Non-free Linux 2.6.10 modules on 386
c   linux-restricted-modules-2.6.8.1-3-386                    - Non-free Linux 2.6.8.1 modules on 386
i   linux-restricted-modules-386                              - Restricted Linux modules on 386.

```

Now I ran the aptitude purge "linux.*386" and got this output:

```

Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Couldn't find package "linux.*386".  However, the following
packages contain "linux.*386" in their name:
  linux-restricted-modules-2.6.10-5-386 linux-386 linux-image-2.6.8.1-3-386
  linux-image-2.6.10-4-386 linux-headers-386
  linux-restricted-modules-2.6.8.1-3-386 linux-image-386
  linux-headers-2.6.10-5-386 linux-image-2.6.10-5-386
  linux-headers-2.6.11-1-386 linux-image-2.6.11-1-386
  linux-restricted-modules-386
The following packages have been kept back:
  libwine libxvidcore4 wine
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done

```

Now I ran aptitude purge "~Dlinux.*386":

```

Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
The following packages have been kept back:
  libwine libxvidcore4 wine
The following packages will be REMOVED:
  linux-386 linux-image-386 linux-restricted-modules-2.6.10-5-386
  linux-restricted-modules-386
0 packages upgraded, 0 newly installed, 4 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 13.2MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... 1%
Writing extended state information... Done
(Reading database ... 96421 files and directories currently installed.)
Removing linux-386 ...
Removing linux-image-386 ...
Removing linux-restricted-modules-386 ...
Removing linux-restricted-modules-2.6.10-5-386 ...
Purging configuration files for linux-restricted-modules-2.6.10-5-386 ...
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done

```

Heres the aptitude search "linux.*386":

```

p   linux-386                                                 - Complete Linux kernel on 386.
p   linux-headers-2.6.10-5-386                                - Linux kernel headers 2.6.10 on 386
p   linux-headers-2.6.11-1-386                                - Linux kernel headers 2.6.11 on 386
p   linux-headers-386                                         - Linux kernel headers on 386
v   linux-image-2.6-386                                       -
c   linux-image-2.6.10-4-386                                  - Linux kernel image for version 2.6.10 on 386.
i A linux-image-2.6.10-5-386                                  - Linux kernel image for version 2.6.10 on 386.
p   linux-image-2.6.11-1-386                                  - Linux kernel image for version 2.6.11 on 386.
c   linux-image-2.6.8.1-3-386                                 - Linux kernel image for version 2.6.8.1 on 386.
p   linux-image-386                                           - Linux kernel image on 386.
v   linux-restricted-modules-2.6-386                          -
p   linux-restricted-modules-2.6.10-5-386                     - Non-free Linux 2.6.10 modules on 386
c   linux-restricted-modules-2.6.8.1-3-386                    - Non-free Linux 2.6.8.1 modules on 386
p   linux-restricted-modules-386                              - Restricted Linux modules on 386.

```

Now when I run dist-upgrade it longer shows that the i386 packages will be installed.  Quite strange.  The i386 kernel is still installed though.  

So then I ran: "aptitude purge linux-image-2.6.10-5-386".  This removed the last reference to i386 and now the dist-upgrade shows everything as expected!!!  That was one strange problem, but its fixed now...

Heres the resulting output from aptitude search "linux.*386" now:

```

aptitude search "linux.*386"
p   linux-386                                                 - Complete Linux kernel on 386.
p   linux-headers-2.6.10-5-386                                - Linux kernel headers 2.6.10 on 386
p   linux-headers-2.6.11-1-386                                - Linux kernel headers 2.6.11 on 386
p   linux-headers-386                                         - Linux kernel headers on 386
v   linux-image-2.6-386                                       -
c   linux-image-2.6.10-4-386                                  - Linux kernel image for version 2.6.10 on 386.
p   linux-image-2.6.10-5-386                                  - Linux kernel image for version 2.6.10 on 386.
p   linux-image-2.6.11-1-386                                  - Linux kernel image for version 2.6.11 on 386.
c   linux-image-2.6.8.1-3-386                                 - Linux kernel image for version 2.6.8.1 on 386.
p   linux-image-386                                           - Linux kernel image on 386.
v   linux-restricted-modules-2.6-386                          -
p   linux-restricted-modules-2.6.10-5-386                     - Non-free Linux 2.6.10 modules on 386
c   linux-restricted-modules-2.6.8.1-3-386                    - Non-free Linux 2.6.8.1 modules on 386
p   linux-restricted-modules-386                              - Restricted Linux modules on 386.

```

Thanks for all your help.  It was greatly appreciated, and the reason I like ubuntu so much!  The USERS!

---

### Post by mendicant on 2005-05-03
Yeah, that's a weird one.  You normally shouldn't have to go through all these hoops.  Not sure why they appeared for you.  Glad it's all working for you now, though.

---

