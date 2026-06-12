---
title: "Ubuntu server 20.04.1 headless"
date: 2020-08-30
forum: Server Platforms
---

### Post by Rui_Duarte on 2020-08-30
Hello,

I have been using ubuntu server 18.04.04 headless without graphic card.
Today I decided to do a fresh install to 20.04.1, I use old graphic card keyboard and mouse to install, and after that I remove the graphic card, keyboard and mouse, but the server wont boott and I can't connect via ssh.
I tried with graphic card etc and it boot OK, if removed doesn't work, any clues?

thank you

---

### Post by TheFu on 2020-08-30
You'll need to setup console mode booting, so the boot messages are seen on a serial tty/console.
Think that's a grub thing.
Google found this answer: [https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode](https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode) but without knowing the exact term to search, no way would you find it.

---

### Post by math492m on 2020-09-03
go back to 18.04 it is more stabil

i did the exact same

---

### Post by Rui_Duarte on 2020-09-07
> **TheFu said:**
> You'll need to setup console mode booting, so the boot messages are seen on a serial tty/console.
Think that's a grub thing.
Google found this answer: [https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode](https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode) but without knowing the exact term to search, no way would you find it.

Hello, 

No joy with grub setting. 

Already have reinstalled Ubuntu server 18.04 and doesnt work. 

Whith graphic card all good working nice, removing card cant connect ssh. 

Any more ideias?

---

### Post by TheFu on 2020-09-07
You can play around with solutions inside a virtual machine that doesn't have a fake-GPU assigned to it.  I have a box that doesn't have any GPU capabilities, but it is the WAN router here and doesn't run Linux. Sorry.

Also, that link wasn't correct. I'm sorry.  Basically, you have to force a serial console connection, not just block the GUI on startup. My mistake.  I'm not able to find anything searching now.  Did you look through help.ubuntu.com under the "server" guides?

---

### Post by Rui_Duarte on 2020-09-08
I will try "serial console connection" and report back

---

