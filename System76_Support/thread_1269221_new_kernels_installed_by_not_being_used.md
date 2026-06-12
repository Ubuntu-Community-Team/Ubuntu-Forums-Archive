---
title: "new kernels installed by not being used"
date: 2009-09-18
forum: System76 Support
---

### Post by mknoop on 2009-09-18
my system is running ubuntu 9.04.  I have been performing the regular update through the update manager.  This has been installing newer linux kernels 2.6.28... but these new kernels are never being used in the grub boot loader.  The system still keeps running 2.6.27-11-generic.

I think I need to run update-grub, but I have not seen any instruction to do so, and so am very reluctant to start messing with the boot loader on my own.

Any ideas?

---

### Post by thomasaaron on 2009-09-18
Please post the output of...

```
cat /boot/grub/menu.lst
```

---

### Post by mknoop on 2009-09-18
Thank you for your reply.  If forgot to mention that this system was updated from version 8.10. a while ago.  Perhaps I messed up there.

 The output is:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda1

## default grub root device
## e.g. groot=(hd0,0)
# groot=f372e9c4-48d4-42e0-9125-d752dd380afc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27-11-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=/dev/sda1 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by thomasaaron on 2009-09-18
> my system is running ubuntu 9.04.

Your menu.lst indicates you are running 8.10.

Are you sure you're 9.04 update succeeded? What is the output of...
```
uname -a
```

Also, what is the output of...
```
ls /boot
```

---

### Post by mknoop on 2009-09-18
I thought it upgraded to 9.04.  There certainly was a dramatic change in the logon display.  Everything else seemed to be upgraded.  Anyway -

uname -a:

Linux ubuntu 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux

ls /boot:

abi-2.6.27-11-generic         memtest86+.bin
abi-2.6.28-13-generic         sarge.bmp
abi-2.6.28-14-generic         sid.bmp
abi-2.6.28-15-generic         System.map-2.6.27-11-generic
coffee.bmp                    System.map-2.6.28-13-generic
config-2.6.27-11-generic      System.map-2.6.28-14-generic
config-2.6.28-13-generic      System.map-2.6.28-15-generic
config-2.6.28-14-generic      vmcoreinfo-2.6.27-11-generic
config-2.6.28-15-generic      vmcoreinfo-2.6.28-13-generic
debian.bmp                    vmcoreinfo-2.6.28-14-generic
debianlilo.bmp                vmcoreinfo-2.6.28-15-generic
grub                          vmlinuz-2.6.27-11-generic
initrd.img-2.6.27-11-generic  vmlinuz-2.6.28-13-generic
initrd.img-2.6.28-13-generic  vmlinuz-2.6.28-14-generic
initrd.img-2.6.28-14-generic  vmlinuz-2.6.28-15-generic
initrd.img-2.6.28-15-generic

---

### Post by snowpine on 2009-09-18
Is Ubuntu the only operating system, or do you have a dual boot?

---

### Post by thomasaaron on 2009-09-18
OK, well, it looks like you have 9.04 installed, but you're certainly not running it.

Let's try this...

```
sudo update-grub
```

Then reboot, login and run...

```
uname -a
```

You should be running something like...
2.6.28-15-generic

---

### Post by Ghidora on 2009-09-18
This is weird.  I seem to be having the same issue with my Starling.

Here's the output of cat /boot/grub/menu.lst

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9fdd20be-ce71-4f01-9861-14fcfe916c81 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9fdd20be-ce71-4f01-9861-14fcfe916c81

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash pciehp.pciehp_force=1

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        9fdd20be-ce71-4f01-9861-14fcfe916c81
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9fdd20be-ce71-4f01-9861-14fcfe916c81 ro quiet splash pciehp.pciehp_force=1 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9fdd20be-ce71-4f01-9861-14fcfe916c81
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9fdd20be-ce71-4f01-9861-14fcfe916c81 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        9fdd20be-ce71-4f01-9861-14fcfe916c81
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```Here's what I get from ls /boot
```

