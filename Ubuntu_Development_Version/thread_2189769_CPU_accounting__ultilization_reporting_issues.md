---
title: "CPU accounting / ultilization reporting issues"
date: 2013-11-23
forum: Ubuntu Development Version
---

### Post by Doug S on 2013-11-23
I am having issues with totally erroneous numbers being reported for CPU user, system, idle, and wait percentages on my older server computer (the one I use for server edition minimum requirements testing). i.e. when using tools such as "top" or "vmstat". I do not observe the issue on a 64 bit 14.04 server VM.

Normally, with an otherwise idle server, we expect to observe little activity:```
doug@test-smy:~/configs$ [COLOR=#ff0000]vmstat 20[/COLOR]
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs [COLOR=#ff0000]us sy id wa[/COLOR]
 0  0    292   3952   4936  48668    0    0   247     5  265  151 14  7 77  2
 1  0    292   3912   4944  48708    0    0     2     2  252   50  0  0 100  0
 1  0    292   3912   4944  48708    0    0     0     0  252   47  0  0 100  0
 0  0    292   3900   4952  48708    0    0     0     2  252   49  0  0 99  1
 0  0    292   3900   4952  48708    0    0     0     1  252   51  0  0 100  0
 0  0    292   2636   4960  49928    0    0    61     1  253   56  0  0 99  1
```The attached graphs show what I am observing with the two most recent trusty kernels. I have tested many many kernels (including 3.13RC1), and believe I have the issue isolated down to the kernel configuration file differences between saucy and trusty. I used the two otherwise same kernels (3.12.0-031200-generic) from the kernel ppa for both saucy and trusty to come to this conclusion. There a lot of configuration differences. The differences file:```
162c162
< # CONFIG_USER_NS is not set
---
> CONFIG_USER_NS=y
165c165
< # CONFIG_UIDGID_STRICT_TYPE_CHECKS is not set
---
> CONFIG_UIDGID_STRICT_TYPE_CHECKS=y
297c297
< # CONFIG_BLK_CMDLINE_PARSER is not set
---
> CONFIG_BLK_CMDLINE_PARSER=y
328c328
< # CONFIG_CMDLINE_PARTITION is not set
---
> CONFIG_CMDLINE_PARTITION=y
383c383
< # CONFIG_KVM_DEBUG_FS is not set
---
> CONFIG_KVM_DEBUG_FS=y
780c780
< # CONFIG_X86_SYSFB is not set
---
> CONFIG_X86_SYSFB=y
941a942
> CONFIG_NETFILTER_SYNPROXY=m
1092c1093
< # CONFIG_IP_NF_TARGET_SYNPROXY is not set
---
> CONFIG_IP_NF_TARGET_SYNPROXY=m
1130c1131
< # CONFIG_IP6_NF_TARGET_SYNPROXY is not set
---
> CONFIG_IP6_NF_TARGET_SYNPROXY=m
1264c1265
< # CONFIG_NET_SCH_FQ is not set
---
> CONFIG_NET_SCH_FQ=m
1972c1973
< # CONFIG_SCSI_ESAS2R is not set
---
> CONFIG_SCSI_ESAS2R=m
2433c2434
< # CONFIG_I40E is not set
---
> CONFIG_I40E=m
2610c2611
< # CONFIG_USB_NET_SR9700 is not set
---
> CONFIG_USB_NET_SR9700=m
2799c2800
< # CONFIG_RT2800USB_RT3573 is not set
---
> CONFIG_RT2800USB_RT3573=y
3266c3267
< # CONFIG_INPUT_IDEAPAD_SLIDEBAR is not set
---
> CONFIG_INPUT_IDEAPAD_SLIDEBAR=m
3371c3372
< # CONFIG_SERIAL_ST_ASC is not set
---
> CONFIG_SERIAL_ST_ASC=m
3426c3427
< # CONFIG_TCG_XEN is not set
---
> CONFIG_TCG_XEN=m
3525c3526
< # CONFIG_SPI_FSL_DSPI is not set
---
> CONFIG_SPI_FSL_DSPI=m
3587c3588
< # CONFIG_PINCTRL_BAYTRAIL is not set
---
> CONFIG_PINCTRL_BAYTRAIL=y
3604c3605
< # CONFIG_GPIO_F7188X is not set
---
> CONFIG_GPIO_F7188X=m
3658c3659
< # CONFIG_GPIO_KEMPLD is not set
---
> CONFIG_GPIO_KEMPLD=m
3736c3737
< # CONFIG_CHARGER_BQ24190 is not set
---
> CONFIG_CHARGER_BQ24190=m
3788c3789
< # CONFIG_SENSORS_HTU21 is not set
---
> CONFIG_SENSORS_HTU21=m
4008c4009
< # CONFIG_BCMA_HOST_SOC is not set
---
> CONFIG_BCMA_HOST_SOC=y
4029c4030
< # CONFIG_MFD_DA9063 is not set
---
> CONFIG_MFD_DA9063=y
4117c4118
< # CONFIG_REGULATOR_88PM800 is not set
---
> CONFIG_REGULATOR_88PM800=m
4128c4129,4130
< # CONFIG_REGULATOR_DA9210 is not set
---
> CONFIG_REGULATOR_DA9063=m
> CONFIG_REGULATOR_DA9210=m
4154c4156
< # CONFIG_REGULATOR_PFUZE100 is not set
---
> CONFIG_REGULATOR_PFUZE100=m
4284c4286
< # CONFIG_USB_GSPCA_STK1135 is not set
---
> CONFIG_USB_GSPCA_STK1135=m
4314c4316,4318
< # CONFIG_VIDEO_STK1160_COMMON is not set
---
> CONFIG_VIDEO_STK1160_COMMON=m
> CONFIG_VIDEO_STK1160_AC97=y
> CONFIG_VIDEO_STK1160=m
4461c4465
< # CONFIG_VIDEO_RCAR_VIN is not set
---
> CONFIG_VIDEO_RCAR_VIN=m
4842c4846
< # CONFIG_DRM_I915_PRELIMINARY_HW_SUPPORT is not set
---
> CONFIG_DRM_I915_PRELIMINARY_HW_SUPPORT=y
4864c4868
< # CONFIG_FB_BOOT_VESA_SUPPORT is not set
---
> CONFIG_FB_BOOT_VESA_SUPPORT=y
4895c4899
< # CONFIG_FB_VESA is not set
---
> CONFIG_FB_VESA=y
5019,5021c5023,5025
< # CONFIG_BACKLIGHT_GPIO is not set
< # CONFIG_BACKLIGHT_LV5207LP is not set
< # CONFIG_BACKLIGHT_BD6107 is not set
---
> CONFIG_BACKLIGHT_GPIO=m
> CONFIG_BACKLIGHT_LV5207LP=m
> CONFIG_BACKLIGHT_BD6107=m
5334c5338
< # CONFIG_HID_XINMO is not set
---
> CONFIG_HID_XINMO=m
5394c5398
< # CONFIG_USB_FOTG210_HCD is not set
---
> CONFIG_USB_FOTG210_HCD=m
5484c5488
< # CONFIG_USB_SERIAL_SIMPLE is not set
---
> CONFIG_USB_SERIAL_SIMPLE=m
5571c5575
< # CONFIG_USB_EHSET_TEST_FIXTURE is not set
---
> CONFIG_USB_EHSET_TEST_FIXTURE=m
5587c5591,5592
< # CONFIG_AM335X_PHY_USB is not set
---
> CONFIG_AM335X_CONTROL_USB=m
> CONFIG_AM335X_PHY_USB=m
5712c5717
< # CONFIG_MS_BLOCK is not set
---
> CONFIG_MS_BLOCK=m
5742c5747
< # CONFIG_LEDS_LP8501 is not set
---
> CONFIG_LEDS_LP8501=m
5746c5751
< # CONFIG_LEDS_PCA963X is not set
---
> CONFIG_LEDS_PCA963X=m
5929c5934
< # CONFIG_RTC_DRV_MOXART is not set
---
> CONFIG_RTC_DRV_MOXART=m
5972c5977
< # CONFIG_UIO_MF624 is not set
---
> CONFIG_UIO_MF624=m
5984,5985c5989,5990
< CONFIG_VIRTIO_BALLOON=m
< CONFIG_VIRTIO_MMIO=m
---
> CONFIG_VIRTIO_BALLOON=y
> CONFIG_VIRTIO_MMIO=y
6173c6178,6180
< # CONFIG_R8188EU is not set
---
> CONFIG_R8188EU=m
> CONFIG_88EU_AP_MODE=y
> CONFIG_88EU_P2P=y
6337c6344
< # CONFIG_USB_MSI3101 is not set
---
> CONFIG_USB_MSI3101=m
6362c6369
< # CONFIG_LTE_GDM724X is not set
---
> CONFIG_LTE_GDM724X=m
6372c6379,6386
< # CONFIG_LUSTRE_FS is not set
---
> CONFIG_LUSTRE_FS=m
> CONFIG_LUSTRE_OBD_MAX_IOCTL_BUFFER=8192
> # CONFIG_LUSTRE_DEBUG_EXPENSIVE_CHECK is not set
> CONFIG_LUSTRE_LLITE_LLOOP=y
> CONFIG_LNET=m
> CONFIG_LNET_MAX_PAYLOAD=1048576
> CONFIG_LNET_SELFTEST=m
> CONFIG_LNET_XPRT_IB=m
6374,6376c6388,6391
< # CONFIG_XILLYBUS is not set
< # CONFIG_DGNC is not set
< # CONFIG_DGAP is not set
---
> CONFIG_XILLYBUS=m
> CONFIG_XILLYBUS_PCIE=m
> CONFIG_DGNC=m
> CONFIG_DGAP=m
6444c6459
< # CONFIG_COMMON_CLK_S2MPS11 is not set
---
> CONFIG_COMMON_CLK_S2MPS11=m
6508c6523
< # CONFIG_BMA180 is not set
---
> CONFIG_BMA180=m
6529c6544
< # CONFIG_NAU7802 is not set
---
> CONFIG_NAU7802=m
6609c6624
< # CONFIG_APDS9300 is not set
---
> CONFIG_APDS9300=m
6640c6655
< # CONFIG_TMP006 is not set
---
> CONFIG_TMP006=m
6825c6840
< # CONFIG_HFSPLUS_FS_POSIX_ACL is not set
---
> CONFIG_HFSPLUS_FS_POSIX_ACL=y
6925c6940
< # CONFIG_CEPH_FSCACHE is not set
---
> CONFIG_CEPH_FSCACHE=y
```While there a lot of configuration differences that are obviously not the issue (or so I think), there are many that I don't know if they could be or not.
Does anyone else observe this issue?

Edit:```
Linux test-smy 3.12.0-4-generic #10-Ubuntu SMP Thu Nov 21 22:11:22 UTC 2013 i686 i686 i686 GNU/Linux
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 1
model name      : Pentium Pro
```Edit: I entered [a bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1254920").

---

### Post by Doug S on 2013-11-30
Just an update: I have isolated the issue to:```
doug@v32-serv03:~/kernel/linux-3.12.0$ diff config_def config_05
781c781
< CONFIG_X86_SYSFB=y
---
> # CONFIG_X86_SYSFB is not set
4869c4869
< CONFIG_FB_BOOT_VESA_SUPPORT=y
---
> # CONFIG_FB_BOOT_VESA_SUPPORT is not set
4900c4900
< CONFIG_FB_VESA=y
---
> # CONFIG_FB_VESA is not set
```Where config_def is the default 14.04 Ubuntu kernel configuration, and config_05 has the minimum (or so I believe) reversions to how they were in Saucy to eliminate the issue.

---

### Post by Doug S on 2014-01-08
This issue is fixed with an up to date 14.04 system.
The test computer involved has been turned off for a few weeks, so I am not certain as to exactly when the issue was fixed.

---

