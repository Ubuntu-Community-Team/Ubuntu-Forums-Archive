---
title: "Just compiled and installed kernel 3.13-rc4 ok"
date: 2013-12-15
forum: Ubuntu Development Version
---

### Post by paul_in_london on 2013-12-15
Downloaded from [https://www.kernel.org/pub/linux/kernel/v3.x/testing/](https://www.kernel.org/pub/linux/kernel/v3.x/testing/)

```
paul@trusty-64:~$ uname -a
Linux trusty-64 3.13.0-rc4-custom #1 SMP Sun Dec 15 21:19:29 GMT 2013 x86_64 x86_64 x86_64 GNU/Linux
paul@trusty-64:~$
```

Not all of the debs are in mainline yet:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-rc4-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-rc4-trusty/)

---

### Post by zika on 2013-12-15
[http://ubuntuforums.org/showthread.php?t=2192225&p=12874492#post12874492](http://ubuntuforums.org/showthread.php?t=2192225&p=12874492#post12874492)
I've anticipated that rc4 will start crippled since daily is alike for couple of days...
I did not get time to investigate but I think that something small is blocking some cogs...

---

### Post by Branimir_Maksimovic on 2013-12-15
This commit is responsible for compile error:
"
commit 3e1e4a5f3a324502c27c4e8808e06ac2ea842360
Author: Krzysztof Kozlowski <k.kozlowski@samsung.com>
Date:   Thu Dec 12 17:12:31 2013 -0800


    mfd/rtc: s5m: fix register updating by adding regmap for RTC
    
    Rename old regmap field of "struct sec_pmic_dev" to "regmap_pmic" and
    add new regmap for RTC.
...
"
Problem is that old field name is regmap and now is regmap_pmic, so drivers
that use it don't compile. I compile regularly so one needs to change
regmap to regmap_pmic in two file where compiler complains.
I guess that nobody compiles that driver, so kernel devels
didn;t catch this error yet ;)

---

### Post by paul_in_london on 2013-12-15
I've never actually tried compiling the source from mainline, only the vanilla source from kernel.org.

Does it fail on the kernel itself or the modules? This box is about 7 years old and I'm using nouveau.

I use the localmodconfig make target which gives me 79 modules on my setup:

```
paul@trusty-64:~$ locate "*.ko" | grep 3.13.0-rc4 | grep -v src
/lib/modules/3.13.0-rc4-custom/kernel/arch/x86/kernel/microcode.ko
/lib/modules/3.13.0-rc4-custom/kernel/crypto/xor.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/acpi/video.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/ata/acard-ahci.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/ata/ahci.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/ata/ahci_platform.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/ata/libahci.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/gpio/gpio-ich.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/gpu/drm/drm.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/gpu/drm/drm_kms_helper.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/gpu/drm/nouveau/nouveau.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/gpu/drm/ttm/ttm.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/hid/hid-logitech.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/hid/hid.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/hid/usbhid/usbhid.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/hwmon/adm1021.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/hwmon/lm90.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/i2c/algos/i2c-algo-bit.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/input/ff-memless.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/macintosh/mac_hid.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/mfd/lpc_ich.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/net/ethernet/broadcom/tg3.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/platform/x86/mxm-wmi.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/platform/x86/wmi.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/pps/pps_core.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/ptp/ptp.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/video/output.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/xen/tmem.ko
/lib/modules/3.13.0-rc4-custom/kernel/drivers/xen/xen-privcmd.ko
/lib/modules/3.13.0-rc4-custom/kernel/fs/btrfs/btrfs.ko
/lib/modules/3.13.0-rc4-custom/kernel/kernel/configs.ko
/lib/modules/3.13.0-rc4-custom/kernel/lib/libcrc32c.ko
/lib/modules/3.13.0-rc4-custom/kernel/lib/raid6/raid6_pq.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/ipv4/netfilter/ip_tables.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/ipv4/netfilter/iptable_filter.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/ipv4/netfilter/iptable_nat.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/ipv4/netfilter/nf_conntrack_ipv4.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/ipv4/netfilter/nf_defrag_ipv4.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/ipv4/netfilter/nf_nat_ipv4.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/ipv6/netfilter/ip6_tables.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/netfilter/nf_conntrack.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/netfilter/nf_conntrack_broadcast.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/netfilter/nf_conntrack_ftp.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/netfilter/nf_conntrack_netbios_ns.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/netfilter/nf_nat.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/netfilter/nf_nat_ftp.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/netfilter/x_tables.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/netfilter/xt_LOG.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/netfilter/xt_addrtype.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/netfilter/xt_conntrack.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/netfilter/xt_limit.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/netfilter/xt_nat.ko
/lib/modules/3.13.0-rc4-custom/kernel/net/netfilter/xt_tcpudp.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/soundcore.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/core/snd-pcm.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/core/snd-timer.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/core/snd.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.13.0-rc4-custom/kernel/sound/pci/hda/snd-hda-intel.ko
```

