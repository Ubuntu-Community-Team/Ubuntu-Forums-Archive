---
title: "Configuring ATI in server with GUI"
date: 2008-05-19
forum: Server Platforms
---

### Post by paladin_knight on 2008-05-19
Hi.. I just installed Hardy server and the GUI as well. But, I don't know how to configure xorg.conf. I had also tried the reconfigure command. I want to install ATI driver as well. Please help me ASAP. You can PM to my account. 

Thanks.:)

---

### Post by aysiu on 2008-05-19
But a PM wouldn't allow more people to help you or for your solution to help future forum readers. Please stay away from PMs for support.

This may help you, though:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way)

---

### Post by cdenley on 2008-05-19
If you want the proprietary ATI drivers
```

sudo apt-get install linux-restricted-modules-2.6.24-16-server xorg-driver-fglrx
sudo aticonfig --initial --input=/etc/X11/xorg.conf
reboot

```

---

### Post by paladin_knight on 2008-05-19
> **cdenley said:**
> If you want the proprietary ATI drivers
```

sudo apt-get install linux-restricted-modules-2.6.24-16-server fglrx
sudo aticonfig --initial --input=/etc/X11/xorg.conf
reboot

```

errr.. cannot find fglrx package.
I have uncommented all the repository. :(

I changed it into xorg-server-fglrx and it worked. But, still I cannot do aticonfig command.

My configuration of xorg.conf is like this
> 
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection


---

### Post by cdenley on 2008-05-20
Sorry, that should be xorg-driver-fglrx, not fglrx. I edited my post.

---

### Post by paladin_knight on 2008-05-20
But how can I configure the xorg.conf. I tried to use aticonfig command but it didn't work at all. :(

---

### Post by cdenley on 2008-05-20
aticonfig is supposed to configure xorg.conf. How did it not work? It is part of the xorg-driver-fglrx package, so you have to install that first. You can also try
```

sudo dpkg-reconfigure xserver-xorg

```

or this should work
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver          "fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

---

### Post by paladin_knight on 2008-05-20
So I just need to add "fglrx" in "Device" Section?. Just to clarify it.:)

---

### Post by cdenley on 2008-05-20
I think so. The latest versions of ubuntu or xorg seem to auto-detect the video card driver if you don't specify, and dpkg won't set the driver in xorg.conf. But then I'm not sure if it would load ati or fglrx. aticonfig should also give you a working configuration.

---

