---
title: "Ubuntu 11.04 Black screen on Poweredge 2600"
date: 2013-01-01
forum: Server Platforms
---

### Post by mrosset on 2013-01-01
for some reason as far as I can tell grub uses some strange vbeinfo mode. I'm using 12.04 but I'm hoping if you are using grub2 this will work for you also. basically you want to turn off graphic's mode uncomment GRUB_TERMINAL=console in /etc/default/grub also comment out GRUB_HIDDEN_TIMEOUT. should look something like this.


```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=auto

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



```

after that make sure you run

```


$ sudo update-grub

or

$ sudo grub-mkconfig -o /boot/grub/grub.cfg


```
then reboot.

I'm using this as a server so I'm not really inclined to research it more then this.

hope, this helps. btw I made an account just to reply.

---

