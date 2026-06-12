---
title: "libvirt and network bridge failing because sysctl.conf not fully loading"
date: 2008-10-14
forum: Virtualisation
---

### Post by danielhs on 2008-10-14
I followed instructions here [http://wiki.libvirt.org/page/Networking#Debian.2FUbuntu_Bridging](http://wiki.libvirt.org/page/Networking#Debian.2FUbuntu_Bridging)
which seem to work very well.  However, it seems that the necessary settings in /etc/sysctl.conf don't get loaded on reboot.  And as a result the network bridge doesn't work.


I thought that, perhaps, I needed to disable dhcdbd as noted here [http://doc.ubuntu.com/ubuntu/serverguide/C/network-configuration.html#bridging](http://doc.ubuntu.com/ubuntu/serverguide/C/network-configuration.html#bridging)
however, that doesn't make a difference at all.


Instead it seems that these sysctl.conf settings have to be put in place but they're simply not loading.


I think this might be related to this bug [https://bugs.launchpad.net/ubuntu/+source/procps/+bug/50093](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/50093)
But, I'm not sure.


Any helping addressing this issue would be greatly appreciated.
How can I set sysctl.conf to reload each time the system boots so that settings are put in place?  There must be a way to do that every time.
Since libvirt, kvm, and bridged networking seem to be emerging as linux and ubuntu standards for virtualization I'm surprised that I'm encountering these types of problems.  Surely, there must be a clean fix for this.

Daniel

---

### Post by ktulu73 on 2008-10-15
Hm,

just add sysctl -p /etc/sysctl.conf to any other (later) start script.
I have no firewall configured on my kvm box, but I think this is the easiest way.

---

### Post by danielhs on 2008-10-15
Ahhhh thanks so much.

Very helpful.

I did a little [reading about runlevels ]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/") and [here]("http://oldfield.wattle.id.au/luv/boot.html#init").

I ended up using sysv-rc-conf to modify procps (the script which triggers sysctl -p /etc/sysctl.conf, see the bug report cited above for more information).  procps was originally on runlevel S.  I added it to runlevels 2 3 4 5.

With that modification it's working great.  Thanks for the help.

Daniel

---

