---
title: "DV6t Xorg error in modesetting_drv"
date: 2012-09-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by erikschmitz on 2012-09-13
I upgraded to the 12.10 beta tonight and am getting a bunch of erratic behavior that I believe is related to this laptops AMD 6770M and Intel 3000 graphics. 

1. Sometimes I get kernel panic
2. Other times I get stuck in an x session displaying services that are starting and stopping
3. yet other times, I get stuck in "low grapcis mode"

My Xorg.0.log consistently shows:
```

[     8.192] (EE) 
[     8.192] (EE) Backtrace:
[     8.192] (EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f11c4b759b6]
[     8.192] (EE) 1: /usr/bin/X (0x7f11c49cd000+0x1ac7e9) [0x7f11c4b797e9]
[     8.192] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f11c3cf3000+0xfcb0) [0x7f11c3d02cb0]
[     8.192] (EE) 3: /usr/bin/X (xf86SetScrnInfoModes+0x275) [0x7f11c4a977e5]
[     8.192] (EE) 4: /usr/bin/X (xf86InitialConfiguration+0x15b8) [0x7f11c4a9b198]
[     8.192] (EE) 5: /usr/lib/xorg/modules/drivers/modesetting_drv.so (0x7f11c0eb4000+0x68e1) [0x7f11c0eba8e1]
[     8.192] (EE) 6: /usr/lib/xorg/modules/drivers/modesetting_drv.so (0x7f11c0eb4000+0x4ad2) [0x7f11c0eb8ad2]
[     8.192] (EE) 7: /usr/bin/X (InitOutput+0xc3e) [0x7f11c4a64c2e]
[     8.193] (EE) 8: /usr/bin/X (0x7f11c49cd000+0x44386) [0x7f11c4a11386]
[     8.193] (EE) 9: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f11c297a76d]
[     8.193] (EE) 10: /usr/bin/X (0x7f11c49cd000+0x448ad) [0x7f11c4a118ad]
[     8.193] (EE) 
[     8.193] (EE) Segmentation fault at address 0x0
[     8.193] 
Fatal server error:
[     8.193] Caught signal 11 (Segmentation fault). Server aborting
[     8.193] 
[     8.193] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[     8.193] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[     8.193] (EE) 
[     8.195] Server terminated with error (1). Closing log file.

```

If I blacklist i915 and radeon modules, then boot, drop to a terminal and
```

sudo -s
modprobe radeon
modprobe i915
modprobe -r psmouse
modprobe psmouse
rm ~/.Xauthority
start lightdm

```

then I can get a working session. Really weird. guessing its in the new 3.5 kernel? everything worked dandy in 12.04.

---

