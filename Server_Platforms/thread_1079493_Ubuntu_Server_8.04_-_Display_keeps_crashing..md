---
title: "Ubuntu Server 8.04 - Display keeps crashing."
date: 2009-02-24
forum: Server Platforms
---

### Post by ashesh0326 on 2009-02-24
Hey all,

I need to run and maintain a server at my house for data storage and extended downloads, etc.

I have Ubuntu server 8.04 running on the machine, and I have automatic login enabled via gdm of a default user.

The server used to run smoothly until some time back, but of late, working on it has become really difficult as the display of the server keeps crashing from time to time. Sometimes it happens within seconds as well. The windows also flicker when I open another window, or browse through a folder. Running applications sometimes just disappear, like ktorrent or transmission. However, there has been no data loss.

The desktop running on this server is gnome. Going through the logs showed this: 
[http://i78.photobucket.com/albums/j104/Ashesh011/Screenshot.png](http://i78.photobucket.com/albums/j104/Ashesh011/Screenshot.png)

Can anyone tell me how to remedy this? Reinstallation is not an answer since there's just too much data on the server.

I've updated the server regularly.

I also noticed and after googling a little while, that this is probably a bug in the kernel. The problem started near a time when one of the updates updated the kernel. Can anyone tell me how to revert grub back to the original settings and use the old kernel, if this problem has no other fix?

Thanks in advance. :)

Server hardware:

Intel Xeon, 3 GHz
3 GB RAM
160 GB SATA HDD (SAMSUNG)
160 GB SATA HDD (SEAGATE)
Ubuntu Server 8.04

---

### Post by sarath_it on 2009-02-24
Smells! 

It could be kernel. 
if, at the time of next crash, you are able to get to console (cli), get this
```
dmesg > /tmp/dmesg.txt
```

It could also be display. did you rattle any screws relating to that? try reconfiguring X first
[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/)

if it doesnot try going back in kernel. If you are doing auto update, you  should have the backups of kernel in /boot and menu items in GRUB. if you dont have them, paste 
```
ls /boot > /tmp/boot-files.txt
cat /boot/grub/menu.lst > /tmp/menu-lst.txt

```

pastebin the info.. to investigate further.

---

### Post by cariboo on 2009-02-24
Why not just stop X and use X forwarding eg:

```
ssh -X user@server
```

then at the prompt type the program name you want to use for example to update or install packages:

```
synaptic
```

Jim

---

### Post by freerkkalsbeek on 2009-02-24
Maybe to odd, but I'm one of the consoleguys: "Why use X at all"
Where do you need it for? It's a server isn't it?

Freerk

---

