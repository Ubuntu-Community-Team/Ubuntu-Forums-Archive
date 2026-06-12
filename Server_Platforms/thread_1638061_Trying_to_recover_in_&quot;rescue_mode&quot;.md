---
title: "Trying to recover in &quot;rescue mode&quot;"
date: 2010-12-05
forum: Server Platforms
---

### Post by merlin4x on 2010-12-05
UBUNTU 10.04 on remote server failed after updating following modules:

An update to grub-common from 1.98-1ubuntu8 to 1.98-1ubuntu9 is available.
An update to grub-pc from 1.98-1ubuntu8 to 1.98-1ubuntu9 is available. 

First updated a OK and second gave an error "wrong name" or something like that

So the update stop the server and I did "Cold Reboot" which seems to work but I can't log in via "root" SSH only by "rescue mode" SSH however I am totally lost there.

I guess I need to finish the "grub-pc" or "grub-common" from prior update process.

I can use rescue mode to effectively boot my server to live cd. I can ssh in to the live cd os and my original os is mounted for me to chroot in / backup / repair.

I have not a clue about what to do next. Help

---

### Post by GDR! on 2010-12-06
It could be a missing kernel or initrd. Try viewing /boot/grub/grub.cfg - "menuentry" section. Locate the menuentry with last kernel that worked for you and note down its 0-based index (it will be probably the third one, that is index will be "2"). 

Then, at the top of the file, edit:
set default="0"
changing "0" to the index you noted down.

Please note it's not a persistent solution but will probably allow you to boot your system. Also, if the server is in datacenter, you can probably open a support ticket and ask them to try different kernels at boot, that's much easier.

---

### Post by sikander3786 on 2010-12-06
Try re-installing Grub.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If that doesn't help, post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us nearly everything about your setup and let us advise more efficiently ;-)

Please wrap your output with proper code tags # from post menu. [/code] at the end [code] at the beginning.

---

### Post by merlin4x on 2010-12-06
I will try all that but basics first. This is what I get after connecting via ssh to live CD.
```
 
 ... DRIVE ALREADY MOUNTED

/dev/hdb3             9.3G  2.3G  6.7G  25% /mnt/RESCUE

fx:/mnt/RESCUE#

```1) should I use chroot? or work in directories above?
2) when I am exiting from the live CD I must use command from the server control panel...... where would I find list of all initializations and what they all should be when I do re boot from the control panel? 
3) While in "rescue mode" sim-links do not work because of relocation.
4) I am getting err:
```
 
fx:/mnt/RESCUE# ifup eth0
SIOCADDRT: File exists
Failed to bring up eth0.

```Should I attribute it to rescue mode because "eth0" looks a OK
```
 
127.0.0.1       localhost.localdomain  localhost
208.111.39.240  fx.airpatrol.us        fx

```
```
 
/etc/hosts
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```
```
 
/etc/network/interfaces
auto lo 
iface lo inet loopback
auto eth0
iface eth0 inet static
    address 208.111.39.240
    broadcast 208.111.39.255
    netmask 255.255.255.0
    gateway 208.111.39.1
    network 208.111.39.0
iface eth0 inet6 static
    address 2607:f740:0000:003f:0000:0000:0000:018b
    netmask 64

```
```
 
fx:/mnt/RESCUE# ifconfig
eth0      Link encap:Ethernet  HWaddr 10:16:3e:7f:1d:54
          inet addr:208.111.39.240  Bcast:208.111.39.255  Mask:255.255.255.0
          inet6 addr: 2607:f740:0:3f:1216:3eff:fe7f:1d54/64 Scope:Global
          inet6 addr: fe80::1216:3eff:fe7f:1d54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2727688 (2.6 MiB)  TX bytes:8327520 (7.9 MiB)
          Interrupt:5 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:28248 (27.5 KiB)  TX bytes:28248 (27.5 KiB)

```Do you see anything wrong?

I get apache to work in rescue mode fine if I do /etc/init.d/apache2 restart

All applications will open too but password is lost probably because of relocation.

