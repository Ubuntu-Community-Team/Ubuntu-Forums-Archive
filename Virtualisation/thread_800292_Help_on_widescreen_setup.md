---
title: "Help on widescreen setup"
date: 2008-05-19
forum: Virtualisation
---

### Post by pwc on 2008-05-19
Help! Can't get widescreen(1680x1050) set up on 64-bit Hardy. I installed virtualbox 1.6.0-30421 and installed XP(32 bit) as guest. Everything seems to work ok except I can't get widescreen choices in resolution. I had it setup on 7.10 and I think I installed drivers from nvidia-can't remember how I did it since I'm 68 with fading memory. However when I download from Nvidia the drivers for my card(Geforce 8800 GT) it will not install. 
 Any ideas how to do this will be appreciated from this old fart.

Thanks and life is still good!
pwc

---

### Post by bradmkjr on 2008-05-19
Remember, you are inside a virtualized machine, so the XP doesn't have direct access to your video card. You need to install the Virtual Machine additions, which includes customized windows video drivers.

Here is a simple video, to give you an idea how to install the guest additions:
[http://www.youtube.com/watch?v=aLo6OrEdTK8&feature=related](http://www.youtube.com/watch?v=aLo6OrEdTK8&feature=related)

This post may give you a little more information:
[http://ubuntuforums.org/showthread.php?t=372285](http://ubuntuforums.org/showthread.php?t=372285)

Good Luck,
Bradford Knowlton
[http://x86Virtualization.com/](http://x86Virtualization.com/)

---

### Post by pwc on 2008-05-20
OK, thanks "bradmkjr" for your response, I'm not sure what the Virtual Machine additions are or how to find them but I'll play with this idea  some and see what happens.

thanks again,
pwc

---

### Post by 00arthuryu on 2008-05-20
hiya
if you have XP in a little window (when its booted up)
go on 'devices' and then 'install guest additions'
After that, you can make it fullscreen by right-ctrl + F and fill your whole screen =)

hope this helps

---