### Post by ashesh0326 on 2009-02-24
Thanks for all the replies, guys. Here's the dmesg output right after another crash (all the menus and panels disappeared, only the desktop kept running when I tried to open a folder)
```

27.481366] sd 2:0:0:0: [sda] Starting disk
[   27.491956] sd 3:0:0:0: [sdb] Starting disk
[   27.512072] PM: Image restored successfully.
[   27.536679] Restarting tasks ... done.
[   27.545072] swsusp: Basic memory bitmaps freed
[   28.502923] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   28.502933] e100: Copyright(c) 1999-2006 Intel Corporation
[   28.503025] PCI: Enabling device 0000:05:08.0 (0000 -> 0003)
[   28.503036] ACPI: PCI Interrupt 0000:05:08.0[A] -> GSI 20 (level, low) -> IRQ 22
[   28.503112] PCI: Setting latency timer of device 0000:05:08.0 to 64
[   28.524462] e100: eth0: e100_probe: addr 0xff901000, irq 22, MAC addr 00:13:20:2a:df:1d
[   29.160991] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.169855] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   29.240318] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   39.939381] eth0: no IPv6 routers present
[10012.897751] metacity[6541]: segfault at 04d086a0 eip b79e7748 esp bfc4a2a0 error 4
[10025.142188] gnome-panel[6577]: segfault at 656d6f7a eip b76bf71c esp bff25a70 error 4
[10027.592694] gnome-panel[8628]: segfault at d5536818 eip b76d9705 esp bfb71a20 error 5
[10042.570029] metacity[8624]: segfault at 04ce3720 eip b79eb748 esp bfcb0cb0 error 4
[10062.937334] pidgin[8760]: segfault at bbad757c eip b7f4dfe6 esp bfec00c8 error 4
[10063.389193] gvfsd[8767]: segfault at 07f6fb0c eip b7e30705 esp bff43f50 error 4
[10063.913107] gnome-panel[8746]: segfault at 0a312445 eip b769c498 esp bfbe9560 error 4
[10063.936433] nautilus[8748]: segfault at 7120e80c eip b7f4201a esp bfe1c578 error 4
[10065.118354] gnome-panel[8777]: segfault at b92e6d38 eip b76b2705 esp bf9f21c0 error 4
[10066.532562] Xorg[8649]: segfault at 0000000b eip b7d0a386 esp bffb082c error 4
[10082.402204] gnome-settings-[8874]: segfault at de6a2150 eip b769f47d esp bf81bdb0 error 5
[10082.443392] gnome-panel[8886]: segfault at 74068228 eip b7f6001a esp bfa058e8 error 4
[10082.776309] nautilus[8891]: segfault at 2d21c6c3 eip b753e71c esp bfb99a20 error 4
[10202.372281] gnome-settings-[8894]: segfault at 04d7f11c eip b761850d esp bfa7da60 error 4
[10202.831175] pidgin[8923]: segfault at 62202c69 eip b7758498 esp bffb4e90 error 4
[10551.077032] bonobo-activati[9068]: segfault at 0a06e97c eip b7dcc705 esp bfe45d70 error 4
[10551.150994] gnome-panel[9057]: segfault at fae56764 eip b769f2ef esp bffef960 error 4
[10551.183847] metacity[9055]: segfault at 0816bc7c eip b791d705 esp bfcdb180 error 4
[10551.398628] nautilus[9059]: segfault at f8448c78 eip b757f47d esp bfd9f4a0 error 4
[10612.948984] metacity[9089]: segfault at ec89fc81 eip b7936303 esp bf9b3460 error 4
[10613.022296] Xorg[8970]: segfault at 0930f15c eip b7da5df3 esp bffa765c error 4
[10629.134291] gnome-power-man[9240]: segfault at ae18fc0c eip b7f1ffe6 esp bfcf9ca8 error 4
[10629.144630] pidgin[9238]: segfault at ec91d1b0 eip b76fad12 esp bfb0e150 error 4
[10629.227877] gnome-panel[9214]: segfault at aafdbbc8 eip b774a47d esp bfa30cc0 error 4
[10629.298553] nautilus[9217]: segfault at fa69f888 eip b75ecd12 esp bff49d00 error 4
[10834.374693] metacity[9213]: segfault at 0822b000 eip b79b3705 esp bf81c210 error 4
[12020.408828] gnome-panel[9247]: segfault at 08595bd8 eip b772e705 esp bfe48ca0 error 4
[12020.541454] gnome-panel[9405]: segfault at fc52f710 eip b767247d esp bfc56590 error 4
[12020.636579] gnome-panel[9419]: segfault at 486b7453 eip b774b71c esp bfa921b0 error 4
[12021.229233] gnome-panel[9432]: segfault at c54bc1dc eip b7721705 esp bfc01280 error 5
[19369.338397] gnome-panel[9446]: segfault at b92e6e18 eip b76b5705 esp bfde43b0 error 4
[19369.838783] gnome-panel[9628]: segfault at c54b71c4 eip b76b1705 esp bfa250a0 error 5
[19370.077642] gnome-panel[9631]: segfault at 00000415 eip b771071c esp bffc1700 error 4
[19901.909589] bonobo-activati[9787]: segfault at b383e690 eip b7f7dfe6 esp bfb69fcc error 4
[19901.954185] gnome-panel[9778]: segfault at a6a5e6f4 eip b76e147d esp bfab0630 error 4
[19902.290168] nautilus[9781]: segfault at 00000034 eip b757c71c esp bf87fe10 error 4
[19902.345027] gnome-power-man[9813]: segfault at 04a0a33c eip b71fd705 esp bfa24ab0 error 4
[19902.925817] pidgin[9804]: segfault at 928127c4 eip b7764705 esp bff80b90 error 4
[26370.701169] gnome-wm[10079]: segfault at b44ae6fc eip b7f48fe6 esp bfc35b48 error 4
[26371.600425] hald[5173]: segfault at 00000000 eip b7c8a283 esp bf95bfbc error 4
[26372.016006] gnome-panel[10080]: segfault at accf89a8 eip b772147d esp bf8f64b0 error 4
[26372.333352] nautilus[10081]: segfault at 6c70706d eip b75c9498 esp bf9354d0 error 4
[26372.645837] gnome-panel[10093]: segfault at 65742d71 eip b768171c esp bfae0c40 error 4
[26490.806427] gnome-power-man[10112]: segfault at a950a170 eip b720e705 esp bfa48e90 error 4
[26493.091828] pidgin[10109]: segfault at 08696890 eip b7764705 esp bfef6cd0 error 4
[32990.829133] gconftool-2[10309]: segfault at b5f4fce8 eip b7d7447d esp bfd52b80 error 4
[33015.690852] aplay[10379]: segfault at fa2d1794 eip b7f8501a esp bfabefdc error 4
[33028.049597] gnome-panel[10456]: segfault at f55f5488 eip b775847d esp bf8431b0 error 4
[33028.262146] gconftool-2[10477]: segfault at ff1df588 eip b7db7705 esp bf8d63d0 error 4
[33028.451705] gnome-power-man[10482]: segfault at 0c458b10 eip b725d498 esp bfb8af80 error 4
[33028.587930] pidgin[10475]: segfault at 07ebe008 eip b773e705 esp bffe3380 error 4
[33028.738933] gnome-panel[10465]: segfault at 28e80851 eip b775c71c esp bfc6a3b0 error 4
[33028.758307] nautilus[10458]: segfault at 362c7379 eip b752a498 esp bff39eb0 error 4
[33056.682691] gnome-keyring-d[10436]: segfault at 0809ec00 eip 0809ec00 esp bfe286bc error 15
[40231.703529] gnome-panel[10485]: segfault at fff476c0 eip b76cf71c esp bff40c70 error 4
[40235.601899] gnome-panel[10881]: segfault at c54b6d24 eip b770a705 esp bfa1cc40 error 5
[61922.284099] gnome-panel[10889]: segfault at e0879158 eip b76af705 esp bfc82770 error 4
[61922.691437] gnome-panel[11680]: segfault at de6444b4 eip b7694705 esp bfc3dca0 error 5
[61922.761454] nautilus[11657]: segfault at c7b7f2a4 eip b75cf705 esp bfcda500 error 5
[61932.601524] nautilus[11699]: segfault at 0000002f eip b757d71c esp b5da1040 error 4
[61932.634212] gnome-panel[11684]: segfault at 06f29d28 eip b7677705 esp bfab08d0 error 4
[61932.681194] metacity[10455]: segfault at 04d24d90 eip b7912748 esp bff3f790 error 4
[61932.901500] gnome-panel[11707]: segfault at f15b03b8 eip b769c47d esp bfea2fe0 error 4
[61932.915858] gnome-panel[11710]: segfault at b645a024 eip b7fdefe6 esp bfb2bf9c error 4
[61959.114352] end_request: I/O error, dev fd0, sector 0
```

