---
title: "Kernel 5.12 RC (Release Candidate) series"
date: 2021-02-28
forum: Ubuntu Development Version
---

### Post by Doug S on 2021-02-28
Kernel 5.12-rc1 has been released. (I'll edit in links when they exist.)

I have been running something very close to 5.12-rc1 for a few hours now, but just compiled:

```
doug@s18:~$ uname -a
Linux s18 5.12.0-rc1-stock #854 SMP PREEMPT Sun Feb 28 16:38:18 PST 2021 x86_64 x86_64 x86_64 GNU/Linux
```

Previous cycle threads: [5.11]("https://ubuntuforums.org/showthread.php?t=2455791"), [5.10]("https://ubuntuforums.org/showthread.php?t=2452692"), [5.9]("https://ubuntuforums.org/showthread.php?t=2448933"), [5.8]("https://ubuntuforums.org/showthread.php?t=2445465"), [5.7]("https://ubuntuforums.org/showthread.php?t=2440607"), [5.6]("https://ubuntuforums.org/showthread.php?t=2436608"), [5.5]("https://ubuntuforums.org/showthread.php?t=2432815"), [5.4]("https://ubuntuforums.org/showthread.php?t=2428734"), [5.3]("https://ubuntuforums.org/showthread.php?t=2423441"), [5.2]("https://ubuntuforums.org/showthread.php?t=2419363"), [5.1]("https://ubuntuforums.org/showthread.php?t=2414938"), [5.0]("https://ubuntuforums.org/showthread.php?t=2409811"), [4.20]("https://ubuntuforums.org/showthread.php?t=2405365"), 4.19 ?, [4.18]("https://ubuntuforums.org/showthread.php?t=2394500"), [4.17]("https://ubuntuforums.org/showthread.php?t=2389561"), [4.16]("https://ubuntuforums.org/showthread.php?t=2384781"), [4.15]("https://ubuntuforums.org/showthread.php?t=2378956"), [4.14]("https://ubuntuforums.org/showthread.php?t=2371638").

See the last few posts on the 5.11 RC series thread for some information on mainline build failures and potential boot issues.

---

### Post by corradoventu on 2021-03-01
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12-rc1/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12-rc1/) build failed

---

