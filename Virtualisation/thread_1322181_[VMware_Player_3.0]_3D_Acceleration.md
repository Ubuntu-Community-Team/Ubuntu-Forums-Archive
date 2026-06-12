---
title: "[VMware Player 3.0] 3D Acceleration"
date: 2009-11-10
forum: Virtualisation
---

### Post by moonscapex on 2009-11-10
Does anyone know how to enable desktop effects in VMWare Player with Ubuntu 9.10 as the guest.  I get the error 'Can not enable desktop effects' when i try.  I have enabled 3D accel in the VMWare prefs.
Thanks,
Will

---

### Post by rlsx on 2009-11-10
I have the same problem running Ubuntu 9.10 as a guest in Vmware Workstation 7.0.

Note the following: I have also tried Kubuntu 9.10. There, to enable visual effects, one is given the choice between "OpenGL" and "XRender". The former option doesn't work, but the second does work.

As I understand it, OpenGL is not (yet?) available for Linux guests in Vmware. Only for Windows guests.

The question that remains: I don't know what "XRender" is. But, can Ubuntu use that same technique/api that Kubuntu does, to implement visual effects?

---

### Post by fjgaude on 2009-11-10
I was unable to install the Linux Tools using Player 3.0 and a Ubuntu 9.10 guest. So many issues with 9.10. I guess as we wait things will get worked out one way or the other.

---

### Post by rlsx on 2009-11-11
> **fjgaude said:**
> I was unable to install the Linux Tools using Player 3.0 and a Ubuntu 9.10 guest.
I am using VMware Workstation 7.0.
Host : Windows 7 x64.
Native processor : Core 2 Duo.
I had no problem whatsoever running Ubuntu 9.10 as guest.

Have you tried, for instance, the appliance:
    [http://www.vmware.com/appliances/directory/371063](http://www.vmware.com/appliances/directory/371063)

---

### Post by fjgaude on 2009-11-11
Workstation 7.0, wonderful!

Question: can you copy, paste text data from the VM to the host and back? What about sharees?

If you can I might spring for the $99 that WS costs.

---

### Post by rlsx on 2009-11-11
> **fjgaude said:**
> Question: can you copy, paste text data from the VM to the host and back? What about shares?

If you can I might spring for the $99 that WS costs.

Everything works as advertised, after you install the VMware tools in the Ubuntu guest.
Only desktop "visual effects" are not available.

You might download a 30-day trial version of Workstation 7.0. Once your VM is set up and configured correctly, you can try running it in the free Player.

---

### Post by fjgaude on 2009-11-11
Thanks for your help... my main setup is Ubuntu 9.10 host with a WinXP guest. But I need to be able to copy and paste text between the two. Up to 8.10 and VMServer 1.0.9 everything works as I needed it to work. Ubuntu 9.04 is unreliable as a copy/paste text host. And with 9.10 neither Server or Player compleley works. You can't install Server at all.

I will continue to seek out what will work for me as a graphic designer.

Thanks again!

---

### Post by moonscapex on 2009-11-11
Any other apps other than vmware and virtualbox that support 3D?

---

