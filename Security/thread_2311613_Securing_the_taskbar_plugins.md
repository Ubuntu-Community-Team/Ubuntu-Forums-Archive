---
title: "Securing the taskbar plugins"
date: 2016-01-28
forum: Security
---

### Post by ineuw on 2016-01-28
I have an Xubuntu 14.04 desktop setup in a community center, where on occasion a curious user fiddles with the taskbar icons & plugins and consequently disconnects the internet. For me, this means a quick visit to restore the icons and reinitialize the connection because in requires the admin password. Is there a way to secure the taskbar and it's contents to prevent anyone fiddling with the plugins and programs. Thanks in advance to anyone who saves me an unnecessary trip, because otherwise Xu serves the purpose admirably.

---

### Post by ajgreeny on 2016-01-28
You could try making all the config files and folders for the xfce4-panel immutable (ie, impossible to edit or delete) with command ```
sudo chattr -R +i /home/*username*/.config/xfce4/panel
```
Now if anyone does change the panel in any way you can simply reset it with ```
xfce4-panel -r
```
This may not reset your connection but it will at least get the panel back to how it was, or I think it will.  Worth a try?

If it does not do what you want you can reverse the immutability with command ```
sudo chattr -R -i /home/*username*/.config/xfce4/panel
``` which you will also need to do if you ever want to edit the panel yourself.

---

