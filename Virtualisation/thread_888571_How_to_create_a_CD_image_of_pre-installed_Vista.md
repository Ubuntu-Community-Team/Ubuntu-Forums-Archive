---
title: "How to create a CD image of pre-installed Vista?"
date: 2008-08-13
forum: Virtualisation
---

### Post by Remane on 2008-08-13
I am a recent Ubuntu user, and therefore please forgive my ignorance in these matters.  For my sins I purchased an Acer 7720G with Vista Ultimate pre-installed.  Have installed Ubuntu Hardy Heron and now wish to use VirtualBox to operate Vista whilst in Ubuntu.  The problem is that I don't possess an cd install disk for Vista, is there any way to create an ISO image for virtualBox to boot Vista or can it be re-directed to boot from the HD? 

Many thanks.
Remane

---

### Post by Quarg on 2008-08-13
and u have it in a dual boot?

---

### Post by Oldsoldier2003 on 2008-08-13
> **Remane said:**
> I am a recent Ubuntu user, and therefore please forgive my ignorance in these matters.  For my sins I purchased an Acer 7720G with Vista Ultimate pre-installed.  Have installed Ubuntu Hardy Heron and now wish to use VirtualBox to operate Vista whilst in Ubuntu.  The problem is that I don't possess an cd install disk for Vista, is there any way to create an ISO image for virtualBox to boot Vista or can it be re-directed to boot from the HD? 

Many thanks.
Remane

Contact Acer and request/demand an installation cd. They are obligated to provide it of you ask.

---

### Post by Quarg on 2008-08-13
The problem is, they might give you a recovery disk, and it may/may not work with a virtualized machine, I've had recovery disks on some computers that only run on that computer, it won't run on other models. But, if you ask for an installation CD, they will give you one, they do have to.

---

### Post by flytripper on 2008-08-13
thats right. you payed for it. youown it. they have it.. demand a copy.

---

### Post by bmwman on 2008-08-14
You can use any backup software that can make a system snapshot on a DVD or CDs. I use Acronis True Image, Ghost also Drive Image works and Paragon Drive back up. There're tons of 'em out there except most are not free. I believe you can find Hirens CD online and it has Drive image and Ghost on it and you don't have to pay for it. Then once you create the image you can restore it  inside the VM.

---

### Post by Remane on 2008-08-14
Thanks guys - on the case to Acer!!  Will also look into ghost apps.  Fingers crossed - just beginning to get the Linux bug!

---

### Post by himagain on 2008-08-14
> **bmwman said:**
> You can use any backup software that can make a system snapshot on a DVD or CDs. I use Acronis True Image, Ghost also Drive Image works and Paragon Drive back up. There're tons of 'em out there except most are not free. I believe you can find Hirens CD online and it has Drive image and Ghost on it and you don't have to pay for it. Then once you create the image you can restore it  inside the VM.

[http://hiren.info](http://hiren.info)
Thanks for that one! 
Just went there and the amount of tools and entertainment is amazing. 

Cheers!

---

### Post by bmwman on 2008-08-15
> **himagain said:**
> [http://hiren.info](http://hiren.info)
Thanks for that one! 
Just went there and the amount of tools and entertainment is amazing. 

Cheers!

I use it on a regular basis at work. You can make USB thumb drive and use it instead of CD.

Let us know how did it go with the conversion.

BTW it'll be alot easier if you look into converting your existing Vista OS into virtual. You don't have to create CD images first and then reinstall it inside VM(unless you want it for other purposes as well). There is a way to do it, just look into the forums here. I've done it many many times, but with VMware Workstation, I don't like VirtualBox.

---

### Post by aggelos.satanas on 2008-08-15
The backup software will copy all device drives along with vista, therefore the operating system will not install onto the virtual machine, it will throw up all kinds of errors due to the virtual motherboard being different to the previous motherboard. Your only options would be to buy an OEM copy of vista (quite cheap now) or pirate it, however that would be wrong so don't do it ;)

---

### Post by bmwman on 2008-08-15
> **aggelos.satanas said:**
> The backup software will copy all device drives along with vista, therefore the operating system will not install onto the virtual machine, it will throw up all kinds of errors due to the virtual motherboard being different to the previous motherboard. Your only options would be to buy an OEM copy of vista (quite cheap now) or pirate it, however that would be wrong so don't do it ;)

It does work. As a matter of fact I did one today. You can boot into Safe Mode the first time (F8) and remove all drivers from Add/Remove programs. Then it will load the VM drivers automatically.

---

