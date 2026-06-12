---
title: "grub booting to &quot;grub prompt&quot; , not the menu"
date: 2008-05-10
forum: Server Platforms
---

### Post by cr-rolo on 2008-05-10
hi, just installed ubuntu hardy server, for amd64. and when i booted after installation, grub is going directly to the grub prompt, not sure why it isnt showing the menu... i have to manually type "configfile /boot/grub/menu.lst" everytime it boots.
would apreciate any help. here is my menu.list file


default 0
timeout 10

title ubuntu 8.04, kernel 2.6.24-16-serv er
root (hd1,0)
kernel /boot/vmlinuz-2.6.26-16-server root=/dev/sdb1 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-server
quiet

title Microsoft Windows XP Profesional
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by joeboentoe on 2008-06-11
I am not an expert but you can try to reinstall grub

in terminal:

```
sudo grub
root (hd?,?)  
```
example: (hd0,2)  first hard disk, 3th partition

replace ? by the correct hard disk and partition where /boot/grub is located

```
setup (hd?)
``` example: (hd0) first hard disk

replace ? by the correct hard disk /boot/grub is located, if you use setup (fd?) then it will copy stage1 of grub to a floppy disk instead of the mbr of the hd. its your choice

reboot and test if it works

---

