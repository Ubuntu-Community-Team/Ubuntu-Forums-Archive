---
title: "Moving from virtualbox to kvm"
date: 2008-02-09
forum: Virtualisation
---

### Post by badrunner on 2008-02-09
I've just installed hardy, so want to try out the newer version of kvm it uses. Is there any way to convert from my old virtualbox images to ones kvm can understand?

---

### Post by kcav45 on 2008-02-09
Why not use VMware server? What so good about Virtual Box?

:confused:

KC

---

### Post by badrunner on 2008-02-10
I dont want to use vmware or virtual box, i want to use kvm ..

---

### Post by cluepon on 2008-02-10
> **kcav45 said:**
> Why not use VMware server? What so good about Virtual Box?

:confused:

KC

It's not really a matter of that. He wants to use neither VBox or VMWare. He wishes to use KVM, which is a kernel emphasised VM package, which uses a modified QEMU. 

I use VirtualBox, and I could ask: what's so great about VMWare? I had Virtualbox up and running in no time. VMWare is a pain. The module was cranky, and had issues being inserted. I had no such issues with Virtualbox's module.  While neither Virtualbox or VMWare are "free" Virtualbox works for what I do, and does what it does quite well. I use VBox for one thing: Photoshop. (GIMP folks, spare me another "switch to gimp" diatribe. GIMP is not a photoshop replacement. Period) 

VBox runs Pshop well, with enough speed, that Im a happy camper. 


As for the original posters question, I do not know how to convert the images. Perhaps you should check the QEMU site as well as the KVM site. I am not sure there is a way to do it. But if there is, I would start there. =)

---

### Post by badrunner on 2008-02-10
> **cluepon said:**
> It's not really a matter of that. He wants to use neither VBox or VMWare. He wishes to use KVM, which is a kernel emphasised VM package, which uses a modified QEMU. 

I use VirtualBox, and I could ask: what's so great about VMWare? I had Virtualbox up and running in no time. VMWare is a pain. The module was cranky, and had issues being inserted. I had no such issues with Virtualbox's module.  While neither Virtualbox or VMWare are "free" Virtualbox works for what I do, and does what it does quite well. I use VBox for one thing: Photoshop. (GIMP folks, spare me another "switch to gimp" diatribe. GIMP is not a photoshop replacement. Period) 

VBox runs Pshop well, with enough speed, that Im a happy camper. 


As for the original posters question, I do not know how to convert the images. Perhaps you should check the QEMU site as well as the KVM site. I am not sure there is a way to do it. But if there is, I would start there. =)

Yeah, i did start there, but havent found any info yet. Plenty of info on how to do qemu->vdi images, but not the other way round.

---

### Post by fergus on 2008-02-13
Figure anything out yet?  I will want to do this in the near future so I interested in what you come up with...  Maybe try using vditool to dump a dd(raw) version of the filesystem.  Then use qemu-img to convert the raw to its image format?

vditool COPYDD image.vdi image.dd
qemu-img convert -f raw image.dd -O qcow2 image.img

I haven't actually tried this but it might work...

fergus

---

### Post by dudacgf on 2008-05-20
I used the following command to convert:

vditool COPYDD WXP.vdi WXPa.img

then I booted into windows XPa using KVM.  The first boot was OK, but I could not reboot after windows reconfigured the drivers.  I will try again in a few days (lunch time is over, work time is back) and will post results here if they are successfull.

cheers

---

