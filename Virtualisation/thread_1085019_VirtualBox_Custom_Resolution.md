---
title: "VirtualBox Custom Resolution"
date: 2009-03-02
forum: Virtualisation
---

### Post by r0yalty on 2009-03-02
Hello,

My monitor can display maximum 1600 x 1200. I want my VirtualBox client running Windows XP to use 1920 x 1440. In VMWare this could be done, and it would add scrollbars as that resolution will not fit on my screen. Is it possible to do something like this with VirtualBox?

---

### Post by r0yalty on 2009-03-02
I managed to do this by "VBoxManage  setextradata global GUI/MaxGuestResolution 1920,1440" and then switching to that resolution in the vm. However, when i resize the window, the resolution will change, is there a way to get scrollbars and keep the resolution?

---

### Post by Ng Oon-Ee on 2009-03-04
Thing is, VBox will automatically adjust resolution for you  when you resize windows etc. Don't know if that's hardcoded, as I haven't messed with it before, but a simple solution would be to not resize the window (you can set compiz to not allow it to be resized).

---

