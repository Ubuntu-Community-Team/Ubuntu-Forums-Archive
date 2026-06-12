---
title: "Wined3d in kvm XP guest"
date: 2009-06-28
forum: Wine
---

### Post by MasterPoulos89 on 2009-06-28
Hello.

I am using kvm on Jaunty host to run XP guest in a virtual machine.

I have set it up to do everything virtualbox can do and it works quit nicely.

I know there is little support at the moment for directx emulation in a vm but I found a program (wined3d) that is supposed to give windows guest directx support.

here is the site: [http://www.nongnu.org/wined3d/](http://www.nongnu.org/wined3d/)

I downloaded the latest version and installed it in safe mode. Then I tested it with a game that uses directx (Combat Arms). It did not give an error about directx as it usually does but it shows a black screen and goes away not bringing me to the log in window.

I assume I must of done it right and the problem is that wine3d3 is in development but I just want to know if there is more to it then just installing it in the guest vm.

I know with VMGL you need to install it on both guest and host.

So my question is, is there anything I need to do to my ubuntu host to make my XP guest recognise the directx from wined3d or did I already do everything right and just have to wait for developers to finish the project?

I don't know if I'm Posting in the right place. Its called WINE3d3 so I thought wine would be a good place to post my question.

Thanks for any help.

---

### Post by MasterPoulos89 on 2009-06-29
I found out I need to first enable Opengl on my windows guest.

Virtualbox has a simple option to enable Opengl on any os but I cant find any help to do this manually so I can enable Opengl in kvm-qemu.

VMGL is the solution for linux guest. Obviously there is a way to do this for windows as well since virtualbox can do it but I can't find any help online.

So does anyone know how to manually enable Opengl on a windows guest. If so please help me.

this seems to be the only step I need to take before enabling 3D with wined3d.

---

### Post by MasterPoulos89 on 2009-06-30
Anyone?????

I need some help.

Why won't anyone help me?????

---

### Post by MasterPoulos89 on 2009-07-02
Now I'm not even sure if opengl is the problem cause I tried it in virtualbox with opengl enabled and got the same problem.

I think wined3d is at a stage where it should at least tell me direct 3d is enabled on the guest so I still thing I must be doing something wrong.

Does anyone know??

---

### Post by cogadh on 2009-07-02
I think the problem actually is that it really doesn't matter if you have OpenGL working or not, (most) VM's still don't have the ability to access your video hardware directly and are just using a generic "device" that doesn't have the capabilities of your actual video card. Whether or not OpenGL or WineD3D is working is moot when you don't actually have the hardware to use either.

---

### Post by MasterPoulos89 on 2009-07-02
> **cogadh said:**
> I think the problem actually is that it really doesn't matter if you have OpenGL working or not, (most) VM's still don't have the ability to access your video hardware directly and are just using a generic "device" that doesn't have the capabilities of your actual video card. Whether or not OpenGL or WineD3D is working is moot when you don't actually have the hardware to use either.


That makes plenty sense and I would believe that that's the end of the story but I read on a site that wined3d does work with virtualbox.

I just reread the site and it seems they are not saying wine d3d works yet.......but they are getting there.

Here is the post: [http://www.virtualbox.org/ticket/2940](http://www.virtualbox.org/ticket/2940)

I still think if I want to do any of that in kvm-qemu I would need to enable opengl first.

Any tips for opengl on a windows guest in kvm-qemu??

---

### Post by cogadh on 2009-07-02
That's because VirtualBox is one of the exceptions. It is one of the few VMs that does have at least partial/experimental support for full 3D hardware access, while I don't believe KVM/QEMU does (though I'm pretty sure its on their "to do" list).

---

### Post by MasterPoulos89 on 2009-07-02
Ohh......I guess then I'll just use virtualbox for a while and test their directx support until it is available in kvm-qemu.

Thanks for clearing that up for me so I don't continue searching for something that doesn't exist yet.

Much thanks.

---

### Post by gareththomasnz on 2009-07-31
I'd like to play my new ARMA2 without a pesky dual boot.

I am not too hopefull of this but will have a play around with it. I have an AMD64 machine with ubuntu hardy.

I stuck XP 64bit into virtualbox but I dont think I will get ARMA2 working in there - will try it with wine on ubuntu and try setting the wined3d in my virtualbox XP to see what happens.

---

