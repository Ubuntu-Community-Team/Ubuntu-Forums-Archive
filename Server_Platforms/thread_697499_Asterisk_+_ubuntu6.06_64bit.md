---
title: "Asterisk + ubuntu6.06 64bit"
date: 2008-02-15
forum: Server Platforms
---

### Post by philippge_g on 2008-02-15
Hi there,

I am trying to install the asterisk+zaptel on the ubuntu server machine facing problems.

Here are basic details:
Linux honeypok 2.6.23.16-20080211a #1 SMP Mon Feb 11 09:47:46 CET 2008 x86_64 GNU/Linux

Asterisk has been successfully installed so far, but zaptel is having problems in building, i.e.

in /usr/src/zaptel, the output of make clean is
```
root@s15285177:/usr/src/zaptel# make clean
rm -f torisatool makefw tor2fw.h radfw.h
rm -f ztcfg ztmonitor ztspeed  zttest fxotune ztpty
rm -f *.o ztcfg tzdriver sethdlc sethdlc-new
rm -f zonedata.lo tonezone.lo libtonezone.so *.lo
make -C /lib/modules/2.6.23.16-20080211a/build SUBDIRS=/usr/src/zaptel clean
make[1]: Entering directory `/usr/src/linux-2.6.23.16'
  CLEAN   /usr/src/zaptel/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-2.6.23.16'
rm -rf .tmp_versions
rm -f gendigits tones.h
rm -f libtonezone*
rm -f tor2ee
rm -f fxotune
rm -f core
rm -f ztcfg-shared fxstest
rm -f fw2h vpm450m_fw.h

```

when I am doing make linux26 i am getting this:
```
root@s15285177:/usr/src/zaptel# make linux26
cc -I. -Iinclude -O4 -g -Wall -DBUILDING_TONEZONE   -m64 -DSTANDALONE_ZAPATA -DZAPTEL_CONFIG=\"/etc/zaptel.conf\" -DHOTPLUG_FIRMWARE  -lm  gendigits.c   -o gendigits
./gendigits > tones.h
cc -I. -Iinclude -O4 -g -Wall -DBUILDING_TONEZONE   -m64 -DSTANDALONE_ZAPATA -DZAPTEL_CONFIG=\"/etc/zaptel.conf\" -DHOTPLUG_FIRMWARE    makefw.c   -o makefw
./makefw tormenta2.rbt tor2fw > tor2fw.h
Loaded 69900 bytes from file
./makefw pciradio.rbt radfw > radfw.h
Loaded 42096 bytes from file
ZAPTELVERSION="1.2.8" build_tools/make_version_h > version.h.tmp
if cmp -s version.h.tmp version.h ; then echo; else \
                mv version.h.tmp version.h ; \
        fi

