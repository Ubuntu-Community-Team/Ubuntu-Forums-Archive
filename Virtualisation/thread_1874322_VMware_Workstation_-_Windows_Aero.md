---
title: "VMware Workstation - Windows Aero"
date: 2011-11-02
forum: Virtualisation
---

### Post by altjx on 2011-11-02
Is it something with VMware with Linux that's not allowing Windows Aero to work in VMware Workstation 8?

I'm not sure what's going on, but is it something with my video driver, or is it a setting I need to tweak manually for VMware Workstation?

---

### Post by Jake.Debord on 2011-11-03
How much vram do you have allocated?

---

### Post by altjx on 2011-11-03
> **jake.debord said:**
> how much vram do you have allocated?

1gb.

---

### Post by Jake.Debord on 2011-11-03
you have 1gb of ram or 1gb of video ram?

---

### Post by altjx on 2011-11-03
> **Jake.Debord said:**
> you have 1gb of ram or 1gb of video ram?

Ah, sorry. I wasn't aware that I had to manually allocate video ram to the VM. I'm currently not at home right now, but I'll definitely check once I make it home.

I'll try increasing it, whatever it is, and let you know. Thanks a lot!

---

### Post by haqking on 2011-11-03
> **altjx said:**
> Ah, sorry. I wasn't aware that I had to manually allocate video ram to the VM. I'm currently not at home right now, but I'll definitely check once I make it home.

I'll try increasing it, whatever it is, and let you know. Thanks a lot!

you also need to enable 3D

---

### Post by altjx on 2011-11-03
I'll check that as well.

---

### Post by altjx on 2011-11-03
Ok, I've checked the settings for the VM, but I do not see anything about allocating video memory to it. I do have Accelerate 3D graphics enabled.

Any other suggestions? How do I check and allocate more vram to the VM?

---

### Post by haqking on 2011-11-03
> **altjx said:**
> Ok, I've checked the settings for the VM, but I do not see anything about allocating video memory to it. I do have Accelerate 3D graphics enabled.

Any other suggestions? How do I check and allocate more vram to the VM?

it is in the display settings that is where you assign video memory

[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1010544](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1010544)

there are tons of stuff out there on working with aero in vmware

---

### Post by altjx on 2011-11-03
> **haqking said:**
> it is in the display settings that is where you assign video memory

[IMG]http://dl.dropbox.com/u/2526790/shot.png[/IMG]

I'm not seeing anything other than Accelerate 3D settings and the resolution/monitors selection.

---

### Post by haqking on 2011-11-03
have a google there is tons of stuff out there 

[http://www.sysprobs.com/windows-7-aero-vmware-player-3-virtual-machine-simple](http://www.sysprobs.com/windows-7-aero-vmware-player-3-virtual-machine-simple)

I dont use vmware i use virtual box

---

### Post by altjx on 2011-11-03
> **haqking said:**
> have a google there is tons of stuff out there 

[http://www.sysprobs.com/windows-7-aero-vmware-player-3-virtual-machine-simple](http://www.sysprobs.com/windows-7-aero-vmware-player-3-virtual-machine-simple)

I dont use vmware i use virtual box

VirtualBox actually supports Windows Aero? I didn't know that. That's actually one of the only reasons I chose to use VMware, along with the thin-provisioning.

---

### Post by haqking on 2011-11-03
> **altjx said:**
> VirtualBox actually supports Windows Aero? I didn't know that. That's actually one of the only reasons I chose to use VMware, along with the thin-provisioning.

since version 4.1

[http://betanews.com/2011/07/22/finally-virtualbox-4-1-brings-aero-support-vm-cloning/](http://betanews.com/2011/07/22/finally-virtualbox-4-1-brings-aero-support-vm-cloning/)

version is currently 4.1.4

However i dont use aero, if i use a VM its not for the graphics ;-)

---

### Post by altjx on 2011-11-03
> **haqking said:**
> since version 4.1

[http://betanews.com/2011/07/22/finally-virtualbox-4-1-brings-aero-support-vm-cloning/](http://betanews.com/2011/07/22/finally-virtualbox-4-1-brings-aero-support-vm-cloning/)

version is currently 4.1.4

However i dont use aero, if i use a VM its not for the graphics ;-)

Gotcha. Lol. Well it's always worked when I was using Windows, so I've just became curious as to why it wasn't working on Linux.

Thanks.

---

### Post by haqking on 2011-11-03
> **altjx said:**
> Gotcha. Lol. Well it's always worked when I was using Windows, so I've just became curious as to why it wasn't working on Linux.

Thanks.

no worries.

Good luck.

If you get it working then remember to mark the thread as solved using thread tools.

Cheers

---

### Post by altjx on 2011-11-03
Thanks, and will do.

---

