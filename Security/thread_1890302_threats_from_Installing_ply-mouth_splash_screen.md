---
title: "threats from Installing ply-mouth splash screen"
date: 2011-12-03
forum: Security
---

### Post by drofart on 2011-12-03
Greeting all folks out here,
     I just want to know that like installing app. from .deb pakage is always not safe , like so installing ply-mouth splash theme from tar.gz pakage can creat any security threat ?

Thanku .

---

### Post by OpSecShellshock on 2011-12-03
Of course it can be a threat. You're talking about installing a .deb package from an arbitrary source. Why would you need to do that? If it's only a splash screen theme, why does it need to come in the form of an installer package?

---

### Post by Basher101 on 2011-12-03
there is a splash-image editor in the Software center somewhere...

---

### Post by drofart on 2011-12-03
> **OpSecShellshock said:**
> Of course it can be a threat. You're talking about installing a .deb package from an arbitrary source. Why would you need to do that? If it's only a splash screen theme, why does it need to come in the form of an installer package?
No, it is a .tar.gz which i have to unpack into /lib/plymouth/themes/ folder & then have to install it.Can it make any problem?

---

### Post by drofart on 2011-12-03
> **Basher101 said:**
> there is a splash-image editor in the Software center somewhere...
Than I can make my own!
Thanks.

---

### Post by bodhi.zazen on 2011-12-03
> **drofart said:**
> No, it is a .tar.gz which i have to unpack into /lib/plymouth/themes/ folder & then have to install it.Can it make any problem?

In theory it can be a problem. Anytime you are installing something into the system you are doing so as root and if the file, install script, or make file contains malicious code you are pwned.

---

### Post by drofart on 2011-12-04
> **bodhi.zazen said:**
> In theory it can be a problem. Anytime you are installing something into the system you are doing so as root and if the file, install script, or make file contains malicious code you are pwned.
Thank you friend(it is clear now) , Is there any way to filter and/or detect a malicious code?

Dr. Mrinal.

---

### Post by bodhi.zazen on 2011-12-04
> **drofart said:**
> Thank you friend(it is clear now) , Is there any way to filter and/or detect a malicious code?

Dr. Mrinal.

You would need to examine the source code / script / files and you may or may not be able to detect a problem.

Some people install untrusted software in a VM.

In general, only install things from trusted projects.

---

