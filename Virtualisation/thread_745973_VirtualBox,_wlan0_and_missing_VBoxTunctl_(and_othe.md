---
title: "VirtualBox, wlan0 and missing VBoxTunctl (and others)"
date: 2008-04-05
forum: Virtualisation
---

### Post by Amorget on 2008-04-05
I am trying to run Vista with VirtualBox for a development platform.  Just the basic setup worked great, however I want it to be visible from the "outside".  So, I went ahead and tried to set up bridging.  However, that didn't go so well.

First it seems I am missing all the scripts (VBoxTunctl, VBoxAddIF, etc) that are called for.

So far all the tutorials I have seen for using the Wireless Lan use VBoxTunctl.

I have tried downloading the .deb package from the VirtualBox site, but that didn't help.

Can anyone tell me how to either A) find the missing scripts or B) set up a Bridge on the Wireless LAN without using those scripts.

Thanks a ton,
Douglas

---

### Post by kamome on 2008-04-05
Same here (missing VBoxTunctl...), Ubuntu 7.10.
VBoxTunctl is not present in the package virtualbox-ose (dpkg -L virtualbox-ose).

---

### Post by sparklyprgs on 2008-04-13
:confused:

Ditto for me.

Downloaded the package in Synaptics, followed the setup guide (section 6.5.1.1, step 4 in the UserManaul.PDF), no VBoxAddIF in site!  After an hour of trying to find the damn VBoxAddIF, I did the following.

If you read the very next section in the PDF, it says:

"To setup a host interface using Debian and Ubuntu's native methods, do the following instead of step 4 above:"

If you follow the next *4* steps in place of the step that needs VBoxAddIF (pasted below), it might work.  I tried it but gave up and just switched to NAT.

:)

1. First install the User Mode Linux utilities package (uml-utilities), which
contains tools to create TAP interfaces. You can do this from the command line
as follows:
sudo apt-get install uml-utilities
In order for VirtualBox to be able to access the interface, the user who will be
running the virtual machine must be added to the group uml-net, for example
with the following command (replace <user> with your user name):
sudo gpasswd -a <user> uml-net
You will have to log in again for the change to take effect.
656 Virtual networking
2. To describe the TAP interface to your Debian or Ubuntu system, add an entry to
the &#64257;le /etc/network/interfaces. This names the the interface and must
also specify the user who will be running the virtual machine using the interface.
The following sample entry creates the interface tap0 for the user <user>
(again, replace with your user name):
auto tap0
iface tap0 inet manual
up ifconfig $IFACE 0.0.0.0 up
down ifconfig $IFACE down
tunctl_user <user>
You will probably want to change the entry based on your networking needs. You
will &#64257;nd documentation in the &#64257;le /usr/share/doc/uml-utilities/README.Debian
on your host computer.
3. To add the TAP interface to the bridge, replace the line
bridge_ports eth0
in the bridge section in /etc/network/interfaces with
bridge_ports eth0 tap0
4. Restart networking on the host:
sudo /etc/init.d/networking restart

---

### Post by sparklyprgs on 2008-04-22
Just an update: I removed VirtualBox totally using synaptic, then downloaded and installed virtualbox_1.5.6-28266_Ubuntu_gutsy_i386.deb, and then VBoxAddIF etc was all there and the instructions worked perfectly.

It was really easy to get it all working once the proper scripts were there. I have NO IDEA why these would be left out of the ubuntu package.  :confused:

---

