---
title: "[SOLVED] [Problem] No network in Virtualbox"
date: 2007-12-04
forum: Virtualisation
---

### Post by gfa on 2007-12-04
SOLVED!!!

*********************************************************

Hi everybody...

I installed VirtualBox in Ubuntu (Gutsy i386) using the official repos (v1.5.0, OSE version) and then installed Windows XP Pro SP2 as guest OS.

After finishing installation, i **can't get any network activity in guest machine** (ping, web, ftp), even when I have enabled a virtual network adapter using NAT and it's recognized in Win right (assigns an IP in the 10.0.2.x range).

I have tried using the repos from virtualbox.org (version 1.5.2, non-OSE) but the problem persists.

I can't use bridged networks because it's a corporate, and is filtered by MAC.

Have two network adapters in the host, wired and wireless (this is using ndiswrapper), but the problem happens when connected in both ways.  I have removed the ndiswrapper driver and tried with only the eth0 if, but still nothing.

Anyone has some idea about it?

Thanks.
gfa


************************************************************
SOLVED!!!

In my case, the solution was "easy"...

I realized that browsing throw static IP addresses in guest was OK.

My problem, I think it is caused because I use a local DNS cache with dnsmasq, so:

- Inside the guest operating system, I setup the network connection manually for the DNS servers.

---

### Post by goyus on 2007-12-04
Hello

I have the same problem, can anyone help us

thanx

---

