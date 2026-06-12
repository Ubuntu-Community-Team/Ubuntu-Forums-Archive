---
title: "libvirt ignores dhcp range in default.xml"
date: 2011-01-05
forum: Virtualisation
---

### Post by tavasti on 2011-01-05
I'm trying to change dhcp range in libvirt default network. Idea is to limit dhcp range, since part of addresses are reserved for static ip's.

First I simply edited /etc/libvirt/qemu/networks/default.xml and run 'service libvirt-bin restart'. No change in dnsmasq. Tried killing dnsmask, and libvirt-bin restart, but dnsmasq was not started at all. Tried rebooting whole machine. No change.

After it, I tried 'virsh net-edit default'. Editing goes fine, but virsh net-dumpxml shows nothing changed. 

So few questions arise:

1) who starts dnsmasq, if not libvirs-bin? I cannot find anythign under /etc
   root@sr1:/etc# find . | grep -i dnsmasq
   root@sr1:/etc# find . -type f -print0 | xargs -0 grep -i dnsmasq
   ./insserv.conf:$named           +named +dnsmasq +lwresd +bind9 $network

2) why editing default.xml or virsh net-edit doesn't have any effect?

3) should I report bug?

System is ubuntu 10.04, all packets updated at the of writing this.

Edit: editing /var/lib/libvirt/network/default.xml and rebooting whole machine fixed it for now, but real answers missing

---

### Post by tavasti on 2011-01-05
More problems, libvirt network mangling messes firewall. Ended up to follow this:
[http://www.systemajik.com/blog/manual-networking-for-kvm/](http://www.systemajik.com/blog/manual-networking-for-kvm/)

Instead of dnsmasq I'm using dhcp3-server to avoid conflict of name server and dnsmasq.

---

### Post by tavasti on 2011-03-11
> **tavasti said:**
> More problems, libvirt network mangling messes firewall. Ended up to follow this:
[http://www.systemajik.com/blog/manual-networking-for-kvm/](http://www.systemajik.com/blog/manual-networking-for-kvm/)

Instead of dnsmasq I'm using dhcp3-server to avoid conflict of name server and dnsmasq.
Anyway libvirt messes firewall, so finally I added this to /etc/rc.local

/sbin/iptables -L  | grep -qi shorewall && /sbin/shorewall restart

So if I have shorewall loaded, it gets restart after all booted up.

---

### Post by theparanoidone on 2012-05-17
> **tavasti said:**
> 
Edit: editing /var/lib/libvirt/network/default.xml and rebooting whole machine fixed it for now, but real answers missing

This appears to work for me.

Using 10.04

1) net-edit default ... did NOT work
2) vi /etc/libvirt/qemu/network/default.xml ... did NOT work
3) vi /var/lib/libvirt/network/default.xml ... DID WORK

Took me an hour to find this post....  so I'm already an hour deep as I was stuck on step 1 and 2... probably would have been here another 3 hours without your post.

(Side notes... for general security... it's best to be able to disable all unnecessary services wherever you can... I feel like this a great contribution what you offer here)

Thank you!

---

### Post by konijntjesbroek on 2012-07-26
Make sure to do a net-destroy and net-start this will reload the config.

---

### Post by brunojcm on 2012-08-07
[konijntjesbroek]("http://ubuntuforums.org/member.php?u=1713107") did the trick, you cannot edit a network that is on. The following worked for me:

virsh net-destroy default
virsh net-edit default
virsh net-start default

About the dnsmasq restart, it only worked after a computer restart!! Neither restart libvirt-bin nor network services were able to kill dnsmasq or start it again. Maybe some other virsh command could do that.

---

