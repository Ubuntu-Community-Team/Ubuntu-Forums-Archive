---
title: "[SOLVED] linux-restricted-modules-2.6.22-14-server doesnt exist?"
date: 2008-06-02
forum: Server Platforms
---

### Post by Titan8990 on 2008-06-02
I am trying to increase my display resolution but I am unable to do so because of a lack of drivers. Whenever I try to go to the restricted drivers manager it informs me that I am missing a package:


When I go to the synaptic package manager I see that this package does not exist. I tried installing the x86 generic version with no luck. Anyone know a work around for this or am I missing something?


Also info on how to put a thumbnail image in your post instead of at the bottom would be helpful.

---

### Post by quelx on 2008-06-02
Ubuntu probably leaves restricted modules out of its server build intentionally because of the security risk using binary packages on a server.  You can edit **/etc/X11/xorg.conf** to increase your resolution or install one of the **-generic** kernels.

---

### Post by Titan8990 on 2008-06-02
I tried one of the generics with no luck. I am going to opt to not mess with the xorg.conf to change resolution because last time I did I ended up having to restore from an old xorg.conf backup.

Thanks for the reply, looks like I will have to live with it (planning on uninstalling ubuntu-desktop when server goes live anyways).

---

### Post by cdenley on 2008-06-02
The generic restricted modules will load if you run the generic kernel. Are you trying to increase the resolution of a server by using closed-source kernel modules? This can be done in hardy, I've done it before out of curiosity. You just have to find the restricted modules package for the server kernel. Unlike the other kernels, there is no metapackage, so the restricted modules won't be updated if you install a newer kernel. I never run any graphics environment on a server, let alone kernel modules compiled by ati or nvidia.

I just checked, and it looks like you're running gutsy and it doesn't have restricted modules for the server kernel. Either upgrade to hardy, or choose between the server kernel and the restricted modules.

---

### Post by Titan8990 on 2008-06-02
Thanks for the reply. The server kernel will be my choice.

---

### Post by Titan8990 on 2008-06-03
Alright I pulled an unmounted drive from the machine. The HDD did nothing yet it still managed to change my display settings. I am now down to max of 800x600 which is unacceptable. My xorg.conf file contains this:

```
Section "Monitor"
	Identifier	"DELL E207WFP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"DELL E207WFP"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

Anyone have an idea on why it will not allow me to select the higher resolutions. Any ideas on how pulling a HDD that was not even being used could lower my max display resolution?

---

### Post by Titan8990 on 2008-06-03
After a reboot it seems that is back to normal. I would still like some insight on what could have been the cause of the problem. Thanks.

---

