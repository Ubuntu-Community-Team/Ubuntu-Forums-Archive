---
title: "NVidia Tearing (Unity/Compiz) - Unrelated to recent driver problems"
date: 2012-05-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-05-04
Despite of the recent problems with NVidia driver 295.33 and 295.40, do you guys see excessive tearing when using recent/working NVidia driver versions (such as 295.17, 295.20, 295.49, 302.07)  on recent/working VGA hardware (powerful enough to not justify any video issue).

I don't have any tearing problem with video, but moving windows fast clearly shows some drawing problems on Unity on a fully updated PP/QQ.

Default Compiz options, Compiz workarounds, GLX Sync to VBlank on CCSM or nvidia-settings, increasing card performance mode, etc makes no difference.

Test: Open any window, like a browser for example. Hold the titlebar and drag the window in fast circles over other windows on the desktop, paying attention to the browser window borders (especially vertical ones). I can easily see them "break" and redraw.

Regards,
Effenberg

---

### Post by ventrical on 2012-05-04
Not here effenberg. I have wobbly windows enabled on a GEForce 210/218/512. The only anomoly I notice is when I open System Settings window and drag that around in circles is that I get tearing between the title bar and main window. All other windows are running smoothly, no tearing at all , no breaking .. fully up dated (but I do not have the libxfont1 ppa enabled- I am still running off the original downgrade . That ppa fix does not apply when using synaptic).  [Unless that has been fixed too?]

Edit: I just realized that I did not have the lastest kernel update *installed* on this machine in the grub menu. It just won't come up.

---

### Post by ventrical on 2012-05-04
Here is the tear on System Settings window. I don't get it - how they have that patched like that because the other windows don't tear like that.



[http://www.youtube.com/watch?v=F6eLKaU4l1I&feature=youtu.be](http://www.youtube.com/watch?v=F6eLKaU4l1I&feature=youtu.be)

---

### Post by QIII on 2012-05-04
I have ATI, not NVIDIA, but last night I found that I was getting a catastrophic segfault enabling Compiz in Xubuntu QQ.

Haven't determined yet if Compiz is a cause or a symptom.

May be deeper than just an NVIDIA issue?

---

### Post by kaldor on 2012-05-04
Have it on my laptop with both Nouveau and the blob. Can't remember when it started.

---

### Post by ventrical on 2012-05-05
@effenberg...

 I can say that I do not have any Nvidia problems with my GeForce 210/218 with compiz or other .. but on a fully updated 3.4.n-n QQ I am forced out of NVidia current and other drivers will not load - rendering me into a 800x600 mode. However it works perfectly with the 3.2.0-24 kernel.

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

---

