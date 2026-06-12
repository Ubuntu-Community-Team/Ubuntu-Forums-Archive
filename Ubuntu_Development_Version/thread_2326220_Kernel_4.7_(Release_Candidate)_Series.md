---
title: "Kernel 4.7 (Release Candidate) Series"
date: 2016-05-29
forum: Ubuntu Development Version
---

### Post by Doug S on 2016-05-29
[Kernel 4.7-rc1 is available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7-rc1-yakkety/").
It does not boot for me, nether does a version I compiled myself, using the same kernel configuration file.

EDIT: If I use the kernel configuration file from [kernel 4.6]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/"), accepting all defaults for new stuff, then the resulting compiled kernel boots fine, and so far seems to run fine.```
doug@s15:~$ uname -a
Linux s15 4.7.0-rc1-old-config #47 SMP Sun May 29 15:42:10 PDT 2016 x86_64 x86_64 x86_64 GNU/Linux
doug@s15:~$
```

---

### Post by kithop on 2016-05-30
Hi! I just noticed I've got the same issue - how are you going about building it?  I got all sorts of issues with it complaining about SPL/ZFS following the fakeroot debian/rules path I found on the Wiki.

I also spotted a udev error on boot when trying the ones from the mainline PPA, and found this on that error:

[http://www.gossamer-threads.com/lists/linux/kernel/858739](http://www.gossamer-threads.com/lists/linux/kernel/858739)

Sure enough, in the common configs, 'CONFIG_UNIX=m', while in 4.6.0 'CONFIG_UNIX=y'.  You can see that in BUILD.LOG as well... maybe this was a typo or unintentional change?  I'm hoping simply swapping that back to y and rebuilding will fix it, without having to completely pull your 4.6 config up (in case of other additions/changes).

---

### Post by MikeMecanic on 2016-05-30
[QUOTE=Doug S;13496718][Kernel 4.7-rc1 is available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7-rc1-yakkety/").
It does not boot for me, nether does a version I compiled myself, using the same kernel configuration file.

                         Same here Doug!  Try Generic, Upstart and recovery mode.  Frozen!  If this can help, this is the message I&#8217;m getting (help is not working):
 
 
 error getting socket: address family not supported by protocol
 error initializing udev control socket
 could not listen on fds: Invalid argument
 Gave up waiting for root device.  Common problem:
 - Boot args (cat / proc / cmdline)
     -check root delay = (did the system wait long enough?)
     -check root = (did the system wait for the right device?)
 -Missing modules (cat / proc /modules; ls /dev
 
 
 Alert!  UUID = e 5612716 &#8211; 4A51-4816 &#8211; b508 &#8211; 5922d499a57b does not exist.  Dropping to a shell!
 
 
 BusyBox V.1.212.1 (Ubuntu 1:1.22.0-15ubuntu1)
 built-in shell (ash)
 enter &#8216;help&#8217; for a list of built-in commands
 (initramfs)

---

### Post by MikeMecanic on 2016-05-30
> **Doug S said:**
> 

EDIT: If I use the kernel configuration file from [kernel 4.6]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/"), accepting all defaults for new stuff, then the resulting compiled kernel boots fine, and so far seems to run fine.```
doug@s15:~$ uname -a
Linux s15 4.7.0-rc1-old-config #47 SMP Sun May 29 15:42:10 PDT 2016 x86_64 x86_64 x86_64 GNU/Linux
doug@s15:~$
```
I'm not sure I'm getting that one? I'm already on 4.6 alone.

---

### Post by kithop on 2016-05-30
One thing I'm about to try using the as-built packages:

[https://www.phoronix.com/forums/forum/phoronix/general-discussion/874145-you-may-want-to-think-twice-about-trying-linux-4-7-git-right-now?p=874152#post874152](https://www.phoronix.com/forums/forum/phoronix/general-discussion/874145-you-may-want-to-think-twice-about-trying-linux-4-7-git-right-now?p=874152#post874152)

I've added 'unix' to /etc/initramfs-tools/modules , installed the kernel, and then ran:
sudo update-initramfs -k 4.7.0-040700rc1-generic -u

Since I'm on the nVidia proprietary driver, that DKMS module failed, so I know I'm not going to get very far this time around just yet, but I'll at least test quick here to see if that gets past the udev issue.

Edit: That got me further! Now it's just X hanging or something refusing to give me a working framebuffer because of my GTX 980.  If you want to use the as-built packages, suggest you rebuild your initramfs with the 'unix' module included as above, if you don't want to recompile the whole kernel with CONFIG_UNIX=y.

---

### Post by MikeMecanic on 2016-05-30
I give up! Its 3 AM east coast.  This is what I'm getting: 

```
$ sudo update-initramfs -k 4.7.0-040700rc1-generic -u
update-initramfs: Generating /boot/initrd.img-4.7.0-040700rc1-generic
W: Possible missing firmware /lib/firmware/i915/skl_guc_ver6.bin for module i915
```

---

### Post by kithop on 2016-05-30
> **MikeMecanic said:**
> I give up! Its 3 AM east coast.  This is what I'm getting: 

```
$ sudo update-initramfs -k 4.7.0-040700rc1-generic -u
update-initramfs: Generating /boot/initrd.img-4.7.0-040700rc1-generic
W: Possible missing firmware /lib/firmware/i915/skl_guc_ver6.bin for module i915
```

I got that same error, but it seemed to want to go fine (?) when booting in; again, I didn't get a full boot because the nVidia driver won't compile its DKMS module, but I didn't get that udev error when trying to boot.

I tried searching for skl_guc_ver6.bin with apt-file and don't have it in the stock xenial repos... not sure where that firmware comes from.

After running that update-initramfs command (again, having added 'unix' to /etc/initramfs-tools/modules), what happens when you try then to boot the 4.7.0-rc1 kernel?

---

### Post by Doug S on 2016-05-30
> **kithop said:**
> I tried searching for skl_guc_ver6.binI get that warning message also. Since I think "skl" means Intel Skylake, and I don't have one, I didn't worry about the warning message.

I use git. How I compile the kernel is described [here]("http://askubuntu.com/questions/718381/how-to-compile-and-install-custom-mainline-kernel/718662#718662"). I started with the kernel configuration file from the [Ubuntu mainline kernel 4.6]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/").
```
doug@s15:~/temp-k-git/linux$ cp /boot/config-4.6.0-040600-generic .config
```
```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]scripts/diffconfig .config-4.6.0-040600-generic .config-4.7.0-040700rc1-generic[/COLOR]
-ACPI_INITRD_TABLE_OVERRIDE n
-ADIS16204 m
-ADIS16220 m
-AMD_IOMMU_STATS y
-AMD_MCE_INJ m
-BMC150_MAGN m
-BMP280 m
-EBC_C384_WDT m
-FS_DAX_PMD y
-GPIO_104_DIO_48E m
-GPIO_104_IDIO_16 m
-GPIO_104_IDI_48 m
-GPIO_WS16C48 m
-HAVE_BPF_JIT y
-IMA_MOK_KEYRING n
-IWLWIFI_UAPSD n
-MD_AUTODETECT y
-MLX5_CORE_EN_VXLAN y
-NET_DSA_MV88E6XXX n
-NET_DSA_MV88E6XXX_NEED_PPU n
-NFC_PN533 m
-RANDOMIZE_BASE_MAX_OFFSET 0x40000000
-REGULATOR_MAX8973 m
-SERIAL_MVEBU_CONSOLE y
-SERIAL_MVEBU_UART y
-STAGING_RDMA m
-ZONE_DMA_FLAG 1
 ACPI_AC y -> m
 ACPI_APEI_ERST_DEBUG n -> m
 ACPI_BATTERY y -> m
 ACPI_BUTTON y -> m
 ACPI_FAN y -> m
 ACPI_THERMAL y -> m
 AGP y -> m
 AGP_AMD64 y -> m
 AGP_INTEL y -> m
 AGP_VIA y -> m
 ATA y -> m
 ATA_GENERIC y -> m
 ATA_PIIX y -> m
 BLK_DEV_DM y -> m
 BLK_DEV_LOOP y -> m
 BLK_DEV_MD y -> m
 BLK_DEV_RAM y -> m
 BLK_DEV_SD y -> m
 BLK_DEV_SR y -> m
 CHR_DEV_SG y -> m
 CPU_FREQ_GOV_CONSERVATIVE y -> m
 CPU_FREQ_GOV_ONDEMAND y -> m
 CPU_FREQ_GOV_POWERSAVE y -> m
 CPU_FREQ_GOV_USERSPACE y -> m
 CRYPTO_CRC32C_INTEL y -> m
 CRYPTO_DEV_PADLOCK y -> m
 CRYPTO_DRBG_CTR y -> n
 CRYPTO_DRBG_HASH y -> n
 CRYPTO_SKEIN y -> m
 DEVFREQ_GOV_PERFORMANCE y -> m
 DEVFREQ_GOV_POWERSAVE y -> m
 DEVFREQ_GOV_SIMPLE_ONDEMAND y -> m
 DEVFREQ_GOV_USERSPACE y -> m
 ECRYPT_FS y -> m
 FAT_FS y -> m
 FDDI y -> m
 FIXED_PHY y -> m
 FUSE_FS y -> m
 INTEL_GTT y -> m
 LEDS_CLASS y -> m
 PATA_SIS y -> m
 PSTORE_CONSOLE n -> y
 RXKAD m -> n
 SCSI y -> m
 SCSI_MOD y -> m
 SERIAL_8250_FINTEK m -> n
 TRUSTED_KEYS y -> m
 TUN y -> m
 [COLOR="#FF0000"]UNIX y -> m[/COLOR]
 USB y -> m
 USB_COMMON y -> m
 USB_DWC2 y -> m
 USB_DWC2_PCI y -> m
 USB_EHCI_HCD y -> m
 USB_EHCI_HCD_PLATFORM y -> m
 USB_EHCI_PCI y -> m
 USB_OHCI_HCD y -> m
 USB_OHCI_HCD_PCI y -> m
 USB_OHCI_HCD_PLATFORM y -> m
 USB_UHCI_HCD y -> m
 USB_XHCI_HCD y -> m
 USB_XHCI_PCI y -> m
 VFAT_FS y -> m
 VIRTIO y -> m
 VIRTIO_BALLOON y -> m
 VIRTIO_BLK y -> m
 VIRTIO_CONSOLE y -> m
 VIRTIO_MMIO y -> m
 VIRTIO_NET y -> m
 VIRTIO_PCI y -> m
 X86_ACPI_CPUFREQ y -> m
 X86_PCC_CPUFREQ y -> m
 X86_POWERNOW_K8 y -> m
 X86_SPEEDSTEP_CENTRINO y -> m
 XEN_ACPI_PROCESSOR y -> m
 XEN_BLKDEV_FRONTEND y -> m
 XEN_NETDEV_FRONTEND y -> m
