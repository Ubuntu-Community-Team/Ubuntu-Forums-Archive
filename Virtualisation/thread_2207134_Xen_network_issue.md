---
title: "Xen network issue"
date: 2014-02-22
forum: Virtualisation
---

### Post by QR72e on 2014-02-22
Hi all,

ususally I seem to find solutions to my issues by means of google or in these forums, but no luck this time and so I am posting this thread.

I have installed Ubuntu server 13.04 and installed the Xen Hypervisor, XCP-XAPI and QEMU-Common packages.
Then I adjusted grub to always boot into the hypervisor.

From this moment on my network card only picks up an IP address form the DHCP server, but I can not access any other machine on my LAN nor on the Internet. Pinging the own IP address works, pinging the default gateway or any other machine on the network results in "Destination Host Unreachable".

Restarting the machine and booting in "standard" Ubuntu instead of Xen 4.3, by selecting anonther boot option in Grub and not changing anything else the network seems to work just fine.

I have checked IPtables, routing, ifconfig, syslog, but no hint to what may cause this issue.

There are probably some people in here that have much more experience than myself when it comes to Xen and I hope to receive some help from you. I assume that it is an issue within Xen, as it is working when booting without it.

Any hint or advise is highly appreciated.

//QR72e

---

### Post by TheFu on 2014-02-22
13.04 support [ended last month]("http://www.ubuntu.com/support"). 
Either wait for 14.04 to start or drop back to 12.04.  For this stuff, always, always, always use an LTS release .... er ... unless there is a very specific support issue.  Newer != Better.  We need to be on supported releases, ALWAYS.

About the networking ... did you setup a static IP?
Did you setup the bridged network so the VMs can connect?

---

### Post by QR72e on 2014-02-22
Sorry for wrong statement in original post, I am on 13.10. And I am just doing some testing. Production system will be 14.04.

I have tried both, static an dhcp. Same error.
The bridged network would be the next step. First I wanted to get the physical card to function.

---

### Post by TheFu on 2014-02-22
Could you please post the output from all those commands here? The output from the other requested questions would be good too.  You might be an expert at this stuff, but we can't assume a trivial mistake didn't happen. To get started, 

```
cat /etc/network/interfaces
cat /etc/hosts
ifconfig
route
sudo iptables -L
```

Please use the **Adv Reply** and "code" tags or it is just too hard to read.

---

### Post by QR72e on 2014-02-22
Let me try to reply as proper as possible. The issue is that I can not copy and paste from the machine, as its network is not working.

cat /etc/network/interfaces
Only default entries here:
```

auto lo
iface lo inet loopback

auto p128p1
iface p128p1 dhcp
```

cat /etc/hosts
Only default entries here and I skip the IPv6 part:
```

127.0.0.1     localhost
127.0.0.1     server-name
```

ifconfig
This is the toughest one to re-write without copy/paste:

It is listing the following network cards:
brp128p1 - not sure where this one is coming from.
eth1 - additional network card, currently not used nor configured.
lo - loopback 
p128p1 - main network card
xenbr1 - Xen bridge, not configured yet.
```

p128p1 Link encap:Ethernet
       inet addr:10.0.1.72  Bcast:10.0.1.255  Mask:255.255.255.0
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

no collision, but RX and TX traffic
```

route
```

Destination      Gateway      Genmask        Flags Metric Ref   Use Iface
default          10.0.1.1     0.0.0.0        UG    0      0       0 p128p1
10.0.1.0         *            255.255.255.0  U     0      0       0 p128p1
```

sudo iptables -L
Nothing defined. Just showing the following three headers, but no entries:
Chain INPUT (policy ACCEPT)
Chain FORWARD (policy ACCEPT)
Chain OUTPUT (policy ACCEPT)


Thanks for helping!

---

### Post by TheFu on 2014-02-22
Thanks for the info.

I'd use a flash USB drive to store the command outputs, transfer them to a working system and post.
Never heard of p128p1 - could that be the issue?  Is there a driver loaded that is connected to that device name?

Is there a DHCP server on the network?
Does 10.0.1.72 make sense for your subnet?

I'd feel better if you were able to use eth[0-9].

---

### Post by QR72e on 2014-02-22
Thanks for the hint with the USB drive. Great idea!

Yes, there is a DHCP server in the network and that is where the 10.0.1.72 is coming from. It does make sense. 

I don't know why the system is calling it "p128p1" and not "eth0". How can I change it?
Never the less all of this is working once I boot in the normal Ubuntu kernel.

Also I got it working when I comment out the "xend_start" and the "xend_stop" lines in /etc/init.d/xen as seen in several tutorials. However then Xen itself is not working anymore but throwing me errors, if I do that.

Now I am trying with a daily build of 14.04...

---

### Post by TheFu on 2014-02-22
I migrated off Xen about 2 yrs ago over issues like this and the problems with kernel updates. Not being able to boot the VM host after a kernel update is a problem. Have been happily using KVM+libvirt ever since then.  Also migrated off virtualbox and ESXi to KVM. Happy with leaving all those for KVM.  Never had any issues with booting post-kernel update under KVM. Not once.

We can't rename devices - it isn't about the name, it is about the driver being used and any name that isn't eth? concerns me.  /etc/udev/ is where those settings are usually made for network devices. When I was running Xen, the ethernet driver was still eth0 and eth1.  Just sayin'.

I guess Xen was selected for a good reason. I wish you luck.

---

