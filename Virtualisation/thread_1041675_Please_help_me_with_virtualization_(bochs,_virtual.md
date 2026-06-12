---
title: "Please help me with virtualization (bochs, virtualbox or other)"
date: 2009-01-16
forum: Virtualisation
---

### Post by Keith_Beef on 2009-01-16
I tried doing this in VirtualBox, but [this thread]("http://ubuntuforums.org/showthread.php?t=1038794") shows the problem I'm having with that...

So I tried Bochs.

I needed to fix the bochsrc file supplied in package 2.3.7-1ubuntu1 to look like this:
```

config_interface: textconfig
display_library: x
romimage: file=/usr/share/bochs/BIOS-bochs-latest
megs: 32
vgaromimage: file=/usr/share/vgabios/vgabios.bin
# floppya: 1_44=/dev/fd0, status=inserted
ata0: enabled=1, ioaddr1=0x1f0, ioaddr2=0x3f0, irq=14
ata1: enabled=0, ioaddr1=0x170, ioaddr2=0x370, irq=15
ata2: enabled=0, ioaddr1=0x1e8, ioaddr2=0x3e0, irq=11
ata3: enabled=0, ioaddr1=0x168, ioaddr2=0x360, irq=9
#ata0-master: type=disk, path="", mode=flat, cylinders=1024, heads=16, spt=63
ata0-slave: type=cdrom, path="/dev/cdrom1", status=inserted

boot: cdrom

ips: 1000000
# floppy_bootsig_check: disabled=0
log: /dev/stdout
panic: action=ask
error: action=report
info: action=report
debug: action=ignore
debugger_log: -
com1: enabled=1, dev=/dev/ttyS0
parport1: enabled=1, file="/dev/lp0"
sb16: midimode=1, midi=/dev/midi00, wavemode=1, wave=/dev/dsp, loglevel=2, log=/dev/stdout, dmatimer=600000
vga_update_interval: 300000
keyboard_serial_delay: 250
keyboard_paste_delay: 100000
# floppy_command_delay: 500
mouse: enabled=1
private_colormap: enabled=0
#ne2k: ioaddr=0x240, irq=9, mac=b0:c4:20:00:00:00, ethmod=linux, ethdev=eth0
#keyboard_mapping: enabled=0, map=/usr/share/bochs/keymaps/x11-pc-de.map
#keyboard_type: mf
#user_shortcut: keys=ctrlaltdel
#magic_break: enabled=1
#cmosimage: cmos.img
#load32bitOSImage: os=nullkernel, path=../kernel.img, iolog=../vga_io.log
#load32bitOSImage: os=linux, path=../linux.img, iolog=../vga_io.log, initrd=../initrd.img
#i440fxsupport: enabled=1
usb1: enabled=1, ioaddr=0xFF80, irq=10
#text_snapshot_check: enable
```

Now I can boot from the CD, but get no further than shown below.
[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/screenshots/th_bochs_boot.png[/IMG]](http://s71.photobucket.com/albums/i121/Keith_Beef/screenshots/?action=view&current=bochs_boot.png)

When I look in the terminal window, I see the same problem as in VirtualBox:
```
00008509524i[BIOS ] Booting from 0000:7c00
00008517941i[BIOS ] int13_cdemu function AH=42 unsupported, returns fail
00008522262i[BIOS ] int13_cdemu function AH=42 unsupported, returns fail
00008526606i[BIOS ] int13_cdemu function AH=42 unsupported, returns fail
...
00009241483i[BIOS ] int13_cdemu function AH=48 unsupported, returns fail
00009248620i[BIOS ] int13_cdemu function AH=48 unsupported, returns fail
00009279910i[BIOS ] int13_harddisk: function 08, unmapped device for ELDL=80
00009287976i[BIOS ] int13_harddisk: function 08, unmapped device for ELDL=80
```

How can I fix or get around this problem?


K.

---

### Post by Keith_Beef on 2009-01-21
BUMP

Am I really the only person on UbuntuForums to want to get this working?

K.

---

