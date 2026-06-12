---
title: "Authentication problem on precise server when in vnc"
date: 2012-06-27
forum: Server Platforms
---

### Post by dsmithhfx on 2012-06-27
Hi,

I'm encountering a weird authentication problem when viewing a fresh precise server installation (with minimal gnome desktop) over vnc: it is rejecting my password whenever I attempt to run admin gui apps like synaptic and users-admin (it always returns "1 incorrect password attempt" -- even after multiple tries). 

My password is accepted for sudo commands in the terminal running on the vnc client, and over ssh from another pc.

This is how I modified the default server installation:

sudo apt-get install xorg gnome-core gdm gnome-system-tools gnome-utils gnome-app-install sysv-rc-conf tightvncserver

I also applied some initial security-hardening measures outlined [here]("http://www.andrewault.net/2010/05/17/securing-an-ubuntu-server/"):

including sshd_config (PermitRootLogin no), and the steps to "Only allow admin users to use su", including "sudo dpkg-statoverride --update --add root admin 4750 /bin/su". 

Thinking this might be the problem, I added root to the admin group, but this didn't fix it.

I've not experienced this problem with launching gui admin tools in vnc from a 10.04 server of somewhat similar configuration.

Any help would be appreciated. Thanks.

---

### Post by papibe on 2012-06-27
Hi dsmithhfx.

It looks like a case of misconfigured gksudo (the graphical sudo). Go into a terminal and run:
```
gksu-properties
```
It'll open a window. Under Behavior there's a field called 'Authentication mode'. If it says su, change it to sudo.

I hope it helps,
Regards.

---

### Post by dsmithhfx on 2012-06-27
Thanks for the gksu-properties tip. It was already set to "sudu".

The problem turned out to be a non-issue, caused by several factors:

1. apparently synaptic does not work in 12.04, at least for some according to my googling, so I would enter the pass and it never launches. I can get by with ubuntu software center, but I'm not happy with it at all.

2. I can't paste in the password. It is a fairly long and complex one, so between failed pastes and mistyping... Careful typing  has it working as per usual.

3. gui app launching in this config seems to be very slow in general (even for stuff like image viewer and evince).

---

### Post by CharlesA on 2012-06-27
Use something other than VNC. NX comes to mind.

Synaptic has worked perfectly fine for me on 12.04.

---

