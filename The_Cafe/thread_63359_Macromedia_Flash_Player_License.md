---
title: "Macromedia Flash Player License"
date: 2005-09-07
forum: The Cafe
---

### Post by c4r1 on 2005-09-07
Why is a package flashplayer-mozilla in the multiverse repositories. Isn't it forbidden to distribute the flash player over the internet?

There is allso a package called flashplugin-nonfree which downloads the installer from the macromedia website.

Why are there two packages?

---

### Post by Kvark on 2005-09-07
I can't find any packages with the names "flashplayer-mozilla" or "flashplugin-nonfree" in the repos. But I did find a package called libflash-mozplugin that appears to be a flash player for mozilla. I don't think that's Macromedia's flash player though.

---

### Post by c4r1 on 2005-09-07
They are in the multiverse repository.

---

### Post by Kvark on 2005-09-07
[QUOTE=c4r1]They are in the multiverse repository.[/QUOTE]
DUH! Stupid forgot that I didn't have that one enabled.

Hmm, yeah those two packages are Macromedia's flash player. Have to agree that it's strange to have those there instead of just using the other flash player.

---

### Post by Burgundavia on 2005-09-07
Universe is for packages that are Debian Free Software Guidelines-free (very similar to and the basis for the Open Source Definition).

Multiverse is for stuff that is not DFSG-free but that they still can redistribute.

Corey

---

### Post by poofyhairguy on 2005-09-07
[QUOTE=c4r1]
Why are there two packages?[/QUOTE]

One is real Macromedia, one is an attempt to reverse engineer macromedia.

And I think you can distribute Flash over the net, because when I installed Internet Explorer on my machine one of the options it gave me was to preinstall flash.

---

### Post by jdong on 2005-09-07
like NVIDIA drivers, you need permission to redistribute it... Macromedia, in my experience, has been very generous with granting redistribution rights.

---

### Post by c4r1 on 2005-09-08
[QUOTE=jdong]like NVIDIA drivers, you need permission to redistribute it...[/QUOTE]
The linux nvidia drivers may be copied and redistributed, provided that the binary files thereof are not modified in any way.

[QUOTE=poofyhairguy]one is an attempt to reverse engineer macromedia[/QUOTE]
both packages include the original macromedia player

---

### Post by jdong on 2005-09-08
[QUOTE=c4r1]The linux nvidia drivers may be copied and redistributed, provided that the binary files thereof are not modified in any way.
[/QUOTE]
The license is pretty unclear about that. Distributing the ".run" files is perfectly fine, but shipping precompiled nvidia.ko and Nvidia TLS libs... that's sketchy.

---

