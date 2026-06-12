---
title: "[SOLVED] Packages needed for samba printer sharing"
date: 2008-12-03
forum: Server Platforms
---

### Post by batfastad on 2008-12-03
Hi everyone

I've been using Ubuntu Server 8.04 for about 6 months as a NAS device with Samba.

I'm now looking to add printer sharing into my Samba configuration so I guess I need to install cups, but what's the package name?

Are there any other packages I would need as well?

Thanks, B

---

### Post by chongzi35 on 2008-12-03
High temperature **[cast steel valves](http://www.valvesupplier.net/cast-steel-gate-valves.htm)** are designed and manufactured to provide reliable shutoff and smooth operation under a high temperature environment. The specified bolt torque is maintained during valve assembly, using specialized torque limiting equipment, to prevent valves from leaking between the valve body and bonnet and providing reliable long term operation once the [cast steel valve]("http://www.valvesupplier.net/cast-steel-gate-valves.htm") is put into service.

---

### Post by batfastad on 2008-12-09
Anyone?

At the moment our printers are shared from a Windows Server 2003 machine, but I'd love to move this over to Ubuntu as well. My goal is to phase out our Windows servers, and that is in sight!

Cheers, B

---

### Post by pdtpatrick on 2008-12-09
if i recall right .. you should just be able to use:

sudo apt-get install cupsd or cups 

or better yet search and see what cups packages are available:

sudo apt-cache search cups

one you install, samba should have a predefined section already for your printers, so you can use their sample.

---

### Post by CarolinaGuy on 2008-12-09
see

[https://help.ubuntu.com/8.10/serverguide/C/cups.html](https://help.ubuntu.com/8.10/serverguide/C/cups.html)

CarolinaGuy

---

### Post by batfastad on 2008-12-10
Aha, perfect!
Yes there's already a section in my smb.conf.default which I will use to configure my printer sharing

Thanks!

---

