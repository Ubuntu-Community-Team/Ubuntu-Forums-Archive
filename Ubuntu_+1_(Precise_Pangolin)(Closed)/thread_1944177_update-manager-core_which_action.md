---
title: "update-manager-core which action?"
date: 2012-03-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cryptotheslow on 2012-03-20
So just doing the routine apt-get update / upgrade routine and got this question:

```
Setting up update-manager-core (1:0.156.9) ...

Configuration file `/etc/update-manager/release-upgrades'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** release-upgrades (Y/I/N/O/D/Z) [default=N] ? 

```

Taking the Difference option gives this:
```
--- /etc/update-manager/release-upgrades        2012-03-16 00:12:37.000942079 +0000
+++ /etc/update-manager/release-upgrades.dpkg-new       2012-03-20 14:10:23.000000000 +0000
@@ -14,4 +14,4 @@
 #           used if the currently-running release is not itself an LTS
 #           release, since in that case the upgrader won't be able to
 #           determine if a newer release is available.
-prompt=never
+Prompt=lts
```

Is this coming up because I disabled all the update notification options in Update Manager?

---

### Post by bluenova on 2012-03-21
Yes

Looks like the default is to now prompt for LTS releases. When I see config file changes I find it prudent to accept the new files then change it to what I want through the GUI.

---

### Post by cryptotheslow on 2012-03-21
Thanks. :)

---

