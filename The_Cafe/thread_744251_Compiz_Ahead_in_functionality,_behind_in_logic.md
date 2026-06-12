---
title: "Compiz: Ahead in functionality, behind in logic?"
date: 2008-04-03
forum: The Cafe
---

### Post by Mazza558 on 2008-04-03
Amazing as Compiz is, it is crippled if you attempt to run another 3D application. Vista handles this better, as it temporarily turns off Aero when a fullscreen 3D app is used. Of course, Compiz blows Vista's 3D effects out of the water, but I think it has a long way to go before it can be used all the time, which is a real shame.

---

### Post by SomeGuyDude on 2008-04-03
What applications are you referring to?

---

### Post by potrick on 2008-04-03
I think this partially depends on the driver you're using, but it really is a shame no one's worked out a way for it to automatically turn on/off depending on whether a full screen game is open.

---

### Post by Mazza558 on 2008-04-03
> **SomeGuyDude said:**
> What applications are you referring to?

Any.  For example, Google Earth will not run with Compiz at the same time for me.

---

### Post by 1875 on 2008-04-03
Get fusion icon if you need to shut down compiz down to run games etc. Better than Vista, you get to choose when and what you disable.[http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/]("http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/")

---

### Post by Hairy_Palms on 2008-04-03
you can get around the problem for wine apps by using the winefix script, it automatically disables compiz while the app is run and enables it afterwards

---

