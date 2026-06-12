---
title: "Kernel 3.6-rc1 is here"
date: 2012-08-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by paul_in_london on 2012-08-03
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc1-quantal/)

---

### Post by kyleabaker on 2012-08-03
Thanks! Gonna install this first thing when I get home. I'm hoping the 3.5 issues I was seeing are resolved in 3.6.

---

### Post by fyfe54 on 2012-08-03
Seems very snappy and quick on Dell Inspiron 1525.  No issues.  So far....
Using 12.04.

---

### Post by VinDSL on 2012-08-03
> **paul_in_london said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc1-quantal/)
Heh!  I think I'm going too far out on the limb...  :D

CliffsNotes...

```
<snip>

Building initial module for 3.6.0-030600rc1-generic
ERROR (dkms apport): **[COLOR="DarkRed"]kernel package linux-headers-3.6.0-030600rc1-generic is not supported[/COLOR]**
Error! Bad return status for module build on kernel: 3.6.0-030600rc1-generic (i686)
Consult /var/lib/dkms/**[COLOR="DarkRed"]nvidia-current/304.30[/COLOR]**/build/make.log for more information.

<snip>
```

Extra credit reading...

```
[B][COLOR="DarkRed"]DKMS make.log for nvidia-current-304.30 for kernel 3.6.0-030600rc1-generic (i686)
Fri Aug  3 19:54:31 MST 2012[/COLOR][/B]
NVIDIA: calling KBUILD...
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (		\
	echo >&2;							\
	echo >&2 "  ERROR: Kernel configuration is invalid.";		\
	echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
	echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo >&2 ;							\
	/bin/false)
mkdir -p /var/lib/dkms/nvidia-current/304.30/build/.tmp_versions ; rm -f /var/lib/dkms/nvidia-current/304.30/build/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/nvidia-current/304.30/build
  cc -Wp,-MD,/var/lib/dkms/nvidia-current/304.30/build/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.7/include -I/usr/src/linux-headers-3.6.0-030600rc1-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.6.0-030600rc1-generic/include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia-current/304.30/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"304.30\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia-current/304.30/build/.tmp_nv.o /var/lib/dkms/nvidia-current/304.30/build/nv.c
In file included from include/linux/kernel.h:19:0,
                 from include/linux/sched.h:55,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-linux.h:38,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv.c:13:
include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
include/linux/bitops.h:66:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
In file included from /usr/src/linux-headers-3.6.0-030600rc1-generic/arch/x86/include/asm/uaccess.h:584:0,
                 from include/linux/poll.h:14,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-linux.h:97,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv.c:13:
/usr/src/linux-headers-3.6.0-030600rc1-generic/arch/x86/include/asm/uaccess_32.h: In function &#8216;copy_from_user&#8217;:
/usr/src/linux-headers-3.6.0-030600rc1-generic/arch/x86/include/asm/uaccess_32.h:208:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia-current/304.30/build/nv.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.6.0-030600rc1-generic/scripts/recordmcount  "/var/lib/dkms/nvidia-current/304.30/build/nv.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia-current/304.30/build/.nv-acpi.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.7/include -I/usr/src/linux-headers-3.6.0-030600rc1-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.6.0-030600rc1-generic/include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia-current/304.30/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"304.30\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_acpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia-current/304.30/build/.tmp_nv-acpi.o /var/lib/dkms/nvidia-current/304.30/build/nv-acpi.c
In file included from include/linux/kernel.h:19:0,
                 from include/linux/sched.h:55,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-linux.h:38,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-acpi.c:15:
include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
include/linux/bitops.h:66:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
In file included from /usr/src/linux-headers-3.6.0-030600rc1-generic/arch/x86/include/asm/uaccess.h:584:0,
                 from include/linux/poll.h:14,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-linux.h:97,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-acpi.c:15:
/usr/src/linux-headers-3.6.0-030600rc1-generic/arch/x86/include/asm/uaccess_32.h: In function &#8216;copy_from_user&#8217;:
/usr/src/linux-headers-3.6.0-030600rc1-generic/arch/x86/include/asm/uaccess_32.h:208:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
/var/lib/dkms/nvidia-current/304.30/build/nv-acpi.c: In function &#8216;nv_acpi_remove&#8217;:
/var/lib/dkms/nvidia-current/304.30/build/nv-acpi.c:303:9: error: too many arguments to function &#8216;acpi_os_wait_events_complete&#8217;
In file included from include/acpi/acpi.h:63:0,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-linux.h:274,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-acpi.c:15:
include/acpi/acpiosxf.h:208:6: note: declared here
make[3]: *** [/var/lib/dkms/nvidia-current/304.30/build/nv-acpi.o] Error 1
make[2]: *** [_module_/var/lib/dkms/nvidia-current/304.30/build] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2
```


Other than no nVidia X driver running, seems to be working fine. ;)

---

### Post by Harry33 on 2012-08-04
You can get the new nvidia-current from xorg-edgers, with a patch to workk with 3.6 rc1.

