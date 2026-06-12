---
title: "Remotely manage VMware Workstation on Ubuntu"
date: 2013-09-17
forum: Virtualisation
---

### Post by joshkuo on 2013-09-17
Hi All,

I have a hard time believing that I am the only person attempting to do this or having this problem, so I am posting my findings here, in hope that some smarter individual already has a better solution than what I currently have.

I have a server running Ubuntu 12.10, and I installed VMware Workstation 10 on it. My goal is to be able to be able to remotely manage my virtual machines without having physical access to my Ubuntu host. Sounds simple, right?

I tried VNC (tightVNC), that was easy to connect to from my laptop (running Mac OSX), but when I launch VMware within my VNC connection, it kills my VNC connection instantly. My VNC log file reads something like this (my VNC display is on 8):

```

Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Logging to /tmp/vmware-jkuo/vmware-modconfig-31113.log
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
gnome-session[30747]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.
ICE default IO error handler doing an exit(), pid = 30795, errno = 11
[1379426121,000,xklavier_config.c:xkl_config_registry_load_helper/] 	Missing registry file /usr/share/xmodmap/base.xml
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
** (gnome-settings-daemon:30773): WARNING **: Name taken or bus went away - shutting down
ICE default IO error handler doing an exit(), pid = 30794, errno = 11
(gnome-settings-daemon:30773): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':8'.
(gnome-fallback-mount-helper:30812): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.
(nautilus:30803): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.
(gdu-notification-daemon:31025): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.
(nm-applet:30800): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server:8.
(telepathy-indicator:31029): Gdk-WARNING **: telepathy-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.
(update-notifier:31078): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.
vmware-tray: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.
vmware: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.
vmware-unity-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.
(vmware-unity-helper:32306): Gtk-WARNING **: cannot open display: :8
(vmware-unity-helper:32320): Gtk-WARNING **: cannot open display: :8

```

Not knowing what really caused this, I tried another route: xrdp. I installed xrdp, fired it up, used my RDP client on the laptop to connect, no problem. But again, without fail, whenever I launch VMware, my RDP session is terminated as well. 

So at this point, my gut feeling is that VMware is fighting with X server over some display ports, and since I still have nightmares about manually configuring X11 configuration, I decide to try another way, which seems to work for now (but not very well):

I used an X11 client (XQuartz on the Mac) to ssh into my Linux host, and then launch vmware from the SSH command line. This works okay, but it's somewhat unstable. From time to time, certain keys become unresponsive and I am forced to re-launch X11, and sometimes I am unable to provision a new virtual machine, its screen just stays black when I start it up, and I have no choice but to put a monitor/keyboard/mouse on the Linux host.

So... I am not sure if this is a VMware issue, it's probably a mix of VMware + X display issue, and perhaps even a little Mac/XQuartz in there. I am hoping that someone here has done something similar, and maybe has already found a better solution.

At the end of the day, I am just lazy and don't want to switch mouse/keyboard, I just want to be able to provision virtual machines over a remote connection. 

TIA

---

### Post by TheFu on 2013-09-18
I manage all my VMs remotely without any issues.  In fact, I use remote desktops running inside a "private cloud" most of the day from all over the world. The desktops run LXDE on Ubuntu to keep the GUI abuse down.

The trick is that I am **NOT using anything from VMware**.  KVM+libvirt+virt-manager for VM management and installation, then FreeNX and a NoMachine NX-client for remote desktops.  Virt-manager runs as a client in a "cloud" desktop. NX and virt-manager work over standard ssh connections (though I listen on 443 to ensure hotels don't block it) with fail2ban rejecting bogus connection attempts. Of course, ssh-keys are used for authentication.

There's a nice FreeNX how-to for Ubuntu.  Took me about 20 minutes the first time, now it is less than 5 to setup.

VMware Workstation is an amazing tool, but it doesn't really work for server-on-server virtualization. I see it more for use by testing and QA teams who sit behind the physical machine.  OTOH, I am not a fan of VMware management - after they screed many customers by changing ESX/ESXi license terms a few yrs ago. Took my company 6 months to swap everything from VMware for KVM. We've never looked back.

---

### Post by joshkuo on 2013-09-21
Okay... so basically you are saying no VMware? I have used KVM (and virt-manager) in the past, I liked it, and I would have liked to use it, but due to work constraints, I need to run a few specific virtual machine images that I can't make them work under KVM (I suspect the vendor did something to make sure it only works on VMware).

KVM/virt-manager is good, but I am just wondering if someone out there has solved a similar issue (remote Mac as client, Linux running VMware Workstation as the server)? Or has anyone even run into the same issue?

---

### Post by TheFu on 2013-09-22
The vendor probably just installed the guest additions for vmwareplayer to make life easier for them and potential clients. I agree this should work.
BTW, I saw vmware-workstation last weekend at an installfest.  It automatically installed the guest additions for CentOS/Ubuntu (can't remember which was being installed). The mouse, keyboard integration "just worked" post-install. It was sorta slick.

Let me re-read the OP .... 
* 12.10 is almost out of support. 12.04 will be supported until early 2017. All the other non-LTS releases get about 9 months of support.
* I see that you've tried vnc and rdp - have you considered [FreeNX]("https://help.ubuntu.com/community/FreeNX") Server?  Get the [OSX client]("http://www.nomachine.com/download-package.php?Prod_Id=3834").  There are clients for many platforms ... I've noticed there isn't a client for Android, which sucks.

Sorry that I don't have an answer, just another thing to try.

---

