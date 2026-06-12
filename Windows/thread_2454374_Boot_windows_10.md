---
title: "Boot windows 10"
date: 2020-11-28
forum: Windows
---

### Post by sqdboyuwu on 2020-11-28
Hi, I installed pop!_Os on my pc, but I want to go back to windows 10. for various reasons; games app etc. When I create the pen drive with the windows 10 iso and I try to start it from boot, it does not boot. how can i solve?



[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAQAAAAngNWGAAAA/0lEQVR4AYXNMSiEcRyA4cfmGHQbCZIipkuxnJgMStlMNmeyD2dwmc8 sZgxYJd9ErIZFHUyYYD7fkr6l4/rnvmtl7 KitrqV/fq2Y5eLY3Z9S48eRLe7BmVZ9qhTLhQ0algzZWQOVKSsCF8OjAnwbxDTWFDUhPK/jMr1H6HE/IqRky2DyvCefuwItwZzodVoYRiLqMkVCXrwpJ9twZ sgfDYEFYl8wIWxZ9uFf7zkallxlJh4YrLGsKjZRx7VGHhLqwgFUN45DGdb8MeXGpgB4ABZdeDcpZEY51A hyLKz4S1W4MQWm3AibWtgWmk6dyISa1pSdyWTOlLXVp0 eL9D/ZPfBTNanAAAAAElFTkSuQmCC[/IMG]

---

### Post by jeremy31 on 2020-11-28
Moved to Windows sub forum

Did you use woeusb to put the Win 10 ISO on USB?

---

### Post by mIk3_08 on 2020-11-28
I suggest you go to multi boot. Set-up your bios/uefi primary boot setting, Also you can use clover boot loader and good to go. Be sure to set-up the windows OS first and then next the Linux pop!_Os.

---

### Post by yancek on 2020-11-28
>  When I create the pen drive with the windows 10 iso 

How did you do that, what software or method did you use to put the windows installer on the usb?  Did you set your BIOS boot options to boot the USB first?

---

### Post by C.S.Cameron on 2020-11-28
I think WoeUSB is not working with 20.04.

Rufus worked for me in Windows as did the Windows media creation tool.

Mkusb-plug worked for me in Ubuntu as did mkusb-dus. [https://ubuntuforums.org/showthread.php?t=1958073&page=103&p=13993880#post13993880](https://ubuntuforums.org/showthread.php?t=1958073&page=103&p=13993880#post13993880)

---

