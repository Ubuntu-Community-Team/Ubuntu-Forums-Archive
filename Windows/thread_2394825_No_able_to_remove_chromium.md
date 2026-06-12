---
title: "No able to remove chromium"
date: 2018-06-21
forum: Windows
---

### Post by savitathakur on 2018-06-21
I have dual booted ubuntu and Windows7 and have installed chromium browser on both. Now I don't know how i can remove the chromium software from both of these.

---

### Post by khojdo0 on 2018-06-21
> **savitathakur said:**
> I have dual booted ubuntu and Windows7 and have installed chromium browser on both. Now I don't know how i can remove the chromium software from both of these.
[COLOR=#111111][FONT=Ubuntu]Execute these commands in terminal to remove chromium from ubuntu:
[/FONT][/COLOR]
sudo apt-get remove chromium --purge
rm -rf ~/.config/chromium
rm -rf ~/.cache/chromium
sudo rm -rf /etc/chromium
[COLOR=#111111][FONT=Ubuntu]Follow this guide to remove chromium from windows : [https://techblot.com/remove-uninstall-chromium-windows-7-8-10/](https://techblot.com/remove-uninstall-chromium-windows-7-8-10/)[/FONT][/COLOR]

---

### Post by savitathakur on 2018-06-21
> **khojdo0 said:**
> [COLOR=#111111][FONT=Ubuntu]Execute these commands in terminal to remove chromium from ubuntu:
[/FONT][/COLOR]
sudo apt-get remove chromium --purge
rm -rf ~/.config/chromium
rm -rf ~/.cache/chromium
sudo rm -rf /etc/chromium
[COLOR=#111111][FONT=Ubuntu]Follow this guide to remove chromium from windows : [https://techblot.com/remove-uninstall-chromium-windows-7-8-10/](https://techblot.com/remove-uninstall-chromium-windows-7-8-10/)[/FONT][/COLOR]
ohh thank you so much sir..

---

### Post by wildmanne39 on 2018-06-22
For the record the command:
```
rm -rf 
```
is a very dangerous command if you get the incorrect path with this command you could wipe out some very important files or your system, also you can just open software center and remove chromium that way, it is much safer.

---

