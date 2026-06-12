---
title: "Found a Guide to disable touchpad when mouse is plugged in"
date: 2009-03-20
forum: The Cafe
---

### Post by andamaru on 2009-03-20
[http://wiki.archlinux.org/index.php/Touchpad_Synaptics#Disable_touchpad_upon_external_mouse_detection](http://wiki.archlinux.org/index.php/Touchpad_Synaptics#Disable_touchpad_upon_external_mouse_detection)

This has been stolen from the archlinux wiki

Does anyone know how I would go about applying these settings to Ubuntu. Touchpad is the biggest thing I hate about laptops

---

### Post by olejorgen on 2009-03-21
Have you tried following the guide? It seems like most of it should work cross-distro.

Personally I've made a script that turns on/off my touchpad. I don't have that big issues with the pad so it works for me.

```

# off
xsetpointer -c "Synaptics Touchpad"
# on
xsetpointer +c "Synaptics Touchpad"

```

---

### Post by MasterNetra on 2009-03-21
Be nice if the disable touch pad while mouse is plugged in option was available by default. but meh.

---

### Post by walard on 2009-03-21
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) ;)

---

### Post by andamaru on 2009-03-21
Thanks for the help, the guide kind of works. When I'm sitting at the gdm screen the touchpad disables itself when a mouse is plugged in but when I log in it enables itself.

---

### Post by speedwell68 on 2009-03-21
Why not just got to System > Administration > Mouse and turn the sodding thing off for good.  I really hate touchpads, they are the tool of Satan.

---

### Post by andamaru on 2009-03-21
> **speedwell68 said:**
> Why not just got to System > Administration > Mouse and turn the sodding thing off for good.  I really hate touchpads, they are the tool of Satan.

thanks, you just solved my issue.

I couldn't figure out why the setting worked in the gdm and not while logged in. When you told me the touchpad could be controlled inside gnome I realized the settings in there were screwing around with it, all I did was unselected all the options and everything worked. Thanks everyone.

Once I can get my blacklight controls working in Ubuntu everything on my laptop will work perfect.

---

