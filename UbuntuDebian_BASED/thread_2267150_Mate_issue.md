---
title: "Mate issue"
date: 2015-02-27
forum: Ubuntu/Debian BASED
---

### Post by mikethebos on 2015-02-27
[COLOR=#000000][FONT=Verdana]Hi,

I am running mate 1.8 on armv7 pc linaro. The pc is headless so i'm connecting to it with tightvnc. i manually installed the ubuntu-software-center to try it out. whenever i try to install something using the center, it says "Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name': ':1.44'}): org.debian.apt.install-or-remove-packages" I have tried to run policy kit manually; it gives "(polkit-gnome-authentication-agent-1:3743): polkit-gnome-1-WARNING **: Unable to determine the session we are in: No session for pid 3743'' The gnome-authentication-agent is set to run at start. /etc/X11/default- display-manager shows that lxdm is default. Synaptic doesn't work either; just doesn't open. Both work perfectly when ran with sudo in the Mate terminal. Any suggestions?
[/FONT][/COLOR]

---

