---
title: "DIrect3D acceleration in virtualization."
date: 2008-02-09
forum: Virtualisation
---

### Post by indianballer24 on 2008-02-09
Is there any virtualization software that supports direct3D acceleration?

---

### Post by yabbadabbadont on 2008-02-09
VMWare has experimental 3d support.  I've only read about it though, not tried it.

Edit: WINE provides D3D emulation.  Sort of...

---

### Post by indianballer24 on 2008-02-09
Which VMware product has experimental support?

---

### Post by yabbadabbadont on 2008-02-09
I don't remember if Server does or not.  I'm fairly sure that workstation does.  Check the vmware website.  Their support forums is where I read about it.

Edit: Let me be clear about it though.  This is not directly supporting your super duper fast 3d video card, but providing an *emulated* 3d video card inside the VM.

---

### Post by DMoRiaM on 2008-02-10
VMWare Player 2.0 had the experimental support. But you need to enable it on the .vmx file. A good place to assemble a virtual hardware and start doing tests is [www.easyvmx.com](www.easyvmx.com), where you will be able to create a starting virtual machine to play with. In that way you will not need to get a vmware server too.

Regards,
Marcelo D'Moriam

---

### Post by yabbadabbadont on 2008-02-11
VMWare Server is free for personal use, just like Player.  Plus it lets you create VMs whereas Player doesn't.

---

### Post by DMoRiaM on 2008-02-11
Indeed! But I fell it a little "fat" and the player only version had a better support for sound. Plus the fact that you may carry your vm with you to any place. I just got an serial number from vmware inc. and started to test it with Ubuntu 7.10. 

Thanks for the reminder about the server version.

Regards, 
Marcelo D'Moriam

---

### Post by indianballer24 on 2008-02-16
> **DMoRiaM said:**
> VMWare Player 2.0 had the experimental support. But you need to enable it on the .vmx file. A good place to assemble a virtual hardware and start doing tests is [www.easyvmx.com](www.easyvmx.com), where you will be able to create a starting virtual machine to play with. In that way you will not need to get a vmware server too.

Regards,
Marcelo D'Moriam
How do you edit the .vmx file to enable it in VMware Player or Server. Server preferably.

---

### Post by CarpKing on 2008-02-16
Is the other DirectX stuff supported?  DirectPlay etc?

---

### Post by DMoRiaM on 2008-02-18
@indianballer24

The .vmx file is the definition file for your VM. Both VMWare Player and Server are abble to use it.

@CarpKing

The Direc3D support is in a very early stage at the moment. I'm not very aware about all the features suported until now. 

Ps.: Brazilian speaker, maybe my english are not very good after all! Sorry!

---

### Post by indianballer24 on 2008-02-21
> **DMoRiaM said:**
> @indianballer24

The .vmx file is the definition file for your VM. Both VMWare Player and Server are abble to use it.

@CarpKing

The Direc3D support is in a very early stage at the moment. I'm not very aware about all the features suported until now. 

Ps.: Brazilian speaker, maybe my english are not very good after all! Sorry!
I understand that, but how do I enable acceleration. What do I edit in the .vmx file?

---

### Post by Shazaam on 2008-02-21
Add this to your .vmx file (open it with a text editor).........
```
# Experimental!
# Accelerated 3-D Graphics
mks.enable3d = "TRUE"
svga.vramSize = "67108864"
vmmouse.present = "FALSE"
```

---

### Post by TheLions on 2008-02-22
> **Shazaam said:**
> Add this to your .vmx file (open it with a text editor).........
```
# Experimental!
# Accelerated 3-D Graphics
mks.enable3d = "TRUE"
svga.vramSize = "67108864"
vmmouse.present = "FALSE"
```


that does nothing! 

i'm using VMware Workstation 6.0.2 build-59824:frown::frown::frown:

EDIT: fixed, i forgot to complete close vmware before editing...

---

