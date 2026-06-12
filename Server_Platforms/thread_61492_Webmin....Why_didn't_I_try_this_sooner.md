---
title: "Webmin....Why didn't I try this sooner?"
date: 2005-08-31
forum: Server Platforms
---

### Post by spacemonkey on 2005-08-31
I run a headless (no monitor/keyboard/mouse) server on my network.  It's not a high traffic server by any means, i host some files for friends and myself, and provide a few other services.  Up till now, admin on the server consisted of SSH, and a vnc to xdm connection and fluxbox if I needed a graphical environment.  I've heard about webmin before, but never tried it.  I finally installed it, installed a bunch of modules, and set it up so that only my desktop, from behind my router can access the webmin server.  All I can say is wow.  This is so easy to use.  I don't have to manually edit a lot of config files anymore, webmin has nice little HTML forms for me.  I haven't been using it long, but I love it.  Just thought I would let everyone know about this.  So far, I think it's a great tool if you run a headless server and need an easier way to manage it.

---

### Post by drummer on 2005-08-31
I aggree, it's a _great_ tool. but i found it tricky to use initially as it had lots of default values for things and i had to search through the filesystem looking for certain files, etc.

---

### Post by TheDanMan on 2005-09-01
I too use webmin however the version in the repositories is often a couple versions behind.  I don't know who the maintainer is but its been like this for a while.  At least it is better than the debian version.  If you install from the apt sources I recomend you grab the tar.gz from the webmin site and do an upgrade.

---

### Post by Velox Letum on 2005-09-04
Its not like its hard to do the .tar.gz install, nor do you have to compile anything. All that you have to do is download it, tar -zxf it, cd to the webmin directory and run ./setup.sh

Easy, simple, clean. Even updates if it detects an install already there.

---