I need to keep the display running on this system because I also use it for torrenting stuff etc.

---

### Post by ashesh0326 on 2009-02-25
Bootfiles:
```

abi-2.6.24-19-server
config-2.6.24-19-server
grub
initrd.img-2.6.24-19-server
initrd.img-2.6.24-19-server.bak
memtest86+.bin
System.map-2.6.24-19-server
vmlinuz-2.6.24-19-server
```


Grub Menu: # ```
menu.lst - See: grub(8), info grub, update-grub(8)
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=2fceb69b-cff1-42a4-97ad-fe41642ce583 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=2fceb69b-cff1-42a4-97ad-fe41642ce583 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=2fceb69b-cff1-42a4-97ad-fe41642ce583 ro single
initrd		/boot/initrd.img-2.6.24-19-server

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by ashesh0326 on 2009-02-26
any answers?

---

### Post by ashesh0326 on 2009-02-27
Reconfiguring X didn't work.

---

### Post by ashesh0326 on 2009-03-03
Can anyone please help me boot with the previous kernel?

---

### Post by sarath_it on 2009-03-05
Run

bash
sudo apt-get install linux-headers

and press tab twice, you will see the list of installable headers with version numbers, choose the one you want, it should come in grub menu after.

You might have to choose server ones.

---

### Post by ashesh0326 on 2009-03-05
> apt-get install linux-headers
Reading package lists... Done
Segmentation faulty tree... 50%

Segfaults all over the place. :(

---

### Post by sarath_it on 2009-03-06
Woaaa bud! You have some serious issues on this installation. I would suggest back up data immediately.

Reinstalling would be much better than trying to solve these unknowns.. 

You may be able to use some help of remastersys - [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html) to restore the application packages 

But thats about it.. I guess..

---

