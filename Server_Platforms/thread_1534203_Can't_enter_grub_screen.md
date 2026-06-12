---
title: "Can't enter grub screen"
date: 2010-07-19
forum: Server Platforms
---

### Post by johnnylee194 on 2010-07-19
I've installed Ubuntu 10.04 server edition and want to enter the recovery mode.

After reboot the system, it directly enter the login window, no grub screen shows.

If I click esc when booting the system, it stops loading and shows a blinking cursor infinitely.

What's the problem here? Is there some way to trouble shooting?

---

### Post by johnnylee194 on 2010-07-19
Here is my grub settings in ```
/etc/default/grub
```

```

GRUB_HIDDEN_TIMEOUT=0 
GRUB_HIDDEN_TIMEOUT_QUIET=true 
GRUB_TIMEOUT=10

```

And I mistakenly removed myself from sudo list :(

---

### Post by richardjh on 2010-07-19
I had this same issue and in the end booted from a live CD such as systemrescueCD.

I can not test this today, but I have a suspicion you cannot enter the grub menu any more since grub2 replaced grub.

If I get time to play I will post back my findings.

---

### Post by richardjh on 2010-07-23
OK I am back with news.

In grub2 you can no longer use ESCAPE key to enter the menu, you need to use the SHIFT key instead.

This has been documented at [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

The relevant section is below, section highlighted bold for reference:

> 

GRUB_HIDDEN_TIMEOUT=0

    *

      The hidden timeout option is available to single-OS computers - if multiple OS's are known to Grub 2, this option is bypassed.
    *

      On single-OS systems, the menu will be hidden unless a # symbol is present at the beginning of this line. ( # GRUB_HIDDEN_TIMEOUT=0 )
    * The default setting initially depends on the presence of other operating systems.
          o Another OS Detected: The menu will be displayed. ( The line will begin with a # symbol. )
          o No other OS Detected: This setting is not used, as determined by the 
    * For integers greater than 0, the system will pause, but not display the menu, for the entered number of seconds.
    *

      0 The menu will not be displayed. There will be no delay.
          o **The user may force displaying the menu as the computer boots by holding down the SHIFT key (single-OS computers only).**
                + During boot, the system will check the SHIFT key status. If it cannot determine the key status, a short delay will enable the user to display the menu by pressing the ESC key. 
                + If enabled, the splash screen designated in 05_debian_theme will be displayed even if the hidden menu feature is selected. 

There is a bug for this [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439592](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439592)

---