---

### Post by VinDSL on 2012-08-04
> **Harry33 said:**
> You can get the new nvidia-current from xorg-edgers, with a patch to workk with 3.6 rc1.
AFAIK, I'm running the latest version...

```
vindsl@Zuul:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.30-0ubuntu1~xedgers~quantal2
  Candidate: 304.30-0ubuntu1~xedgers~quantal2
  Version table:
 *** 304.30-0ubuntu1~xedgers~quantal2 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status
     302.17-0ubuntu2 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/restricted i386 Packages
vindsl@Zuul:~$ 

```

Is there a newer version of nvidia-current that I'm unaware?!?!?

BTW, I saw the patch sitting in the nvidia-current folder.  

Do I have to run the patch against nv-acpi.c, or is it automatically detected on install?

**EDIT**

But, wait.  I'm running Linux 3.6 rc2.  Maybe, that's the problem.

Here's the patch...

```
--- a/nv-acpi.c
+++ b/nv-acpi.c
@@ -300,7 +300,11 @@ static int nv_acpi_remove(struct acpi_de
     if (pNvAcpiObject->notify_handler_installed)
     {
         // no status returned for this function
**[COLOR="DarkRed"]+#if LINUX_VERSION_CODE >= KERNEL_VERSION(3,6,0)[/COLOR]**
+        acpi_os_wait_events_complete();
+#else
         acpi_os_wait_events_complete(NULL);
+#endif
 
         // remove event notifier
         status = acpi_remove_notify_handler(device->handle, ACPI_DEVICE_NOTIFY, nv_acpi_event);
```

---

### Post by VinDSL on 2012-08-04
Doh!  I think I see the prob.

From the log file above...

```
<snip>

In file included from /usr/src/linux-headers-3.6.0-030600rc1-generic/arch/x86/include/asm/uaccess.h:584:0,
                 from include/linux/poll.h:14,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-linux.h:97,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-acpi.c:15:
/usr/src/linux-headers-3.6.0-030600rc1-generic/arch/x86/include/asm/uaccess_32.h: In function &#8216;copy_from_user&#8217;:
/usr/src/linux-headers-3.6.0-030600rc1-generic/arch/x86/include/asm/uaccess_32.h:208:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
/var/lib/dkms/nvidia-current/304.30/build/nv-acpi.c: In function &#8216;nv_acpi_remove&#8217;:
/var/lib/dkms/nvidia-current/304.30/build/nv-acpi.c:303:9: **[COLOR="DarkRed"]error: too many arguments to function &#8216;acpi_os_wait_events_complete&#8217;[/COLOR]**
In file included from include/acpi/acpi.h:63:0,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-linux.h:274,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-acpi.c:15:
include/acpi/acpiosxf.h:208:6: note: declared here

<snip>
```

I *think* the diff/patch is being applied incorrectly.

Gotta run.

BBL

---

### Post by paul_in_london on 2012-08-04
> **VinDSL said:**
> Doh!  I think I see the prob.

From the log file above...

```
<snip>

In file included from /usr/src/linux-headers-3.6.0-030600rc1-generic/arch/x86/include/asm/uaccess.h:584:0,
                 from include/linux/poll.h:14,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-linux.h:97,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-acpi.c:15:
/usr/src/linux-headers-3.6.0-030600rc1-generic/arch/x86/include/asm/uaccess_32.h: In function &#8216;copy_from_user&#8217;:
/usr/src/linux-headers-3.6.0-030600rc1-generic/arch/x86/include/asm/uaccess_32.h:208:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
/var/lib/dkms/nvidia-current/304.30/build/nv-acpi.c: In function &#8216;nv_acpi_remove&#8217;:
/var/lib/dkms/nvidia-current/304.30/build/nv-acpi.c:303:9: **[COLOR="DarkRed"]error: too many arguments to function &#8216;acpi_os_wait_events_complete&#8217;[/COLOR]**
In file included from include/acpi/acpi.h:63:0,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-linux.h:274,
                 from /var/lib/dkms/nvidia-current/304.30/build/nv-acpi.c:15:
include/acpi/acpiosxf.h:208:6: note: declared here

<snip>
```

I *think* the diff/patch is being applied incorrectly.

Gotta run.

BBL

Another nvidia-current update has just cone through:

```
paul@quantal-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.30-0ubuntu1~xedgers~quantal3
  Candidate: 304.30-0ubuntu1~xedgers~quantal3
  Version table:
 *** 304.30-0ubuntu1~xedgers~quantal3 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status
     302.17-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted amd64 Packages
paul@quantal-64:~$
```

Builds for 3.6-rc1 ok now:

```
Building initial module for 3.6.0-030600rc1-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.6.0-030600rc1-generic/updates/dkms/

depmod.......

DKMS: install completed.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.6.0-030600rc1-generic
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB
```

---

### Post by paul_in_london on 2012-08-04
And another update:

