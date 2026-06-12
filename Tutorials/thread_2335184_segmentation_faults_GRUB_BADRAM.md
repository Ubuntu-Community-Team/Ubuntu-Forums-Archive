---
title: "segmentation faults GRUB_BADRAM"
date: 2016-08-26
forum: Tutorials
---

### Post by jimpster1 on 2016-08-26
Fix segmentation faults by using GRUB_BADRAM parameter in grub.

-This is for other newbies that don't want to spend 4 hours running all over the Internet getting clues.
-This is for 64 bit everything. I am running Kubuntu Xenial.
-If you can do better write your own tutorial, or if know of a better thread, speak up.

If you have bad memory, and decline to get new memory you can uncomment out something in /etc/default/grub  -->GRUB_BADRAM....

At boot- hold down shift key, select recovery mode, select memtest86+ and let it do a couple passes, write down the problem address's, then ctl+c or esc. yada yada yada
There where 600+ errors for me, after reviewing the list they all started with 003fab8**** and 0015f58****.
All the tutorials for editing GRUB, and uncommenting GRUB_BADRAM out there are for 32 bit machines and unclear, I run 64bit and have 16GB of memory.

This did not work! --> GRUB_BADRAM="3fab80000,3fab8ffff"

This did work--> GRUB_BADRAM="0x00000003fab80000,0xffffffffffff0000,0x000000015f580000,0xffffffffffff0000"
As you can see I added 0x and a bunch of zero's. thats 18 bits total.
The GRUB_BADRAM format is a pattern: memory block address start, then mask (amount of memory), memory address start, mask, .....
Here is my grub file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_CMDLINE_LINUX="quiet splash"
GRUB_BADRAM="0x00000003fab80000,0xffffffffffff0000,0x000000015f580000,0xffffffffffff0000"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

don't forget to: sudo update-grub -when your finished.
If you get it wrong you might not get back in. I managed too each time in recovery, but just barely. lol
If you memtest again from the grub menu you will see no errors hopefully. By the way most of what I read today strongly suggests to just replace the memory in question.
Again, I contributed what I learned today, because of lack of better tutorial.

---

