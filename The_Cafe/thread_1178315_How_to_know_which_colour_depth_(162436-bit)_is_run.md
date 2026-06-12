---
title: "How to know which colour depth (16/24/36-bit) is running?"
date: 2009-06-04
forum: The Cafe
---

### Post by afeasfaerw23231233 on 2009-06-04
System -> Preference -> Display doesn't show it

---

### Post by blueturtl on 2009-06-04
Unless you are running a particularly old system, X will default to running at the highest possible color depth.

---

### Post by Dark Aspect on 2009-06-04
> **afeasfaerw23231233 said:**
> System -> Preference -> Display doesn't show it

If you have an Nvidia card, after you install your video driver, you can use:

```
/usr/bin/nvidia-settings
```

Otherwise you can take a look at your xorg file, look for your color depth after:

```
sudo gedit /etc/X11/xorg.conf
```

Should look like:

```
Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
**	DefaultDepth    24**
	SubSection "Display"
**		Depth       24**
	EndSubSection
EndSection
```

---

### Post by afeasfaerw23231233 on 2009-06-04
I am not using nVidia. My graphic is a SiS IGP. I download the driver from here [http://ncc-1701a.homelinux.net/~linux-sis/](http://ncc-1701a.homelinux.net/~linux-sis/)

---

### Post by Dark Aspect on 2009-06-04
> **afeasfaerw23231233 said:**
> I am not using nVidia. My graphic is a SiS IGP. I download the driver from here [http://ncc-1701a.homelinux.net/~linux-sis/](http://ncc-1701a.homelinux.net/~linux-sis/)

Than try the xorg method, however, if your video card doesn't support 24-bit color depth than changing it the xorg will break your X-server.

---

### Post by saulgoode on 2009-06-04
xwininfo -root | grep Depth:

---

### Post by afeasfaerw23231233 on 2009-06-05
```
 Depth: 24
```
Thanks

---

### Post by dragos240 on 2009-06-05
Do you mean 16/24/**32** bit?

---

### Post by afeasfaerw23231233 on 2009-06-08
yes, sorry for typo error

---

