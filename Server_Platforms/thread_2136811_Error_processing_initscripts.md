---
title: "Error processing initscripts"
date: 2013-04-18
forum: Server Platforms
---

### Post by brivelt on 2013-04-18
Hi Folks,

I am installing my new VPS with Ubuntu 12.04 LTS 64bit but ran into a problem.
I do have some issues with setting up initscripts correctly, see code below for terminal output.

```
Setting up initscripts (2.88dsf-13.10ubuntu11.1) ...mount: permission denied
dpkg: error processing initscripts (--configure):
 subprocess installed post-installation script returned error exit status 1

```

This error shows up every time I install or update a package. It's listed as an update / install in progress.

Maybe someone can help me out.

-Brian

---

### Post by matt_symes on 2013-04-18
Hi

Does this sound like your bug ?

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/1036796](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/1036796)

Kind regards

---

