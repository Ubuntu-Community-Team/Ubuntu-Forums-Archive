---
title: "MyUnity bug"
date: 2012-09-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by chrissy.millichamp on 2012-09-03
while opening MyUnity I get this error message. This application has raised an unexpected error and must be abort, [6] type mismatch: wanted integer, got Null instead. Mlauncher.?.0.
So whats the fix on this?

---

### Post by effenberg0x0 on 2012-09-03
> **chrissy.millichamp said:**
> while opening MyUnity I get this error message. This application has raised an unexpected error and must be abort, [6] type mismatch: wanted integer, got Null instead. Mlauncher.?.0.
So whats the fix on this?

Well, you can change the function return type from int to void, #define NULL 0 or return 0 instead of NULL.

Now seriously: I'm not seeing this problem here. If your QQ is up-to-date to default QQ repos, there's nothing to do but add to the existing bug reports and wait for a fix. Google the exact error message you posted and you'll find bug reports with the exact same message. It's likely a problem with gambas implementation in Ubuntu or in MyUnity source code. 

Meanwhile, some of the stuff in MyUnity can be done using UnSettings. All of it (and more) can be done using compizconfig-settings-manager (both available in Ubuntu Software Center).r

Regards,
Effenberg

---

### Post by mc4man on 2012-09-03
Take your pick, likely related
[https://bugs.launchpad.net/ubuntu/+source/myunity/+bug/996930](https://bugs.launchpad.net/ubuntu/+source/myunity/+bug/996930)
[https://bugs.launchpad.net/ubuntu/+source/myunity/+bug/1041417](https://bugs.launchpad.net/ubuntu/+source/myunity/+bug/1041417)
what can you do?, not much, maybe directly fixed or maybe it'll just start working at some point.

(Ubuntu is very consistent with inconsistent behavior...

---

### Post by philinux on 2012-09-24
Seems like it's now gone for good.

[http://www.ubuntuupdates.org/package/core/quantal/universe/base/myunity](http://www.ubuntuupdates.org/package/core/quantal/universe/base/myunity)

[https://launchpad.net/ubuntu/quantal/amd64/myunity](https://launchpad.net/ubuntu/quantal/amd64/myunity)

---

### Post by jbicha on 2012-09-24
More precisely, gone until it's fixed to work with current Unity.

---

