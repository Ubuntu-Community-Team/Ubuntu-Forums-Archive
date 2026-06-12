---
title: "Disable graphcal mcrypt password entry screen"
date: 2015-03-14
forum: Security
---

### Post by belecjm on 2015-03-14
On my Ubuntu install, I use full disk encryption through mcrypt. On boot, I am presented with a screen to type my decryption password to continue booting. On my system, the graphical screen does not allow me to enter my password. When I reboot it switches to a console-based version and all is fine. is there a way to permanently change this password screen to the console version?

[ATTACH=CONFIG]260623[/ATTACH]

---

### Post by Thirtysixway on 2015-03-18
belecjm,

If you just type in your password and hit enter does it go through?  I don't have mine encrypted so I can't test but it could be just not displaying characters as you type.

---

### Post by belecjm on 2015-03-27
No, graphical password entry does not work at all. This is inside a virtualbox vm btw. I just want it to behave like ubuntu server, where graphical password entry is disabled and it falls back to a console based prompt.

---

### Post by belecjm on 2015-03-27
I found a temporary workaround. I set GRUB_CMDLINE_LINUX_DEFAULT="" in /etc/default/grub. The downside is I don't get the pretty graphical boot screen or the text based purple boot screen.

---