```
paul@trusty-64:~$ inxi -F
System:    Host: trusty-64 Kernel: 3.13.0-rc4-custom x86_64 (64 bit) Desktop: Fluxbox 1.3.5 Distro: Ubuntu 14.04 trusty
Machine:   System: Hewlett-Packard product: HP xw4300 Workstation
           Mobo: Hewlett-Packard model: 0A00h Bios: Hewlett-Packard version: 786D3 v01.08 date: 03/10/2006
CPU:       Dual core Intel Pentium D CPU (-MCP-) cache: 2048 KB flags: (lm nx sse sse2 sse3 vmx) 
           Clock Speeds: 1: 3200.00 MHz 2: 2400.00 MHz
Graphics:  Card: NVIDIA NV41GL [Quadro FX 1400] 
           X.Org: 1.14.5 drivers: nouveau (unloaded: fbdev,vesa) Resolution: 1920x1080@60.0hz 
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.3, 128 bits) GLX Version: 2.1 Mesa 10.0.0
Audio:     Card: Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel 
           Sound: Advanced Linux Sound Architecture ver: k3.13.0-rc4-custom
Network:   Card: Broadcom NetXtreme BCM5752 Gigabit Ethernet PCI Express driver: tg3 
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: 00:17:a4:f3:32:a3
Drives:    HDD Total Size: 160.0GB (9.0% used) 1: id: /dev/sda model: SAMSUNG_HD160JJ/ size: 160.0GB 
Partition: ID: / size: 40G used: 14G (35%) fs: btrfs ID: /home size: 40G used: 14G (35%) fs: btrfs 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 105 Uptime: 1:04 Memory: 800.0/2001.9MB Client: Shell (bash) inxi: 1.9.14 
paul@trusty-64:~$     Processes: 105 Uptime: 1:04 Memory: 800.0/2001.9MB Client: Shell (bash) inxi: 1.9.14 
```

---

### Post by Branimir_Maksimovic on 2013-12-15
It fails on modules. If you don't compile that module compilation is ok. I use .config from Ubuntu compiled kernels, and
those have everything included, so that is how I hit error ;)

---

### Post by paul_in_london on 2013-12-15
Ok. At the start of the 3.13 cycle I copied  /boot/config-3.13.0-031300rc1-generic to use when compiling my custom kernels before running make localmodconfig.

Maybe you could try that way? Here are the steps I used:

```
cd /usr/src
tar vxf ~/Downloads/linux-3.13-rc4.tar.xz
cd linux-3.13-rc4
cp -v ../linux-3.13-rc3/.config .
make-kpkg clean
make localmodconfig
make prepare
make modules_prepare
time fakeroot make-kpkg -j3 --initrd --append-to-version=-custom kernel-image kernel-headers
cd ..
sudo dpkg -i li*.deb
```

EDIT: ...except I don't seem to be using the problematic driver you mentioned.

---

### Post by Branimir_Maksimovic on 2013-12-15
I have compiled kernel, already. Corrected following files:
#       modified:   drivers/clk/clk-s2mps11.c
#       modified:   drivers/regulator/s2mps11.c

---

### Post by zika on 2013-12-16
> **Branimir_Maksimovic said:**
> This commit is responsible for compile error:
"
commit 3e1e4a5f3a324502c27c4e8808e06ac2ea842360
Author: Krzysztof Kozlowski <k.kozlowski@samsung.com>
Date:   Thu Dec 12 17:12:31 2013 -0800


    mfd/rtc: s5m: fix register updating by adding regmap for RTC
    
    Rename old regmap field of "struct sec_pmic_dev" to "regmap_pmic" and
    add new regmap for RTC.
...
"
Problem is that old field name is regmap and now is regmap_pmic, so drivers
that use it don't compile. I compile regularly so one needs to change
regmap to regmap_pmic in two file where compiler complains.
I guess that nobody compiles that driver, so kernel devels
didn;t catch this error yet ;)
Thank You. (Hvala.)

---

### Post by zika on 2013-12-21
It almost takes more than between two kernels to solve that problem and have new rc4 compiled on mainline...
Is it that big bug? Judging from mesasges above it is just a typo (to call it that way)... It almost makes me want to compile it... ;)

Update&#8321;: [http://ubuntuforums.org/showthread.php?t=2195166](http://ubuntuforums.org/showthread.php?t=2195166)

---

