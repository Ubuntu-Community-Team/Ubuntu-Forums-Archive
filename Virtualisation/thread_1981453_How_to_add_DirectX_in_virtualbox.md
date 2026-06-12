---
title: "How to add DirectX in virtualbox ?"
date: 2012-05-16
forum: Virtualisation
---

### Post by Docmero on 2012-05-16
[CENTER]Hi , 
I've installed windows 7 64bit in virtual-box
The system is working well . 
I have  core i5 750 , I allocated 2 cores to the system .
I have 4 GB ram , I allocated 1.6 GB to the system .
**_I have GTX 470 , I don't know to add this to the system !!_**
**_So my issue is , How to add DirectX to my virtual machine ._**
So that I can activate Aero and 3D applications .
I'd like to add that I've checked the  3D and 2D in the settings 
but noticed no difference .
My host is ubuntu 11.10
Thanks
[/CENTER]

---

### Post by Docmero on 2012-05-16
UPDATE : I installed virtualbox additions and the experimental 3D drivers , The system became smoooother  , faster and Directx 11 was added to the system but the GFX card - GTX 470- is not recognized though !! and video memory is only now 256 although the video memory of GTX 470is 1280  .

---

### Post by Amorget on 2012-05-16
You won't be able to add your GTX 470, it doesn't work like that.  The guest machine won't ever see your machines video card as what it is.

---

### Post by Docmero on 2012-05-17
So , the virtual system never uses the full capacity of the GPU ?
I tried to activate Aero in virtualbox but it didn't work although I did all the required step ,
after trying for a while I found the system can activate Aero only after restarting , but if I changed any personalization option , Aero is deactivated again !!
I tried Vmware instead of Virtualbox and came with great results , all my video ram was detected  in the system , Aero is working well , all my USB devices were detected , It's a bit slower than virtual box to be honest but I think I can take the performance hit to ensure stability of the system . _(if you know how to make it as fast as possible , please tell me ;-)_
Another problem , It's harder to switch from Win7 Desktop to ubuntu Desktop in Vmware _( I have exit full screen mode to be able to see ubuntu Desktop )_ . I'll make more experiments on both systems to keep this updated for next users .
Thanks

---

### Post by Amorget on 2012-05-17
Correct, Virtualization in general is not for gaming.

The only thing it took for me to get Aero working on my machine was to install the VBox additions in Safe Mode.  After that it worked just fine.

I have no comment on VMWare as I haven't used it.

---

### Post by Rebelli0us on 2012-05-17
The Guest OS does not control any hardware, it simply uses the Host's resources, just like another app. So you cannot add hardware to the Guest through Windows' Device Manager.

---

### Post by sepo on 2012-08-22
Some quote from the VirtualBox's manual ([https://www.virtualbox.org/manual/ch04.html#guestadd-3d](https://www.virtualbox.org/manual/ch04.html#guestadd-3d)), just to clarify :D.
About Guest Additions' Hardware 3D acceleration:
> ...With this feature, if an application inside your virtual machine       uses 3D features through the OpenGL or Direct3D 8/9 programming       interfaces, instead of emulating them in software (which would be slow),       VirtualBox will attempt to use your host's 3D hardware...and again
> Technically, VirtualBox implements this by installing an       additional hardware 3D driver inside your guest when the Guest Additions       are installed. This driver acts as a hardware 3D driver and reports to       the guest operating system that the (virtual) hardware is capable of 3D       hardware acceleration. When an application in the guest then requests       hardware acceleration through the OpenGL or Direct3D programming       interfaces, these are sent to the host through a special communication       tunnel implemented by VirtualBox, and then the *host*       performs the requested 3D operation via the host's programming       interfaces.
It surely does not implement directx 10 / 11 (nor 7), but works for OpenGL and d3d8/9. :)

---

### Post by sonnet on 2012-08-27
For (relatively) good 3d performances use Vmware player: you can play most of the games (even recent ones)

---

