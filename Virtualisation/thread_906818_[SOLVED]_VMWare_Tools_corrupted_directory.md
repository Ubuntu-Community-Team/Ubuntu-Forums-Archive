---
title: "[SOLVED] VMWare Tools corrupted directory"
date: 2008-08-31
forum: Virtualisation
---

### Post by lazyart on 2008-08-31
Running Gutsy AMD64.  Installed VMWare a couple of distros ago with no problems.  Have a few machines running under it-- Windows XP in one, A Debian web server (no gui) and a Debian mail server with gui.

The problem is that I can't install VMWare Tools in the Debian gui box.  It mounts the VMWare Tools virtual CD, but the directory is full of gibberish (looks like bits and pieces of source code).  See the attached screenshot.

I thought it was a problem with the VM so I created a new one but had the same problem.  Upgrade my VMware Server to current (1.0.6 build-91891) and it persists.

Any ideas?

That I shouldn't have a gui on a server is immaterial, so please don't bring that up.

---

### Post by lazyart on 2008-09-01
Found my own answer-- /usr/lib/vmware/isoimages contains the images for vmware tools for the different platforms.  Don't know why I'm getting the problem, but I can mount the .iso file and install that way.

---

