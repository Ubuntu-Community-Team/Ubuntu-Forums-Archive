---
title: "Xubuntu Function Key Support?"
date: 2009-09-09
forum: System76 Support
---

### Post by Iteria on 2009-09-09
So I got my Pangolin (pan5) laptop and I was smitten with it. after toying with it a bit, installed the XFCE interface and removed the gnome one (since, I never use gnome) through synaptic. Only now... the function key things don't work. For example I can't use fn + F3 to mute the volume anymore. 

I tried using the system76 driver installer to install the drivers, then rebooting, but I have the same issue. Does System76 only support Ubuntu and not Xubuntu? Or am I just doing something wrong?

---

### Post by jml on 2009-09-09
The function key support is provided by the custom S76 drivers.  To the best of my knowledge, System 76 (and by inference the S76 drivers,) officially only supports Ubuntu and not the derivative distros.  However, I have seen Tom try to assist with the other *buntu's if the problem could be resolved by editing a config file or something similar.  Wait and see what Thom says.  Good luck.

Joe

---

### Post by jdb on 2009-09-09
I run Xubuntu on a Daru2 & the System 76 drivers load without error & the special keys work.

You might try a clean load from an Xubuntu CD.

jdb

---

### Post by Iteria on 2009-09-09
I'll try a fresh install, but my internet is pretty slow, so it will probably be a day or so I before a get an iso, install and get back to you.

---

### Post by gila_monster on 2009-09-09
It's true that S76 officially supports only Ubuntu, but the S76 driver should work for Xubuntu and Kubuntu. I've tried both, the driver did install and run. Other distributions, including Ubuntu-based ones such as Mint...no such luck.

---

### Post by thomasaaron on 2009-09-10
The driver will *run* in [K/X]ubuntu. However, whether or not the fixes actually work, it's hard to say. We only test them in Ubuntu.

---

### Post by Iteria on 2009-09-10
So I did a fresh install. The drivers installed and I rebooted, but the computer doesn't acknowledge the function. I ran xev to make sure, just in case I only needed to set the shortcuts, but xev doesn't acknowledge that the key was pressed.

---

### Post by thomasaaron on 2009-09-11
Well, it definitely seems to be xubuntu related, then. In Ubuntu, those keys can be mapped via System > Preferences > Keyboard Shortcuts. However, I don't know what the Xubuntu equivalent is. And if it's not sending a keycode in Xubuntu, then mapping it might not work anyway.

---

### Post by jdb on 2009-09-11
> **thomasaaron said:**
> Well, it definitely seems to be xubuntu related, then. In Ubuntu, those keys can be mapped via System > Preferences > Keyboard Shortcuts. However, I don't know what the Xubuntu equivalent is. And if it's not sending a keycode in Xubuntu, then mapping it might not work anyway.

Usually if the key isn't detected by xev it is one that's handled by acpi.
In Xubuntu keys can be mapped using:
Applications > Settings > keyboard > Application Shortcuts

It might work even if xev doesn't see the key because it doesn't ask for a key code.
After selecting the command or script to assign to the key,
you just press the key combo to assign it to.

I'm not real hopeful, but it's worth a try.

jdb

---

### Post by Iteria on 2009-09-11
That didn't work. The shortcut capturer thing didn't acknowledge the fn key. Maybe it's a problem with the keyboard layout I gave it. I just gave it the default, which is Generic 105 (Intl) PC according to Xubuntu. 

Maybe giving it a better keyboard layout will map the key?

---

### Post by jdb on 2009-09-11
> **Iteria said:**
> That didn't work. The shortcut capturer thing didn't acknowledge the fn key. Maybe it's a problem with the keyboard layout I gave it. I just gave it the default, which is Generic 105 (Intl) PC according to Xubuntu. 

Maybe giving it a better keyboard layout will map the key?

That sounds like a good idea but I have no idea what to use for a pan5.

jdb

---

### Post by thomasaaron on 2009-09-11
On a Pangolin, it should be Generic 105 key (Intl) set to a USA default.

I'd advise booting from a live CD and seeing if the keys work. That way, if it's a hardware problem, you won't spin your wheels too much.

But, most likely, it is just a matter of figuring out how to enable the key in Xubuntu.

---

### Post by Iteria on 2009-09-11
I'm not really sure what happened, but the problem fixed itself. When I booted the live CD and tried the function keys they worked out of the box. I thought that was strange because that means that it should work out of the box for Xubuntu, since the live CD doesn't have the drivers. I attempted to set a shortcut again in Xubuntu and... it worked.

I'm not sure what fixed it, since I didn't do anything. Maybe my laptop just need a reboot.

---

