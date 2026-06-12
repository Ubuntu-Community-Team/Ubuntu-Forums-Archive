---
title: "ubuntu server 12.04 - will not boot unattended after power failure"
date: 2013-04-21
forum: Server Platforms
---

### Post by nicolasdiogo on 2013-04-21
hello 

i have noticed a 'feature' that seems to stop my servers from reboot/booting after a power-failure.

instead of booting up when power is restored these system just get to the GRUB menu and wait for an user to click on an option.

is there any option that i can edit on the GRUB config files that can change to make these system boot up un-attended?

thanks,

---

### Post by cariboo on 2013-04-21
You can edit /etc/default/grub to set the time out, to allow your server to boot. The file looks like this:

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
```

As you can see the default is set to 10, on my server, I change it to 0

---

### Post by nicolasdiogo on 2013-04-25
thanks (and apologies for delay in responding)

i think this problem may be related to this:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/447725](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/447725)

i have this **recordfail**
at the top of the grub entry of the boot menu

so when i try to edit it - i find this recordfail


it seems that we can have this sorted with this:
> 
For ubuntu 12 there is specific option that can be set in /etc/default/grub.

For example, if you want to have a 2 seconds timeout (thus avoiding hangs for unattended reboots) just add the following line in /etc/default/grub:

GRUB_RECORDFAIL_TIMEOUT=2

Remember to run update-grub after that...

source:
[http://serverfault.com/questions/243343/headless-ubuntu-server-machine-sometimes-stuck-at-grub-menu](http://serverfault.com/questions/243343/headless-ubuntu-server-machine-sometimes-stuck-at-grub-menu)


i will try these options - not tested yet..

---

### Post by nicolasdiogo on 2013-08-04
yep it has done the work.

---