"sudo" works only if I use "chroot"

---

### Post by merlin4x on 2010-12-06
> **sikander3786 said:**
> Try re-installing Grub.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If that doesn't help, post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us nearly everything about your setup and let us advise more efficiently ;-)

Please wrap your output with proper code tags # from post menu. [/code] at the end ```
 at the beginning.

OK I have done bootinfoscript in chroot /mnt/RESCUE before reinstalling grub2.

[code]
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         


============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0)
/dev/sda1        /boot                    ext3       (rw)

=============================== StdErr Messages: ===============================

sort: open failed: /tmp/BootInfo0/BLKID: No such file or directory


```

---

### Post by merlin4x on 2010-12-06
> **GDR! said:**
> It could be a missing kernel or initrd. Try viewing /boot/grub/grub.cfg - "menuentry" section. Locate the menuentry with last kernel that worked for you and note down its 0-based index (it will be probably the third one, that is index will be "2"). 

Then, at the top of the file, edit:
set default="0"
changing "0" to the index you noted down.

Please note it's not a persistent solution but will probably allow you to boot your system. Also, if the server is in datacenter, you can probably open a support ticket and ask them to try different kernels at boot, that's much easier.


There is no /boot/grub/grub.cfg file.
So I will try to reinstall grub2

---

### Post by merlin4x on 2010-12-06
> **sikander3786 said:**
> Try re-installing Grub.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")


I need help to install grub2 in rescue mode on remote server. My drive is Already Mounted when I select Rescue Mode on the remote server panel as follows:
```

/dev/hdb3             9.3G  2.3G  6.7G  25% /mnt/RESCUE

```How would you convert it to the following command from the above help ubuntu link using choice (1).
```

sudo mount /dev/sdXY /mnt  ;Do I have to do that if it appears done?

sudo grub-install --root-directory=/mnt/ /dev/sdX  ;how should I properly construct this command?

```Whhile executing the install should /mnt/ be chroot or not?

Here is info from fdisk -l
```

Disk /dev/hda: 2147 MB, 2147483648 bytes
255 heads, 63 sectors/track, 261 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b8ff2

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          15      120456   83  Linux
/dev/hda2              16          77      498015   82  Linux swap / Solaris
/dev/hda3              78         261     1477980   83  Linux

Disk /dev/hdb: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00020da4

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13       96256   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/hdb2              13          75      499712   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/hdb3              75        1305     9885420+  83  Linux

```Here is info from blkid
```

/dev/hda1: UUID="cc6fae87-307d-40a6-b19c-a1de83ddc5cc" TYPE="ext3" 
/dev/hda2: TYPE="swap" 
/dev/hda3: UUID="556bdd21-6e18-44e6-b843-83692bb8708c" TYPE="ext3" 
/dev/hdb1: UUID="275b721c-892d-457d-bf04-d16c66d4e17f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb2: TYPE="swap" UUID="55adeb37-bc7e-470d-be94-5d47951d6b05" 
/dev/hdb3: UUID="05123bac-fd0d-4bbf-b433-1121b6f05b68" TYPE="ext3" 

```

---

### Post by sikander3786 on 2010-12-06
You needed to run that bootinfoscript while not in the chroot environment.

And you need to do these commands from  a Live CD Terminal only, not from chroot either.

sda3 seems to be your root partition. So your commands would be,

```
sudo mount /dev/sda3 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Note for the second one, it is just sda without an integer and not sda3.

Reboot and see if that worked.

If not, run bootinfoscript once again from Live CD (not from chroot) and post its output.

---

### Post by merlin4x on 2010-12-07
That worked perfectly** sikander3786**
Here is the current status before reinstalling grub2 

