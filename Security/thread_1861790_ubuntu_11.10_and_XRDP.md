---
title: "ubuntu 11.10 and XRDP"
date: 2011-10-16
forum: Security
---

### Post by Monery on 2011-10-16
Hello and greetings
 
I have on my network a newly upgraded Ubuntu 11.10 server running XRDP for serving a few applications up that I can't find in the Windows world
 
Since the upgrade when trying to log into the server from Windows 7 Pro or Home Ed, I now get a blue background with nothing on it. My guess is that Unity broke something that worked beautifully under GNOME. Anyone have ideas on how to fix this short of moving to another OS?

---

### Post by gradwell on 2011-12-04
I have encountered the same problem and bug reported it as Bug #900016

[https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/900016](https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/900016)

---

### Post by Jive Turkey on 2011-12-05
I've had great results using putty and Xming together to achieve X11 forwarding for remote linux apps on windows 7.  nxserver and nxclient from nomachine work pretty well too for the true RDP type of experience.  I've never tried XRDP though.

---

### Post by Kissell on 2011-12-05
I've been getting the same problem as Mr. gradwell.  I used to use xrdp, but after doing a fresh install of Ubuntu 11.10 it hasn't worked no matter what I try.

---

### Post by cariboo on 2011-12-05
Have you tried a different desktop environment, like gnome-classic? To install gnome-classic, use your preferred method of installing packages and install gnome-session-fallback. On a reboot, select gnome-classic from the lightdm menu and login.

@gradwell, if there is already a bug report about the problem, why create a new one, especially with so little information?

---

