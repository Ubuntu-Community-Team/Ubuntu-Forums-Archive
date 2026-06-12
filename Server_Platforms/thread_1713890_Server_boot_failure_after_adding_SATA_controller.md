---
title: "Server boot failure after adding SATA controller"
date: 2011-03-24
forum: Server Platforms
---

### Post by MakOwner on 2011-03-24
I have a PowerEdge 1750 booting off the scsi hardware raid volume.
This is the "megaraid" driver I think.

I added a PCI-X eSATA controller to add some cheap disk.

After adding the controller, grub can no longer find the boot device.  
I take the controller out, and it boots again.

the /dev/disk/by-uuid is present when I'm dropped to a shell when the boot fails, and it matches the entry in the fstab.

Anyone know what gives?
I can just reload the OS on the machine, no big deal, but I'd really like to know why this isn't working.

---

### Post by Vegan on 2011-03-24
I wonder if there is a ROM on the controller that is taking over

---

### Post by MakOwner on 2011-03-24
> **Vegan said:**
> I wonder if there is a ROM on the controller that is taking over

I don't think so, but I do see the new controller bios first.
Even so, it should be booting off the disk identified by the correct UUID shouldn't it?

---

### Post by disabledaccount on 2011-03-24
There are many possible reasons, but at this point most important question is: have you tried to boot manually from shell (set root, etc) ?

---

### Post by MakOwner on 2011-03-24
> **tomazzi said:**
> There are many possible reasons, but at this point most important question is: have you tried to boot manually from shell (set root, etc) ?

I tried re-installing grub while the card was in to update the boot device but no luck.  

I just pulled the card and the machine boots normally.


I'm going to put the card back in and putz around in the bios.
Hopefully something in there will let me change priority.

---

### Post by disabledaccount on 2011-03-25
I'm affraid it's not because of BIOS boot sequence, but indeed it can be BIOS - related problem, such as wrong IRQ routing or crappy controller software. You can try to disable new controller BIOS - it should be possible inside MB BIOS by setting Boot Other Devices = NO (or similar) or inside controller BIOS (it will only configure its PCI registers, then exit) - consult the manual.

---

### Post by MakOwner on 2011-03-26
> **MakOwner said:**
> I tried re-installing grub while the card was in to update the boot device but no luck.  

I just pulled the card and the machine boots normally.


I'm going to put the card back in and putz around in the bios.
Hopefully something in there will let me change priority.

Argh - quoting myself which is bad but....

So, I take the card out, things work OK.
Put the card in, and the system won't boot.
Nothing in the BIOS seems to affect this - so far.

So, it means I need to fix the boot information so that the boot process points at the correct location. 

Keep in mind there are no additional new disk, only the new controller and the old boot volumes was addressed as /dev/sda and the only volume in the system afterboot with the new card in is still /dev/sda...

So, I tried a grub-install /dev/sda and grub-install /dev/sda2 (which was the partition with the boot flag...)

Neither of which improve the chances of booting.

This tells me I need to dig deeper.

Can anyone help me figure this out, or point me at the appropriate information?

---

### Post by MakOwner on 2011-03-26
OK, this sucks.
I got pissed and just wiped the system and re-installed.

It still won't boot!

How/why would the installer set up a boot process that fails?

Let me rephrase that: Anyone have any idea how to get the system to boot off /dev/sda with the extra controller installed?

---

### Post by disabledaccount on 2011-03-27
Try putting the controller in another slot(s) - this will change IRQ routing and possibly could help. Furthermore You can mark some IRQs as "reserved" in PCI configuration inside MB BIOS.

---

### Post by MakOwner on 2011-03-27
> **tomazzi said:**
> Try putting the controller in another slot(s) - this will change IRQ routing and possibly could help. Furthermore You can mark some IRQs as "reserved" in PCI configuration inside MB BIOS.

I have.  The Dell BIOS even has the ability to change some IRQ assignments.
Nothing I have been able to do so far allows the server to boot.

At this point, I just need a way to for the boot disk/partition I guess.

---

### Post by disabledaccount on 2011-03-27
Have You tried to boot off grub shell by manually applying 'insmod', 'set root' etc?

---

### Post by MakOwner on 2011-03-27
> **tomazzi said:**
> Have You tried to boot off grub shell by manually applying 'insmod', 'set root' etc?

Tomorrow evening will be the next chance I get to work on it again.

---

### Post by MakOwner on 2011-03-28
> **tomazzi said:**
> Have You tried to boot off grub shell by manually applying 'insmod', 'set root' etc?

Just got a chance to try again.
It drops me in initramfs, and no way to get to grub.

If I use a recovery disk, shouldn't re-install grub fix this?

grub-install /dev/sda or grub-install /dev/sda1 ?

Can I do this directly from a rescue shell or do I have to chroot first?

It also occurs to me -- the controller I have added is a generic SiL3124 I have soem other generic controllers that install fin in this version of Linux, 
but I have always done them from a "full" install, not the minimal install CD I'm using for this -- could it be that the missing modules are causing the boot failure?
There are no disk attached yet, so I can't see why it wouldn't just go on with the boot...

---

### Post by disabledaccount on 2011-03-28
definitively >grub-install /dev/sda - this installs grub in MBR
You don't have to chroot, it is sufficient to give target root dir as argument:
>grub-install --root-directory=<dir_with_mounted_sda1> --recheck /dev/sda

I don't think that minimal CD has limitted version of GRUB - I suppose this can be bug in PCI BIOS or in pci GRUB module (I' always using full CD)

---

