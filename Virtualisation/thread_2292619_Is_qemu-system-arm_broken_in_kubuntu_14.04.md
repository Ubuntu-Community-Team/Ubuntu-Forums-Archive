---
title: "Is qemu-system-arm broken in kubuntu 14.04"
date: 2015-08-29
forum: Virtualisation
---

### Post by J_Me on 2015-08-29
Hello
I'm having trouble booting this test file 'arm-test-0.2.tar.gz' from qemu's wiki page [http://wiki.qemu.org/Testing](http://wiki.qemu.org/Testing)
Qemu gives me this error and just hangs
```
$ qemu-system-arm -M versatileab -kernel zImage.integrator -initrd arm_root.img -m 1024
pulseaudio: set_sink_input_volume() failed                                                                                                                    
pulseaudio: Reason: Invalid argument                                                                                                                          
pulseaudio: set_sink_input_mute() failed                                                                                                                      
pulseaudio: Reason: Invalid argument 

```I should add that in the README which says
> Kernel and small root FS for use with qemu ARM emulation.

The kernel config is included in the kernel.  It can be extracted from the
image with linux/scripts/extract-ikconfig or accessed as /proc/config.gz
on a running kenel.

The root FS should be loaded as an initrd.  eg:

./qemu-system-arm -kernel zImage.integrator -initrd arm_root.img

Or without graphical output:

./qemu-system-arm -kernel zImage.integrator -initrd arm_root.img -nographic -append "console=ttyAMA0"Qemu also gives me another error message but this time just exits
```
$ qemu-system-arm -kernel zImage.integrator -initrd arm_root.img
No machine specified, and there is no default.
Use -machine help to list supported machines!
```Could someone tell me if I'm doing something wrong.
Thanks

---

### Post by redger on 2015-09-02
first a qualifier ... I've never used the Arm machine with qemu - only the x86 ... and qemu is definitely NOT broken

having said that, your definition looks a bit light on

in the first instance you quote, you can provide PulseAudio parameters to qemu using this format (not sure why you're seeing this error, but here's how to set pulseaudio up, assuming it's available on the host)
```
QEMU_PA_SAMPLES=128 QEMU_AUDIO_DRV=pa
qemu-system-arm -M versatileab -kernel zImage.integrator -initrd arm_root.img -m 1024
```

in the second instance qemu is complaining that it doesn't know what sort of machine to instantiate ie. too few parameters provided - starting with the machine type ("-machine or -M")

it might be good if you attached some storage and IO devices to your virtual machine ..... see this page for more info [http://wiki.qemu.org/download/qemu-doc.html]("http://wiki.qemu.org/download/qemu-doc.html")
or here [http://dev.man-online.org/man1/qemu-system-arm/]("http://dev.man-online.org/man1/qemu-system-arm/")

here's an example
```
qemu-system-arm -M vexpress-a9 -cpu cortex-a9 -m 256            \
  -sd disk.img                                                  \
  -net nic,macaddr=52:54:00:fa:ce:13                            \
  -net user,hostfwd=tcp::2013-:22                               \
  -kernel vmlinuz-3.2.0-4-vexpress                              \
  -initrd initrd.gz                                             \
  -append "root=/dev/ram"                                       \
  -display vnc=localhost:17
```

from this link [https://gmplib.org/~tege/qemu.html]("https://gmplib.org/~tege/qemu.html")
another example can be found here [http://www.aurel32.net/info/debian_arm_qemu.php]("http://www.aurel32.net/info/debian_arm_qemu.php")
Mr Google will surely find more for you

---

### Post by J_Me on 2015-09-04
Hello redger

Thanks for the reply and links I'll go over them in more detail later. In the mean time I gave this a try but the core dumped (note that the machine and cpu are not for arm but at least it gave some feedback)
```
$ QEMU_PA_SAMPLES=128 QEMU_AUDIO_DRV=pa qemu-system-arm -M vexpress-a9 -cpu cortex-a9 -m 512 -net nic,macaddr=52:54:00:fa:ce:13 -net user,hostfwd=tcp::2013-:22 -kernel zImage.integrator -initrd arm_root.img -append "root=/dev/ram" -display vnc=localhost:17
pulseaudio: set_sink_input_volume() failed
pulseaudio: Reason: Invalid argument
pulseaudio: set_sink_input_mute() failed
pulseaudio: Reason: Invalid argument
qemu: fatal: Trying to execute code outside RAM or ROM at 0x04000000

R00=00000000 R01=00000000 R02=00000000 R03=c01ea770
R04=00000000 R05=00000000 R06=00000000 R07=00008000
R08=0000000d R09=00000000 R10=60127d9c R11=00001880
R12=c020a09c R13=00000001 R14=00008005 R15=04000000
PSR=400001d3 -Z-- A svc32
s00=00000000 s01=00000000 d00=0000000000000000
s02=00000000 s03=00000000 d01=0000000000000000
s04=00000000 s05=00000000 d02=0000000000000000
s06=00000000 s07=00000000 d03=0000000000000000
s08=00000000 s09=00000000 d04=0000000000000000
s10=00000000 s11=00000000 d05=0000000000000000
s12=00000000 s13=00000000 d06=0000000000000000
s14=00000000 s15=00000000 d07=0000000000000000
s16=00000000 s17=00000000 d08=0000000000000000
s18=00000000 s19=00000000 d09=0000000000000000
s20=00000000 s21=00000000 d10=0000000000000000
s22=00000000 s23=00000000 d11=0000000000000000
s24=00000000 s25=00000000 d12=0000000000000000
s26=00000000 s27=00000000 d13=0000000000000000
s28=00000000 s29=00000000 d14=0000000000000000
s30=00000000 s31=00000000 d15=0000000000000000
s32=00000000 s33=00000000 d16=0000000000000000
s34=00000000 s35=00000000 d17=0000000000000000
s36=00000000 s37=00000000 d18=0000000000000000
s38=00000000 s39=00000000 d19=0000000000000000
s40=00000000 s41=00000000 d20=0000000000000000
s42=00000000 s43=00000000 d21=0000000000000000
s44=00000000 s45=00000000 d22=0000000000000000
s46=00000000 s47=00000000 d23=0000000000000000
s48=00000000 s49=00000000 d24=0000000000000000
s50=00000000 s51=00000000 d25=0000000000000000
s52=00000000 s53=00000000 d26=0000000000000000
s54=00000000 s55=00000000 d27=0000000000000000
s56=00000000 s57=00000000 d28=0000000000000000
s58=00000000 s59=00000000 d29=0000000000000000
s60=00000000 s61=00000000 d30=0000000000000000
s62=00000000 s63=00000000 d31=0000000000000000
FPSCR: 00000000
Aborted (core dumped)
```I also tried the above using a different machine(-M integratorcp) and cpu(-cpu cortex-a8) but it just hangs with no error output at all, how can I turn on human readable debugging information for qemu.
I can boot the x86 examples from qemu's wiki page just fine but not for arm. Could you(or anyone reading this) take a few minutes to see if you can boot that wiki arm image [http://wiki.qemu.org/download/arm-test-0.2.tar.gz](http://wiki.qemu.org/download/arm-test-0.2.tar.gz) it's only 3.2 MB in size if it works for you then at least I'll know that the problem is on my laptop.

Regards

---

### Post by rbacik on 2016-02-13
this works for me:
qemu-system-arm -kernel zImage.integrator -initrd arm_root.img  -machine integratorcp

---

### Post by J_Me on 2016-02-16
@ rbacik Hey thanks for the reply. Yes that works for me also.

---

