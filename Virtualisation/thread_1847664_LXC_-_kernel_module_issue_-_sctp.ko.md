---
title: "LXC - kernel module issue - sctp.ko"
date: 2011-09-21
forum: Virtualisation
---

### Post by ddav on 2011-09-21
Hi,

I have CentOS 5.6 running using LXC within Ubuntu.

Kernel: 2.6.38-11-generic

All is working well but I have run into a problem when trying to load the sctp kernel module.

I have sctp.ko loaded from the host and I have the lksctp tools installed on CentOS. (version 1.0.6).

When I try to create an SCTP socket (IPv4) I get the error code 97 - address family not supported by this protocol.

I can create an IPv6 SCTP socket but future connects, binds etc. fail.

Also when I run netstat within CentOS I get the following:

netstat: no support for `AF INET (sctp)' on this system.

From a search on the web this error is due to the fact the SCTP kernel object is not installed. I have confirmed it is installed via lsmod.

I have tried copying the relative kernel files to my CentOS installation and doing the modproble from there rather than from the host but without success.

Has anyone had any similar issues with Kernel objects not getting recognized within the LXC instance.

Any help would be greatly appreciated.

Thanks in advance,
Dave.

---