```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/hdb and looks on the same drive in 
    partition #1 for /grub.

hda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

hda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /etc/fstab

hdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

hdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 2147 MB, 2147483648 bytes
255 heads, 63 sectors/track, 261 cylinders, total 4194304 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b8ff2

Partition  Boot         Start           End          Size  Id System

/dev/hda1                  63       240,974       240,912  83 Linux
/dev/hda2             240,975     1,237,004       996,030  82 Linux swap / Solaris
/dev/hda3           1,237,005     4,192,964     2,955,960  83 Linux


Drive: hdb ___________________ _____________________________________________________

Disk /dev/hdb: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders, total 20971520 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00020da4

Partition  Boot         Start           End          Size  Id System

/dev/hdb1    *          2,048       194,559       192,512  83 Linux
/dev/hdb2             194,560     1,193,983       999,424  82 Linux swap / Solaris
/dev/hdb3           1,193,984    20,964,824    19,770,841  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda1        cc6fae87-307d-40a6-b19c-a1de83ddc5cc   ext3                                     
/dev/hda2                                               swap                                     
/dev/hda3        556bdd21-6e18-44e6-b843-83692bb8708c   ext3                                     
/dev/hdb1        275b721c-892d-457d-bf04-d16c66d4e17f   ext3                                     
/dev/hdb2        55adeb37-bc7e-470d-be94-5d47951d6b05   swap                                     
/dev/hdb3        05123bac-fd0d-4bbf-b433-1121b6f05b68   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/hda3        /                        ext3       (rw,errors=remount-ro)
/dev/hda1        /boot                    ext3       (rw)
/dev/hdb3        /mnt/RESCUE              ext3       (rw)


============================= hda1/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

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

title        Debian GNU/Linux, kernel 2.6.26-2-amd64
root        (hd0,0)
kernel        /vmlinuz-2.6.26-2-amd64 root=/dev/hda3 ro quiet
initrd        /initrd.img-2.6.26-2-amd64

title        Debian GNU/Linux, kernel 2.6.26-2-amd64 (single-user mode)
root        (hd0,0)
kernel        /vmlinuz-2.6.26-2-amd64 root=/dev/hda3 ro single
initrd        /initrd.img-2.6.26-2-amd64

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== hda1: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.26-2-amd64
    .0GB: vmlinuz-2.6.26-2-amd64

=============================== hda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== hda3: Location of files loaded by Grub: ===================


    .6GB: initrd.img
    .6GB: vmlinuz

============================= hdb1/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 05123bac-fd0d-4bbf-b433-1121b6f05b68
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 275b721c-892d-457d-bf04-d16c66d4e17f
set locale_dir=($root)/grub/locale
set lang=
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 275b721c-892d-457d-bf04-d16c66d4e17f
    linux    /vmlinuz-2.6.32-26-generic-pae root=UUID=05123bac-fd0d-4bbf-b433-1121b6f05b68 ro   quiet
    initrd    /initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 275b721c-892d-457d-bf04-d16c66d4e17f
    echo    'Loading Linux 2.6.32-26-generic-pae ...'
    linux    /vmlinuz-2.6.32-26-generic-pae root=UUID=05123bac-fd0d-4bbf-b433-1121b6f05b68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 275b721c-892d-457d-bf04-d16c66d4e17f
    linux    /vmlinuz-2.6.32-25-generic-pae root=UUID=05123bac-fd0d-4bbf-b433-1121b6f05b68 ro   quiet
    initrd    /initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 275b721c-892d-457d-bf04-d16c66d4e17f
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /vmlinuz-2.6.32-25-generic-pae root=UUID=05123bac-fd0d-4bbf-b433-1121b6f05b68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 275b721c-892d-457d-bf04-d16c66d4e17f
    linux    /vmlinuz-2.6.32-24-generic-pae root=UUID=05123bac-fd0d-4bbf-b433-1121b6f05b68 ro   quiet
    initrd    /initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 275b721c-892d-457d-bf04-d16c66d4e17f
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /vmlinuz-2.6.32-24-generic-pae root=UUID=05123bac-fd0d-4bbf-b433-1121b6f05b68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 275b721c-892d-457d-bf04-d16c66d4e17f
    linux    /vmlinuz-2.6.32-22-generic-pae root=UUID=05123bac-fd0d-4bbf-b433-1121b6f05b68 ro   quiet
    initrd    /initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 275b721c-892d-457d-bf04-d16c66d4e17f
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /vmlinuz-2.6.32-22-generic-pae root=UUID=05123bac-fd0d-4bbf-b433-1121b6f05b68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 275b721c-892d-457d-bf04-d16c66d4e17f
    linux    /vmlinuz-2.6.32-21-generic-pae root=UUID=05123bac-fd0d-4bbf-b433-1121b6f05b68 ro   quiet
    initrd    /initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 275b721c-892d-457d-bf04-d16c66d4e17f
    echo    'Loading Linux 2.6.32-21-generic-pae ...'
    linux    /vmlinuz-2.6.32-21-generic-pae root=UUID=05123bac-fd0d-4bbf-b433-1121b6f05b68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 275b721c-892d-457d-bf04-d16c66d4e17f
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 275b721c-892d-457d-bf04-d16c66d4e17f
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== hdb1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-21-generic-pae
    .0GB: initrd.img-2.6.32-22-generic-pae
    .0GB: initrd.img-2.6.32-24-generic-pae
    .0GB: initrd.img-2.6.32-25-generic-pae
    .0GB: initrd.img-2.6.32-26-generic-pae
    .0GB: vmlinuz-2.6.32-21-generic-pae
    .0GB: vmlinuz-2.6.32-22-generic-pae
    .0GB: vmlinuz-2.6.32-24-generic-pae
    .0GB: vmlinuz-2.6.32-25-generic-pae
    .0GB: vmlinuz-2.6.32-26-generic-pae

=========================== hdb3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== hdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=05123bac-fd0d-4bbf-b433-1121b6f05b68 /               ext3    errors=remount-ro,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0 0       1
# /boot was on /dev/sda1 during installation
UUID=275b721c-892d-457d-bf04-d16c66d4e17f /boot           ext3    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=55adeb37-bc7e-470d-be94-5d47951d6b05 none            swap    sw              0       0

=================== hdb3: Location of files loaded by Grub: ===================


    .8GB: boot/grub/menu.lst



```

