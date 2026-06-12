---
title: "JBONEST RTL8821AU Kernel compile failure"
date: 2017-06-11
forum: Ubuntu/Debian BASED
---

### Post by nightforce2 on 2017-06-11
Hello,
I have been fighting the problem of figuring out how to compile this Kernel driver for this new hardware.  The current hardware is a JBonest dualband AC Adapter for extending WIFI range and allowing for better speeds and connectivity.

The first problems I noticed when trying to configure the make file for compilation was that it was missing settings for **CONFIG_PLATFORM_ARM_RPI** out of the box, so I added them as so:

```
CONFIG_PLATFORM_I386_PC = n
CONFIG_PLATFORM_ANDROID_X86 = n
CONFIG_PLATFORM_ANDROID_INTEL_X86 = n
CONFIG_PLATFORM_JB_X86 = n
CONFIG_PLATFORM_ARM_S3C2K4 = n
CONFIG_PLATFORM_ARM_PXA2XX = n
CONFIG_PLATFORM_ARM_S3C6K4 = n
CONFIG_PLATFORM_ARM_RPI    = y
```

```
ifeq ($(CONFIG_PLATFORM_ARM_RPI), y)
EXTRA_CFLAGS += -DCONFIG_LITTLE_ENDIAN
EXTRA_CFLAGS += -DCONFIG_IOCTL_CFG80211 -DRTW_USE_CFG80211_STA_EVENT
ARCH := arm
CROSS_COMPILE := 
KVER := $(shell uname -r)
KSRC := /lib/modules/$(KVER)/build
MODDESTDIR := /lib/modules/$(KVER)/kernel/drivers/net/wireless/
INSTALL_PREFIX :=
endif
```

After saving and initiating make. I get several errors pertaining to symbols missing and debug problems not being ignored as usual. Here is what I get during compilation:

