---
title: "HOWTO: Restore Simulink and Xilinx functionality after upgrading 10.10 -&gt; 11.04"
date: 2011-08-11
forum: Tutorials
---

### Post by pjd99 on 2011-08-11
Tested with Matlab 2010b and Xilinx ISE 13.1, on Ubuntu 11.04 Natty Narwhal (x86_64).


After a distribution upgrade from Maverick to Natty, Simulink loses its ability to simulate using Xilinx blocks, and Xilinx system generator fails during compilation.

Firstly, to get Simulink running properly again you need to symlink gcc to the previous version:
```

sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-4.4 /usr/bin/gcc

```&#8298;
**&#8298;EDIT: N.B. Link back to gcc-4.5 before compiling any kernel modules and/or upgrades (e.g. nVidia dkms modules, VMWare modules, compat-wireless etc), otherwise you can end up with a less-than-usable system. **
&#8298;
&#8298;
Next, to get system generator compiling again you need to back up the saferun scripts and modify them. You may need to use locate to find the scripts if not using the default install directory, or are on a 32-bit system.
```

locate saferun
sudo cp /opt/Xilinx/13.1/ISE_DS/ISE/sysgen/bin/lin/saferun /opt/Xilinx/13.1/ISE_DS/ISE/sysgen/bin/lin/saferun.bak
sudo cp /opt/Xilinx/13.1/ISE_DS/ISE/sysgen/bin/lin64/saferun /opt/Xilinx/13.1/ISE_DS/ISE/sysgen/bin/lin64/saferun.bak

```Open the first saferun script:
```

gksu gedit /opt/Xilinx/13.1/ISE_DS/ISE/sysgen/bin/lin/saferun

```And cut it down so only the first line and last three lines are still present:
```

#!/bin/sh
# Now run the executable
cmd=`readlink -f $0`
$cmd.bin "$@"

```Repeat for the remaining script:
```

gksu gedit /opt/Xilinx/13.1/ISE_DS/ISE/sysgen/bin/lin64/saferun

```&#8298;
&#8298;
&#8298;
&#8298;
Another possible solution to the sysgen problem may be to change the interpreter used for sh (use bash instead of dash). I have not tested this personally.

```

sudo ls -la /bin/sh
          lrwxrwxrwx 1 root root 4 2011-08-10 12:28 [COLOR=Blue]/bin/sh[/COLOR] -> dash

sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh

```Attached is a short script for launching sysgen (works for default x64 install, modify for your system) for use with a menu launcher.

Any other Natty Matlab/Simulink/Xilinx tips are appreciated.

---

### Post by dang2327 on 2012-03-07
Thanks a lot. I have been trying to figure this out since the longest time. I did the saferun trick last year to get it to work, but gcc 4.6 recently acted up and gave me many issues.

---

### Post by dang2327 on 2012-03-07
After changing to gcc 4.4, now I'm getting another gcc error:
```
as: unrecognized option '-Qy'
```
Do you have any idea why?

Thanks and regards,
Danh.

---

