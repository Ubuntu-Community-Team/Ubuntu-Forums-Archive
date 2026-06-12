---
title: "Microsoft Digital Media Keyboard  with VirtualBox"
date: 2011-07-20
forum: Virtualisation
---

### Post by ubrox on 2011-07-20
I have a Microsoft Digital Media Keyboard connected to my MacBook Pro 17" host. I am using VBox 4.0.1 (and previous versions) to host a 32-bit Ubuntu 11.04 (and earlier versions). The keyboard has special keys for Mail, Calculator, Sleep, logoff etc. Mac only recognizes sleep and sound buttons. 

I have selected the right keyboard model in Ubuntu and it automatically sets the keyboard shortcuts too. But I dont think it is receiving the keystrokes when I press the special buttons because, nothing happens when I use the keys. I have used keytouch and set the right keyboard model as well. Also, I used the showkey to see if it is receiving the scancodes, and it is not. How to I make sure mac sends all the scancodes to the guest?

---

### Post by 2F4U on 2011-07-20
I am not sure but my understanding of VirtualBox is that it provides the guest operating system (Ubuntu) with standardized hardware. For example, the graphics card in Ubuntu would not be the same as that in Mac OSX, since Ubuntu is given a standard graphics card, while the Mac sees the real graphics card.

---