[https://paste.ubuntu.com/24833311/](https://paste.ubuntu.com/24833311/)

I read a few places that it might be a kernel version problem or might be linked to debugging being enabled? Is this my case and if so. How do I continue? If not, What am I missing? Both Ubuntu 14.04 and Kali both have this exact same issue. Tried on Raspian Jesse, Ubuntu, and Kali.

Below is required information:
uname -a
```
Linux kali 4.4.50-v7 #1 SMP Fri Apr 21 01:18:29 CDT 2017 armv7l GNU/Linux
```
dmsg
[https://paste.ubuntu.com/24833333/](https://paste.ubuntu.com/24833333/)

lsusb -v
[https://paste.ubuntu.com/24833337/](https://paste.ubuntu.com/24833337/)
  
:**Update 17:49:**
After commenting out a few of the macro statements used in rtw_cmd.c and hal_com.h. A few of the errors have disappeared. Also using the command ```
make modules
``` Does not generate Module.symvers as required for compilation.

lines 410-414 of hal_com.h
```
#ifdef CONFIG_LOAD_PHY_PARA_FROM_FILE
extern char *rtw_phy_file_path;
/*extern char file_path[PATH_LENGTH_MAX];*/ <-- duplicate as it is defined somewhere else in kernel tree.
#define GetLineFromBuffer(buffer)   strsep(&buffer, "\n")
#endif

```

lines 3289-3318 rtw_cmd.c 
```
void btinfo_evt_dump(void *sel, void *buf) // This should be ok since it should not need debug code in a release build.
{
    /*struct btinfo *info = (struct btinfo *)buf;
    
    DBG_871X_SEL_NL(sel, "cid:0x%02x, len:%u\n", info->cid, info->len);

    if (info->len > 2)
        DBG_871X_SEL_NL(sel, "byte2:%s%s%s%s%s%s%s%s\n"
            , info->bConnection?"bConnection ":""
            , info->bSCOeSCO?"bSCOeSCO ":""
            , info->bInQPage?"bInQPage ":""
            , info->bACLBusy?"bACLBusy ":""
            , info->bSCOBusy?"bSCOBusy ":""
            , info->bHID?"bHID ":""
            , info->bA2DP?"bA2DP ":""
            , info->bFTP?"bFTP":""
        );

    if (info->len > 3)
        DBG_871X_SEL_NL(sel, "retry_cnt:%u\n", info->retry_cnt);

    if (info->len > 4)
        DBG_871X_SEL_NL(sel, "rssi:%u\n", info->rssi);

    if (info->len > 5)
        DBG_871X_SEL_NL(sel, "byte5:%s%s\n"
            , info->eSCO_SCO?"eSCO_SCO ":""
            , info->Master_Slave?"Master_Slave ":""
        );*/
}
```

New errors are as follows:
```
# make modules
make ARCH=arm CROSS_COMPILE= -C /lib/modules/4.4.50-v7/build M=/root/Desktop/jbonest/Driver/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51  modules
make[1]: Entering directory '/usr/src/kernel'

  WARNING: Symbol version dump ./Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/Desktop/jbonest/Driver/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o
/bin/sh: 1: ./scripts/recordmcount: Exec format error
scripts/Makefile.build:258: recipe for target '/root/Desktop/jbonest/Driver/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o' failed
make[2]: *** [/root/Desktop/jbonest/Driver/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o] Error 2
Makefile:1402: recipe for target '_module_/root/Desktop/jbonest/Driver/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51' failed
make[1]: *** [_module_/root/Desktop/jbonest/Driver/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51] Error 2
make[1]: Leaving directory '/usr/src/kernel'
Makefile:1563: recipe for target 'modules' failed
make: *** [modules] Error 2

```

---

### Post by jeremy31 on 2017-06-11
*Thread moved to **Ubuntu/Debian BASED**.*
I am not sure about Kali but for Ubuntu you can find the Modules.symvers at  /usr/src/linux-headers-$(uname -r)/Module.symvers

But there are quite a few other errors while compiling.  You might want to see if there is rtl8821au source code on github that works

---

### Post by nightforce2 on 2017-06-11
Ty for the info Jeremy. Will go try that out and see how far it helps. Never truly had to do this before. Learning in the process. So far both arm systems do not have the kernel src in /usr/src/. Checking Ubuntu no.

---

### Post by SeijiSensei on 2017-06-12
I just compiled the RTL8821AU driver yesterday using the source code here:  [https://github.com/diederikdehaas/rtl8812AU](https://github.com/diederikdehaas/rtl8812AU)

I downloaded rtl8812AU-driver-4.3.14.zip, expanded it, and ran "make; sudo make install".  Then I plugged in my TP-LINK AC1200 USB adapter.  It connected on 5 GHz and reports an 867 Mbit transfer rate.

I'm on 14.04 with kernel 4.4.0-66-generic.  I believe some more recent kernels have a [pre-built driver]("https://packages.ubuntu.com/xenial/kernel/rtl8812au-dkms") that can be installed with apt.

---

### Post by nightforce2 on 2017-06-12
Jeremy31,
The location worked like a charm. Got the kernel to compile after heavy editing of the source of the driver that came  with the hardware. Still having trouble with driver  or actual hardware. The led does not lightup. 'Lsusb -v' shows realtek USB is installed in usb port.

---

### Post by nightforce2 on 2017-06-12
SeijiSensei, Will try your  driver suggestion next after I get a good look at the source code. Do you know where to get './make_drive'? It is missing. Need it t select chipset.

---

### Post by nightforce2 on 2017-06-12
SeijiSensei,
Compiled very smoothly. No warnings. No errors. Works like a charm so far. Although the download speed from ifconfig is saying 17kb down and 16kb up. Have noticed this be normal and thus used a different bandwidth tool to measure with??

---

### Post by SeijiSensei on 2017-06-15
I don't see anything in the output of ifconfig that reports on the connection's speed.  On my 14.04 system it only shows packets and bytes transmitted and received as the command always has.

The iwconfig command, on the other hand, reports the "Bit Rate:"
```

$ iwconfig
wlan1     IEEE 802.11AC  ESSID:"XXXXX-5"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:5.18 GHz  Access Point: 98:DE:D0:7D:91:32   
          Bit Rate:867 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=89/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

With my older N adapter, I had bit rates in the 54-72 Mbit range.

---

### Post by nightforce2 on 2017-06-19
Mine is connecting to a N router. Might be where that is going so low.

---