### Post by indianballer24 on 2008-02-23
> **Shazaam said:**
> Add this to your .vmx file (open it with a text editor).........
```
# Experimental!
# Accelerated 3-D Graphics
mks.enable3d = "TRUE"
svga.vramSize = "67108864"
vmmouse.present = "FALSE"
```
Does that work in VMware Server, or is it just for VMware workstation?

---

### Post by TheLions on 2008-02-24
> **indianballer24 said:**
> Does that work in VMware Server, or is it just for VMware workstation?

it works in workstation, Idunno for server...

---

### Post by indianballer24 on 2008-02-25
> **TheLions said:**
> it works in workstation, Idunno for server...
Is there any way to enable it in VMware server?

---

### Post by OmegaBLK on 2008-02-25
Direct3D is not supported in VMware Server version 1.4 or any previous version.  Not really sure if Server 2.0 Beta has support.  I doubt that is does from what I can gather.

---

### Post by Shaythong on 2008-03-02
VMWare Server 2.0 has experimental Direct3D support, same as VMWare Workstation 6. They both support Directx 8 with no pixel shaders.

---

### Post by fjgaude on 2008-03-02
> **Shaythong said:**
> VMWare Server 2.0 has experimental Direct3D support, same as VMWare Workstation 6. They both support Directx 8 with no pixel shaders.

Gosh, this is good news. When 2.0 is released I move over to it.

---

### Post by indianballer24 on 2008-03-03
> **Shaythong said:**
> VMWare Server 2.0 has experimental Direct3D support, same as VMWare Workstation 6. They both support Directx 8 with no pixel shaders.
Will I be able to play games such as halo1 using Directx 8?

---

### Post by Shaythong on 2008-03-03
> **indianballer24 said:**
> Will I be able to play games such as halo1 using Directx 8?

I don't think so, but it's worth a try. :)

---

### Post by indianballer24 on 2008-03-04
> **Shaythong said:**
> I don't think so, but it's worth a try. :)

Can anyone confirm or refute this for me?

---

### Post by Shaythong on 2008-03-05
> **indianballer24 said:**
> Can anyone confirm or refute this for me?

Well actually I just found out that Halo 1 (Combat Evolved) for PC requires DirectX9.
[http://support.microsoft.com/kb/829479](http://support.microsoft.com/kb/829479)

---

### Post by indianballer24 on 2008-03-05
> **Shaythong said:**
> Well actually I just found out that Halo 1 (Combat Evolved) for PC requires DirectX9.
[http://support.microsoft.com/kb/829479](http://support.microsoft.com/kb/829479)
Is there any virtualization product that supports Directx 9?

---

### Post by Shaythong on 2008-03-05
> **indianballer24 said:**
> Is there any virtualization product that supports Directx 9?

Yes there is, I think Parallels and VMWare Fusion do support full graphics virtualization, but they are for Mac OS X only.

---

### Post by indianballer24 on 2008-03-06
> **Shaythong said:**
> Yes there is, I think Parallels and VMWare Fusion do support full graphics virtualization, but they are for Mac OS X only.
What linux virtualization software has the best graphics virtualization or plans to have it in the near future?

---

### Post by fjgaude on 2008-03-06
I would put my money on VMware. But on the other hand, I wonder if the business world needs graphic acceleration? I know gamers do. <smile>

I'm amazed that VMware gives away Server and Player. For that I'm thankful.

---

### Post by indianballer24 on 2008-03-06
Does VMware workstation have better DirectX emulation than VMware player, or is it the same?

---

### Post by fjgaude on 2008-03-06
> **indianballer24 said:**
> Does VMware workstation have better DirectX emulation than VMware player, or is it the same?

As far as I know they are the same and really a beta issue. I believe when version 2.0 comes out it'll be the best it can be for awhile.

---

### Post by Shaythong on 2008-07-10
VMWare Workstation 6.5 Beta seems to be suprising. :)

---

### Post by Masoris on 2008-07-10
> **Shaythong said:**
> VMWare Workstation 6.5 Beta seems to be suprising. :)

I already wrote about that:
[http://ubuntuforums.org/showthread.php?t=846675](http://ubuntuforums.org/showthread.php?t=846675)

---

