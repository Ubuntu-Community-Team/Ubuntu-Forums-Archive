---
title: "Public IP on Host, Private IP on Guest"
date: 2015-01-27
forum: Virtualisation
---

### Post by Jesse_Turner on 2015-01-27
Is there a way to set up a guest on my private network with an IP when the host computer uses one of our public IP addresses?  I have Ubuntu 12.04 LTS Server w/ Desktop overlay as the host machine which has the public IP address and I have VMware running Ubuntu 12.04 LTS server for Owncloud installation which I need to use a private IP address so it says behind our firewall. Please help!

Thank You

---

### Post by TheFu on 2015-01-27
Yes. Yes, there is.

However, it would be smarter to have the guest on the public IP and the host on the private network from a security perspective.
Also, it is smarter to use different physical connections for the hostOS and guest.  Protect the hostOS at all costs.

Normal linux bridging handles this.  Do it with KVM VMs.

Can't say anything about VMware - you didn't say which VMware product.  ESXi can definitely do it - don't know how, but folks use their fancy virtual networking for everything.

---

### Post by Jesse_Turner on 2015-01-27
I am using VMware Workstation 11.  Owncloud is going to sync with our users files on their computer so our Management would like the guest OS to be behind our firewall. Say our host OS has a public IP address of 50.60.70.80 and our guest OS has an ip of 192.168.10.10. Would just port forwarding be used to tell the public IP to forward all request to the guest OS so the are able to log into owncloud or do you have a better suggestion?

Thank You

---

### Post by TheFu on 2015-01-27
Better suggestions? Ok.

a) Use a router to manage the public IP. That is a separate box, not a general purpose OS that also runs VMs. If the beachhead is lost, every VM is gone too. Don't risk it. Have the router only open the 1 port you need for the VPN to work. Nothing else.
b) Don't connect any general purpose OS directly to the internet. This is a standard network security practice.
c) Don't use a desktop virtualization tool for server virtualization. Consider ESXi, Xen, KVM or even that MS VM server option.
d) Only use Owncloud with a real VPN over the internet.  Don't know, but may be worth looking at Seafile. I've never used either. Both need to be protected by a VPN if any business proprietary data is shared.

I can post linux bridge configs for the original problem that work with multiple ethernet ports so the guest OS and hostOS aren't on the same port or subnet.

---

