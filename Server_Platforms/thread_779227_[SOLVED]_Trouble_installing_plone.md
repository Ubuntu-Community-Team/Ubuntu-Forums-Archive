---
title: "[SOLVED] Trouble installing plone"
date: 2008-05-02
forum: Server Platforms
---

### Post by mysticmatrix on 2008-05-02
Hi,
 I installed plone-site metapackage from Synaptic.

It asked my password and port it wanted. I gave it 8081(the default) and proceeded.
However, I can not run the zope instance by doing [http://localhost:8081/manage](http://localhost:8081/manage) in my browser.

Also. the command for starting zope gives

```
$ sudo /etc/init.d/zope2.9 start
 * Zope2.9: no instances found.

```

Any help on where to start from?

---

### Post by SkyyBugg on 2008-05-05
I used the unified installer on Plone.org.  If you use that, it installs correct version of Python, Zope, and Plone.  It installs it in your home dir of the user installing it.  I have installed it several times after I went down the road you are going.  Plone.org will give you the latest version 3.0.6.  They recommend you install via source for production.

The only prereq for Unified installer is is gc++.

To answer you question there is a config file for Zope containing the port number if you want to try another port.  (/home/(username)/Plone-3.0.6/zinstance/etc/zope.conf or wherever synaptic put it.
Also,  I would grep for *lone in process table to make sure it is not already running.

I hope this helps.
SkyyBugg

---

### Post by SkyyBugg on 2008-05-05
I used the unified installer on Plone.org.  If you use that, it installs correct version of Python, Zope, and Plone.  It installs it in your home dir of the user installing it.  I have installed it several times after I went down the road you are going.  Plone.org will give you the latest version 3.0.6.  They recommend you install via source for production.

The only prereq for Unified installer is is gc++.

To answer you question there is a config file for Zope containing the port number if you want to try another port.  (/home/(username)/Plone-3.0.6/zinstance/etc/zope.conf or wherever synaptic put it.
Also,  I would grep for *lone in process table to make sure it is not already running.

I hope this helps.
SkyyBugg

PS Also try this command to start.:
 /home/username/Plone-3.0.6(your plone installdir)/zinstance/bin/**zopectl** start

I think zopectl is what you are looking for.

---

