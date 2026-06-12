---
title: "Virtualbox Lubuntu shared clipboard"
date: 2015-08-16
forum: Virtualisation
---

### Post by Richard_Romick on 2015-08-16
I am using Virtualbox to run Lubuntu 64-bit.  My host machine is Ubuntu 64-bit.

I have installed guest additions, but the bi-directional shared clipboard does not seem to be working.  Do I have to do anything special to get it working under Linux?  Thank you for your time.

I quickly found out that Virtualbox additions were in fact not installed, but rather the installer errored out.

The make utility was not found. If the following module compilation fails then
this could be the reason and you should try installing it.

The gcc utility was not found. If the following module compilation fails then
this could be the reason and you should try installing it.

Building the main Guest Additions module ...fail!

Does anyone know the answer to this problem?

---

### Post by Richard_Romick on 2015-08-17
I'm glad nobody responded to this because it was my own fault.  I needed to install all the updates on my guest OS, then install build-essential.  After that, the guest additions installed.

---

