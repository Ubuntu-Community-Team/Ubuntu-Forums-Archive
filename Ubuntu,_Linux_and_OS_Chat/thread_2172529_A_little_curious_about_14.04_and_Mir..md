---
title: "A little curious about 14.04 and Mir."
date: 2013-09-05
forum: Ubuntu, Linux and OS Chat
---

### Post by TeamRocket1233c on 2013-09-05
Just a little curious about something, with 14.04 LTS rumored to ship with Mir as its only default display server, what'll happen if you do a base command-line install, and wanna use Wayland or X or something instead of Mir?

I mean, if you do a base command-line install of 13.04, for example, and either leave it at 13.04 or dist-upgrade it to 13.10, you can just install X and whatever DE or WM you want and be good to go, but wondering if the same will be true of 14.04 LTS.

---

### Post by grahammechanical on 2013-09-06
Ubuntu 13.04 has X and Xserver. That will not change. Ubuntu 13.10 still has X and Xserver but on release Xmir will be the default instead of Xserver but Xserver will still be there. So, there will be no need to install X on Ubuntu 13.10. It will already be there.

Making something the default does not mean that alternatives are not possible. Unity is the default user interface. That has not stopped people putting XFCE, KDE, LXDE and others on to Ubuntu.

At the moment Xmir works only with Nouveau the open source video driver. The removal of the X stack from the distribution depends on proprietary video drivers becoming available and producing an acceptable user experience. So, the next six months are going to be very interesting.

I would like to see some evidence that MIR will replace X on Ubuntu 14.04 LTS. From what I have read 14.04 will have Unity 7 and Xmir as the default without the fall back to Xserver that exists in 13.10. And Ubuntu 14.10 will have Unity 8 with MIR as the default and with rootless X support for legacy X applications. 

I think confusion exists because some people talk about Xmir as if it is MIR, which it is but MIR is something greater than Xmir. So, I read this at OMG Ubuntu

> XMir, which runs on top of Mir, and will front the Unity 7 desktop in  13.10, is used to provide backwards compatibility for applications and  services that rely on X.

Xmir does not run on top of MIR. Ubuntu 13.10 will have Xmir but not MIR. When Ubuntu 14.10 is released it will have MIR and Unity 8 but not Xmir for MIR will take over from Xmir.

I am at present running Saucy Salamander with Xmir. I do not notice any difference between Xserver and Xmir. I have also had all the flavours except Ubuntu Gnome running on Xmir. As regards Wayland, I read this in the MIR wiki

> Wayland support could be added either by providing a Wayland-specific  frontend implementation for our display server or by providing a  client-side implementation of libwayland that ultimately talks to Mir.

I can confirm that Saucy Salamander does have libraries for Wayland. But until Wayland/Weston makes its appearance in distribution useable form there is no need for Ubuntu developers to provide those additons.

Regards.

---

