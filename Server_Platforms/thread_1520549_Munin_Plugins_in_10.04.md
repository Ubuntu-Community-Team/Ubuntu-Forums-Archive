---
title: "Munin Plugins in 10.04"
date: 2010-06-29
forum: Server Platforms
---

### Post by mcdjork on 2010-06-29
I had some problems today getting Munin plugins to load on a Ubuntu 10.04 server. I finally solved the problem, in case anyone else has the same experience. This applies to the munin-plugins-extra and munin-libvirt-plugins too (probably munin-java-plugins too, but I didn't install it).

On install, Munin's plugin directory is set to /etc/munin/plugins. Within this directory, each of the default munin plugin files is linked individually to their location in /usr/share/munin/plugins. When new plugins are installed in /usr/share/munin/plugins, the links are of course not created. I'm not sure why the install was set up this way in the first place, but all I did to solve the problem was backup (or remove) the /etc/munin/plugins directory and create a symbolic link to /usr/share/munin/plugins. Remember to also restart the munin node.

```

sudo mv /etc/munin/plugins /etc/munin/plugins.bak
sudo ln -s /usr/share/munin/plugins /etc/munin/plugins
sudo restart munin-node

```

This also has to be done on any nodes. You may also have to change some permissions in the /usr/share/munin/plugins directory.

Hopefully this will same other users some trouble!

---

### Post by K.Mandla on 2010-06-29
Moved to Server Platforms.

---

