---
title: "Pangolin and gnome 3 graphics"
date: 2011-10-12
forum: System76 Support
---

### Post by twopointfour on 2011-10-12
I have a System76 Pangolin Performance laptop with an ATI video card. I'm running Ubuntu Oneiric and I'm very excited to get to use Gnome 3 instead of Unity by installing the gnome-shell package.

The 3d support is very messed up, however. It seems to work fine in unity though, so I think this is most likely an issue with gnome 3 not supporting my video driver. The bar at the top of the screen is has random blocks of cyan all over it, and every time I do something that requires 3d-ness (like press the Super key and watch all my open windows re-arrange) the display flickers and a lot. Interestingly enough, when I take screenshots with the printscreen the cyan blocks stay. I've attached a screenshot.

When I run lspci, here is my video card:

02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500/5100 Series]

Without installing any proprietary drivers I have some 3d support. In Additional Drivers the options are "ATI/AMD proprietary FGLRX graphics driver" and "ATI/AMD proprietary FGLRX graphics driver (post-release updates)" and neither of those solve this problem. I went to ATI's website and downloaded their drivers (a binary file you run as root), and installed it, and it removed all 3d support altogether. I have managed to uninstall it.

Has anyone else had this problem, or does anyone have suggestions on how to fix it? Thanks!

---

### Post by isantop on 2011-10-13
You're getting the problem using both the open source and the proprietary video drivers?

---

### Post by twopointfour on 2011-10-13
> **isantop said:**
> You're getting the problem using both the open source and the proprietary video drivers?

Yup. The problem appears to be the same with both drivers. Both drivers appear to work fine with Unity though.

---

### Post by paul555 on 2011-10-26
I have the same problem with the same video card in a hp pavilion dv6 laptop. Any solution to this?

---

### Post by foogoo on 2011-10-30
Same issue here with the exact same specs and situation as the OP. Any help from System76?

---

### Post by albin.jones on 2011-11-12
I have the same issue (same problem, same hardware).  I've tried both open and proprietary drivers, no joy.  Any suggestions?  Any solutions?

Has anyone at System76 been able to replicate the problem?

---

### Post by isantop on 2011-11-14
We have been able to replicate the issue, and have confirmed that the issue is with the ATI proprietary drivers. Gnome Shell is incompatible with the ATI proprietary drivers, and trying to remove the drivers does not completely remove them, preventing use of any 3D accelerated environment. You can properly remove them using these commands run at a terminal:

```
sudo /usr/share/ati/fglrx-uninstall.sh #This one may not work; if not, that's okay.
sudo apt-get remove --purge fglrx
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg- video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:i386 libgl1-mesa-dri:amd64 xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```

This will properly remove the drivers and allow you to run Gnome Shell.

---

### Post by albin.jones on 2011-11-14
Thank you.  That worked.

I executed the commands as you suggested.  (The first executable didn't exist.)  After a quick reboot the new drivers (and the new Gnome) seemed to be in working order.

(Well, I had a [likely unrelated] problem with my wireless networking after the first reboot.  But the second reboot did the trick.)

Thanks again.

---

### Post by paul555 on 2011-11-15
Thank you very much. It also worked for me.

---

