---
title: "startup-manager"
date: 2012-03-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ibbill on 2012-03-31
Running 12.04 beta 2 I need to change the  resolution on the boot up screen as I have 3 systems installed.

Since I installed 12.04 have been unable to change it and there is not startup-manager that I use to use.

Has the name been changed or is just not available any more.

Really need to change the resolution thanks for your help.

---

### Post by wojox on 2012-03-31
```
wojox@wojox-desktop:~$ cat /etc/default/grub
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
[COLOR="Purple"]GRUB_GFXMODE=640x480[/COLOR]

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Did you modify this file and update grub?

---

### Post by sffvba[e0rt on 2012-03-31
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*


404

---

### Post by ibbill on 2012-03-31
oh wow thanks. That is far to much for me to handle. Going to go back and use Lisa Mint 12.

Hope some day they will make ubuntu user friendly again.

---

### Post by wojox on 2012-03-31
> **ibbill said:**
> oh wow thanks. That is far to much for me to handle. Going to go back and use Lisa Mint 12.

Hope some day they will make ubuntu user friendly again.

Your in beta testing. :p

---

### Post by dino99 on 2012-03-31
> **ibbill said:**
> oh wow thanks. That is far to much for me to handle. Going to go back and use Lisa Mint 12.

Hope some day they will make ubuntu user friendly again.

grub-customizer can do what you want :)

add this ppa to get it:  [https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

---

### Post by ibbill on 2012-03-31
thanks for the help and info.

Why please someone tell me why they would  take  something that was so easy to use away from users of ubuntu?

---

### Post by wojox on 2012-03-31
> **ibbill said:**
> thanks for the help and info.

Why please someone tell me why they would  take  something that was so easy to use away from users of ubuntu?

It hasen't been built for Precise as of yet.

---

### Post by ibbill on 2012-03-31
okay  awesome tks will wait and use Mint 12 till the final comes out at the end of April tks again.

---

### Post by oldos2er on 2012-03-31
> **ibbill said:**
> thanks for the help and info.

Why please someone tell me why they would  take  something that was so easy to use away from users of ubuntu?

Are you referring to Startupmanager? It was never fully developed to be compatible with grub2. 
[https://launchpad.net/startup-manager/+announcement/8300](https://launchpad.net/startup-manager/+announcement/8300)

---

### Post by rburkartjo on 2012-03-31
dino tks works like a charm for me in 12.04b2. had an older version but wouldnt work

---

### Post by dino99 on 2012-03-31
> **rburkartjo said:**
> dino tks works like a charm for me in 12.04b2. had an older version but wouldnt work

my pleasure :) have a nice WE

---

