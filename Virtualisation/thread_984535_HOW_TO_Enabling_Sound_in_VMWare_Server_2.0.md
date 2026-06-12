---
title: "HOW TO: Enabling Sound in VMWare Server 2.0"
date: 2008-11-16
forum: Virtualisation
---

### Post by BoGs on 2008-11-16
So I had switched from VirtualBox to VMWARE since its free and has much easier bridging behind the scenes for my virtual machines. Currently I run linux as my main computer and well the necessities of certain office windows products I was missing and their linux counterparts didn’t work as well. I had created a windows xp virtual machine from my computers license key since I no longer have the thing installed.

Creating the virtual machine and setting up linux went fine and smooth. Once in windows I started to tweak it and noticed there is no sound. I had shut down the machine and tried to add a sound device on “auto detect” was my only option. Booting the virtual machine I received an error that the sound was not able to be initialized, where I started to search the internet with no luck.

Finally I had figured it out and I have SOUND! Below you can find the steps I took and hope they work out as well for you as for me.

First is first - figure out what your device is for sound. I loaded up amarok and went to the configuration. From there to “Engine” and there it beholds “Device:”. For me there were two options:

```

/dev/dsp
/dev/sound/dsp

```

I had restarted amarok with each as my device and figured out that /dev/dsp was the one for me.

Then go to “/var/lib/vmware/Virtual Machines/” and open “.vmx” and look for the following lines:
	
```

..........
sound.present = "TRUE"
sound.allowGuestConnectionControl = "FALSE"
sound.fileName = "/dev/dsp" (changed from -1)
sound.autodetect = "FLASE" (changed from TRUE)
 
sound.pciSlotNumber = "36"
sound.startConnected = "TRUE"

```

Save the file and reboot the virtual machine and there we have sound! Isn’t that fantastic?!? If you have comments or suggestions please leave them as others might be experiencing the same issues as you.

Later!

Link: [http://www.bogdanmatu.com/?p=17](http://www.bogdanmatu.com/?p=17)

---

### Post by mpm on 2009-06-16
Worked like a charm. Thanks!

---

