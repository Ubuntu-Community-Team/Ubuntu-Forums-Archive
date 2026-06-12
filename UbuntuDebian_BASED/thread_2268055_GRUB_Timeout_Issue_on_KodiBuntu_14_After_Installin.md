---
title: "GRUB Timeout Issue on KodiBuntu 14 After Installing Updates"
date: 2015-03-05
forum: Ubuntu/Debian BASED
---

### Post by Kirk Schnable on 2015-03-05
Hello All,

I recently did a fresh install of KodiBuntu which is a Ubuntu based installation with extra packages for media centers (previously known as XBMC).

I used this install image
[http://mirrors.xbmc.org/releases/kodibuntu/kodibuntu-14.0~helix_amd64.iso](http://mirrors.xbmc.org/releases/kodibuntu/kodibuntu-14.0~helix_amd64.iso)

The system initially booted up fine with no issues.

I hopped on the TTY to install an SSH server and I decided to also do an apt-get dist-upgrade to get all my packages up to latest version.

Since doing that, my system hangs at the GRUB menu at boot.  There is no problem and it boots successfully after someone hits Enter, so it seems to be merely a GRUB timeout issue.

I tried manually changing a few timeout values as suggested online, and edited /etc/default/grub, then ran update-grub, and rebooted.  The issue persists.  Here is my /etc/default/grub

```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


GRUB_RECORDFAIL_TIMEOUT=0


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
GRUB_GFXPAYLOAD_LINUX=keep
GRUB_GFXPAYLOAD_LINUX=keep
GRUB_RECORDFAIL_TIMEOUT=0
```

Any idea what the issue is?  Surely this is just a setting.

Here are some software versions for your reference as well.

```
root@MediaPC:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS - KODIbuntu
Release:    14.04
Codename:    trusty
root@MediaPC:~# 
```

```
root@MediaPC:~# uname -a
Linux MediaPC 3.13.0-46-generic #76-Ubuntu SMP Thu Feb 26 18:52:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
root@MediaPC:~# 
```

```
root@MediaPC:~# dpkg --list | grep grub
ii  grub-common                                 2.02~beta2-9ubuntu1                   amd64        GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists                       0.6                                   amd64        GRUB gfxpayload blacklist
ii  grub-pc                                     2.02~beta2-9ubuntu1                   amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                                 2.02~beta2-9ubuntu1                   amd64        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                                2.02~beta2-9ubuntu1                   amd64        GRand Unified Bootloader (common files for version 2)
root@MediaPC:~# 
```

Thanks,
Kirk

---

### Post by sblack55 on 2015-05-01
I see you got no replies to your question here.  I presume you found what you needed elsewhere.  Can you (or anyone) share anything useful?

My problem is dist-upgrade installed kernel 3.13.0-51, and updated grub's boot entries, but grub is still loading 3.13.0-49.  I tried tweaking settings as you mentioned, but I cannot get grub to boot the new kernel or display a visible menu.

---

