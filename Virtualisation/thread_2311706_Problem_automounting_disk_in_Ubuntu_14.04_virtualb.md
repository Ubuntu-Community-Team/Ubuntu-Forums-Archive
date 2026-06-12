---
title: "Problem automounting disk in Ubuntu 14.04 virtualbox guest and starting VPN"
date: 2016-01-29
forum: Virtualisation
---

### Post by James Wilde on 2016-01-29
I'm running 14.04 as a guest on a machine running OSX 10.9

When my vm has started I want to mount the shared folder on the host as a folder called host in my home directory.  If I run the following command in a terminal window, I get the shared folder appearing in the right place:

sudo mount -t vboxsf -o rw,uid=1001,gid=1001 james ~/host

I have put the same command, minus the initial sudo in a file called mounthost in /etc/init.d.  This file is owned by root:root, and has mode 777.  From /etc/init.d I have made symlinks to it in all /etc/rcn.d directories except /etc/rc6.d.  The symlink was called K71mounthost.  Nothing happened.  I could not see any files in my home host directory.  Then I realised that the K stands for Kill, and I should have S for Start, so I changed the name to S71mounthost.  Still nothing happened.  I opened a terminal and typed in the line above and my disk was mounted.

So what am I doing wrong?

The other problem concerns starting a VPN automatically.  If I enter the following command in a terminal it stops part way through the process.

sudo openvpn --config /etc/openvpn/Los\ Angeles.ovpn

The lines immediately before its stopping are:

Fri Jan 29 16:17:05 2016 TUN/TAP device tun0 opened
Fri Jan 29 16:17:05 2016 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Fri Jan 29 16:17:05 2016 /sbin/ip link set dev tun0 up mtu 1500
Fri Jan 29 16:17:05 2016 /sbin/ip addr add dev tun0 10.10.20.66/26 broadcast 10.10.20.127
Fri Jan 29 16:17:05 2016 Initialization Sequence Completed

But no VPN open and I can't start it from the network icon.  In fact the only way I can start it is from the network icon when no previous attempt has been made to start it.  (Before anybody asks, I have my id and password in a file and refer to that file in the LA.ovpn file on the line for auth-user-pass line.

So how do I start this automagically on boot-up?

TIA

---

### Post by jim_deadlock on 2016-01-29
What I do to mount a shared folder in VB is:

1. Make sure Guest Additions are installed in the guest (important).
2. On the host, add your user to the vboxusers group, eg 'sudo adduser jim vboxusers'
3. Start your VM, go to Shared Folder Settings (icon bottom of window), create new folder with Folder path = path on the host, Folder name = anything, Auto-mount CHECKED, Make Permanent CHECKED
4. Restart VM and folder should appear

Re the VPN, if you're saying you just can't get the VPN service to run properly on your Ubuntu guest then that's not really a Virtualbox problem so maybe start a new thread in the networking forum.

---

### Post by Bucky Ball on 2016-01-30
*Thread moved to **Virtualisation**.*

---

### Post by James Wilde on 2016-01-30
> **jim_deadlock said:**
> What I do to mount a shared folder in VB is:

1. Make sure Guest Additions are installed in the guest (important).
Done on installation
> **jim_deadlock said:**
> 2. On the host, add your user to the vboxusers group, eg 'sudo adduser jim vboxusers'
There is no vboxusers group on the host.  There is no vboxanything group.
> **jim_deadlock said:**
> 3. Start your VM, go to Shared Folder Settings (icon bottom of window), create new folder with Folder path = path on the host, Folder name = anything, Auto-mount CHECKED, Make Permanent CHECKED
Had already done this on installation.
> **jim_deadlock said:**
> 4. Restart VM and folder should appear
Nope.  I need to run the sudo command in my OP to get the shared folder loaded into a directory in my home directory.  There is an entry /media/sf_james but this is owned by root:vboxsf, and I can't change this or the mode of the directory, not even with sudo.

> **jim_deadlock said:**
> Re the VPN, if you're saying you just can't get the VPN service to run properly on your Ubuntu guest then that's not really a Virtualbox problem so maybe start a new thread in the networking forum.
OK, thanks, I'll try there or on the Virtualbox.org forum.

---

### Post by jim_deadlock on 2016-01-30
I can't remember if VB creates the vboxusers group during installation, maybe not, but in any case you definitely need to create the vboxusers group on the host and add your user to it. I don't know how to do that on a Mac but on Ubuntu it would be:

```
sudo addgroup vboxusers
sudo adduser jim vboxusers
```

If that still doesn't work it might be worth reinstalling Guest Additions because it can be a bit flakey.

If you're having trouble accessing the VPN service from outside the VM once it's running then you may need to mess around with port forwarding, but just getting the service to start is a straightforward Ubuntu networking issue.

---