+ACPI_TABLE_UPGRADE y
+AD5592R n
+AD5593R n
+AM2315 n
+BH1780 n
+BMC150_MAGN_I2C n
+BMC150_MAGN_SPI n
+BMI160_I2C n
+BMI160_SPI n
+CC_OPTIMIZE_FOR_PERFORMANCE y
+COMMON_CLK_OXNAS n
+COMMON_CLK_PIC32 n
+CPU_FREQ_DEFAULT_GOV_SCHEDUTIL n
+CPU_FREQ_GOV_ATTR_SET y
+CPU_FREQ_GOV_SCHEDUTIL n
+CPU_NO_EFFICIENT_FFS n
+CROS_KBD_LED_BACKLIGHT n
+DEVFREQ_GOV_PASSIVE n
+DEV_DAX m
+DEV_DAX_PMEM m
+DRM_AMDGPU_GART_DEBUGFS n
+DRM_ANALOGIX_ANX78XX n
+DRM_I915_DEBUG n
+DRM_I915_WERROR n
+DS1803 n
+EFI_BOOTLOADER_CONTROL n
+EFI_CAPSULE_LOADER n
+ELFCORE y
+F2FS_FAULT_INJECTION n
+GENERIC_ADC_THERMAL n
+GTP n
+HAVE_ARCH_HASH n
+HAVE_EBPF_JIT y
+HAVE_EXIT_THREAD y
+HAVE_NMI y
+HID_ASUS n
+HIST_TRIGGERS n
+HP03 n
+HP206C n
+IMA_BLACKLIST_KEYRING n
+INET_SCTP_DIAG m
+INT3406_THERMAL n
+INTEL_PMC_CORE n
+ISCSI_TARGET_CXGB4 n
+KEY_DH_OPERATIONS n
+LEDS_TRIGGER_MTD n
+LEDS_TRIGGER_PANIC n
+MAX44000 n
+MCE_AMD_INJ n
+MCP4131 n
+MEMORY_HOTPLUG_DEFAULT_ONLINE n
+NFC_PN533_I2C n
+NFC_PN533_USB n
+NMI_LOG_BUF_SHIFT 13
+NVDIMM_DAX y
+PCIE_DPC n
+PERF_EVENTS_INTEL_CSTATE y
+PERF_EVENTS_INTEL_RAPL y
+PRINTK_NMI y
+QEDE_GENEVE n
+QEDE_VXLAN n
+QED_SRIOV y
+RADIX_TREE_MULTIORDER y
+RCU_PERF_TEST n
+REGULATOR_PV88080 n
+RTC_DRV_DS1302 n
+SATA_DWC n
+SECONDARY_TRUSTED_KEYRING n
+SECURITY_LOADPIN n
+SENSORS_MAX31722 n
+SG_POOL y
+SND_SOC_INTEL_BXT_RT298_MACH n
+SND_SOC_TAS5720 n
+SND_SOC_WM8960 n
+SPI_ROCKCHIP m
+SYNC_FILE n
+TCM_QLA2XXX_DEBUG n
+TEST_HASH n
+UCSI n
+USBIP_VUDC n
+USB_DWC2_DUAL_ROLE n
+USB_DWC2_PERIPHERAL n
+USB_OHCI_HCD_SSB n
+VEML6070 n
+VIDEO_TW686X n
+VIDEO_TW686X_KH n
+VIDEO_V4L2_TPG m
+WIZNET_W5100_SPI n
+Z3FOLD n
doug@s15:~/temp-k-git/linux$