```
paul@quantal-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.32-0ubuntu1~xedgers~quantal1
  Candidate: 304.32-0ubuntu1~xedgers~quantal1
  Version table:
 *** 304.32-0ubuntu1~xedgers~quantal1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status
     302.17-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted amd64 Packages
[1]+  Done                    ./firefox.sh
paul@quantal-64:~$ 
```

Still builds ok for 3.6-rc1.

---

### Post by VinDSL on 2012-08-04
> **paul_in_london said:**
> Another nvidia-current update has just come through [...]

> **paul_in_london said:**
> And another update [...]
~Cool

I'm on the trot right now, but will give them a whirl when I return to the abode.

Thanks!  ;)

---

### Post by VinDSL on 2012-08-04
Sweet!  It works...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-4-aug-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-4-aug-2012-1.png")[/INDENT]

```
vindsl@Zuul:~$ apt-cache policy lxde
lxde:
  Installed: 0.5.0-4ubuntu3
  Candidate: 0.5.0-4ubuntu3
  Version table:
 *** 0.5.0-4ubuntu3 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/universe i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$
```

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.5.20 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo

~ VinDSL Unity Debug Script 12.5.20 (vindsl.com) ~
Current Date/Time: Sat Aug  4 16:48:04 MST 2012
Distro Release: Ubuntu quantal (development branch)
Kernel Release: Linux 3.6.0-030600rc1-generic
Unity Release: unity 6.0.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.32

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch
  Installed: 2:1.12.99.903+git20120801.afa53fe7-0ubuntu0ricotz

vindsl@Zuul:~$ 

```

Thanks, my friend!  Onwards & upwards.

Bring on the breakage...  :)

---

### Post by VinDSL on 2012-08-17
Kernel 3.6-rc2 is available now...  ;)

Linkage:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc2-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc2-quantal/)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-16-aug-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-16-aug-2012-1.png")[/INDENT]

---

### Post by kuvanito on 2012-08-18
what's going on with the kernel site? no access...

---

### Post by cariboo on 2012-08-18
> **kuvanito said:**
> what's going on with the kernel site? no access...

It may not be back up yet due to the move to a new data centre.

---

### Post by kuvanito on 2012-08-19
yeap,all working fine here too :guitar:

---

### Post by VinDSL on 2012-08-22
Kernel 3.6-rc3 is here...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-22-aug-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-22-aug-2012-1.png")[/INDENT]


Works fine on Unity, including the "banned/uninstallable" 304.37 nVidia driver.

Don't ask me WHY it's working.  It's a mystery, even to me!  :D

---

### Post by kyleabaker on 2012-08-22
Is there a repo that I can add in order to install Kernel 3.6rc3? How did everyone else get these installed? I keep getting the following message everything I attempt to install **linux-headers-3.6.0-030600rc3-generic_3.6.0-030600rc3.201208221735_amd64.deb**.

> Dependency is not satisfiable: linux-headers-3.6.0-030600rc3

Must be doing something wrong. Any tips?

---

### Post by VinDSL on 2012-08-22
> **kyleabaker said:**
> Any tips?
There are 4 .debs required.

I download these 4 files to a folder -- all by themselves.
```
vindsl@Zuul:~$ dir Downloads/Kernel
linux-headers-3.6.0-030600rc3_3.6.0-030600rc3.201208221735_all.deb
linux-headers-3.6.0-030600rc3-generic_3.6.0-030600rc3.201208221735_i386.deb
linux-image-3.6.0-030600rc3-generic_3.6.0-030600rc3.201208221735_i386.deb
linux-image-extra-3.6.0-030600rc3-generic_3.6.0-030600rc3.201208221735_i386.deb

```

Then, I use dpkg to install them.
```
vindsl@Zuul:~$ cd Downloads/Kernel && sudo dpkg -i *.deb

```

That's it...

---

### Post by kuvanito on 2012-08-23
thank you vindsl!!!
try this instead: cd Downloads Kernel && sudo dpkg -i *.deb

---

### Post by dino99 on 2012-08-23
works fine here with nouveau & without xorg.conf (8500gt) on 3.6 rc3

---

### Post by xeizo on 2012-08-23
RC2 couldn't write to a ntfs-disk(but could read it), back to 3.5.11 ....

---

### Post by kuvanito on 2012-08-23
i am also having problems with my Logitech C500 Webcam not working...

---

### Post by sacridex on 2012-09-01
Will it land into QQ? Or will it stay with 3.5 in the final release?

---

### Post by dino99 on 2012-09-01
> **sacridex said:**
> Will it land into QQ? Or will it stay with 3.5 in the final release?

3.5 as Quantal repos are frozen now

---

### Post by jerrylamos on 2012-09-01
Chasing a wireless WPA bug Launchpad asked me to install 3.6.0-030600rc3-generic which I assume is rc3.  Wireless WPA bug is still there, otherwise no additional problems.  Usual Libre Write/Unity freeze occurs.

---

