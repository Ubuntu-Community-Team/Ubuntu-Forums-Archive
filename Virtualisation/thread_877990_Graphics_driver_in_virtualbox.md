---
title: "Graphics driver in virtualbox"
date: 2008-08-02
forum: Virtualisation
---

### Post by ZeldaFan on 2008-08-02
Is there a way to install graphics drivers (and now that I think about it, sound drivers as well) in a windows vista guest in virtualbox. Do I need to do anything extra or can I just install the standard drivers that came with my PC? I have a CD for that.

---

### Post by jualin on 2008-08-02
The Virtual Machine will emulate a generic driver, usually an Intel Driver which Vista can recognize. For instance if you have a nVidia graphics card in Linux, the Vista guest machine (virtual machine) will recognize it as Intel Video Card, you cannot make it recognize it as an Nvidia. You can change the generic drivers but the list is pretty limited. You can do this by going to "Preferences" on your Virtual Machine.

---

### Post by fergus on 2008-08-02
you need to install 'Guest Additions' to get the right driver support... Should be an option in one of the menus.  It should then autostart the driver install.

fergus

---

### Post by ZeldaFan on 2008-08-02
Thanks for the replies everyone. I installed guest addition and video/audio works, although it's kinda disappointing not to have 3D support. It doesn't really matter much to me though because I only installed a bare bones version without any other programs except the ones that come by default and microsoft office because office is the only reason I need it. I have a local shared folder to share files b/w host and guest and no internet (so I dont need antivirus/anti-spyware). So I think I have everything finally set up for seamless use. The only downside is that USB does not work no matter what I do.

---

