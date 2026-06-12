---
title: "Can't get to login (text mode) Ubuntu Server 10.4"
date: 2010-08-31
forum: Server Platforms
---

### Post by LtPitt on 2010-08-31
Hello everybody...

I don't know what happened but I'm unable to get to the login screen.
All I get is the ubuntu textual splash screen, if I press esc I can read only:

fsck from util-linux-ng 2.17.2
/dev/sda1: clean. 11057/9191424 files. 419873/36734622 blocks

and a blinking cursor under it, nothing more.

If I try to switch to a different terminal (ctrl+alt+f1 etc) I can freely login.

ps
in my case different people suggest to

Edit /boot/grub/menu.1st - Add 'debug' option to the kernel and you can see exactly where it hangs.

But I have a different grub version on 10.4...

I've read that now I have to modify /etc/default/grub
is the debug option still the same?

Please excuse me for bothering about "rtfm" information but I don't want to make things worse :/ :)

---

