---
title: "Cannot go fullscreen in VM after installing guest additions?"
date: 2014-10-15
forum: Virtualisation
---

### Post by boyan2 on 2014-10-15
Sorry in advance if I've posted in the wrong forum section, but I'm new to the whole Ubuntu/Linux experience and this forum too.

So I installed Ubuntu on a virtual box, and everything is fine up to the point of going **fullscreen**. I installed the guest additions as I was supposed to, but then "auto-resize display" remained grayed out. I tried to manually open the *VBoxWindowsAdditions.exe* but I either get an error, or if I don't, "auto-resize display" remains grayed out... Any suggestions about what I should do, because its practically impossible to work at a 640x480 resolution in windowed mode. 

Thank you in advance guys!

---

### Post by ibjsb4 on 2014-10-15
You also need to install dkms in the guest.
```
sudo apt-get install virtualbox-guest-dkms 
```

---