### Post by zika on 2021-03-01
"Frozen Wasteland" 
[https://www.phoronix.com/forums/forum/phoronix/latest-phoronix-articles/1241719-linux-5-12-rc1-released-as-the-frozen-wasteland-kernel](https://www.phoronix.com/forums/forum/phoronix/latest-phoronix-articles/1241719-linux-5-12-rc1-released-as-the-frozen-wasteland-kernel)

---

### Post by zika on 2021-03-03
```
:~$ uname -r5.12.0-051200rc1drmtip20210304-generic
```
Great thanks to everyone involved.

---

### Post by Doug S on 2021-03-04
Oh for goodness sake, so now they broke the build for everybody.
This kernel config change (old .config is from 5.11):
```
doug@s18:~/temp-k-git/linux$ scripts/diffconfig .config .config-5.12.0-051200rc1-lowlatency
...
 SURFACE_HOTPLUG n -> m
 SVC_I3C_MASTER n -> m
 [COLOR="#FF0000"]SYSTEM_TRUSTED_KEYS "" -> "debian/canonical-certs.pem"[/COLOR]
 TCG_TIS_I2C_CR50 n -> m
 USB_CDNS_SUPPORT n -> m
```

Causes this:

```
make KERNELRELEASE=5.12.0-rc1-doug ARCH=x86     KBUILD_BUILD_VERSION=857 -f ./Makefile
...
  CALL    scripts/checksyscalls.sh
make[5]: *** No rule to make target 'debian/canonical-certs.pem', needed by 'certs/x509_certificate_list'.  Stop.
make[5]: *** Waiting for unfinished jobs....
...
  CC      kernel/fork.o
make[4]: *** [Makefile:1849: certs] Error 2
make[4]: *** Waiting for unfinished jobs....

```
So now the compile mainline with stolen Ubuntu mainline kernel configuration procedure becomes (.config starts as copied from 5.12-rc1):

```
doug@s18:~/temp-k-git/linux$ scripts/config --disable DEBUG_INFO
doug@s18:~/temp-k-git/linux$ scripts/config --set-str SYSTEM_TRUSTED_KEYS ""
doug@s18:~/temp-k-git/linux$ scripts/diffconfig .config-5.12.0-051200rc1-lowlatency .config
 DEBUG_INFO y -> n
 SYSTEM_TRUSTED_KEYS "debian/canonical-certs.pem" -> ""
doug@s18:~/temp-k-git/linux$ time make -j7 olddefconfig bindeb-pkg LOCALVERSION=-doug
```

My entire [compile mainline kernel procedure]("https://askubuntu.com/questions/718381/how-to-compile-and-install-custom-mainline-kernel/718662#718662")

---

### Post by Doug S on 2021-03-04
By the way, and just in case anyone is interested, I am using 5.12-rc1 with this change:

```
doug@s18:~/temp-k-git/linux$ git diff
diff --git a/drivers/idle/intel_idle.c b/drivers/idle/intel_idle.c
index 3273360f30f7..3464defa004e 100644
--- a/drivers/idle/intel_idle.c
+++ b/drivers/idle/intel_idle.c
@@ -636,8 +636,8 @@ static struct cpuidle_state skl_cstates[] __initdata = {
                .enter_s2idle = intel_idle_s2idle, },
        {
                .name = "C1E",
-               .desc = "MWAIT 0x01",
-               .flags = MWAIT2flg(0x01) | CPUIDLE_FLAG_ALWAYS_ENABLE,
+               .desc = "MWAIT 0x03",
+               .flags = MWAIT2flg(0x03) | CPUIDLE_FLAG_ALWAYS_ENABLE,
                .exit_latency = 10,
                .target_residency = 20,
                .enter = &intel_idle,

```As a potential solution to an HWP (HardWare Pstate) control problem in Intel processors. It has taken 9 months to figure out. [Bug report]("https://bugzilla.kernel.org/show_bug.cgi?id=210741").

EDIT: the patch is specific to my HWP capable processor, i5-9600K, and needs to be propagated for others.
EDIT 2: I have now entered a downstream [bug report, on launchpad]("https://bugs.launchpad.net/linux/+bug/1917813").

---

### Post by zika on 2021-03-05
HU:
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.12-rc2-Likely-Soon](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.12-rc2-Likely-Soon)
Disable swapfile as a precaution.

---

