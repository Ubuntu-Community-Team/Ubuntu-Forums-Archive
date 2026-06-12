---
title: "External display troubles (serp1)"
date: 2008-09-11
forum: System76 Support
---

### Post by Kaloma on 2008-09-11
Okay, why I am only finally seeking help for this now I don't know. I guess because I had something of a workaround, that recently stopped working.

The keyboard combination for switching displays (Fn+F3) has never worked for me since I go the laptop, but I was able to get around this by restarting X after connect the external display (usually a projector for lectures). It was annoying, but bearable.

Then one day, I upgrade to Hardy, and voila! everything worked beautifully, keyboard combos and all! So summer break comes along, I don't use my laptop for lectures for several months, and upon returning to campus I can no longer get it to work. Not only that, but even my old workaround doesn't do the trick. If I restart the machine, I will get some output to the projector screen, but only until X is started.

Various updates to hardy have happened over the past several months, so I don't know what the culprit is. I wonder if it could be related to an nvidia driver update.

It is important to me that I can use my laptop for presentations, so I am hoping someone might be able to help. Thanks.

EDIT: I should mention that I have looked around for help with this issue but haven't come up with the solution. A similar thread for the Darter apparently does not relate to me, because my system doesn't use the asus_acpi module at all.

-Matthew-

---

### Post by thomasaaron on 2008-09-11
Plug in your monitor and go to a terminal and enter this command:

sudo nvidia-settings

You should be able to detect your monitor from there.
Let me know if you need more help with it.

---

### Post by Kaloma on 2008-09-11
You know, I remember trying this now that you bring it up, though I launched the Nvidia Control Panel from the Preferences menu.

I tried it again to refresh my memory, and I can get output to the projector. However, a problem remains: I can only get 640x480 resolution (or a lower 320x240) on the projector, which is definitely not a limit of the hardware (since I used to do this successfully). Thus, only a small portion of my desktop is visible. Perhaps you have heard of this issue?

---

### Post by compholio on 2008-09-12
> **Kaloma said:**
> You know, I remember trying this now that you bring it up, though I launched the Nvidia Control Panel from the Preferences menu.

I tried it again to refresh my memory, and I can get output to the projector. However, a problem remains: I can only get 640x480 resolution (or a lower 320x240) on the projector, which is definitely not a limit of the hardware (since I used to do this successfully). Thus, only a small portion of my desktop is visible. Perhaps you have heard of this issue?

Try visiting the "X Server Display Configuration" and choosing the "Advanced" option.  You should now have control over resolution and panning on your displays.

---