abi-2.6.28-11-generic     config-2.6.28-15-generic      System.map-2.6.28-11-generic  vmcoreinfo-2.6.28-15-generic
abi-2.6.28-13-generic     grub                          System.map-2.6.28-13-generic  vmlinuz-2.6.28-11-generic
abi-2.6.28-14-generic     initrd.img-2.6.28-11-generic  System.map-2.6.28-14-generic  vmlinuz-2.6.28-13-generic
abi-2.6.28-15-generic     initrd.img-2.6.28-13-generic  System.map-2.6.28-15-generic  vmlinuz-2.6.28-14-generic
config-2.6.28-11-generic  initrd.img-2.6.28-14-generic  vmcoreinfo-2.6.28-11-generic  vmlinuz-2.6.28-15-generic
config-2.6.28-13-generic  initrd.img-2.6.28-15-generic  vmcoreinfo-2.6.28-13-generic
config-2.6.28-14-generic  memtest86+.bin                vmcoreinfo-2.6.28-14-generic
```And here's the output of uname -a
```
Linux system76-netbook 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```I tried running the sudo update-grub command and rebooting, but the results are unchanged.

---

### Post by mknoop on 2009-09-18
No - my system is not dual-boot.

Okay.  I ran sudo update-grub and then rebooted.  Nothing has changed.  Here is the output from update-grub:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

But - /boot/grub/menu.lst does not change at all.  It is exactly the same and rebooting just runs 2.6.27-11-generic

---

### Post by gpstar on 2009-09-19
> **Ghidora said:**
> This is weird.  I seem to be having the same issue with my Starling.

Here's the output of cat /boot/grub/menu.lst

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9fdd20be-ce71-4f01-9861-14fcfe916c81 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9fdd20be-ce71-4f01-9861-14fcfe916c81

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash pciehp.pciehp_force=1

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        9fdd20be-ce71-4f01-9861-14fcfe916c81
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9fdd20be-ce71-4f01-9861-14fcfe916c81 ro quiet splash pciehp.pciehp_force=1 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9fdd20be-ce71-4f01-9861-14fcfe916c81
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9fdd20be-ce71-4f01-9861-14fcfe916c81 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        9fdd20be-ce71-4f01-9861-14fcfe916c81
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```Here's what I get from ls /boot
```

abi-2.6.28-11-generic     config-2.6.28-15-generic      System.map-2.6.28-11-generic  vmcoreinfo-2.6.28-15-generic
abi-2.6.28-13-generic     grub                          System.map-2.6.28-13-generic  vmlinuz-2.6.28-11-generic
abi-2.6.28-14-generic     initrd.img-2.6.28-11-generic  System.map-2.6.28-14-generic  vmlinuz-2.6.28-13-generic
abi-2.6.28-15-generic     initrd.img-2.6.28-13-generic  System.map-2.6.28-15-generic  vmlinuz-2.6.28-14-generic
config-2.6.28-11-generic  initrd.img-2.6.28-14-generic  vmcoreinfo-2.6.28-11-generic  vmlinuz-2.6.28-15-generic
config-2.6.28-13-generic  initrd.img-2.6.28-15-generic  vmcoreinfo-2.6.28-13-generic
config-2.6.28-14-generic  memtest86+.bin                vmcoreinfo-2.6.28-14-generic
```And here's the output of uname -a
```
Linux system76-netbook 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```I tried running the sudo update-grub command and rebooting, but the results are unchanged.

looks like you have the latest kernels, just need to have grub select it for booting. just edit the /boot/grub/menu.lst

sudo gedit /boot/grub/menu.lst

and add this entry near the end of the file below the 2.6.28-11 entries,

```

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        9fdd20be-ce71-4f01-9861-14fcfe916c81
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=9fdd20be-ce71-4f01-9861-14fcfe916c81 ro quiet splash pciehp.pciehp_force=1 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

```

and when you boot, press ESC if it asks you to enter the grub menu and select that entry to see if it boots into the 2.6.28-15 kernel. If it does, then you can move that entry above the 2.6.28-11 entries in the menu.lst near the bottom so it automatically boots into it from now on.

---

### Post by Ghidora on 2009-09-19
Thank you gpstar.  This worked for me.

---

### Post by thomasaaron on 2009-09-21
mknoop,

Try this. It will ask you if you want to generate a new menu.lst...

sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo update-grub

Select "y" when it asks you if you want it to generate a new menu.lst.

Make sure you actually have a *new* menu.lst file now by running...

cat /boot/grub/menu.lst

Once it's run, let's make sure your kernel-img.conf file is set to run update-grub after every kernel update.

Run...
```
sudo gedit /etc/kernel-img.conf
```

If it doesn't have these lines in it...

```
postinst_hook = update-grub
postrm_hook = update-grub

```
add them and save the file. That *should* get you back on the right track.

---

### Post by mknoop on 2009-09-21
thomasaaron - 

Thank you.  That seems to have done it.  My system is now running the most recent kernel version.

I really appreciate you taking the time to help me.  Thank you again.

---

