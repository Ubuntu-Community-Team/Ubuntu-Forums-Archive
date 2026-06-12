---
title: "Is it me?"
date: 2020-07-15
forum: Ubuntu Development Version
---

### Post by IanW on 2020-07-15
Updates seem to have stalled due to repository errors as below:-

```
http://gb.archive.ubuntu.com/ubuntu/dists/groovy-backports/main/binary-amd64/Packages.xz
File has unexpected size (64 != 1276). Mirror sync in progress? [IP: 91.189.88.142 80]
Hashes of expected file:
 - Filesize:1276 [weak]
 - SHA256:237d7dba1b7e6d762f7c74cf65facfa0836d51612e3c08bfea927be5d8051910
 - SHA1:7c72e565eb858fd478fc502b3fc218bb155aafbd [weak]
 - MD5Sum:774f8478661e5a9a0a244346f11fdb7e [weak]
Release file created at: Sat, 02 May 2020 12:22:48 +0000


http://gb.archive.ubuntu.com/ubuntu/dists/groovy-backports/main/binary-i386/Packages.xz


http://gb.archive.ubuntu.com/ubuntu/dists/groovy-backports/main/i18n/Translation-en.xz


http://security.ubuntu.com/ubuntu/dists/groovy-security/main/binary-amd64/Packages.xz
File has unexpected size (64 != 1276). Mirror sync in progress? [IP: 2001:67c:1562::18 80]
Hashes of expected file:
 - Filesize:1276 [weak]
 - SHA256:237d7dba1b7e6d762f7c74cf65facfa0836d51612e3c08bfea927be5d8051910
 - SHA1:7c72e565eb858fd478fc502b3fc218bb155aafbd [weak]
 - MD5Sum:774f8478661e5a9a0a244346f11fdb7e [weak]
Release file created at: Sat, 02 May 2020 12:22:48 +0000


http://security.ubuntu.com/ubuntu/dists/groovy-security/main/binary-i386/Packages.xz


http://security.ubuntu.com/ubuntu/dists/groovy-security/main/i18n/Translation-en.xz
```

Have I broken something? Or is it them?

---

### Post by dino99 on 2020-07-16
hey, backports can only exist from u+1; and you have already understood that groovy is the actual u+1 release don't you ? So no need to activate the backport archive

---

### Post by IanW on 2020-07-17
> **dino99 said:**
> hey, backports can only exist from u+1; and you have already understood that groovy is the actual u+1 release don't you ? So no need to activate the backport archive

Thanks. Forgot to disable that when I switched from Focal. :oops:

I also had an issue with the security repo, due to devs changing the distro name in sources from "focal-security" to just "groovy" not "groovy-security".
Running "sudo sed -i 's/focal/groovy/g' /etc/apt/sources.list" didn't account for that.

---

### Post by zika on 2020-07-17
> **IanW said:**
> Thanks. Forgot to disable that when I switched from Focal. :oops:

I also had an issue with the security repo, due to devs changing the distro name in sources from "focal-security" to just "groovy" not "groovy-security".
Running "sudo sed -i 's/focal/groovy/g' /etc/apt/sources.list" didn't account for that.There are both focal and focal-security and all subbranches, as I can see it: security.ubuntu.com ...

---

### Post by zika on 2020-07-17
> **IanW said:**
> Thanks. Forgot to disable that when I switched from Focal. <img src="images/smilies/icon_redface.gif" border="0" alt="" title="Embarassed" smilieid="30" class="inlineimg"><br>
<br>
I also had an issue with the security repo, due to devs changing the distro name in sources from "focal-security" to just "groovy" not "groovy-security".<br>
Running "sudo sed -i 's/focal/groovy/g' /etc/apt/sources.list" didn't account for that.There are both focal and focal-security and all subbranches, as I can see it: [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)
P.S. I missed the point that You're using Kubuntu so... Mea culpa.

---

### Post by IanW on 2020-07-18
> **zika said:**
> There are both focal and focal-security and all subbranches, as I can see it: [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)
P.S. I missed the point that You're using Kubuntu so... Mea culpa.

No biggie, I missed it on my profile. Fixed now.

---

