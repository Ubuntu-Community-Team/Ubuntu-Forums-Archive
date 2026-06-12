---
title: "How to boot straight into terminal?"
date: 2010-01-19
forum: Server Platforms
---

### Post by guitarhero183 on 2010-01-19
I have installed the ubuntu-desktop package on top of ubuntu server 9.1 but now I would like to remove it and boot straight into terminal. I have tried searching for an answer but found nothing that helps. I would just like to have a basic server that goes straight into terminal.

---

### Post by carcar1 on 2010-01-19
```
sudo apt-get uninstall ubuntu-desktop
``` Should work.

---

### Post by steveneddy on 2010-01-19
[http://ubuntuforums.org/showpost.php?p=2083338&postcount=2](http://ubuntuforums.org/showpost.php?p=2083338&postcount=2)

---

### Post by fancypiper on 2010-01-19
> **guitarhero183 said:**
> I have installed the ubuntu-desktop package on top of ubuntu server 9.1 but now I would like to remove it and boot straight into terminal. I have tried searching for an answer but found nothing that helps. I would just like to have a basic server that goes straight into terminal.If you meant Ubuntu 9.10, I think you can edit /etc/default/grub and comment out a couple of lines, then update-grub.
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=0
# GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=800X600
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

---

### Post by guitarhero183 on 2010-01-19
Thanks for the help but I ended up fixing the problem by going into Synaptic Package Manager and deleting all the packages I did not want.

---

