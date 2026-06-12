---
title: "bulletin is not released for security patch"
date: 2020-01-31
forum: Security
---

### Post by kondannangi163 on 2020-01-31
hi,
  I have executed the command** apt list --upgradable | grep security **to retrieve all the security patches available from ubuntu.
 I retrieved a list of the patches applicable to my machine.
but the issue is that i am not able to find security bulletins  in usn.ubuntu.com for some of the  patches that I retrieved from command.

I use bulletins often to check what type of  bug that i am fixing .
if there is no security bulletien released for a patch then how can we treat it as security patch.

I checked these repos and found out that so many patches available here are not having bulletien
[http://archive.ubuntu.com/ubuntu/dists/bionic-security/](http://archive.ubuntu.com/ubuntu/dists/bionic-security/)
[http://security.ubuntu.com/ubuntu/dists/bionic-security/](http://security.ubuntu.com/ubuntu/dists/bionic-security/)

Even though if we think that ubuntu product bulletin for only critical security patches then there should not be bulletins for non critical patches.

Please let me know why some patches are not having bulletins.

---

### Post by deadflowr on 2020-01-31
As far as I know or can tell security notices are only for affected packages and not for any required dependencies.

---

### Post by kondannangi163 on 2020-02-05
Wlll **apt list --upgradable | grep security  **List out the dependency pathces?


security.ubuntu.com/ubuntu/pool/main/a/amd64-microcode/amd64-microcode_3.20191021.1+really3.20181128.1~ubuntu0.18.04.1_amd64.deb
is the debian package that i am getting under this command but not able to find the bulletien.

Please let know why i am not getting the buletin for this package.

---

