---
title: "KVM Fullscreen with Compiz"
date: 2009-11-27
forum: Virtualisation
---

### Post by fatmcgav on 2009-11-27
Hi there, 

I'm running Ubuntu 9.10 x64 with Compiz and KVM. 
I've installed a Windows 7 guest which I've set-up to run on Workspace 3 in fullscreen mode. However i'm having issues with being able to switch out of the Fullscreen VM back to other displays... 

Initially Ctrl+Alt was the KVM grab combo, but i've appended the '-alt-flag' option to the KVM startup line, so it now looks like this
```
kvm -vga std -full-screen -hda /var/lib/libvirt/images/Poseidon.img -boot c -m 512 -alt-grab
```

So i can now Release control from KVM by using Ctrl+Alt+Shift, however I then can't use Ctrl+Alt+<Arrow> to move between work-spaces... 

Any ideas where I'm going wrong???

Cheers
Gavin

---

### Post by Tomy on 2009-12-01
You might try getting rid of the ctrl-alt-grab-the-mouse feature and just going with the virtual mouse - or whatever they call it. I believe the code to add is:

-usb -usbdevice tablet

---

### Post by bodhi.zazen on 2009-12-01
Depending on the version of KVM you can simply add 

-usbdevice tablet

I have a brief blog entry here as well :

[http://blog.bodhizazen.net/linux/kvm-mouse-integration/](http://blog.bodhizazen.net/linux/kvm-mouse-integration/)

---

### Post by fatmcgav on 2009-12-02
Hi there, 

Cheers for the posts... 
I've managed to work it another way by amending the xml config for my Guest, changing the video device to vga, and restarted libvirt-bin - Virt-manager now starts my Windows 7 guest with full resolution support, and auto-fullscreen - and as i'm doing it through Virt-manager, i get the handy toolbar at the top of the screen :) 

Cheers
Gav

---

