---
title: "Programmatically changing gnome proxy config"
date: 2010-09-26
forum: Ubuntu Dev Link Forum
---

### Post by DarthCrap on 2010-09-26
Hi

I have been writing a program to enable and disable the usage of a university's proxy, so I don't have to go into five bazillion places every time I go back to my real home etc, and instead can just use a script to disable it in one go.

I can successfully enable/disable the use of the proxy for apt, bash ($http_proxy etc), synaptic and firefox, via a script.
However, I cannot seem to effect the gnome settings, which can be set with the program gnome-network-properties.

I have found out that gnome-network-properties uses gconf to write gconf values in /system/proxy and /system/http_proxy to the gconf configuration files at /home/$USER/.gconf and /etc/gconf/gconf.xml.defaults.
However, using gconftool to change these values does not seem to have any effect. 
gconftool reveals these values were written, but it does not seem to have any effect, as the proxy is still used. gnome-network-properties also does not show any chnages.

My questions are: 
1.) Does gnome-network-properties write to anywhere else that I am not changing?
2.) Is there an easier way to programmatically do what gnome-network-properties does?

Sorry for the badly written description. I suck at those. Hope you can understand it though.

Scott

Note: This thread may be in the wrong forum. If so, please let me know.

---

