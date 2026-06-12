---
title: "Problem with the flashplugin-nonfree package"
date: 2006-09-20
forum: Ubuntu Backports
---

### Post by Frostmourne on 2006-09-20
Yesterday the package reported to have an updated backport (7.0r68 I think it was) so I went ahead and installed it. During the installation a dialog box came up and asked me if I accepted the license, and I clicked Continue. The window froze, and after killing the window the package manager tried to install it again, and the window froze. Then I got an error saying the package installation exited with an error code 1 (I think that was the number.)  Firefox's about:plugins screen reports the updated Flash version, however. What I am concerned with is everytime I remove/add packages in Synaptic it tries and fails to install the Flash plugin, which is annoying. Is anyone else experiencing this problem?

---

### Post by Delkster on 2006-09-20
Yes, actually I just went on to file a bug report about that:

[https://launchpad.net/products/dapper-backports/+bug/61404](https://launchpad.net/products/dapper-backports/+bug/61404)

---

### Post by jamo on 2006-09-21
You can do a "sudo apt-get install -f" in your console to see what happens. I guess it's a typo somewhere in the control file.

---

### Post by missmoondog on 2006-09-21
running sudo apt-get install -f, gets the exact same results.

---

### Post by LuisC-SM on 2006-09-21
If you click on the link for the bug report previously provided, you'll find the answer for this.

Or as Conrad Knauer states:
> 

7.0.68~ubuntu2 isn't showing up in dapper-backports via Synaptic yet, but the package is in the archives and works quite nicely with Gdebi :)

[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.68~ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.68~ubuntu2_i386.deb)

In Gdebi, be sure to click 'Terminal' to be able to say yes to the EULA.


It really works

Regards

Luis C. Suárez

---

