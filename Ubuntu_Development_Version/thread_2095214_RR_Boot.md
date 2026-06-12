---
title: "RR Boot?"
date: 2012-12-16
forum: Ubuntu Development Version
---

### Post by kuvanito on 2012-12-16
first of all i acknowledge that RR13.04 is not even alpha yet BUT i still want to ask:
when i boot i get something like a hex file first(black screen and white numbers) sure it's a hex then my system boots OK
i would like to clean my Grub so that it does not show this hex numbers at boot.i am using the daily builds of RR13.04 and it is my only OS installed,here is a copy of my Grub:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


is there any line that i should comment to clean my boot?
Thank You and Happy Holidays!

---

### Post by jerrylamos on 2012-12-16
With early unstable linux the messages on the screen have been very useful to me in case of problems.  I"ll even turn "quiet" off to see what's going on.  Many times the last messages on the screen will give me a clue.

Now once the release is out and complete, bugs are down to a dull roar, sure, turn quiet off.

---

### Post by grahammechanical on 2012-12-16
This line should prevent what you are seeing.

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

In a normal situation that line would prevent any of those messages from appearing but something is over-riding the quiet mode and for good reason.

At the moment I am getting messages about buffer in/out on sda5, which is the swap partition. Every thing seems to work OK, as far as I can tell.

We are not in a normal situation. Are we? As all the bits and pieces that make up Raring Ringtail are brought together, these issues will go away. I hope.

Other than that, I cannot see any changes that you can make to the Grub configuration file that will hide those messages. Except perhaps this:

> # Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

I have never done this. I cannot say what the effect will be. I am not sure if we are still using grub-pc anyway. 

Regards.

---

