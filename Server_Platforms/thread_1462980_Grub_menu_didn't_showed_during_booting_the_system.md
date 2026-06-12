---
title: "Grub menu didn't showed during booting the system"
date: 2010-04-26
forum: Server Platforms
---

### Post by ivancheng on 2010-04-26
Hi,

Here's exracted from ubuntu [Grub2]("https://help.ubuntu.com/community/Grub2?action=fullsearch&context=180&value=linkto%3A%22Grub2%22") document [https://help.ubuntu.com/community/Grub2:](https://help.ubuntu.com/community/Grub2:)

***GRUB_HIDDEN_TIMEOUT=0*** 

[LIST]
[*]This setting determines how long a screen without the GRUB 2 menu will be displayed. While the screen is blank, the user can press any key to display the menu.
[*]The default behavior is to hide the menu if only one operating system is present. If a user with only Ubuntu wishes to display the menu, place a **#** symbol at the start of this line to disable the hidden menu feature.
[/LIST]
According to above information, I have tried to set below in order the show the menu:

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT="20"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

However, the menu didn't show up regarding to reboot or power up the system.

Is there any missing in the configuration?

Thanks in advance.

Rgds,
Ivan

---

### Post by ghost_ryder35 on 2010-04-26
did you run 'update-grub' after making the changes?

---

### Post by BobVila on 2010-04-26
> **ivancheng said:**
> Hi,

Here's exracted from ubuntu [Grub2]("https://help.ubuntu.com/community/Grub2?action=fullsearch&context=180&value=linkto%3A%22Grub2%22") document [https://help.ubuntu.com/community/Grub2:](https://help.ubuntu.com/community/Grub2:)

***GRUB_HIDDEN_TIMEOUT=0*** 

[LIST]
[*]This setting determines how long a screen without the GRUB 2 menu will be displayed. While the screen is blank, the user can press any key to display the menu.
[*]The default behavior is to hide the menu if only one operating system is present. If a user with only Ubuntu wishes to display the menu, place a **#** symbol at the start of this line to disable the hidden menu feature.
[/LIST]
According to above information, I have tried to set below in order the show the menu:

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT="20"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

However, the menu didn't show up regarding to reboot or power up the system.

Is there any missing in the configuration?

Thanks in advance.

Rgds,
Ivan

Did it sit at a black screen for 20 seconds? I'd uncomment the hidden timeout lime and change the value to 20 or something similar. During boot, you'll see the countdown in the upper-left corner of your primary display and can press a key to get to the grub list. Someone else can probably chime in with what you'll need to do to have the grub list show automatically - I only did this as an emergency as I botched a 2.6.34 kernel update and needed to get back to 2.6.31

---

### Post by ivancheng on 2010-04-26
Hi,

The problem was fixed after issuing "update-grub".

Thanks a lot.

Rgds,
Ivan

---

