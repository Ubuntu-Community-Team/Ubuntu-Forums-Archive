---
title: "KVM Spice no Keyboard in VNC Session"
date: 2014-05-20
forum: Virtualisation
---

### Post by xbriank on 2014-05-20
I have 14.04 running KVM with a couple test VMs.  The VMs use SPICE as display type.  I can connect to the server with VMM from my laptop or any other machine and everything works fine.  If I use VNC to connect to the desktop of the host (KDE Desktop) I can launch VMM but keystrokes are not passed to the VM.  If I am sitting in front of the host with a monitor and keyboard it works fine. If I change the display to VNC on the VM it also works from a VNC session to the host.

Anyone have any ideas?  I have this same setup running on a CentOS 6 host with no issues (Migrating to Ubuntu from CentOS) I suppose I could use VNC display for the VMs but I really like SPICE better.

---

### Post by xbriank on 2014-05-23
Anyone have any Ideas?  I know it is not the most common thing to be running Virt-manager from within a VNC session to the host, but it is something I have gotten used to doing.  I can rule out that it is a KDE only issue, as I was able to replicate the problem in xfce4.  also it is not a strictly Ubuntu problem as I was able to replicate in Debian.

---

### Post by xbriank on 2014-07-11
After taking another look at this I realized that there was a big difference between CentOS and Ubunt and Debian - the VNC server they use.  on Ubuntu and Debian I was running vnc4server (also tried tightvncserver on both with the same results)  on CentOS I am running TigerVNC-server.  I found a tigervnc .deb package for 14.04 in here: [https://www.mail-archive.com/tigervnc-users@lists.sourceforge.net/msg00892.html](https://www.mail-archive.com/tigervnc-users@lists.sourceforge.net/msg00892.html) which points to this page for the downloads: [http://tigervnc.sourceforge.net/tiger.nightly](http://tigervnc.sourceforge.net/tiger.nightly) 

A quick purge of the installed VNC server and install of this one and my problem has been solved.  maybe this will help someone else.

---

### Post by TheFu on 2014-07-14
Or just use virt-viewer with spice ... or am I missing something?  I avoid VNC - either NX or spice are the options when ssh CLI doesn't do it.  After using NX, I can't imagine ever using VNC - much too slow.

---

