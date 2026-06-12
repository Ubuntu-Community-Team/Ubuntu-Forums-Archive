---
title: "Centos and Ubuntu different behaviour"
date: 2012-01-09
forum: Server Platforms
---

### Post by deepakdeshp on 2012-01-09
I have installed Ubuntu server 10.04 , backed it up using Clonezilla and restored it on a different machine with a different hardware, and it works without any problem.

I tried the same thing with CentOS 5.6 but it doesnt work. Can anybody tell the reason and suggest a work around for CentOS?

---

### Post by richardjh on 2012-01-20
When you say it doesn't work, that doesn't really help to get you an answer :)
Do you get any errors, does it get to grub, does grub find and boot the kernel, do the disks get mounted...

Possible reason for problem:
I suspect the problem is that CentOS you have cloned does not contain the required drivers for some critical bit of hardware on the new server.

Possible solution:
You can try [Mondo Rescue]("http://www.mondorescue.org/"), I used to use that for cloning CentOS webservers to move them to newer hardware.

---

