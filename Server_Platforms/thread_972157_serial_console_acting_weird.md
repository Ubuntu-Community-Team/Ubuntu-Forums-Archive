---
title: "serial console acting weird"
date: 2008-11-05
forum: Server Platforms
---

### Post by thouters on 2008-11-05
Hi,

I set up a getty on ttyS0 like in [https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto) on my Hardy machine that now has been promoted to server.

The configuration seems to be in effect, but this is what I experience when I boot the box:

I get the GRUB ~press any key~ prompt, which times out when I don't press a key, but when I do press a key the default entry boots, I never get to see the GRUB menu.

Linux boots and I get all the usual messages and when it's finished I can login at the login: prompt, which accepts correct logins.

As soon as /etc/motd is shown however, no bash or zsh apears on the serial console.  Noting gets printed thereafter (perhaps kernel debug messages but none got printed at that time), until I hit Ctrl-C.  A new login: prompt is presented then.

This seems to be odd behaviour.  GRUB's behaviour could be due to it being the version I installed last year with my Gentoo install.  That is however unlikely to affect Hardy.

I have also ruled out my terminal emulator at the other end of the nullmodem cable (I tried gtkterm and screen /dev/ttyUSB0 115200, same results - screen showed some weird behaviour of its own though)

I verified that ttyS0 is in /etc/securetty.

I have no clue what could be the cause of this.
I did serial consoles on Gentoo and Debian before ([http://www.thouters.be/SerialTerminalLinux](http://www.thouters.be/SerialTerminalLinux)), and I'm out of ideas.

Thanks in advance for all comments.

---

