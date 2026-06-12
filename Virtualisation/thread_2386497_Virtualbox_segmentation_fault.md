---
title: "Virtualbox segmentation fault"
date: 2018-03-06
forum: Virtualisation
---

### Post by fallenshadow on 2018-03-06
I don't know where to start debugging this. I just get segmentation fault(core dumped) in the terminal if I run the virtualbox by command line.

---

### Post by QIII on 2018-03-06
Hello!

What release are you running as the host?  The guest?  Which version of VirtualBox?  Does it run if you open the VBox GUI?

Could you copy and paste the command and results in code tags here?

Thanks!

---

### Post by fallenshadow on 2018-03-06
Hi there,

The host is Ubuntu 17.10 64bit.
The guest is Linux Mint currently.
Virtualbox version is 5.2.8 64bit.
Doesn't run if I launch the GUI.. but only if I delete the Virtualbox config folder it will open again.

```

virtualbox
Segmentation fault (core dumped)

```

One thing I did notice. After deleting the config folder I was able to re-import my VMs. However, I enabled 3D acceleration on Linux Mint and then Virtualbox crashed instantly. Not sure if this extra information helps, just letting you know.

---

### Post by fallenshadow on 2018-03-08
Found this in the Ubuntu error report tool:

> segvreason
writing VMA /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-B.ttf

---

