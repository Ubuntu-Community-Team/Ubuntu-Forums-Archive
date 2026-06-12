---
title: "I somehow don't have grub"
date: 2021-12-05
forum: Ubuntu/Debian BASED
---

### Post by hellwraiz on 2021-12-05
(I tried this on kubuntu and pop_os where I am currently)
I tried holding shift while restarting my pc already a thousand times, but NOTHING.
And there was no grub file in etc/default/, well...until I accidentally created it. And it still didn't help because of the next thing.
and apparently even the command sudo upgrade-grub doesn't exist, so I am very confused, my laptop is in a constant state of agony because of this and some stupid i915 drivers, so if I somehow don't fix this I will give up and go back to windows.

---

### Post by howefield on 2021-12-05
Moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by dragonfly41 on 2021-12-05
Trying to understand pop_os (news to me) I read here
[https://www.reddit.com/r/pop_os/comments/cqpw5g/how_to_install_grub_menu_on_pop_os/](https://www.reddit.com/r/pop_os/comments/cqpw5g/how_to_install_grub_menu_on_pop_os/)

which says ..

[COLOR=#1A1A1B][FONT=&quot]"It's important to be aware that Pop_OS! does [/FONT][/COLOR][COLOR=#1A1A1B][FONT=&quot]not[/FONT][/COLOR][COLOR=#1A1A1B][FONT=&quot] use Grub, ..."

[/FONT][/COLOR]It also refers to rEFInd and since I use that (but in Ubuntu) to sit alongside Grub you could try installing that.

Another article on pop_os found here ..
[https://linuxconfig.org/pop-os-vs-ubuntu-linux](https://linuxconfig.org/pop-os-vs-ubuntu-linux)

---

### Post by hellwraiz on 2021-12-05
Oh sorry, didn't know that existed.

---

### Post by dragonfly41 on 2021-12-05
Nor did I know that pop_os existed.  I do endorse rEFInd. Good luck. Better than going back to Windows.

---

### Post by hellwraiz on 2021-12-06
hey, do you happen to know the refind alternative to GRUB_CMDLINE_LINUX_DEFAULT? I just can't seem to be able to figure it out.

---