### Post by MakOwner on 2011-03-28
> **tomazzi said:**
> definitively >grub-install /dev/sda - this installs grub in MBR
You don't have to chroot, it is sufficient to give target root dir as argument:
>grub-install --root-directory=<dir_with_mounted_sda1> --recheck /dev/sda

I don't think that minimal CD has limitted version of GRUB - I suppose this can be bug in PCI BIOS or in pci GRUB module (I' always using full CD)

Something is FUBAR.  boot from the minimal disk in rescue mode and when drooped to a root shell on /dev/sda1 where I can SEE the grub configuration files and what not, no grub command work.  grub is not installed.
apt-get install grub get it installed, but none of the install or update commands will actually.  

I'll try this from a full desktop install next.

---

### Post by MakOwner on 2011-03-28
> **tomazzi said:**
> definitively >grub-install /dev/sda - this installs grub in MBR
You don't have to chroot, it is sufficient to give target root dir as argument:
>grub-install --root-directory=<dir_with_mounted_sda1> --recheck /dev/sda

I don't think that minimal CD has limitted version of GRUB - I suppose this can be bug in PCI BIOS or in pci GRUB module (I' always using full CD)

Christ on a bicycle.  Now I remember why I was using the minimal install CD instead of the server or desktop disks.  Freaking full install can't get through the installer setup.  Like I really freaking need the full freaking distro loaded into memory for an installation.  Gimme a break.

I'm going back to 9.10.  I had been able to load a 9.10 desktop on this hardware once before.

This is a quad core (Twin dual, I think, anyway) 3.06 Xeon chipset with 8GB RAM and the 10.04 installer pukes. Hell, even Windows will install on this crap. ](*,)

---

### Post by MakOwner on 2011-03-28
OK, 9.10 server installation CD will get me a loaded OS that boots with the controller installed.

So, 10.04 LTS server installer/grub is broken?
](*,)

We'll see if an upgrade to 10.04 will still be able to boot.

---

### Post by MakOwner on 2011-03-28
arrgggghhh........

How and why is this so farked up is beyond me.
The issue appears to be grub in the Lucid repositories.
I thought things were supposed to get *better*, not worse?

Upgrade from Karmic to Lucid halts at the grub upgrade.  It thinks no version of grub is installed, and you can't install the new version, but when you say to skip the install it proceeds to clobber the currently installed and functional grub. Great job that...

Anyone know how to downgrade to a functional grub that works with 10.04 LTS or am I just stuck at 9.x and screwed?

---

### Post by MakOwner on 2011-03-29
OK, still no resolution and after looking back over my notes, I see I had the same situation with a 2450, I just gave it up and let it go with 9.10 on it.

So, because I do intend to use this hardware I'm continuing to try to get this to work.  I have made another post on here to offer up this particular set of hardware up for testing if it will help identify this issue.

This is what works:
grub 1.97 beta 4 on 9.10 from server install

```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 8db66730-24d2-4574-8f79-21bda443ce59
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
if [ ${recordfail} = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-23-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8db66730-24d2-4574-8f79-21bda443ce59
	linux	/boot/vmlinuz-2.6.31-23-generic-pae root=UUID=8db66730-24d2-4574-8f79-21bda443ce59 ro rootdelay=10  quiet splash
	initrd	/boot/initrd.img-2.6.31-23-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-23-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8db66730-24d2-4574-8f79-21bda443ce59
	linux	/boot/vmlinuz-2.6.31-23-generic-pae root=UUID=8db66730-24d2-4574-8f79-21bda443ce59 ro single rootdelay=10
	initrd	/boot/initrd.img-2.6.31-23-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8db66730-24d2-4574-8f79-21bda443ce59
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=8db66730-24d2-4574-8f79-21bda443ce59 ro rootdelay=10  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8db66730-24d2-4574-8f79-21bda443ce59
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=8db66730-24d2-4574-8f79-21bda443ce59 ro single rootdelay=10
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=10
    else
      set timeout=10
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=10
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```


This does NOT work - 10.04.2 grub 1.98 from 10.04 minimal install with updates during install (Note that I have forced a 10 second menu timeout in grub so I have an opportunity to edit the command line)

```

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 9407f497-da88-4083-9b9e-a6af29c62b1d
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
search --no-floppy --fs-uuid --set 9407f497-da88-4083-9b9e-a6af29c62b1d
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9407f497-da88-4083-9b9e-a6af29c62b1d
	linux	/boot/vmlinuz-2.6.32-30-generic-pae root=UUID=9407f497-da88-4083-9b9e-a6af29c62b1d ro rootdelay=10  splash quiet
	initrd	/boot/initrd.img-2.6.32-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9407f497-da88-4083-9b9e-a6af29c62b1d
	echo	'Loading Linux 2.6.32-30-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-30-generic-pae root=UUID=9407f497-da88-4083-9b9e-a6af29c62b1d ro single rootdelay=10
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9407f497-da88-4083-9b9e-a6af29c62b1d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9407f497-da88-4083-9b9e-a6af29c62b1d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=10
    else
      set timeout=10
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=10
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

---

### Post by MakOwner on 2011-03-30
OK, this is NOT solved, but there is a workaround.
The bug stands with grub and I'm still trying to chase down the exact area where issue occurs.

The current iteration of grub(version2 actually) used on minimal installation is

grub-common 1.98-1ubuntu10
grub-pc 1.98-1ubuntu10


using a --rootdelay=100 parameter on boot will allow the discovery of the disk by UUID.  

Editing of the /etc/default/grub file and using update-grub will update the boot parameters (at least the rootdelay, anyway).
I can't get grub2 to display a boot menu with manually editing /boot/grub/grub.cfg.  
GRUB_TIMEOUT in /etc/default/grub is ignored, or at least if it is honored, there is no display during boot.

---

