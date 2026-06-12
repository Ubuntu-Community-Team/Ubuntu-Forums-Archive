---
title: "Wine (config) starting but process exit with no gui"
date: 2011-02-18
forum: Wine
---

### Post by mbogevik on 2011-02-18
Hi all,

I have a issue with a new IPX computer with Ubuntu 10.10 x64 (updated) and Wine.  When starting "Wine config" program it starts as a process but after a few seconds it exits without any gui coming up at all.  Trying to right-click and install a program with Wine does the same. 
I have tried latest Wine 1.2 and beta 1.3, even also with Ubuntu 10.10 x32. I would think this is hardware related since I have a laptop with Wine working "perfect".

My hardware is a Gigabyte GA-D525TUD, with a Atom D525 on.
[http://www.gigabyte.com/products/product-page.aspx?pid=3549#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3549#sp)
The computer is set up to be my server and everything else is 100% stable with a good 1Gbit performance (about 80Mbyte/s write)

Anyone have a tip on how to find out what is happening here ?  Any logfile in Ubuntu or Wine that can give any indication of what is happening ?

---

### Post by mbogevik on 2011-02-18
I was able to get this fail log :

X Error of failed request:  XF86VidModeExtensionDisabled
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  6 (XF86VidModeGetAllModeLines)
  Serial number of failed request:  89
  Current serial number in output stream:  89
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
X Error of failed request:  XF86VidModeExtensionDisabled
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  6 (XF86VidModeGetAllModeLines)
  Serial number of failed request:  89
  Current serial number in output stream:  89

I could be that my Ubuntu PC have no monitor connected.  If so this would be a common problem ?

---

### Post by mbogevik on 2011-02-18
After searching on forums and tested and rebooted a lot I finally found a solution setting up a headless monitor that makes Wine start by editing xorg.conf.

First I open xorg.conf:
```

sudo gedit /etc/X11/xorg.conf

```

Then I fill in this :
```

Section "Device"
	Identifier "VNC Device"
	Driver "fbdev"
EndSection

Section "Screen"
	Identifier "VNC Screen"
	Device "VNC Device"
	Monitor "VNC Monitor"

	SubSection "Display"
		Virtual	1024 768
	EndSubSection
EndSection

Section "Monitor"
	Identifier "VNC Monitor"
	HorizSync 30-70
	VertRefresh 50-75
EndSection
```

There is a lot of examples out on the internet containing **Driver "vesa"**, but this driver leaves me in text mode.

Now Wine seems to work fines and I can try to install something !

---

