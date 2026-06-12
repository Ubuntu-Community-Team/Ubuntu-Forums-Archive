---
title: "grub menu"
date: 2010-10-26
forum: Server Platforms
---

### Post by Vegan on 2010-10-26
Seems that if there is no keyboard present, the grub menu freezes.

Anyway to fix that so I can disconnect a keyboard from the machine to make it a real server.

---

### Post by the_original_billq on 2010-10-26
Set your BIOS to point the console to ttya, and include:

```

console=ttys0,57600

```

on your "kernel" line.

---

### Post by Vegan on 2010-10-26
where is grub hiding on 10.10?

---

### Post by the_original_billq on 2010-10-26
It's now grub2.  Oh, happy day.

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")


"Booting from a serial console

If you want GRUB to operate over a serial line, you will need to uncomment GRUB_TERMINAL in /etc/default/grub and set it to serial (instead of the console default). The default serial console settings are to operate on the first serial port (ttyS0) at a 9600 bit/s transfer rate with 8 data bits, 1 stop bit and no parity.

If you want to use another serial port or if your console uses different settings, you must add a GRUB_SERIAL_COMMAND line to specify additional parameters to the serial command. The serial command in GRUB 2 uses the same syntax as its GRUB Legacy counterpart (documented here). For example, for a 4800 bit/s serial line with 7 data bits, 1 stop bit and even parity:

GRUB_SERIAL_COMMAND="serial --unit=0 --speed=4800 --word=7 --parity=even --stop=1"
"

---

### Post by Vegan on 2010-10-26
I just want that menu to disappear.

Defaulting to the main OS

---

### Post by Vegan on 2010-10-27
Anyone good with grub? Want that menu gone.

---

### Post by CharlesA on 2010-10-27
You have to edit the default setting in Grub2. See [here]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202")

The setting you want is GRUB_DEFAULT and GRUB_TIMEOUT

---

### Post by Vegan on 2010-10-27
Looks alright but the menu persists, until I plug in a keyboard and whack enter.

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by CharlesA on 2010-10-27
What happens if you set the GRUB_TIMEOUT to 0 instead of 2?

Mine says this:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

But it doesn't just sit there after a reboot.

---

### Post by Vegan on 2010-10-27
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-22-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done


That change seems to be what I needed, I changed the grub file as suggested and ran update-grub as the manual said and rebooted.

I was able to remote in so its working.

BTW the 10.10 was a fresh install on a 160 GB disk. So that was the default menu, not so server friendly in my humble opinion. Server needs to be up, not stuck on some off-handed menu.

Thanks.

:guitar:

---

