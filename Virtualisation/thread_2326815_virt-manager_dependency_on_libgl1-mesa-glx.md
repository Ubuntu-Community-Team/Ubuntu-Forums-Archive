---
title: "virt-manager dependency on libgl1-mesa-glx"
date: 2016-06-05
forum: Virtualisation
---

### Post by philled on 2016-06-05
I have been running KVM on Ubuntu 14.04 successfully for some time. Stuffed up my server this week so decided to start from scratch and use Ubuntu 16.04. I found that I couldn't get virt-manager to run - it kept failing with this error:

[FONT=courier new]Couldn't open libGL.so.1: libGL.so.1: cannot open shared object file: No such file or directory[/FONT]

The solution is to install libgl1-mesa-glx and then it works. I'm seeing this message now when it starts but it doesn't seem to stop it running so it's not a big problem. I think it's somethgni to do with not having nVidia drivers installed - but this is a headless server not running X, so I don't need them.
[FONT=courier new]
libGL error: No matching fbConfigs or visuals found[/FONT]
[FONT=courier new]libGL error: failed to load driver: swrast[/FONT]


Odd that the libgl1-mesa-glx package isn't identified as a dependency for virt-manager. Is it a packaging error, perhaps?

---

### Post by houstonbofh on 2016-06-06
Virt-manager is a GUI program.  Why are you running it on a headless server?  It is not needed on the server, but on the client.  It connects to libvirt directly via ssh.  The only thing needed on the server is kvm, libvirt and ssh.

---

### Post by philled on 2016-06-06
> **houstonbofh said:**
> Virt-manager is a GUI program.  Why are you running it on a headless server?  It is not needed on the server, but on the client.  It connects to libvirt directly via ssh.  The only thing needed on the server is kvm, libvirt and ssh.

The client is a Windows PC. I'm using X11 forwarding to display the virt-manager on the Windows PC. There is no virt-manager software for Windows as far as I'm aware so unless I have a Linux desktop PC this is the only of doing it that I'm aware of. Have I got this wrong?

---

### Post by MAFoElffen on 2016-06-07
XServer headless =
```

sudo apt-get install xserver-xorg-video-dummy

```
Then an xorg.conf file that  points to device driver "dummy" and also tells to IgnoreEdid true... because there is no monitor to get that info...

---

### Post by philled on 2016-06-07
> **MAFoElffen said:**
> 
```

sudo apt-get install xserver-xorg-video-dummy

```

Thanks - that worked. I've installed xserver-xorg-video-dummy and I no longer get the error. Thanks for the simple solution.

---

