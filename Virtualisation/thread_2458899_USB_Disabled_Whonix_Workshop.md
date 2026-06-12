---
title: "USB Disabled Whonix Workshop"
date: 2021-03-06
forum: Virtualisation
---

### Post by roadrunner510 on 2021-03-06
[COLOR=#000000][FONT=arial]I am running whonix  Gateway and whonix workshop on Virtual Box Manager I am have downloaded  some guides and would like to load them onto a USB for cold.storage but  when i plug in my stick and look to load files onto USB i am seeing that  USB is 'Disabled' under the VM Workshop Settings Sorry if the question  comes off as dumb but i have looked around and the only posts i can find  explain to input the command : sudo usermod -aG vboxusers 'I have  attempted this command both with and without "Vboxusers" and nothing  works I have also download VirtualBox Extension Pack hoping that would  fix the problem as well with no Luck Lmk if you have any suggestiong on  how to enable USB on Whonix Workshop Thanks in ADvance !![/FONT][/COLOR]

---

### Post by CelticWarrior on 2021-03-06
In Virtualbox you're supposed to use the menu Devices > USB to pass USB devices from the host OS to the guest OS. This is especially useful for peripherals but not so much for mass storage devices because mount options in the host may prevent it from being "disconnected".

Knowing that, shared folders is preferable: [https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

---

### Post by ajgreeny on 2021-03-06
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

