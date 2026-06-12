---
title: "Intel SNA PPA"
date: 2012-09-25
forum: The Cafe
---

### Post by Welly Wu on 2012-09-25
[http://www.techlw.com/2012/08/install-latest-intel-gpu-drivers-in.html](http://www.techlw.com/2012/08/install-latest-intel-gpu-drivers-in.html)

My System76 Lemur Ultra Thin (lemu4) has an Intel HD Graphics 4000 integrated GPU and I did some research into the Intel Sandy Bridge New Acceleration PPA. Well, I added it and I installed and updated the software packages and I created the recommended xorg.conf file in my /etc/X11 folder and I rebooted my PC. It made a tremendous difference! My graphics are super ultra fast right now! K Desktop Environment 4.9.1 is highly responsive and Opera with 3D graphics hardware acceleration and OpenGL enabled is super fast! I am seeing at least a 20 percent increase in graphics speed across the board. It also works with the older Intel Sandy Bridge CPUs with Intel HD Graphics 3000 integrated GPUs. Ubuntu 12.10 64 bit will include Intel SNA by default.

This is solved for me.

---

### Post by jrog on 2012-09-25
> **Welly Wu said:**
> [http://www.techlw.com/2012/08/install-latest-intel-gpu-drivers-in.html](http://www.techlw.com/2012/08/install-latest-intel-gpu-drivers-in.html)

My System76 Lemur Ultra Thin (lemu4) has an Intel HD Graphics 4000 integrated GPU and I did some research into the Intel Sandy Bridge New Acceleration PPA. Well, I added it and I installed and updated the software packages and I created the recommended xorg.conf file in my /etc/X11 folder and I rebooted my PC. It made a tremendous difference! My graphics are super ultra fast right now! K Desktop Environment 4.9.1 is highly responsive and Opera with 3D graphics hardware acceleration and OpenGL enabled is super fast! I am seeing at least a 20 percent increase in graphics speed across the board. It also works with the older Intel Sandy Bridge CPUs with Intel HD Graphics 3000 integrated GPUs. Ubuntu 12.10 64 bit will include Intel SNA by default.

This is solved for me.
Thanks for sharing this; I have a similar system and will likely try it out.

EDIT: Hmm, just read the last sentence of your main paragraph (was just skimming before). Maybe I'm using this already? I'm on 12.10 Beta 1 64-bit.

---

### Post by KiwiNZ on 2012-09-25
Spelling in thread title corrected

---

### Post by jrog on 2012-09-25
> **jrog said:**
> Thanks for sharing this; I have a similar system and will likely try it out.

EDIT: Hmm, just read the last sentence of your main paragraph (was just skimming before). Maybe I'm using this already? I'm on 12.10 Beta 1 64-bit.
Answering myself here, but my /var/log/Xorg.0.log mentions only UXA, not SNA, so it looks like I'm not using it right now.

---

### Post by Welly Wu on 2012-09-25
[http://www.phoronix.com/scan.php?page=article&item=intel_sna_sep2012&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_sna_sep2012&num=1)

Phoronix has a lot of articles about Intel SNA. Do your reading.

---

### Post by jrog on 2012-09-25
Just an update: this *is* already included in 12.10 Beta 1, so to anyone who is already on Quantal, all you have to do to enable it is create an /etc/X11/xorg.conf file with the following content: 

```
Section "Device"
 Identifier	"Card0"
 Driver	"intel"
 Option	"AccelMethod" "sna"
EndSection
```

Playing with it right now and I already notice a speed increase!

---

### Post by Welly Wu on 2012-09-25
Your ASUS K55A is similar to my System76 Lemur Ultra Thin (lemu4). You and I should see roughly a 20 percent improvement in graphics speed compared to the older UXA. Download and install Opera 12.02 64 bit web browser and enable 3D graphics hardware acceleration and OpenGL. You will be amazed by the web browsing speed and performance! As an alternative, you could try Google Chrome and turn on graphics acceleration.

Intel SNA PPA is no joke!

---

### Post by Linuxisfast on 2012-10-31
> **Welly Wu said:**
> Your ASUS K55A is similar to my System76 Lemur Ultra Thin (lemu4). You and I should see roughly a 20 percent improvement in graphics speed compared to the older UXA. Download and install Opera 12.02 64 bit web browser and enable 3D graphics hardware acceleration and OpenGL. You will be amazed by the web browsing speed and performance! As an alternative, you could try Google Chrome and turn on graphics acceleration.

Intel SNA PPA is no joke!

From version 2x I have been a paid Opera user and then used their free version till 11x when they began to have too many issues, it was my all in one browser/email/news reader and worked quite well. There was no other browser in my system be it Linux or Windows. Since then I have become a regular user of Chrome but with all your feedback, I am thinking of going back to Opera. I have enabled SNA on my ASUS K53E with Intel HD3000 and icore5, so far no tearing etc. and performance generally is very good with GPU enabled Chrome.

---

