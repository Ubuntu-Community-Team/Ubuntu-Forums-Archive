---
title: "How may I get non-PAE version of ubuntu witj Linux kernel 3.16 or latest."
date: 2017-08-29
forum: Ubuntu, Linux and OS Chat
---

### Post by helloami on 2017-08-29
Dear folks,
 
How can I download latest Ubuntu version with non-PAE kernel 3.16 or more than it? We are using 1GHz dual core **DMP Vortex86DX3** processor.
 
Please suggest for DMP vortex processor. We don't have forcepae flag support.
 
Thanks,
helloami

---

### Post by QIII on 2017-08-29
Since that appears to be a 32bit processor intended for embedded systems, I would suggest having a look [here]("https://help.ubuntu.com/community/Installation/MinimalCD") for the minimal installation image.  16.04 is the most recent Long Term Support version.  The kernel version is 4.4.

---

### Post by sudodus on 2017-08-29
If I understand correctly, there is 'almost' no officially supported non-pae Ubuntu version. The last version with a non-pae kernel was Ubuntu 12.04 LTS (and 12.04.1 LTS with the precise kernel, but not 12.04.5 LTS because it has the trusty kernel), and there is no longer any free support. There is paid support available: 'Extended security maintenance for Ubuntu Advantage customers'.

See this link, [www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)

You might find a custom non-pae kernel for newer versions of Ubuntu via the internet.

[hr][/hr]
The related linux distro 'Debian Jessie' comes with the kernel 3.16 and there is a non-pae version. The new version 'Debian Stretch' is released without a non-pae version, but *Jessie is still supported*.

See this link, [https://wiki.debian.org/LTS](https://wiki.debian.org/LTS)

There are also versions with a non-pae kernel from several linux distros based on Debian Jessie.

---

