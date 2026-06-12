---
title: "VNC/VMWare Workstation issue"
date: 2011-04-18
forum: Virtualisation
---

### Post by alienzx on 2011-04-18
I primarily interface with  my box through a tightvnc server. unfortunately its not very stable.  When it crashes, it takes all my vms on workstation with it.


  Is there a way to make vmware workstation run as a service or not rely on that vnc session?
  Is there a better vnc solution, perhaps a session that runs independent of vnc?


  I'm not too experienced in the gui side as I have been running ubuntu server only for a few years.

---

### Post by HermanAB on 2011-04-21
Simple really, don't use VNC, it is mostly a Windows thing and on Linux, it is almost always the wrong solution.  Use SSH, like everybody else does and life will be good.

---

### Post by alienzx on 2011-04-21
but ssh is command line only. In this case I need GUI to run certain software (vmware workstation)

---

### Post by HermanAB on 2011-04-21
SSH does X forwarding.  So all you need is a X server on your workstation (any Linux desktop) then connect like this:
$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"

or even:
$ ssh -X -C -c blowfish user@server "gnome-panel"

and go click happy.

That also works from Windows using Cygwin.

---

### Post by alienzx on 2011-04-21
I have previously used xming like this, but it seems to be slow over the internet. I am also usually on windows boxes without the ability to install all of the tools I need for this type of environment.

---

