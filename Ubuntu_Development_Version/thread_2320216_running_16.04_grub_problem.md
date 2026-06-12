---
title: "running 16.04 grub problem"
date: 2016-04-11
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2016-04-11
okay i am over looking something. was trying to modify grub so the screen did not time out after 10 seconds. goofed. now grub menu only appears if i hold down the shift key at startup

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
GRUB_BACKGROUND=

tks

---

### Post by izznogooood on 2016-04-11
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="noprompt persistent"
```

I dont know if the last line is because of the kernel I´m running, but your missing  it...

---

### Post by grahammechanical on 2016-04-11
From my reading of the Grub manual we get the situation where a key press is required to display the Grub menu when

GRUB_TIMEOUT=0
GRUB_HIDDEN_TIMOUT=0

your /usr/share/grub/default file is correct for displaying the menu with a 10 second delay before loading the default OS. It is exactly the same as the file on my system. I can only guess that you have re-edited the file to correct the changes you have made but not run

```
sudo update-grub
```

I quote the Grub manual

> &#8216;GRUB_TIMEOUT&#8217;

Boot the default entry this many seconds after the menu is displayed, unless
a key is pressed. The default is &#8216;5&#8217;. Set to &#8216;0&#8217; to boot immediately without
displaying the menu, or to &#8216;-1&#8217; to wait indefinitely.

&#8216;GRUB_HIDDEN_TIMEOUT&#8217;

Wait this many seconds for a key to be pressed before displaying the menu.
If no key is pressed during that time, display the menu for the number of
seconds specified in GRUB TIMEOUT before booting the default entry. We
expect that most people who use GRUB HIDDEN TIMEOUT will want to
have GRUB TIMEOUT set to &#8216;0&#8217; so that the menu is not displayed at all
unless a key is pressed. Unset by default.


Regards.

---

### Post by rburkartjo on 2016-04-12
gra i did set the timeout to -1 and it did not work. just needed a sanity check to make sure . /tks

---

