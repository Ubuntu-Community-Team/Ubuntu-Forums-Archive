---
title: "Error on PXE Boot with LTSP on Ubuntu 8.04 with Scovery XS ThinClient"
date: 2009-01-28
forum: Server Platforms
---

### Post by tomcon on 2009-01-28
Hello,

I'm working part time as system-administrator for a small ngo that is educating young people from a social difficult background. We aquired a new project and need to setup a new classroom with ~ 10 computers.

Since we don't have a big budget I was able to convince my colleques to give Ubuntu with LTSP a chance - they agreed :-)

I've setup another Ubuntu Server 8.04 running LTSP (recent version). The Server is working and I can successfully login to the LTSP-Server when booting with PXE-Boot from some machines (IBM Laptops).

Unfortunately I can't PXE-Boot from our ThinClients we bought were cheap (Fujitsu Siemens Scovery XS, Pentium III, 900Mhz, 256 MB Ram, No HDS).

The ThinClients are getting an IP from the LTSP-Server but then the boot-process is interrupted with the error message:

"BUG: Int 6: CR2 00000000" error
[...]
followed by a "Stack" error

Doing some research I think it has something todo with the kernel versions I'm using on the LTSP 

[LIST]
[*]2.6.24-19-generic
[*]2.6.24-22-generic
[*]2.6.24-23-generic
[/LIST]

Maybe these kernel version doesn't work with older hardware when booting with PXE? Strangely it works when booting from "newer hardware" like an IBM X31.

Question:
Do you have an idea how to tell LTSP to use a kernel that older hardware like my Scovery XS clients are able to pxe-boot from?

Any hints would be great, since I really want to show that Linux can be used in our organization. :KS

Kind regards from Berlin

- Tom

---

