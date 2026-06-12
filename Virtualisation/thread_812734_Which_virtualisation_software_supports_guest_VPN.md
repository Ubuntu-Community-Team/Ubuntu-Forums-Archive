---
title: "Which virtualisation software supports guest VPN?"
date: 2008-05-30
forum: Virtualisation
---

### Post by speedsix on 2008-05-30
VirtualBox doesn't pass GRE packets so guest VPN doesn't work, which is dissapointing.

Do any of the others, I want VPN working in an XP guest?



Thanks

---

### Post by Rinzwind on 2008-05-30
Hmmm, yes it does (!?)

You always need to run > sudo /etc/init.d/networking restart from the terminal before try to log into the  guest.

edit: found it on virtualbox.org; user knowisdom. 

> Guys, I was totally going to change to VMware when I couldn't get VPN access to work on a VBox windows guest, but with a little voice inside said no (and when I looked at the 105mb file download for VMware, compared to the 20+mbs for Vbox, I was like, "I can't go out like this!..")

Here is how I did it. This setup for me created a semi permanent solution, you'll see what I mean later on:

Before I begin, I want to go through the process that got me the solution. When I first installed virtualbox, I followed the instructions here [https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03](https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03) under networking, to setup Host Interface Networking. When I did this, I was able to login to my VPN (checkpoint) on the windows xp guest. However, when I restarted, all the config went bye bye, so I turned to manual to see if there was a permanent way.

I followed the steps in the manual for a permanent connection, but that caused my internet not to work on the guest and the host. So what I did, is followed the steps described in the link above, but took steps to make those steps permanent.

1. Edit your /etc/network/interfaces file as root (what I do is alt+f2, then type gksu gedit. Once it's up I browse to the folder, and open interfaces) to look like this:

auto eth0
iface eth0 inet dhcp
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down

auto br0
iface br0 inet dhcp
bridge_ports eth0 vbox0

you will notice that I enable promiscuous mode on my primary eth0 int. This will ensure that all traffic passed on the bridge is accessible by my primary int. I then create the bridge, set it to dhcp, and add ports eth0, and vbox0 to the bridge.

2. Create vbox0 (or vbox(and any number). Type this in the command prompt: sudo VBoxAddIF vbox0 <username>, where the username is the user who has rights to the interface. This will probably be the username you use to log in to ubuntu.

3. Add this line to your /etc/vbox/interfaces file:

vbox0 wilsdx [br0]

This will add the interface you created to the br0 bridge. You might only need to add the "[br0] part, as the previous command will add the interface and your username.

4. Restart your network interfaces:

sudo /etc/init.d/networking restart

5. Create an interface in Vbox settings (GUI). Choose "host interface" and type vbox0 as the interfaces name.

6. Load and test.

There you go, I am at work now and have my VPN running. Post back if you have questions. SAY NO TO VMware, Virtualbox is awesome, and it was just purchased by Sun, so it's going to get awesome..err., lol.

--Knowisdom

[http://forums.virtualbox.org/viewtopic.php?p=16861&sid=8bd0df0aaa83e567ed0610583984fc4c](http://forums.virtualbox.org/viewtopic.php?p=16861&sid=8bd0df0aaa83e567ed0610583984fc4c)

---

### Post by speedsix on 2008-05-30
I've tried that, bridging doesn't work with a wifi connection :(

---

