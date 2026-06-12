---
title: "Session x11 not working. Any action on desktop is ignored."
date: 2019-10-31
forum: Ubuntu Development Version
---

### Post by corradoventu on 2019-10-31
Session x11 not working. Any action on desktop is ignored, only mouse arrow moves on the screen.
Session wayland works fine.
Also live session from Ubuntu 20.04 LTS "Focal Fossa" - Alpha amd64 (20191030) and 20191031
has the same problem.

---

### Post by Irihapeti on 2019-10-31
I've been having what sounds like similar problems, but with both X11 and Wayland. Restarting X (when using X11) via SSH seems to result in the system locking up again almost immediately. Mine's running in KVM, and I had wondered if that was making any difference.

---

### Post by P-I H on 2019-11-01
I have installed focal in Boxes and updated today. It works fine with x11.

---

### Post by corradoventu on 2019-11-01
Installed on a different partition from last ISO Ubuntu 20.04 LTS "Focal Fossa" - Alpha amd64 (20191101) I have the same problem.
Also on a different hardware with ISO dated 20191019 was working fine but after update+upgrade I have the same problem.
Opened a bug: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1850969](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1850969)

---

### Post by Irihapeti on 2019-11-01
Thanks. I've marked myself as affected.

---

### Post by mc4man on 2019-11-03
Saw same when installing from daily pending image several days ago.
Live session unusable, after direct install an Ubuntu session develops same issue sometime within several minutes. 
However then installed the unity session, it works fine so sorta doubt this is an xorg bug, maybe gnome-shell

---

### Post by Irihapeti on 2019-11-04
On further investigation, I think that my particular Wayland problem is with Synaptic. (I guess it's bug-report time. :) ) Otherwise, Wayland seems to work well. Xorg seems to be the one that's locking up on me. I notice that if I try logging in via ssh and issue a shutdown command, ssh gets disconnected but the VM won't close down.

Gnome-shell had some xorg bugs during the latter stages of eoan testing, so this might well be yet another one.

---

### Post by corradoventu on 2019-11-04
The problem of Synaptic in Wayland is old and still unresolved: [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1731324](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1731324)
in my Ubuntu 20.04 with Wayland Synaptic can be used if called with SUDO.

---

### Post by Irihapeti on 2019-11-04
Thanks, that might be a workaround in the meantime.

---

### Post by corradoventu on 2019-11-09
bug [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1850969](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1850969) has been closed, after last updates the x11 session works fine.

---

### Post by lammert-nijhof on 2019-11-09
Running Ubuntu 20.04 in Virtualbox, I still have that problem of a black screen and no reaction to mouse or keyboard, when starting in full screen mode. If I start in windowed mode the system works normal and I can put the system in full screen mode after login. I'm not using 3D mode for 20.04.
I have some other problems with Virtualbox related to 3D acceleration with windows Vista and 7 and with Ubuntu 16.04 and Ubuntu 19.04. I'll wait for these problems to be solved first and then if not solved, I will write an Ubuntu bug-report. In the latest version of Virtualbox 6.0.14 I had more problems with their display driver then in all versions since 2011.

---

