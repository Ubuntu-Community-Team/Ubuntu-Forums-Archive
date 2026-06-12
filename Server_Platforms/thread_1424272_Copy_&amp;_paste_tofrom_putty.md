---
title: "Copy &amp; paste to/from putty?"
date: 2010-03-07
forum: Server Platforms
---

### Post by Donny Bahama on 2010-03-07
Documentation online says click & drag to select will auto-copy, right-click will paste. Not working for me, so I tried the old school "shift+del" and "ctrl+insert". These do work, but only within putty. When I try to copy the output from a command in putty, then paste it into a post here, it's not on the clipboard. What's the right way to do this?

---

### Post by cjhabs on 2010-03-07
> **Donny Bahama said:**
> Documentation online says click & drag to select will auto-copy, right-click will paste. Not working for me, so I tried the old school "shift+del" and "ctrl+insert". These do work, but only within putty. When I try to copy the output from a command in putty, then paste it into a post here, it's not on the clipboard. What's the right way to do this?

May I ask why you are using Putty when you can ssh and telnet right from a terminal window?

---

### Post by Donny Bahama on 2010-03-07
> **cjhabs said:**
> May I ask why you are using Putty when you can ssh and telnet right from a terminal window?For whatever reason, I can't seem to get ssh to work from a terminal.

---

### Post by Donny Bahama on 2010-03-07
OK... so I couldn't even remember what the problem was so I tried it again. It works. Heh. Sorry for the confusion!

---

### Post by rezsbc on 2011-10-19
> **Donny Bahama said:**
> Documentation online says click & drag to select will auto-copy, right-click will paste. Not working for me, so I tried the old school "shift+del" and "ctrl+insert". These do work, but only within putty. When I try to copy the output from a command in putty, then paste it into a post here, it's not on the clipboard. What's the right way to do this?

I have the exact same issue and it's giving me loads of trouble.

I can copy & paste within putty by clicking my two mouse buttons at the same time (simulates the 'third' mouse button my laptop doesn't have).  I can copy from gedit or similar and paste into putty by using CTRL-SHIFT-INSERT keys at the same time.

I *cannot* paste from a regular desktop application such as gedit into putty under Ubuntu no matter what I do however.

FYI I am using putty for terminal emulation to connect to devices via RS232.  It is about the only usable option for doing this under Ubuntu that I can find, if people have an alternative then please let me know.

---

### Post by shimmey on 2012-06-25
You can paste the selected characters from PuTTY into other applications by clicking the middle button of the mouse.
I got this answer from this URL:
[https://bugs.launchpad.net/ubuntu/+source/putty/+bug/116165](https://bugs.launchpad.net/ubuntu/+source/putty/+bug/116165)

It works well in my computer: ubuntu 10.04.

---

