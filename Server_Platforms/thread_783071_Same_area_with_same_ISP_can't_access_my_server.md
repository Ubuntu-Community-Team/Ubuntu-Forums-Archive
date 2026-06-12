---
title: "Same area with same ISP can't access my server"
date: 2008-05-05
forum: Server Platforms
---

### Post by ricketick on 2008-05-05
My friend who has the same ISP and lives in the same area as me can not access my server, but several other computers can, including my cellphone.

(The first xxx.xxx are the same on all ips)
Server's address: xxx.xxx.109.xxx
Server's gateway: xxx.xxx.108.1
Server's netmask: 255.255.252.0

Friend's address: xxx.xxx.108.xxx
Friend's gateway: xxx.xxx.108.1
Friend's netmask: 255.255.252.0

Could it be a "subnet" issue? An ambiguity problem since we share the same ISP and/or gateway? Also, why am I using the same gateway as him? Shouldn't my gateway be xxx.xxx.109.1? I've tried changing gateway but the network won't run on 108.1.

---

### Post by yogensha on 2008-05-06
This is actually very common on ISP networks.  For security reasons, ISPs like to prevent users in the same broadcast domain (often the same thing as the same subnet) from communicating with each other.  This prevents people from being able to browse open windows shares that people may have inadvertently left open.

Both of your subnet masks are 255.255.252.0, which means that .108.xxx and .109.xxx (as well as .110 and .111) are in the same subnet.  That's why you have the same gateway, and probably why you can't talk to each other.

In my experience, the ISP only filters broadcast traffic, which is usually sufficient to break connectivity between clients because it causes ARP resolution to fail.  You can try and build static ARP entries on both machines and see if that helps.  'man arp' on your server for details.  Windows has an arp command as well if the other end is on windows.

---

### Post by DrNick on 2008-05-07
> **yogensha said:**
> This is actually very common on ISP networks.  For security reasons, ISPs like to prevent users in the same broadcast domain (often the same thing as the same subnet) from communicating with each other.  This prevents people from being able to browse open windows shares that people may have inadvertently left open.

Both of your subnet masks are 255.255.252.0, which means that .108.xxx and .109.xxx (as well as .110 and .111) are in the same subnet.  That's why you have the same gateway, and probably why you can't talk to each other.

In my experience, the ISP only filters broadcast traffic, which is usually sufficient to break connectivity between clients because it causes ARP resolution to fail.  You can try and build static ARP entries on both machines and see if that helps.  'man arp' on your server for details.  Windows has an arp command as well if the other end is on windows.

I agree 100%, I'm sure this is probably what your problem is.

---

### Post by coloradocolin on 2009-11-21
I know this is an old thread, but I am dealing with this exact same problem and I would love to find a workaround. I checked out the man page on ARP but its over my head. Can anybody out there help me figure out this issue?

---

