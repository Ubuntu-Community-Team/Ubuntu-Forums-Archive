---
title: "Horizontal dimension in scaled mode view apears stretched"
date: 2015-09-04
forum: Virtualisation
---

### Post by AbleTassie on 2015-09-04
Hi,  I recently installed Virtualbox 5.02 using Lubuntu 14.04.3 LTS as the host and installed Windows XP as a virtual machine. Everything seems to work OK. But when I switch the view from windowed mode to scaled mode, the horizontal dimension appears stretched out. So icons are not as clear and text in Microsoft Word is not as clear as in windowed mode. In windowed mode, unfortunately the window is pretty small.  Is there anything I can do about this?       Thanks,   Able

---

### Post by AbleTassie on 2015-09-06
I initially thought  that this problem was purely a Virtualbox problem. But I was able to improve the situation by changing the settings in WIndows XP: right click the desktop> Properties>Settings> screen resolution and then changing the screen resolution to a different value. Of note is that when I click on View>VirtualScreen 1, the values for pixel numbers (ie X x Y) are grayed out. But I am in the Windows 2 machine. I removed the Windows 1 machine.  Any comments for anybody?  Thanks  Able

---

### Post by AbleTassie on 2015-09-10
I was able to solve this by getting the screen resolution set to the native screen resolution of the computer (which was correctly set in Lubuntu) and then using the Full Screen view in Virtualbox.

Thanks,

A.

---

