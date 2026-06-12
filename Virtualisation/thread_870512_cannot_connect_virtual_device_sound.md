---
title: "cannot connect virtual device sound?"
date: 2008-07-25
forum: Virtualisation
---

### Post by chunchengch on 2008-07-25
I am running VMware Workstation 6 on Ubuntu 8.04, and I always get the error message

[COLOR="Red"]"Cannot connect virtual device sound. No corresponding device is available on the host."[/COLOR]

[ATTACH]78975[/ATTACH]


I look into the .vmx file and find these lines

[COLOR="Blue"]sound.present = "TRUE"
sound.fileName = "-1"
sound.autodetect = "TRUE"[/COLOR]

I tried to replace [COLOR="Blue"]sound.fileName = "-1"[/COLOR] with [COLOR="Blue"]sound.fileName = "/dev/dsp"[/COLOR] ,but the error remains.

How can I fix this sound problem? thanks for help.

---

### Post by bamboomy on 2008-11-25
maybe this can help ?

[http://ubuntuforums.org/showthread.php?t=992273](http://ubuntuforums.org/showthread.php?t=992273)

grtz,

S.

---