```

---

### Post by MikeMecanic on 2016-05-30
@ Kithop
 It was too late last light to try that, but adding <<unix>> is a pretty easy solution that works.  _It boots normally_ and the only things that went wrong is that there was no network icon.  Logout-login is always the solution.  I don&#146;t have Skylake but have an Intel Graphic.
 
 
 So, here’s what I did (4.7-rc1 was already installed):

  	 	 	 	   
```
sudo -i gedit /etc/initramfs-tools/modules
```
   	 	 	 	   
Add unix at the end.  Save and exit  
     	 	 	 	   
Then
 ```
sudo update-initramfs -k 4.7.0-040700rc1-generic -u
```  
```
sudo reboot
```  
  	 	 	 	   Final result:
     	 	 	 	   ```
uname -a

 Linux k 4.7.0-040700rc1-generic #201605291331 SMP Sun May 29 17:33:48 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

     	 	 	 	   ```
$ dpkg --list | grep linux-image

 ii  [COLOR=#ff3333]**linux-image**[/COLOR]-4.6.0-040600-generic                4.6.0-040600.201605151930                           amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP

 ii  [COLOR=#ff3333]**linux-image**[/COLOR]-4.7.0-040700rc1-generic             4.7.0-040700rc1.201605291331                        amd64        Linux kernel image for version 4.7.0 on 64 bit x86 SMP

```
    	 	 	 	   Thanks a lot for this one.  @ Doug thanks for replying but the <<unix>> method is much more easier.

---

### Post by Doug S on 2016-05-31
> **MikeMecanic said:**
> ... adding <<unix>> is a pretty easy solution that works.   
 
 So, here’s what I did (4.7-rc1 was already installed):
 	   
```
sudo -i gedit /etc/initramfs-tools/modules
```
   	 	 	 	   
Add unix at the end.  Save and exit  
     	 	 	 	   
Then
 ```
sudo update-initramfs -k 4.7.0-040700rc1-generic -u
```  
```
sudo reboot
```  
  	 	 	 	   Final result:
     	 	 	 	   ```
uname -a

 Linux k 4.7.0-040700rc1-generic #201605291331 SMP Sun May 29 17:33:48 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```
  @ Doug thanks for replying but the <<unix>> method is much more easier.Yes, the <<unix>> method worked for me also:
