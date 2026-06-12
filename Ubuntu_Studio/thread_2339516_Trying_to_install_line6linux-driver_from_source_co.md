---
title: "Trying to install line6linux-driver from source code"
date: 2016-10-09
forum: Ubuntu Studio
---

### Post by saturnine2 on 2016-10-09
Hey!

So I'm trying to get my Line6 keyboard to work with Ubuntu Studio and I'm getting the following error:

saturnine@Host-001:/lib/modules/4.4.0-38-lowlatency/build/sound/usb/line6$ sudo make install
./set_revision.sh
make -C /lib/modules/4.4.0-38-generic/build CONFIG_LINE6_USB=m SUBDIRS=/usr/src/linux-headers-4.4.0-38/sound/usb/line6 modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-38-generic'
  CC [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/capture.o
  CC [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/driver.o
  CC [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/midi.o
  CC [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/midibuf.o
  CC [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/pcm.o
  CC [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/playback.o
  LD [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-line6.o
  CC [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/pod.o
  LD [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-pod.o
  CC [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/podhd.o
  LD [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-podhd.o
  CC [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/toneport.o
  LD [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-toneport.o
  CC [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/variax.o
  LD [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-variax.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-line6.mod.o
  LD [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-line6.ko
  CC      /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-pod.mod.o
  LD [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-pod.ko
  CC      /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-podhd.mod.o
  LD [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-podhd.ko
  CC      /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-toneport.mod.o
  LD [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-toneport.ko
  CC      /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-variax.mod.o
  LD [M]  /usr/src/linux-headers-4.4.0-38/sound/usb/line6/snd-usb-variax.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-38-generic'
mkdir -p /lib/modules/4.4.0-38-generic/kernel/drivers/staging/line6 /usr/bin /usr/share/doc/packages/line6usb
find /lib/modules/4.4.0-38-generic -name line6usb.ko -delete
cp line6usb.ko /lib/modules/4.4.0-38-generic/kernel/drivers/staging/line6
cp: cannot stat 'line6usb.ko': No such file or directory
GNUmakefile:25: recipe for target 'install-only' failed
make: *** [install-only] Error 1

Someone please help me out?

---

### Post by gnottage on 2016-10-13
I'm not familiar with this line6 driver, so can only make suggestions on what's here. It looks like it cannot find the [FONT=Courier New]line6usb.ko[/FONT] file, which will be the driver that should have been built. It looks like the [FONT=Courier New]sudo make install[/FONT] is trying to build and install the driver, but I wonder if a preceding step (such as [FONT=Courier New]./configure[/FONT] and/or [FONT=Courier New]make[/FONT]) has been missed... Usually there is a text file called [FONT=Courier New]INSTALL[/FONT] or [FONT=Courier New]README[/FONT] that will have full build instructions. If you did follow all of them then there was a problem earlier in the build, such as missing libraries?

---

### Post by hmollercl on 2017-01-30
Hi, line6linux is already in the kernel, ist should be in (replacing 4.4.0-57xxxxx with your current kernel)
/lib/modules/4.4.0-57-generic/kernel/sound/usb/line6/
try using modprobe. In my case (pod hd) it is:
sudo modprobe --first-time snd-usb-podhd.

However, It doesn't work for me. 
You could also see what dmesg says after plugging the keyboard.

Let us know how it goes.

---

