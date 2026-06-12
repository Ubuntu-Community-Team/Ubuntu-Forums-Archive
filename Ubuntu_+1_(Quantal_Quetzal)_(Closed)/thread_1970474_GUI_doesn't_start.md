---
title: "GUI doesn't start"
date: 2012-05-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Sworddragon on 2012-05-01
After the updates from today (~100) lxdm doesn't start anymore. I tried to use gdm but the same problem happens. /var/log/Xorg.0.log says:

```
[   605.117] [dix] Could not init font path element built-ins, removing from list!
[   605.117] 
Fatal server error:
[   605.117] could not open default font 'fixed'
[   605.117] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   605.117] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   605.117] 
[   605.850]  ddxSigGiveUp: Closing log
[   605.850] Server terminated with error (1). Closing log file.
```

I have now downgraded to 12.04 and all is working fine. Has somebody an idea which package triggered this problem?

---

### Post by Harry33 on 2012-05-01
> **Sworddragon said:**
> After the updates from today (~100) lxdm doesn't start anymore. I tried to use gdm but the same problem happens. /var/log/Xorg.0.log says:

```
[   605.117] [dix] Could not init font path element built-ins, removing from list!
[   605.117] 
Fatal server error:
[   605.117] could not open default font 'fixed'
[   605.117] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   605.117] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   605.117] 
[   605.850]  ddxSigGiveUp: Closing log
[   605.850] Server terminated with error (1). Closing log file.
```I have now downgraded to 12.04 and all is working fine. Has somebody an idea which package triggered this problem?

This has already been discussed here:
[http://ubuntuforums.org/showthread.php?t=1965997&page=11](http://ubuntuforums.org/showthread.php?t=1965997&page=11)

You have to downgrade the package libxfont1 back to the precise version 1.4.4-1

---

### Post by paul_in_london on 2012-05-01
> **Harry33 said:**
> This has already been discussed here:
[http://ubuntuforums.org/showthread.php?t=1965997&page=11](http://ubuntuforums.org/showthread.php?t=1965997&page=11)

You have to downgrade the package libxfont1 back to the precise version 1.4.4-1

Yes, I've been bitten by this too. Took the opportunity to upgrade my remaining OO install to PP and I'm using that until the current QQ breakage is fixed.

---

### Post by Sworddragon on 2012-05-01
I have just pinned now libxfont1 to Ubuntu 12.04. So I can install all other packages from Quantal.

---

### Post by Harry33 on 2012-05-01
That will be fixed, but it may take a while.
Jeremy Bicha has made a bug report (#992745) about this issue:

[https://bugs.launchpad.net/ubuntu/+source/libxfont/+bug/992745](https://bugs.launchpad.net/ubuntu/+source/libxfont/+bug/992745)

---

