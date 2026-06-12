---
title: "How to make &quot;Ubuntu 8.04 Server&quot; to identify all the four quad-core server?"
date: 2009-01-12
forum: Server Platforms
---

### Post by arpcar on 2009-01-12
we had bought a server "DELL-R900" which was installed four physical quad-core INTEL E7310 .In BIOS, CPU is set to 64 bit&#65292;no virtualization support.
   ubuntu 8.04 SERVER default installation. I found out that only two physical CPUs were detected by the kernel(2.6.24-server smp).
  How to make Ubuntu 8.04 Server to find out all four INTEL E7310? thanks a lot.

information below is the server's cpuinfo:

corp@dell-r900:/proc$ cat cpuinfo
processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 15
model name : Intel(R) Xeon(R) CPU E7310 @ 1.60GHz
stepping : 11
cpu MHz : 1596.001
cache size : 2048 KB
physical id : 0
siblings : 4
core id : 0
cpu cores : 4
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 10
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips : 3194.08
clflush size : 64

processor : 1
vendor_id : GenuineIntel
cpu family : 6
model : 15
model name : Intel(R) Xeon(R) CPU E7310 @ 1.60GHz
stepping : 11
cpu MHz : 1596.001
cache size : 2048 KB
physical id : 0
siblings : 4
core id : 1
cpu cores : 4
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 10
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips : 3191.89
clflush size : 64

processor : 2
vendor_id : GenuineIntel
cpu family : 6
model : 15
model name : Intel(R) Xeon(R) CPU E7310 @ 1.60GHz
stepping : 11
cpu MHz : 1596.001
cache size : 2048 KB
physical id : 0
siblings : 4
core id : 2
cpu cores : 4
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 10
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips : 3191.90
clflush size : 64

processor : 3
vendor_id : GenuineIntel
cpu family : 6
model : 15
model name : Intel(R) Xeon(R) CPU E7310 @ 1.60GHz
stepping : 11
cpu MHz : 1596.001
cache size : 2048 KB
physical id : 0
siblings : 4
core id : 3
cpu cores : 4
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 10
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips : 3191.90
clflush size : 64

processor : 4
vendor_id : GenuineIntel
cpu family : 6
model : 15
model name : Intel(R) Xeon(R) CPU E7310 @ 1.60GHz
stepping : 11
cpu MHz : 1596.001
cache size : 2048 KB
physical id : 2
siblings : 4
core id : 0
cpu cores : 4
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 10
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips : 3191.92
clflush size : 64

processor : 5
vendor_id : GenuineIntel
cpu family : 6
model : 15
model name : Intel(R) Xeon(R) CPU E7310 @ 1.60GHz
stepping : 11
cpu MHz : 1596.001
cache size : 2048 KB
physical id : 2
siblings : 4
core id : 1
cpu cores : 4
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 10
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips : 3191.91
clflush size : 64

processor : 6
vendor_id : GenuineIntel
cpu family : 6
model : 15
model name : Intel(R) Xeon(R) CPU E7310 @ 1.60GHz
stepping : 11
cpu MHz : 1596.001
cache size : 2048 KB
physical id : 2
siblings : 4
core id : 2
cpu cores : 4
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 10
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips : 3191.92
clflush size : 64

processor : 7
vendor_id : GenuineIntel
cpu family : 6
model : 15
model name : Intel(R) Xeon(R) CPU E7310 @ 1.60GHz
stepping : 11
cpu MHz : 1596.001
cache size : 2048 KB
physical id : 2
siblings : 4
core id : 3
cpu cores : 4
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 10
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips : 3191.93
clflush size : 64

corp@dell-r900:/proc$ cd /boot/grub/
corp@dell-r900:/boot/grub$ ls
default fat_stage1_5 menu.lst stage1
device.map installed-version minix_stage1_5 stage2
e2fs_stage1_5 jfs_stage1_5 reiserfs_stage1_5 xfs_stage1_5
corp@dell-r900:/boot/grub$ cat menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5ddd79d4-351a-4c58-9b42-6a3687f41e40 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-16-server
root (hd0,1)
kernel /vmlinuz-2.6.24-16-server root=UUID=5ddd79d4-351a-4c58-9b42-6a3687f41e40 ro quiet splash
initrd /initrd.img-2.6.24-16-server
quiet

title Ubuntu 8.04, kernel 2.6.24-16-server (recovery mode)
root (hd0,1)
kernel /vmlinuz-2.6.24-16-server root=UUID=5ddd79d4-351a-4c58-9b42-6a3687f41e40 ro single
initrd /initrd.img-2.6.24-16-server

title Ubuntu 8.04, memtest86+
root (hd0,1)
kernel /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
corp@dell-r900:/boot/grub$

---

### Post by electrogeist on 2009-01-16
Look at the kernel configuration for CONFIG_NR_CPUS

Does Ubuntu set this to 8?

---