### Post by FuturePilot on 2008-04-03
[http://ubuntuforums.org/showthread.php?t=656336]("http://ubuntuforums.org/showthread.php?t=656336")

---

### Post by Mazza558 on 2008-04-03
Actually, is there a lightweight compositor instead of Compiz which is faster?

I'd like to run emerald and some other composited stuff...

---

### Post by FuturePilot on 2008-04-03
Metacity has a built in compositor in Hardy. But I don't find it any faster since it doesn't seem to utilize the GPU at all. All compositing seems to be done on the CPU which has some undesired effects.

Emerald will only work with Compiz.

---

### Post by 1875 on 2008-04-03
> **Mazza558 said:**
> Actually, is there a lightweight compositor instead of Compiz which is faster?

I'd like to run emerald and some other composited stuff...

[http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/]("http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/")

Can't say I've used it myself but may be useful for you.

---

### Post by Mazza558 on 2008-04-03
> **1875 said:**
> [http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/]("http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/")

Can't say I've used it myself but may be useful for you.

Hmm, thanks.

Only problem is it's quite slow and obviously doesn't support emerald.

---

### Post by 1875 on 2008-04-03
> **Mazza558 said:**
> Hmm, thanks.

Only problem is it's quite slow and obviously doesn't support emerald.

As far as I'm aware you require compiz for Emerald. I would recommend using the fusion icon applet, you can just drop down to Metacity when required, then start up Compiz when ready.

---

### Post by eragon100 on 2008-04-03
Aren't hardy's effects much less than regular compiz ?

---

### Post by Outworlder on 2008-04-03
> **Mazza558 said:**
> Amazing as Compiz is, it is crippled if you attempt to run another 3D application. Vista handles this better, as it temporarily turns off Aero when a fullscreen 3D app is used. Of course, Compiz blows Vista's 3D effects out of the water, but I think it has a long way to go before it can be used all the time, which is a real shame.

Why do you even need to disable Aero to run 3D applications? They run fine even windowed. After all, that's what the whole new "Windows Driver Model" is about, GPU scheduling and all.

I don't have to disable Compiz to run my games either. In fact, turning off Compiz has -no- effect in my framerate.

Using ATI, by chance?

---

### Post by Mazza558 on 2008-04-03
> **Outworlder said:**
> 

Using ATI, by chance?

Yeah, their "new" and "improved" non-xgl driver which comes with Hardy. It's not all that good to be honest, and has loads of problems running Compiz (e.g slow 2d rendering, laggy scrolling, and tearing on windows).

---

### Post by herbster on 2008-04-03
Haven't used Compiz in a while but why not make a shortcut or desktop launcher that does

```
compiz --replace
```

and vice versa with Metacity.

---

### Post by reacocard on 2008-04-03
> **Mazza558 said:**
> Amazing as Compiz is, it is crippled if you attempt to run another 3D application. Vista handles this better, as it temporarily turns off Aero when a fullscreen 3D app is used. Of course, Compiz blows Vista's 3D effects out of the water, but I think it has a long way to go before it can be used all the time, which is a real shame.

The fix for this is 'redirected direct rendering', which is implemented in the new DRI2. This has already been committed upstream, it should trickle down into mainstream by the end of this year/early next year.

See here for more information: [http://hoegsberg.blogspot.com/2008/03/i-just-committed-last-bit-of-dri2-work.html](http://hoegsberg.blogspot.com/2008/03/i-just-committed-last-bit-of-dri2-work.html)

---

### Post by Mazza558 on 2008-04-03
> **reacocard said:**
> The fix for this is 'redirected direct rendering', which is implemented in the new DRI2. This has already been committed upstream, it should trickle down into mainstream by the end of this year/early next year.

See here for more information: [http://hoegsberg.blogspot.com/2008/03/i-just-committed-last-bit-of-dri2-work.html](http://hoegsberg.blogspot.com/2008/03/i-just-committed-last-bit-of-dri2-work.html)

Ah, it's nice to know a fix is on the way. :)

---

### Post by klange on 2008-04-03
> **Mazza558 said:**
> Amazing as Compiz is, it is crippled if you attempt to run another 3D application. Vista handles this better, as it temporarily turns off Aero when a fullscreen 3D app is used. Of course, Compiz blows Vista's 3D effects out of the water, but I think it has a long way to go before it can be used all the time, which is a real shame.
Your "long way to go" is a lot shorter than you think. And it's not so much a "fix on the way" as it is a "fix that's already done and just has a few kinks to work out".
This problem has been solved, pending a major list of bug fixes and integration into the master git repo of the Intel X driver implementation will begin on 'radeon'.  I can attest to the fact that it works, but it crashes and permanently cripples the X server way too often to be truly ready. As soon as the crashes are fixed it's looking pretty good for release in X.org 7.5 (I highly doubt it'll make it into 7.4, but that would be nice.).

**edit**: I find it quite humorous that krh doesn't use any sort of texture filtering in Compiz. That picture would have looked a lot better with it...

---

### Post by Mazza558 on 2008-04-04
I only wish there was a fix for 2D rendering, which is really awful...

---

### Post by reacocard on 2008-04-04
> **Mazza558 said:**
> I only wish there was a fix for 2D rendering, which is really awful...

what do you mean?

---

### Post by Mazza558 on 2008-04-04
> **reacocard said:**
> what do you mean?

There's 2 main problems with the drivers - 

1. Tearing - When watching videos, it's possible to see the frames update, so it shows the top half of one frame and the bottom half of a previous frame...

2. Scrolling Lag/Rendering Lag - Windows visibly render, showing the buttons/window elements slowly. Scrolling is also not instant.

---

### Post by reacocard on 2008-04-04
> **Mazza558 said:**
> There's 2 main problems with the drivers - 

1. Tearing - When watching videos, it's possible to see the frames update, so it shows the top half of one frame and the bottom half of a previous frame...

2. Scrolling Lag/Rendering Lag - Windows visibly render, showing the buttons/window elements slowly. Scrolling is also not instant.

what drivers and card are you using? I'm on intel (915 and X3100) and I can't say I've ever noticed such issues, even back when compiz was still very new.  For the first, have you ensured compiz is  set to sync to vblank in preferences? That's supposed to help with tearing. The second one sounds like it might be an issue with EXA.

---

### Post by Mazza558 on 2008-04-04
> **reacocard said:**
> what drivers and card are you using? I'm on intel (915 and X3100) and I can't say I've ever noticed such issues, even back when compiz was still very new.  For the first, have you ensured compiz is  set to sync to vblank in preferences? That's supposed to help with tearing. The second one sounds like it might be an issue with EXA.

The new non-xgl fglrx ATI drivers which are from the restricted manager in Hardy.

---

### Post by reacocard on 2008-04-04
> **Mazza558 said:**
> The new non-xgl fglrx ATI drivers which are from the restricted manager in Hardy.

Go figure, its ATI. Their drivers are the worst by far right now, both intel and nvidia work well with compiz. This is why proprietary software is bad, you're completely at the manufacturer's mercy.

---

### Post by Mazza558 on 2008-04-04
> **reacocard said:**
> Go figure, its ATI. Their drivers are the worst by far right now, both intel and nvidia work well with compiz. This is why proprietary software is bad, you're completely at the manufacturer's mercy.

Yeah... I might just go back to Xgl if it's possible.

---

### Post by reacocard on 2008-04-04
> **Mazza558 said:**
> Yeah... I might just go back to Xgl if it's possible.

If xserver-xgl is still in the repos all you should have to do is install that and it should still work. Having AIGLX support in the drivers doesn't prevent you from running XGL, it just removes the need.

---

### Post by Mazza558 on 2008-04-04
> **reacocard said:**
> If xserver-xgl is still in the repos all you should have to do is install that and it should still work. Having AIGLX support in the drivers doesn't prevent you from running XGL, it just removes the need.

Unfortunately, this made no difference, and stopped the gnome settings daemon from working. Thanks anyway.

---

### Post by klange on 2008-04-04
> **reacocard said:**
> Go figure, its ATI. Their drivers are the worst by far right now, both intel and nvidia work well with compiz. This is why proprietary software is bad, you're completely at the manufacturer's mercy.

So much so that the 'radeon' driver actually works better (though it lacks some things). Again, with DRI2, this has been fixed, as xv will now render beautifully in all sorts of transformed positions. If you're using X11/xshm, then, yeah, it's going to happen because it's drawing the texture onto the window, not drawing the texture directly. When it's all handled in the right rendering scope there is no tearing.

---