rm -f version.h.tmp
cc -I. -Iinclude -O4 -g -Wall -DBUILDING_TONEZONE   -m64 -DSTANDALONE_ZAPATA -DZAPTEL_CONFIG=\"/etc/zaptel.conf\" -DHOTPLUG_FIRMWARE   -c -o ztcfg.o ztcfg.c
cc -c -fPIC -I. -Iinclude -O4 -g -Wall -DBUILDING_TONEZONE   -m64 -DBUILDING_TONEZONE -o zonedata.lo zonedata.c
cc -c -fPIC -I. -Iinclude -O4 -g -Wall -DBUILDING_TONEZONE   -m64 -DBUILDING_TONEZONE -o tonezone.lo tonezone.c
ar rcs libtonezone.a zonedata.lo tonezone.lo
cc -o ztcfg ztcfg.o libtonezone.a -lm
cc -I. -Iinclude -O4 -g -Wall -DBUILDING_TONEZONE   -m64 -DSTANDALONE_ZAPATA -DZAPTEL_CONFIG=\"/etc/zaptel.conf\" -DHOTPLUG_FIRMWARE -o ztmonitor.o -c ztmonitor.c
cc -I. -Iinclude -O4 -g -Wall -DBUILDING_TONEZONE   -m64 -DSTANDALONE_ZAPATA -DZAPTEL_CONFIG=\"/etc/zaptel.conf\" -DHOTPLUG_FIRMWARE -o ztmonitor ztmonitor.o
cc  -o ztspeed.o -c ztspeed.c
cc  -o ztspeed ztspeed.o
cc -I. -Iinclude -O4 -g -Wall -DBUILDING_TONEZONE   -m64 -DSTANDALONE_ZAPATA -DZAPTEL_CONFIG=\"/etc/zaptel.conf\" -DHOTPLUG_FIRMWARE    zttest.c   -o zttest
cc -I. -Iinclude -O4 -g -Wall -DBUILDING_TONEZONE   -m64 -DSTANDALONE_ZAPATA -DZAPTEL_CONFIG=\"/etc/zaptel.conf\" -DHOTPLUG_FIRMWARE -o fxotune.o -c fxotune.c
cc -I. -Iinclude -O4 -g -Wall -DBUILDING_TONEZONE   -m64 -DSTANDALONE_ZAPATA -DZAPTEL_CONFIG=\"/etc/zaptel.conf\" -DHOTPLUG_FIRMWARE -o fxotune fxotune.o -lm
cc -I. -Iinclude -O4 -g -Wall -DBUILDING_TONEZONE   -m64 -DSTANDALONE_ZAPATA -DZAPTEL_CONFIG=\"/etc/zaptel.conf\" -DHOTPLUG_FIRMWARE    ztpty.c   -o ztpty
ztpty.c: In function âmainâ:
ztpty.c:80: warning: implicit declaration of function âioctlâ
/lib/modules/2.6.23.16-20080211a/build
make -C /lib/modules/2.6.23.16-20080211a/build SUBDIRS=/usr/src/zaptel modules
make[1]: Entering directory `/usr/src/linux-2.6.23.16'
  CC [M]  /usr/src/zaptel/zaptel.o
/usr/src/zaptel/zaptel.c:189: warning: âfcstabâ defined but not used
  CC [M]  /usr/src/zaptel/tor2.o
/usr/src/zaptel/tor2.c: In function âtor2_probeâ:
/usr/src/zaptel/tor2.c:544: warning: âdeprecated_irq_flagâ is deprecated (declared at include/linux/interrupt.h:64)
/usr/src/zaptel/tor2.c:544: warning: âdeprecated_irq_flagâ is deprecated (declared at include/linux/interrupt.h:64)
/usr/src/zaptel/tor2.c:544: warning: passing argument 2 of ârequest_irqâ from incompatible pointer type
  CC [M]  /usr/src/zaptel/torisa.o
/usr/src/zaptel/torisa.c: In function âtor_initâ:
/usr/src/zaptel/torisa.c:1075: warning: âdeprecated_irq_flagâ is deprecated (declared at include/linux/interrupt.h:64)
/usr/src/zaptel/torisa.c:1075: warning: passing argument 2 of ârequest_irqâ from incompatible pointer type
/usr/src/zaptel/torisa.c: At top level:
/usr/src/zaptel/torisa.c:1145: warning: âset_tor_baseâ defined but not used
  CC [M]  /usr/src/zaptel/wcusb.o
/usr/src/zaptel/wcusb.c: In function âwcusb_async_readâ:
/usr/src/zaptel/wcusb.c:463: warning: passing argument 7 of âusb_fill_control_urbâ from incompatible pointer type
/usr/src/zaptel/wcusb.c: In function âwcusb_async_writeâ:
/usr/src/zaptel/wcusb.c:511: warning: passing argument 7 of âusb_fill_control_urbâ from incompatible pointer type
/usr/src/zaptel/wcusb.c: In function âprepare_transfer_urbsâ:
/usr/src/zaptel/wcusb.c:1043: warning: assignment from incompatible pointer type
/usr/src/zaptel/wcusb.c:1058: warning: assignment from incompatible pointer type
  CC [M]  /usr/src/zaptel/wcfxo.o
/usr/src/zaptel/wcfxo.c: In function âwcfxo_init_oneâ:
/usr/src/zaptel/wcfxo.c:901: warning: âdeprecated_irq_flagâ is deprecated (declared at include/linux/interrupt.h:64)
/usr/src/zaptel/wcfxo.c:901: warning: passing argument 2 of ârequest_irqâ from incompatible pointer type
  CC [M]  /usr/src/zaptel/wctdm.o
/usr/src/zaptel/wctdm.c: In function âwctdm_init_oneâ:
/usr/src/zaptel/wctdm.c:2242: warning: âdeprecated_irq_flagâ is deprecated (declared at include/linux/interrupt.h:64)
/usr/src/zaptel/wctdm.c:2242: warning: passing argument 2 of ârequest_irqâ from incompatible pointer type
  CC [M]  /usr/src/zaptel/wctdm24xxp.o
/usr/src/zaptel/wctdm24xxp.c: In function âwctdm_init_oneâ:
/usr/src/zaptel/wctdm24xxp.c:2751: warning: âdeprecated_irq_flagâ is deprecated (declared at include/linux/interrupt.h:64)
/usr/src/zaptel/wctdm24xxp.c:2751: warning: passing argument 2 of ârequest_irqâ from incompatible pointer type
/usr/src/zaptel/wctdm24xxp.c: In function âwctdm_initâ:
/usr/src/zaptel/wctdm24xxp.c:2868: error: implicit declaration of function âpci_module_initâ
make[2]: *** [/usr/src/zaptel/wctdm24xxp.o] Error 1
make[1]: *** [_module_/usr/src/zaptel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.23.16'
make: *** [linux26] Error 2

```

I have already ran this ```
dpkg-reconfigure locales
tzconfig

```
to change locale to that of London.

What I am missing? Any help would be highly appreciated.

PG

---