### Post by Doug S on 2021-03-05
> **zika said:**
> HU: [https://www.phoronix.com/scan.php?page=news_item&px=Apple-M1-For-Linux-V3](https://www.phoronix.com/scan.php?page=news_item&px=Apple-M1-For-Linux-V3)
Disable swapfile as a precaution.Sorry zika, but I am not following/understanding your caution from that article. Could you expand?

---

### Post by zika on 2021-03-05
> **Doug S said:**
> Sorry zika, but I am not following/understanding your caution from that article. Could you expand?Sorry,  the mistake is mine, wrong URL. I've edited my mesasge above. Mea culpa. Old fingers and old eyes and bad connection between those... ;)

---

### Post by Doug S on 2021-03-05
> **zika said:**
> Sorry, mistake is mine, wrong URL. I've edited my mesasge above. Mea culpa. Old fingers and old eyes and bad connection between those... ;)Oh my. Thank you very much for the heads up.

And about the "Old fingers and old eyes and bad connection between those". Ya, me also.

EDIT: By the way, I have never heard of such a caution before. I looked back at every tag in the mainline git tree and there has never been a "dontuse" tag before (or any other odd tag).

EDIT 2: I see that 5.12-rc1 has also been removed from [kernel.org]("https://www.kernel.org/")

---

### Post by zika on 2021-03-06
What is changed and how small it is but with large consecuences:
[https://github.com/torvalds/linux/commit/caf6912f3f4af7232340d500a4a2008f81b93f14](https://github.com/torvalds/linux/commit/caf6912f3f4af7232340d500a4a2008f81b93f14)

---

### Post by zika on 2021-03-06
> **Doug S said:**
> EDIT 2: I see that 5.12-rc1 has also been removed from [kernel.org]("https://www.kernel.org/")
**Beware**: it is not removed completely since *drmtip* and *daily* on [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/) kernels are newly brewed as rc1.
(after deeper look in changes, once I've got some spare time, it looks like those, eventhough marked as rc1, have those patches for trouble with swapfile included)...
Also, rc2 is, now, brewed and available on [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/).
Yes, that is the first time as much as I know.
Fortune protects brave:
```
:~$ uname -r
5.12.0-051200rc2-lowlatency
```

---

### Post by T6&amp;sfpER35% on 2021-03-06
[https://arstechnica.com/gadgets/2021/03/psa-linux-folks-stay-away-from-the-5-12-rc1-kernel/](https://arstechnica.com/gadgets/2021/03/psa-linux-folks-stay-away-from-the-5-12-rc1-kernel/)

---

### Post by xyz-t on 2021-03-14
All good:

```
5.12.0-051200rc3-generic #202103142231 SMP Sun Mar 14 22:33:40 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2021-03-26
I missed -rc3. For -rc4 I got some never seen before "unmet direct dependencies" at the start of compile:

```
doug@s19:~/temp-k-git/linux$ [COLOR="#FF0000"]time make -j13 olddefconfig bindeb-pkg LOCALVERSION=-stock[/COLOR]

WARNING: unmet direct dependencies detected for ADI_AXI_ADC
  Depends on [n]: IIO [=m] && HAS_IOMEM [=y] && OF [=n]
  Selected by [m]:
  - AD9467 [=m] && IIO [=m] && SPI [=y]
#
# configuration written to .config
#
  SYNC    include/config/auto.conf.cmd

WARNING: unmet direct dependencies detected for ADI_AXI_ADC
  Depends on [n]: IIO [=m] && HAS_IOMEM [=y] && OF [=n]
  Selected by [m]:
  - AD9467 [=m] && IIO [=m] && SPI [=y]

WARNING: unmet direct dependencies detected for ADI_AXI_ADC
  Depends on [n]: IIO [=m] && HAS_IOMEM [=y] && OF [=n]
  Selected by [m]:
  - AD9467 [=m] && IIO [=m] && SPI [=y]

WARNING: unmet direct dependencies detected for ADI_AXI_ADC
  Depends on [n]: IIO [=m] && HAS_IOMEM [=y] && OF [=n]
  Selected by [m]:
  - AD9467 [=m] && IIO [=m] && SPI [=y]
sh ./scripts/package/mkdebian
dpkg-buildpackage -r"fakeroot -u" -a$(cat debian/arch)  -b -nc -uc
dpkg-buildpackage: info: source package linux-5.12.0-rc4-stock
...
```

I also observe some Dell stuff being included by default now:

```
doug@s19:~/temp-k-git/linux$ [COLOR="#FF0000"]scripts/diffconfig .config-5.12.0-051200rc2-lowlatency .config-5.12.0-051200rc4-lowlatency[/COLOR]
-SND_SOC_SIRF_AUDIO_CODEC m
 ACPI_FPDT n -> y
 BCM_VK_TTY n -> y
 CIO2_BRIDGE n -> y
 DMA_VIRTUAL_CHANNELS m -> y
 DTPM n -> y
 INTEL_LDMA n -> y
 KVM_XEN n -> y
 LEDS_BLINK n -> y
 MLX5_SF n -> y
 MMC_CRYPTO n -> y
 PLAYSTATION_FF n -> y
 SND_INTEL_BYT_PREFER_SOF n -> y
 USB_CDNS3_GADGET n -> y
 USB_CDNS3_HOST n -> y
 USB_CDNSP_GADGET n -> y
 USB_CDNSP_HOST n -> y
 [COLOR="#FF0000"]X86_PLATFORM_DRIVERS_DELL n -> y[/COLOR]
+ALIENWARE_WMI m
+DCDBAS m
+DELL_LAPTOP m
+DELL_RBTN m
+DELL_RBU m
+DELL_SMBIOS m
[COLOR="#FF0000"]+DELL_SMBIOS_SMM y[/COLOR]
[COLOR="#FF0000"]+DELL_SMBIOS_WMI y[/COLOR]
+DELL_SMO8800 m
+DELL_WMI m
+DELL_WMI_AIO m
+DELL_WMI_DESCRIPTOR m
+DELL_WMI_LED m
+DELL_WMI_SYSMAN m
+DTPM_CPU y
+MLX5_SF_MANAGER y
+USB_CDNS_HOST y
```

Anyway, running it now:

```
doug@s19:~$ uname -a
Linux s19 5.12.0-rc4-stock #866 SMP PREEMPT Fri Mar 26 06:50:24 PDT 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by xyz-t on 2021-03-29
No new Kernel since the 24th?

---

### Post by Doug S on 2021-03-29
> **xyz-t said:**
> No new Kernel since the 24th?Well, kernel 5.12-rc5 was released on kernel.org pretty much at the usual time. But yes, it seems the daily Ubuntu mainline PPA builds are broken, yet again.

---

### Post by zika on 2021-03-30
I've changed my longstanding habbits and I'm now using linux-image-unsigned-5.12.0-5-generic 5.12.0-5.5 from [http://ppa.launchpad.net/canonical-kernel-team/unstable/ubuntu/](http://ppa.launchpad.net/canonical-kernel-team/unstable/ubuntu/)... It works for me but I'm kind of sad because years of using Ubuntu mainline left their mark on me.
```
:~$ apt-cache showpkg linux-image-unsigned-5.12.0-5-generic 5.12.0-5.5
Package: linux-image-unsigned-5.12.0-5-generic
Versions: 
5.12.0-5.5 (/var/lib/apt/lists/ppa.launchpad.net_canonical-kernel-team_unstable_ubuntu_dists_devel_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/ppa.launchpad.net_canonical-kernel-team_unstable_ubuntu_dists_devel_main_binary-amd64_Packages
                  MD5: a9742fe5a6723ea5b35e724cf5ada219
 Description Language: en
                 File: /var/lib/apt/lists/ppa.launchpad.net_canonical-kernel-team_unstable_ubuntu_dists_devel_main_i18n_Translation-en
                  MD5: a9742fe5a6723ea5b35e724cf5ada219


Reverse Depends: 
  linux-image-5.12.0-5-generic,linux-image-unsigned-5.12.0-5-generic
  linux-modules-extra-5.12.0-5-generic,linux-image-unsigned-5.12.0-5-generic
  linux-modules-5.12.0-5-generic,linux-image-unsigned-5.12.0-5-generic
Dependencies: 
5.12.0-5.5 - kmod (0 (null)) linux-base (2 4.5ubuntu1~16.04.1) linux-modules-5.12.0-5-generic (0 (null)) linux-image-5.12.0-5-generic (0 (null)) grub-pc (16 (null)) grub-efi-amd64 (16 (null)) grub-efi-ia32 (16 (null)) grub (16 (null)) lilo (0 (null)) initramfs-tools (16 (null)) linux-initramfs-tool (0 (null)) fdutils (0 (null)) linux-doc (16 (null)) linux-unstable-source-5.12.0 (0 (null)) linux-unstable-tools (0 (null)) linux-headers-5.12.0-5-generic (0 (null)) linux-modules-extra-5.12.0-5-generic (0 (null)) 
```
Nevertheless it is nice to have &#8222;official&#8220; kernel at least this much fresh, at least every week, since *daily* and *drmtip* are now so far apart between...
Thank You Canonical kernel team...

---

### Post by xyz-t on 2021-03-30
Thanks Zika! 

The ppa appears to be this one and I did not try it since a long time:
[https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/unstable](https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/unstable)

Otherwise, when Debian packages are not available on a daily basis, at least on Sunday, Ubuntu flavors are less attractive.
```
pacman -Qii linux512
Name            : linux512
Version         : 5.12.rc5.d0328.ga5e13c6-1
Description     : The Linux512 kernel and modules
Architecture    : x86_64
URL             : http://www.kernel.org/
Licenses        : GPL2
Groups          : None
Provides        : linux=5.12.rc5.d0328.ga5e13c6  VIRTUALBOX-GUEST-MODULES
                  WIREGUARD-MODULE
Depends On      : coreutils  linux-firmware  kmod  mkinitcpio>=27
Optional Deps   : crda: to set the correct wireless channels of your country
                  [installed]
Required By     : None
Optional For    : None
Conflicts With  : None
Replaces        : None
Installed Size  : 157.61 MiB
Packager        : Helmut Stult <helmut@manjaro.org>
Build Date      : Mon 29 Mar 2021 12:14:33 PM EDT
Install Date    : Mon 29 Mar 2021 01:52:06 PM EDT
Install Reason  : Explicitly installed
Install Script  : No
Validated By    : Signature
Backup Files    :
(none)
```

Backup

```
pacman -Q linux511
linux511 5.11.10-1
```

Will give it a try later, thank you again.

---

### Post by Doug S on 2021-04-01
mainline PPA compiles have been fixed, and [5.14-rc5 is there]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12-rc5/").

```
doug@s19:~$ uname -a
Linux s19 5.12.0-051200rc5-lowlatency #202103292143 SMP PREEMPT Thu Apr 1 01:15:36 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by xyz-t on 2021-04-03
```
5.12.0-051200rc5daily20210404-generic #202104032200 SMP Sun Apr 4 02:03:49 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2021-04-04
kernel 5.12-rc6 has been released. Observe these kernel configuration differences between Ubuntu mainline PPAs -rc5 and -rc6:

```
doug@s19:~/temp-k-git/linux$ scripts/diffconfig .config-5.12.0-051200rc5-lowlatency .config-5.12.0-051200rc6-lowlatency
 ATH11K_DEBUGFS n -> y
 ATH11K_TRACING n -> y
 KFENCE n -> y
+ATH11K_SPECTRAL y
+KFENCE_NUM_OBJECTS 255
+KFENCE_SAMPLE_INTERVAL 0
+KFENCE_STATIC_KEYS y
+KFENCE_STRESS_TEST_FAULTS 0
```
I still get dependency warning during compile:
```
doug@s19:~/temp-k-git/linux$ time make -j13 olddefconfig bindeb-pkg LOCALVERSION=-stock

WARNING: unmet direct dependencies detected for ADI_AXI_ADC
  Depends on [n]: IIO [=m] && HAS_IOMEM [=y] && OF [=n]
  Selected by [m]:
  - AD9467 [=m] && IIO [=m] && SPI [=y]
#
# configuration written to .config
#
  SYNC    include/config/auto.conf.cmd

WARNING: unmet direct dependencies detected for ADI_AXI_ADC
  Depends on [n]: IIO [=m] && HAS_IOMEM [=y] && OF [=n]
  Selected by [m]:
  - AD9467 [=m] && IIO [=m] && SPI [=y]

WARNING: unmet direct dependencies detected for ADI_AXI_ADC
  Depends on [n]: IIO [=m] && HAS_IOMEM [=y] && OF [=n]
  Selected by [m]:
  - AD9467 [=m] && IIO [=m] && SPI [=y]

WARNING: unmet direct dependencies detected for ADI_AXI_ADC
  Depends on [n]: IIO [=m] && HAS_IOMEM [=y] && OF [=n]
  Selected by [m]:
  - AD9467 [=m] && IIO [=m] && SPI [=y]
  UPD     include/config/kernel.release
sh ./scripts/package/mkdebian
dpkg-buildpackage -r"fakeroot -u" -a$(cat debian/arch)  -b -nc -uc
dpkg-buildpackage: info: source package linux-5.12.0-rc6-stock
```

---

### Post by xyz-t on 2021-04-13
[https://bugzilla.kernel.org/show_bug.cgi?id=212675](https://bugzilla.kernel.org/show_bug.cgi?id=212675)

```
dpkg --list | grep linux-image
ii  linux-image-5.11.0-14-generic                 5.11.0-14.15                                                         amd64        Signed kernel image generic
ii  linux-image-generic                           5.11.0.14.15                                                         amd64        Generic Linux kernel image
ii  linux-image-unsigned-5.12.0-051200rc7-generic 5.12.0-051200rc7.202104112331                                        amd64        Linux kernel image for version 5.12.0 on 64 bit x86 SMP
```

---

### Post by Doug S on 2021-04-14
> **xyz-t said:**
> [https://bugzilla.kernel.org/show_bug.cgi?id=212675](https://bugzilla.kernel.org/show_bug.cgi?id=212675)Was that bug report entered by you, i.e. are you "Mik"? I ask because it is an upstream bug report, but refers to things like "Proposed", which is a distro specific reference.

---

### Post by Doug S on 2021-04-28
Mainline Kernel 5.12 seems to have a dependency change which is problem for my main 20.04 test server.
I am a bit behind and didn't know until I saw [this question]("https://askubuntu.com/questions/1334633/mainline-ppa-kernel-now-depends-on-libc6-2-33-uninstallable-in-focal") over on askubuntu.

Requires  libc >=2.33

but focal is at 2.31-0ubuntu9.2

However, if I compile myself, it installs fine. I.E. the dependency is compiler version dependent.

---