```
doug@s15:~$ [COLOR="#FF0000"]uname -a[/COLOR]
Linux s15 4.7.0-040700rc1-generic #201605291331 SMP Sun May 29 17:33:48 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
doug@s15:~$
```

---

### Post by Doug S on 2016-06-05
Kernel [4.7-rc2 is available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7-rc2-yakkety/"). I am compiling now.

Edit: Now running, seems O.K., so far.```
doug@s15:~$ uname -a
Linux s15 4.7.0-rc2-stock #48 SMP Sun Jun 5 16:49:20 PDT 2016 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by MikeMecanic on 2016-06-05
Messy splash screen at the end of the week, after Thursday updates (the one with ImageMagik and worse after Snapd upgrade:).  Removing 4.6.0 and snapd did not help, long delay to restart.   
 
 Made a fresh install today (xx).   [There is no bug in Kernel 4.6.0]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/").  So far, so good for rc-2.

                        
```
~$ dpkg --list | grep linux-image

 ii  [COLOR=#ff3333]**linux-image**[/COLOR]-4.6.0-040600-generic           4.6.0-040600.201605151930                           amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
 ii [COLOR=#ff3333]** linux-image**[/COLOR]-4.7.0-040700rc2-generic        4.7.0-040700rc2.201606051831                        amd64        Linux kernel image for version 4.7.0 on 64 bit x86 SMP

```

---

### Post by cYbercOsmOnauT on 2016-06-06
This worked fine for my nonbooting 4.6.1. I just had to change the update-initramfs line a bit.

---

### Post by jimmy-frydkaer on 2016-06-06
I did it - Succes:

```
jimmy@lechef:~$ uname -r
4.7.0-040700rc2-lowlatency
jimmy@lechef:~$ 



```

---

### Post by mikedawson2013 on 2016-06-06
I just installed 4.7rc2 and it booted up fine. Can I remove unix from [COLOR=#000000][FONT=&quot]/etc/initramfs-tools/modules[/FONT][/COLOR]?

---

### Post by Doug S on 2016-06-06
> **mikedawson2013 said:**
> I just installed 4.7rc2 and it booted up fine. Can I remove unix from [COLOR=#000000][FONT=&quot]/etc/initramfs-tools/modules[/FONT][/COLOR]?that is a good question. 
No, it does not seem to be needed anymore. The guilty kernel configuration change appears to have been reverted.

```

doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]scripts/diffconfig .config-4.7.0-040700rc1-generic .config-4.7.0-040700rc2-generic[/COLOR]
-DEVPTS_MULTIPLE_INSTANCES y
 [COLOR="#FF0000"]UNIX m -> y[/COLOR]
+IPV6_FOU m
+IPV6_FOU_TUNNEL m
+TEST_UUID n

```

---

### Post by fyfe54 on 2016-06-11
4.7rc2 was updated on June 10th in [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline) and booted perfectly .  Running with no issues for me, so far.

---

### Post by Doug S on 2016-06-11
> **fyfe54 said:**
> 4.7rc2 was updated on June 10th in [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline) and booted perfectly .Interesting. It can pretty much only be a change in kernel configuration, since changes to -rc2 will become -rc3. The differences are:
```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]scripts/diffconfig .config-4.7.0-040700rc2-generic.old .config-4.7.0-040700rc2-generic[/COLOR]
 CPU_FREQ_STAT y -> m
 CRC16 y -> m
 CRYPTO_CRC32C y -> m
 DNS_RESOLVER y -> m
 EDD y -> m
 EFIVAR_FS y -> m
 EFI_VARS y -> m
 EXT4_FS y -> m
 FS_MBCACHE y -> m
 GPIO_LYNXPOINT y -> m
 I2C_CHARDEV y -> m
 JBD2 y -> m
 LUSTRE_FS n -> m
 X86_PMEM_LEGACY y -> m
+LUSTRE_DEBUG_EXPENSIVE_CHECK n
+LUSTRE_LLITE_LLOOP m
+LUSTRE_OBD_MAX_IOCTL_BUFFER 8192
```

---

### Post by Doug S on 2016-06-12
Kernel 4.7-rc3 is has been released (hours earlier than normal), but is not yet on the [Ubuntu Mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"). I'm compiling now, using the updated Ubuntu kernel configuration from a couple of days ago (see previous posts).

EDIT: It is now available via the [Ubuntu mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7-rc3-yakkety/").

---

### Post by MikeMecanic on 2016-06-12
Perfect week!  S-T-A-B-L-E
 
 
 ```
~$ dpkg --list | grep linux-image
 ii  [COLOR=#ff3333]**linux-image**[/COLOR]-4.7.0-040700rc3-generic        4.7.0-040700rc3.201606121131                        amd64        Linux kernel image for version 4.7.0 on 64 bit x86 SMP
  
```

---

### Post by jimmy-frydkaer on 2016-06-12
Boots perfectly on my HP Pavillion Elite:

 ```
uname -a
Linux lechef 4.7.0-040700rc3-lowlatency #201606121131 SMP PREEMPT  Sun Jun 12 15:39:36 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by mrfelker on 2016-06-13
I had many of the problems reported here with RC1.  However I had none with RC2.  Now I've installed the just released RC3.  My host is openSUSE Leap 42.2 Alpha 1.  I'm running ubuntuMATE Yakkey in a VMware Ws 12.1.1 VM.  Here's my output from uname -r

Linux ubuntu 4.7.0-040700rc3-generic #201606121131 SMP Sun Jun 12 15:34:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Works great! Extremely smooth and very fast. Can't tell the difference in speed from running on my physical machine.

---

### Post by MikeMecanic on 2016-06-17
The SKL message still there and it is the third time that it comes out of update manager (no incidence each time).  Too many problems at the beginning of the week to run rc3 alone: Unstable DE.  Even made a fresh install but alongside 4.4.0.25 it is back to normal.
 
 
 I’m getting black screen on boot up more frequently now, especially if I pass by the Grub menu. Unless it was there before (trials and errors), there seems to be a new feature for that:  
 
 
 **CTRL+ALT+F1** a few times and then **CTRL+ALT+DELETE** will reboot the machine if you wait for the boot sequence to complete (with no video output, automatic login enable).
 
 
 _It is also possible to enter the password in a black screen_ (encrypted or not) and then run the 2 shortcuts to reboot.  Will call this one under Ubuntu , <<DD>> for Double Debugging black screen issue*.
 
 
 I always have the suspend mode key stroke (HP Keyboard) to exit black screen,  but feel good to have a second one a share it with members of the community.
 
 
 Today’s updates:
```


… Setting up vim-common (2:7.4.1689-3ubuntu1.1) ...
 Setting up vim-tiny (2:7.4.1689-3ubuntu1.1) ...
 Setting up libgif7:amd64 (5.1.4-0.3~16.04) ...
 Processing triggers for initramfs-tools (0.122ubuntu8.1) ...
 [COLOR=#ff3333]**update-initramfs: Generating /boot/initrd.img-4.7.0-040700rc3-generic**[/COLOR]
 [COLOR=#ff3333]**W: Possible missing firmware /lib/firmware/i915/skl_guc_ver6.bin for module i915**[/COLOR]
 Processing triggers for libc-bin (2.23-0ubuntu3) …

```    
  	 	 	 	   [PHP]Commit Log for Fri Jun 17 19:59:55 2016

 
 
 
 
 Upgraded the following packages:
 console-setup (1.108ubuntu15.1) to 1.108ubuntu15.2
 console-setup-linux (1.108ubuntu15.1) to 1.108ubuntu15.2
 grub-common (2.02~beta2-36ubuntu3) to 2.02~beta2-36ubuntu3.1
 grub-pc (2.02~beta2-36ubuntu3) to 2.02~beta2-36ubuntu3.1
 grub-pc-bin (2.02~beta2-36ubuntu3) to 2.02~beta2-36ubuntu3.1
 grub2-common (2.02~beta2-36ubuntu3) to 2.02~beta2-36ubuntu3.1
 keyboard-configuration (1.108ubuntu15.1) to 1.108ubuntu15.2

 libgif7 (5.1.2-0.2) to 5.1.4-0.3~16.04
 vim-common (2:7.4.1689-3ubuntu1) to 2:7.4.1689-3ubuntu1.1
 vim-tiny (2:7.4.1689-3ubuntu1) to 2:7.4.1689-3ubuntu1.
[/PHP]
  	 	 	 	   All the best,
 
 
 *Ubuntu DD: Double Debugging Black Screen Issue Xenial Xerus
 Mikemecanic, Ubuntu Forums, June 17[SUP]th[/SUP], 2016

---

### Post by Doug S on 2016-06-20
[Kernel 4.3-rc4 is available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7-rc4-yakkety/"). It'll be a day or two before I can try it.

---

### Post by jimmy-frydkaer on 2016-06-20
Can't find the deb-files for the 20th, only those for the 19th

---

### Post by jimmy-frydkaer on 2016-06-20
Just installed the kernel from 6-19-2016; 4.7.0.0.999 (I believe it is) and **BOY** is that a *fast*&#8203; kernel? I'm glad I tried that install, it just works on my yakkety on my Lenovo Ideapad 100

---

### Post by Doug S on 2016-06-20
> **jimmy-frydkaer said:**
> Can't find the deb-files for the 20th, only those for the 19thOh Crap, I missed that. I'll go on IRC and ask if they will fix it. I see from the build logs that it appears to be a permissions issue.

I am running my own compiled version now.```
Linux s15 4.7.0-rc4-stock #55 SMP Mon Jun 20 07:45:03 PDT 2016 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2016-06-20
The build issue was fixed, and the .debs for -rc4 are now there.

---

### Post by jimmy-frydkaer on 2016-06-20
And there we are

> uname -a

Linux selap 4.7.0-040700rc4-lowlatency #201606201235 SMP PREEMPT Mon Jun 20 16:40:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


And mann-oh-mann is that a speedy kernel on boot up

---

### Post by jimmy-frydkaer on 2016-06-21
And now i t went on to my HP Pavillion Elite:

> jimmy@leboss:~$ uname -a

Linux leboss 4.7.0-040700rc4-lowlatency #201606201235 SMP PREEMPT Mon Jun 20 16:40:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

jimmy@leboss:~$ 




Edit:

And *now* I got  a [I]responsive  system 

[/I]:popcorn:

---

### Post by cariboo on 2016-06-21
Just out of curiosity, how much faster? My start up:

```
systemd-analyze
Startup finished in 225us (firmware) + 205us (loader) + 2.605s (kernel) + 1.785s (userspace) = 4.391s
```

using:

```
uname -a
Linux skynet 4.4.0-25-generic #44-Ubuntu SMP Fri Jun 10 18:19:48 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by jimmy-frydkaer on 2016-06-21
Five year old but upgraded system:

CPU - Intel Core i7 3,4 GHz
16 GB DDR RAM
7200 rpm WD hdd

boot up time on kernel 4.4.0.25 is about 55 sec from power up to login
boot up time on kernel 4.7 RC4 is 30 sec from power up to login - I believe it's okay for a system that old with yakkety

---

### Post by Doug S on 2016-06-21
For what it's worth, here is the startup info from my computer (16.04 server, i7-2600K. Currently with some startup issue with LXD containers):
```
$ systemd-analyze
Startup finished in 7.410s (kernel) + 25.639s (userspace) = 33.049s
$ uname -a
Linux s15 4.7.0-rc4-stock #55 SMP Mon Jun 20 07:45:03 PDT 2016 x86_64 x86_64 x86_64 GNU/Linux

$ uname -a
Linux s15 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
$ systemd-analyze
Startup finished in 7.286s (kernel) + 24.845s (userspace) = 32.131s

```

---

### Post by QDR06VV9 on 2016-06-21
Just a tad bit quicker...but this series of kernels is shaping up quite nicely.:D
```
$ systemd-analyze
Startup finished in 5.751s (kernel) + 26.483s (userspace) = 32.235s
me@me-Aspire-M3300:~$ uname -r
4.4.0-24-generic
****************************************
$ systemd-analyze
Startup finished in 5.592s (kernel) + 26.672s (userspace) = 32.264s
~$ uname -r
4.7.0-040700rc4-lowlatency
```
And one big bonus I still have sound...LOL

---

### Post by jimmy-frydkaer on 2016-06-22
Okay it's even better than timing on my watch

> jimmy@leboss:~$ systemd-analyze

Startup finished in 2.910s (kernel) + 24.797s (userspace) = 27.707s
____-

jimmy@leboss:~$ uname -r

4.7.0-040700rc4-lowlatency

Edit:

This is on a five year old HP Pavillion with: CPU Core i7 3.4 GHz, 16 GB DDR3 RAM and 7200 rpm WD hdd so it's well done, I suppose

---

### Post by MikeMecanic on 2016-06-23
Faster?  I would say bigger.
 
 
 ```
$ systemd-analyze _for __**4.4.0.25**__ alone after a fresh install_
Startup finished in 2.704s (kernel) + 10.329s (userspace) = 13.033s
$ systemd-analyze _for __**4.4.0.27**__ with .25_
Startup finished in 2.814s (kernel) + 10.263s (userspace) = 13.077s
$ systemd-analyze _for __**4.7-rc4**__ alone or with .27_
Startup finished in 5.114s (kernel) + 12.576s (userspace) = 17.690s
$ df -h | grep ^/dev/sda3
[COLOR=#ff3333]**/dev/sda3**[/COLOR]       236M   65M  159M  29% /boot
$ dpkg --list | grep linux-image
ii [COLOR=#ff3333]** linux-image**[/COLOR]-4.7.0-040700rc4-generic        4.7.0-040700rc4.201606201235                                amd64        Linux kernel image for version 4.7.0 on 64 bit x86 SMP

```

---

### Post by MikeMecanic on 2016-06-27
Rc4 was a perfect one, no bug on Kylin (20160619_xx).
 Will be traveling for a pretty long period.  Good continuity!
 
 
 ```
Linux xx 4.7.0-040700rc5-generic #201606262232 SMP Mon Jun 27 02:34:07 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


```

---

### Post by IanW on 2016-06-27
[RC5 has landed]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7-rc5-yakkety/").

---

### Post by jimmy-frydkaer on 2016-06-27
RC5 is installed without a flaw

> jimmy@jfd:~$ uname -a

Linux jfd 4.7.0-040700rc5-lowlatency #201606262232 SMP PREEMPT Mon Jun 27 02:44:19 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux



---

### Post by jimmy-frydkaer on 2016-06-27
On my old Pavillion Elite (Core i7 3.4 GHz, 16 GB DDR3 RAM and 7200 rpm WD hdd) I get this systemd-analyze on a LVM install and kernel 4.7RC5

> jimmy@jfd:~$ systemd-analyze

Startup finished in 25.291s (kernel) + 27.065s (userspace) = 52.356s



It's a long boot time, I know, but I'm surprised to se that on a LVM install time is under one minut, I'd expeted a slower boot

---

### Post by Doug S on 2016-06-29
I am just catching up.

> **MikeMecanic said:**
> Faster?  I would say bigger.
 
 
 ```
$ systemd-analyze _for __**4.4.0.25**__ alone after a fresh install_
Startup finished in 2.704s (kernel) + 10.329s (userspace) = 13.033s
$ systemd-analyze _for __**4.4.0.27**__ with .25_
Startup finished in 2.814s (kernel) + 10.263s (userspace) = 13.077s
$ systemd-analyze _for __**4.7-rc4**__ alone or with .27_
Startup finished in 5.114s (kernel) + 12.576s (userspace) = 17.690s
$ df -h | grep ^/dev/sda3
[COLOR=#ff3333]**/dev/sda3**[/COLOR]       236M   65M  159M  29% /boot
$ dpkg --list | grep linux-image
ii [COLOR=#ff3333]** linux-image**[/COLOR]-4.7.0-040700rc4-generic        4.7.0-040700rc4.201606201235                                amd64        Linux kernel image for version 4.7.0 on 64 bit x86 SMP

```

Mike: I never did understand your post, as I had not observed any significant increase in the .deb file size or whatever.

All: There is a staggering reduction in the .deb file size for -rc5. The last time I synchronized with the Ubuntu kernel configuration was -rc2, and the differences between the -rc5 kernel configuration are overwhelming.

Aghh... For those that want to try it, like me, I see that the new scheduler based CPU frequency scaling governor for the acpi-cpufreq driver is now included as a module.
Oh, I also see that the default scheduler has changed, from "deadline" to "cfq".
I could go on and on, but the suggestion to users is that they review the differences themselves, looking for any changes that might be relevant to their particular situation.

EDIT 1: Holy crap!!! My own compile took:```
real    45m37.520s
user    290m42.136s
sys     18m55.332s

```Whereas it typically took about 22 minutes before. Investigation pending.
EDIT 2: I have not been able to repeat the above mentioned much longer compile time.
The available CPU frequency scaling governors seems messed up to me:```

doug@s15:~/temp$ uname -a
Linux s15 4.7.0-rc5-stock #74 SMP Wed Jun 29 08:11:59 PDT 2016 x86_64 x86_64 x86_64 GNU/Linux
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpufreq/policy*/scaling_available_governors
ondemand performance
ondemand performance
ondemand performance
ondemand performance
ondemand performance
ondemand performance
ondemand performance
ondemand performance

```Because I sometimes use the other ones that used to be available.
```
Linux s15 4.6.0-040600-generic #201605151930 SMP Sun May 15 23:32:59 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
doug@s15:~$ cat /sys/devices/system/cpu/cpufreq/policy*/scaling_available_governors
conservative ondemand userspace powersave performance
conservative ondemand userspace powersave performance
conservative ondemand userspace powersave performance
conservative ondemand userspace powersave performance
conservative ondemand userspace powersave performance
conservative ondemand userspace powersave performance
conservative ondemand userspace powersave performance
conservative ondemand userspace powersave performance
```

EDIT 3:  Oh, if a CPU frequency governor is a module instead of built in, then it won't appear in the list of available governors until it is either loaded via attempting to use it, or force loaded via "modprobe". My list now is:
```
doug@s15:~/test_kernels$ cat /sys/devices/system/cpu/cpufreq/policy*/scaling_available_governors
schedutil powersave ondemand performance
schedutil powersave ondemand performance
schedutil powersave ondemand performance
schedutil powersave ondemand performance
schedutil powersave ondemand performance
schedutil powersave ondemand performance
schedutil powersave ondemand performance
schedutil powersave ondemand performance
```because I forgot and switched to "powersave" and because I did "sudo modprobe cpufreq_schedutil".

---

### Post by Doug S on 2016-07-04
Kernel [4.7-rc6]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7-rc6-yakkety/") is available. The Ubuntu kernel configuration is the same as -rc5, so the big config changes were between -rc4 and -rc5 (see previous post).
I'm not running it yet, as it is still compiling.

EDIT: Been running for over a day now without issues.

---

### Post by rowan-potgieter on 2016-07-05
I must be honest I have no idea where to log this bug - I tried using "ubuntu-bug linux" but since I've switched to a non-standard kernel I get blocked. I also have an issue with Kernel 4.7 rc6 though...

I use my laptop (details below) with an HP dock connected to 2 x Dell Display Port monitors. I cannot remember the exact dates but at the beginning of June my setup was fine (this is a brand new laptop so it was a fresh install). At some point in June I believe there was a kernel update and after reboot my laptop would hang during boot. I figured out that the issue was related to whenever the dock was connected. Looking at the dmesg output were intel graphics failures when the 2 monitors were initialised.
I switched to the intel nightly kernel from 2016-06-06-yakkety and this has resolved my issues. This is still not perfect because my screens occasionally go "blank" for a second or 2 when moving the mouse between them but it is 100% useable. 
I am logging this bug because today I tried the 4.7-rc6-yakkety kernel and the issue has not been resolved - my laptop locks up when starting the 2 x Display Port monitors. 
    
    some info from "sudo lshw"
    description: Notebook
    product: HP EliteBook 820 G3 (T9X46EA#ACQ)
    vendor: HP
       *-display
             description: VGA compatible controller
             product: Sky Lake Integrated Graphics
             vendor: Intel Corporation

If there is a better place/way to log this issue please let me know :-)

---

### Post by mikedawson2013 on 2016-07-11
[4.7-rc7]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7-rc7/") is out! Just installed it. Everything works fine so far.

---

### Post by Doug S on 2016-07-27
Kernel [4.7]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7/") has been available for a few days. I have been running it for a few hours now without issues. I compile my own, and did not check if the Ubuntu kernel configuration changed between 4.7-rc7 and 4.7, but at some point I will.

---

### Post by mave-m on 2016-08-03
Today i updated my 4.7 kernel as there seems to be a new build, but i still get the i915 module errors about missing firmware for skylake based systems. 

> update-initramfs: Generating /boot/initrd.img-4.7.0-040700-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915
W: Possible missing firmware /lib/firmware/i915/skl_guc_ver6.bin for module i915

These are the currently installed packages:

> linux-headers-4.7.0-040700_4.7.0-040700.201608021801_all.deb
linux-headers-4.7.0-040700-generic_4.7.0-040700.201608021801_amd64.deb
linux-image-4.7.0-040700-generic_4.7.0-040700.201608021801_amd64.deb


---

### Post by Doug S on 2016-08-03
> **mave-m said:**
> Today i updated my 4.7 kernel as there seems to be a new build, but i still get the i915 module errors about missing firmware for skylake based systems.I still get those messages also. As mentioned somewhere earlier, since I don't have a skylake (and now kbl, whatever the actual name is), I don't care.

---

### Post by mave-m on 2016-08-04
> **Doug S said:**
> I still get those messages also. As mentioned somewhere earlier, since I don't have a skylake (and now kbl, whatever the actual name is), I don't care.
Good for you, i have a skylake-based system so i do care. "kbl" is Kaby Lake, Skylake's successor.

---

### Post by Doug S on 2016-08-04
> **mave-m said:**
> Good for you, i have a skylake-based system so i do care. "kbl" is Kaby Lake, Skylake's successor.You could look at [this]("https://ubuntuforums.org/showthread.php?t=2326072"). And try [here]("https://01.org/linuxgraphics/intel-linux-graphics-firmwares"), from the link therein. I do not know if you would then need to manually set a link from /lib/firmware/i915/skl_guc_ver6.bin to /lib/firmware/i915/skl_guc_ver6_1.bin, similar to:```
doug@s15:~/c$ ls -l /lib/firmware/i915/skl*
-rw-r--r-- 1 root root   8824 Apr 25 05:56 /lib/firmware/i915/skl_dmc_ver1_23.bin
-rw-r--r-- 1 root root   8928 Apr 25 05:56 /lib/firmware/i915/skl_dmc_ver1_26.bin
lrwxrwxrwx 1 root root     19 Apr 25 05:56 [COLOR="#00FFFF"]/lib/firmware/i915/skl_dmc_ver1.bin[/COLOR] -> skl_dmc_ver1_26.bin
-rw-r--r-- 1 root root 109636 Apr 25 05:56 /lib/firmware/i915/skl_guc_ver1_1059.bin
lrwxrwxrwx 1 root root     21 Apr 25 05:56 [COLOR="#00FFFF"]/lib/firmware/i915/skl_guc_ver1.bin[/COLOR] -> skl_guc_ver1_1059.bin
-rw-r--r-- 1 root root 128320 Apr 25 05:56 /lib/firmware/i915/skl_guc_ver4_3.bin
lrwxrwxrwx 1 root root     18 Apr 25 05:56 [COLOR="#00FFFF"]/lib/firmware/i915/skl_guc_ver4.bin[/COLOR] -> skl_guc_ver4_3.bin
```Or if that would happen during install.

---

### Post by Doug S on 2016-09-02
> **Doug S said:**
> All: There is a staggering reduction in the .deb file size for -rc5. The last time I synchronized with the Ubuntu kernel configuration was -rc2, and the differences between the -rc5 kernel configuration are overwhelming.

Aghh... For those that want to try it, like me, I see that the new scheduler based CPU frequency scaling governor for the acpi-cpufreq driver is now included as a module.
Oh, I also see that the default scheduler has changed, from "deadline" to "cfq".
I could go on and on, but the suggestion to users is that they review the differences themselves, looking for any changes that might be relevant to their particular situation.
Immediately after boot the reported load average is, for example, 266.59, 63.19, 20.92 (1, 5, 15 minute load averages). I have traced this back to the massive kernel configuration changes between kernel 4.7-rc4 and 4.7-rc5, but haven't figured out which specific change. Such load average numbers could be from a one time load of very approximately 4000, meaning it seems likely that it isn't being initialized properly. It isn't clear to me how such an issue would be kernel config related as opposed to kernel code related.

EDIT: So as to catch the load average as soon as possible after boot I added a script to the end of the boot sequence, and caught 24 uptimes:

```
[   25.009523]  08:01:57 up 0 min,  0 users,  load average: 271.03, 58.94, 19.23
[   30.011377]  08:02:02 up 0 min,  0 users,  load average: 296.57, 67.76, 22.29
[   35.012966]  08:02:07 up 0 min,  0 users,  load average: 430.90, 99.40, 32.78
[   40.014476]  08:02:12 up 0 min,  0 users,  load average: 396.39, 97.75, 32.60
[   45.015993]  08:02:17 up 0 min,  0 users,  load average: 364.65, 96.13, 32.42
[   49.958482]  08:02:22 up 0 min,  0 users,  load average: 335.45, 94.53, 32.25
[   54.830996]  08:02:27 up 0 min,  0 users,  load average: 308.59, 92.96, 32.08
[   59.765276]  08:02:32 up 1 min,  0 users,  load average: 283.88, 91.42, 31.90
[   64.731895]  08:02:37 up 1 min,  0 users,  load average: 261.14, 89.90, 31.73
[   69.715492]  08:02:42 up 1 min,  0 users,  load average: 240.23, 88.41, 31.56
[   74.707682]  08:02:47 up 1 min,  0 users,  load average: 220.99, 86.94, 31.39
[   79.704409]  08:02:52 up 1 min,  0 users,  load average: 203.30, 85.50, 31.22
[   84.702339]  08:02:57 up 1 min,  0 users,  load average: 187.02, 84.08, 31.06
[   89.701102]  08:03:02 up 1 min,  0 users,  load average: 172.04, 82.68, 30.89
[   94.701362]  08:03:07 up 1 min,  0 users,  load average: 158.26, 81.31, 30.72
[   99.702528]  08:03:12 up 1 min,  0 users,  load average: 145.59, 79.96, 30.56
[  104.703988]  08:03:17 up 1 min,  0 users,  load average: 133.93, 78.63, 30.39
[  109.705740]  08:03:22 up 1 min,  0 users,  load average: 123.21, 77.33, 30.23
[  114.707627]  08:03:27 up 1 min,  0 users,  load average: 113.34, 76.04, 30.07
[  119.709598]  08:03:32 up 2 min,  0 users,  load average: 104.26, 74.78, 29.91
[  124.711804]  08:03:37 up 2 min,  0 users,  load average: 95.91, 73.54, 29.74
[  129.714023]  08:03:42 up 2 min,  0 users,  load average: 88.23, 72.32, 29.58
[  134.716183]  08:03:47 up 2 min,  0 users,  load average: 81.17, 71.12, 29.43
[  139.718354]  08:03:52 up 2 min,  0 users,  load average: 74.67, 69.93, 29.27

```To get those numbers the load samples would have been approximately 590 at 30 seconds and 1985 at 35 seconds and 0 thereafter.

EDIT: see [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1626564")

---

