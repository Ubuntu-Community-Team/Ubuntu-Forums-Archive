---
title: "Detecting Real video card in Virtual box"
date: 2009-02-25
forum: Virtualisation
---

### Post by Sojurner on 2009-02-25
I am trying to figure out a way to play my games using Direct X. I am currently using Ubuntu 8.10 and using Virtual box to run windows. 

Is there anyway to make virtualbox detect and use my real videocard  with the correct drivers so that i can still play the games i want without having to make a real installation of windows on my computer?.

Should i be using another virtualization program other than virtbox to achieve this or is it just not possible.

---

### Post by Jose Catre-Vandis on 2009-02-25
Make sure you are using the latest version of VirtualBox (2.12 -> 2.1.4) and in the settings for your VM tick the 3d Acceleration box on the General/Basic tab. This should give you the 3D capabilities of your hosts graphics card. Can't promise the world, but you should see an improvement.

You won't get direct access/recognition to the / of the physical card.

You might want to try VMware as an alternative

---

### Post by konqueror7 on 2009-02-25
you can try VMware, it currently has a experimental DirectX support...haven't tried it personally though, only without DirectX...;)

---

### Post by Sojurner on 2009-02-25
thanks for the ideas. i may have to go the vmware route because most of my games wont load because its not detecting direct x or my real video card...

does anyone know if VMware uses ur actual video card or fakes it like in virtualbox. So that maybe i could install updated drivers in vmware where i cant in virtualbox.

---

### Post by Jose Catre-Vandis on 2009-02-25
In reality, you are probably going to be better off playing your games in a real Windows environment rather than trying to kludge the directX/graphics elements. I know its heresy, but you can always run ubuntu in a VM on your windows setup if you need to do ubuntu and games at the same time.

---

### Post by Ng Oon-Ee on 2009-02-25
Just so everyone reading this thread knows, the virtualized card in VBox is NOT your real card, its exactly that, a virtualized card with 3D acceleration. ONLY OpenGL at this point. VMWare actually has DirectX 8 or roundabouts, useful for older games but not much else. For more recent games with high 3D requirements, you're stuck with either Wine or booting to Windows to play.

There is no way to detect your real video card in a VM. That's the whole point of virtualization, the VM is not aware of the 'real' machine. Else, if the VM took the video card, what would the host OS use for its display?

---

### Post by rocknzen on 2009-03-02
> **Ng Oon-Ee said:**
> Just so everyone reading this thread knows, the virtualized card in VBox is NOT your real card, its exactly that, a virtualized card with 3D acceleration. ONLY OpenGL at this point. VMWare actually has DirectX 8 or roundabouts, useful for older games but not much else. For more recent games with high 3D requirements, you're stuck with either Wine or booting to Windows to play.

There is no way to detect your real video card in a VM. That's the whole point of virtualization, the VM is not aware of the 'real' machine. Else, if the VM took the video card, what would the host OS use for its display?

Thanks for that clear explenation. I'm new to Virtualization and still trying to figure out what you can and can't do.

Cheers!

---

### Post by bodhi.zazen on 2009-03-02
> **Ng Oon-Ee said:**
> Just so everyone reading this thread knows, the virtualized card in VBox is NOT your real card, its exactly that, a virtualized card with 3D acceleration. ONLY OpenGL at this point. VMWare actually has DirectX 8 or roundabouts, useful for older games but not much else. For more recent games with high 3D requirements, you're stuck with either Wine or booting to Windows to play.

There is no way to detect your real video card in a VM. That's the whole point of virtualization, the VM is not aware of the 'real' machine. Else, if the VM took the video card, what would the host OS use for its display?

+1 , I was going to say the same.

This also applies to all your virtualized hard ware although there are some options to say use your physical HD, any attempt to use your actual hard ware remains , IMO, in Beta.

For using physical hard drives I have had success with VMWare and KVM. I have not tried virtualbox.

---

### Post by darco on 2009-03-02
to be exact, vmware gives you access to Direct X 9.0c settings.

darco

---

