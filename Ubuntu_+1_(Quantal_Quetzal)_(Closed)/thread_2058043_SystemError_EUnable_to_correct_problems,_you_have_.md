---
title: "SystemError: E:Unable to correct problems, you have held broken packages."
date: 2012-09-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by robtygart on 2012-09-14
Ok I am back at it again but with Kubuntu, and still with graphic problems. I keep getting this error message when trying to use nvidia-173 from the additional drivers menu, can't even use apt-get, > SystemError: E:Unable to correct problems, you have held broken packages.only nvidia-current will work. and that is giving me trouble, can't use second monitor and it is glitchy.

```
rob@Mobile:~/Documents$ lspci -nnk | grep -iA2 vga
00:12.0 VGA compatible controller [0300]: NVIDIA Corporation C67 [GeForce 7150M / nForce 630M] [10de:0531] (rev a2)
        Subsystem: Hewlett-Packard Company Device [103c:30cf]
        Kernel driver in use: nvidia
rob@Mobile:~/Documents$ 

```

---

### Post by cariboo on 2012-09-14
I'd suggest you use:

```
sudo apt-get purge nvidia-173
```

to completely remove the package and it's configuration files, as you are trying to use the wrong driver. According to Nvidia for your chipset you should be using the latest driver in the repositories. I'd suggest using nvidia-current-updates.

---

### Post by robtygart on 2012-09-14
> **cariboo907 said:**
> I'd suggest you use:

```
sudo apt-get purge nvidia-173
``` I'd suggest using nvidia-current-updates.

I purged nvidia-173 and nvidia-current, installed nvidia-current-updates and my external monitor looks like crap, the laptop itself using its monitor looks beautiful.

---

### Post by robtygart on 2012-09-14
is there anything open source?

---

### Post by cariboo on 2012-09-14
> **robtygart said:**
> I purged nvidia-173 and nvidia-current, installed nvidia-current-updates and my external monitor looks like crap, the laptop itself using its monitor looks beautiful.

That isn't a very helpful comment, what do you mean? If the resolution is off, you should be able to set it using nvidia-settings. Press alt-F2 and type:

```
nvidia-settings
```

to access it.

---

### Post by robtygart on 2012-09-15
On the external monitor the text is awful, and I can't get everything to fit the screen, the panel bar is at the bottom out of vew. 

Changing the resolution does not help. I have a few ideas I will try in the morning.

---