---

### Post by merlin4x on 2010-12-07
I get following error when executing first command
```

fx:/# mount /dev/sda3 /mnt
mount: you must specify the filesystem type
fx:/#

```

---

### Post by sikander3786 on 2010-12-07
You drives are being read as hda1, hdb1 (I don't know why) and also you seem to have a separate /boot partition so your commands would look like this.

```
sudo mkdir /mnt/boot
sudo mount /dev/hdb3 /mnt
sudo mount /dev/hdb1 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/hdb
```

I would suggest to try the above commands as an initial workaround. They might be or might not be successul because there seems to be another problem, menu.lst on your Lucid partition.

> hdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   **/boot/grub/menu.lst** /etc/fstab

So if the above commands are not successul, you need to adopt the method in following thread and purge Grub completely and then re-install.

Courtesy of forum member **drs305**

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Good Luck!

---

### Post by merlin4x on 2010-12-07
So I have decided to purge the grub as prescribed in above link.

As I got to the folowing step I got error.
```

sudo chroot /mnt/temp
chroot: cannot run command `/bin/bash': No such file or directory

```The /bin/bash is on life CD system as well as in rescued system   /mnt/RESCUE which I try to chroot.

Everything was return back as I started purge grub procedure.

Now I get this:
```

chroot /mnt/RESCUE /bin/bash
chroot: cannot run command `/bin/bash': No such file or directory

```I should say that I have copied "/bin/bash" into the "/mnt/temp" and then I removed it from there but the original is unattached.

So I am lost again.

How come that "chroot" does not see "/bin/bash"
Which "/bin/bash" are we talking about the one on live CD or the one in RESCUE directory?
How can I restore it?

---

### Post by sikander3786 on 2010-12-08
Not sure about that chroot stuff. (I have never done that honestly).

If you don't get responses in this thread, I would suggest to make a post in **drs305's** Grub Rescue Megathread here.

[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

They will definitely help you ;-)

---

