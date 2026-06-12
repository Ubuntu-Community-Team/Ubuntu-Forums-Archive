---
title: "Weird Errors in update after the use of a purge command"
date: 2015-12-12
forum: Server Platforms
---

### Post by grier-devon on 2015-12-12
Hey everyone, 
I had to fully remove owncloud off of my ubuntu 14.04 server image, remove would get the job done so I bit the bullet and went with a purge command. Reinstalled and everything is fine and working but I am getting errors when I run updates and I am hoping someone can help out. Thanks.

```
Preparing to unpack .../libembymagickcore-6.q8-2_8%3a6.9.2-8_amd64.deb ...Unpacking libembymagickcore-6.q8-2:amd64 (8:6.9.2-8) ...
dpkg: error processing archive /var/cache/apt/archives/libembymagickcore-6.q8-2_8%3a6.9.2-8_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libMagickCore-6.Q8.so.2.0.0', which is also in package libmagickcore-6.q8-2:amd64 8:6.9.1-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../libembymagickwand-6.q8-2_8%3a6.9.2-8_amd64.deb ...
Unpacking libembymagickwand-6.q8-2:amd64 (8:6.9.2-8) ...
dpkg: error processing archive /var/cache/apt/archives/libembymagickwand-6.q8-2_8%3a6.9.2-8_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libMagickWand-6.Q8.so.2.0.0', which is also in package libmagickwand-6.q8-2:amd64 8:6.9.1-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libembymagickcore-6.q8-2_8%3a6.9.2-8_amd64.deb
 /var/cache/apt/archives/libembymagickwand-6.q8-2_8%3a6.9.2-8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks.

---

### Post by ian-weisser on 2015-12-13
> **grier-devon said:**
> dpkg: error processing archive /var/cache/apt/archives/**libembymagickcore-6.q8-2_8%3a6.9.2-8_amd64**.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libMagickCore-6.Q8.so.2.0.0', which is also in package **libmagickcore-6.q8-2:amd64 8:6.9.1-2**

The two packages have a *file conflict*. Both try to install the same package. They conflict - you cannot have both  packages installed at the same time.

> **grier-devon said:**
>  dpkg: error processing archive /var/cache/apt/archives/**libembymagickwand-6.q8-2_8%3a6.9.2-8_amd64**.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libMagickWand-6.Q8.so.2.0.0', which is also in package **libmagickwand-6.q8-2:amd64 8:6.9.1-2**

Two different package that also have a file conflict.

I do not know what PPA or other non-Ubuntu repository you are trying to install libembymagick* from, but stop doing it. You already have libmagick* installed.
I do not see how a previous 'purge' action is relevant. It might be, or your problem might be coincidental.

One way to fix the problem.
1) Delete the libembymagick* packages from your local cache (/var/cache/apt/archives),
2) Remove that source from your apt sources (/etc/apt/sources.list*),
3) Refresh your package database (sudo apt update),
4) Test your package manager (sudo apt upgrade).

---

### Post by grier-devon on 2015-12-15
Thanks, got this fixed thanks to your support. The repository was from when I was using to maintain Emby which was official repository they offered, however I removed it around this same time. Thanks.

---

