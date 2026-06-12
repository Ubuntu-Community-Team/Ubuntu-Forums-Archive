---
title: "&quot;Ccleaner&quot;"
date: 2008-04-16
forum: Security Discussions
---

### Post by snakedog on 2008-04-16
There's an app available for Windows called Ccleaner that's great for deleting all kinds of temp files, and clearing cookies and caches.  Are there similar tools for Ubuntu?  Or is anything like this really needed?

I've noted the contents of the /tmp folder generally get deleted on rebooting.  And I routinely clear my private data in Firefox.  Anything else I need to keep Xubuntu 'clean'?

TIA, Karl

---

### Post by Oldsoldier2003 on 2008-04-16
> **snakedog said:**
> There's an app available for Windows called Ccleaner that's great for deleting all kinds of temp files, and clearing cookies and caches.  Are there similar tools for Ubuntu?  Or is anything like this really needed?

I've noted the contents of the /tmp folder generally get deleted on rebooting.  And I routinely clear my private data in Firefox.  Anything else I need to keep Xubuntu 'clean'?

TIA, Karl
```
sudo apt-get clean
```clears out your apt cache
if you absolutely must, you can always clear out your temp directory manually.

here is a command to purge your thumbnails that are older than 7 days (they can add up quite fast if you do a lot of graphics) :
```

find ~/.thumbnails -type f -atime +7 -exec rm {} \;
```

---

### Post by FakeOutdoorsman on 2008-04-17
There is /etc/init.d/bootclean that automatically cleans out /tmp.  I'm not sure if it is enabled by default or not.

---

### Post by Oldsoldier2003 on 2008-04-17
> **FakeOutdoorsman said:**
> There is /etc/init.d/bootclean that automatically cleans out /tmp.  I'm not sure if it is enabled by default or not.
```

update-rc.d -f bootclean remove
``` will disable that init script in debian... it should do the same in Ubuntu

---

### Post by Ziggy72 on 2008-04-18
**localepurge** will recover diskspace wasted by unneeded locale files and localized man pages and **deboprphan** will find and help look after the deletion of orphaned packages. Both can be installed with synaptic.

---

### Post by netlogic on 2008-04-18
Hey snakedog!
These are great suggestion for you.  My suggestion is add all these suggestions to a simple shell script and launch them through a crontab (/etc/crontab).

---

### Post by Oldsoldier2003 on 2008-04-18
> **Ziggy72 said:**
> **localepurge** will recover diskspace wasted by unneeded locale files and localized man pages and **deboprphan** will find and help look after the deletion of orphaned packages. Both can be installed with synaptic.

I totally forgot about localepurge, and i have that installed on my system !   I'm a bit paranoid about deborphan since I tend to use several different installation methods and I'm afraid that because of this using it would create issues. (I.E. I use aptitude,apt-get, synpatic, checkinstall, dpkg , and make install depending on the situation- so there are bound to be some packages that will be mislabeled as orphans along the way)

---

### Post by pietjanjaap on 2008-04-19
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

