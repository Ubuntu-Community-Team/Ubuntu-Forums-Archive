---
title: "Warty Backport: Gaim-encryption 2.34"
date: 2005-02-15
forum: Ubuntu Backports
---

### Post by rufius on 2005-02-15
**Synopsis**
I built gaim-encryption from scratch for gaim 1.1.2

**Backporting Process**
The source archive directly came from the original programmer. I debianized it myself and the build went without errors.

**Packaging Status:**
i386 -- Staging at revision 38
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**
I tested the plugin and it works fine from what I can tell. I received no bugs while testing it.

---

### Post by Nano on 2005-02-16
[QUOTE=rufius]**Synopsis**
I built gaim-encryption from scratch for gaim 1.1.2

**Backporting Process**
The source archive directly came from the original programmer. I debianized it myself and the build went without errors.

**Packaging Status:**
i386 -- Staging at revision 38
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**
I tested the plugin and it works fine from what I can tell. I received no bugs while testing it.[/QUOTE]

Great! I want to test it!
However, I can't find it in the repositories...

Where is it exactly?

THanks again for your great job

---

### Post by jdong on 2005-02-16
dists/warty-backports-staging/universe/binary-i386/gaim-encryption_2.34-1~4.10ubp1_i386.deb



I would recommend moving it from warty-backports-staging to warty-extras-staging, as no such package exists in Hoary or Debian.

---

### Post by rufius on 2005-02-16
[QUOTE=jdong]dists/warty-backports-staging/universe/binary-i386/gaim-encryption_2.34-1~4.10ubp1_i386.deb



I would recommend moving it from warty-backports-staging to warty-extras-staging, as no such package exists in Hoary or Debian.[/QUOTE]
 jdong, ah sorry, I didn't note that. I'll move it now.

---

### Post by Technoviking on 2005-02-16
I'm getting the following error upgrading gaim

Setting up gaim-data (1.1.2-3ubuntu1-4.10ubp1) ...
Setting up gaim (1.1.2-3ubuntu1-4.10ubp1) ...
rmdir: `/usr/share/doc/gaim': No such file or directory
dpkg: error processing gaim (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gaim-dev:
 gaim-dev depends on gaim (= 1:1.1.2-3ubuntu1-4.10ubp1); however:
  Package gaim is not configured yet.
dpkg: error processing gaim-dev (--configure):
 dependency problems - leaving unconfigured

The following fixes the error
```
sudo mkdir /usr/share/doc/gaim
``` 

Mike

---

### Post by Technoviking on 2005-02-16
Working great, Thanks

---

### Post by rufius on 2005-02-16
[QUOTE=Mike Basinger]Working great, Thanks[/QUOTE]
 Any time :).

---

### Post by mojorising on 2005-02-26
I can't seem to get it to work. 

Gaim and gaim-encryption seemed to install fine and Gaim works but the plugin does not appear in my plugins list in gaim. 

Below is what my /etc/apt/sources.list file looks like:

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras-staging universe multiverse restricted


What am I doing wrong/ not doing at all?


Thanks in advance!

Mike

---

