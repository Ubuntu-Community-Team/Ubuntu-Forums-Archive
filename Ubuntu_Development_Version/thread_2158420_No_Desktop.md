---
title: "No Desktop"
date: 2013-06-28
forum: Ubuntu Development Version
---

### Post by Sef on 2013-06-28
My desktop has disappeared. What can I do to get it back?  Removing the desktop and reinstalling it does not work.

---

### Post by ventrical on 2013-06-29
> **Sef said:**
> My desktop has disappeared. What can I do to get it back?  Removing the desktop and reinstalling it does not work.

Same here on a new, fresh install after updates. I just went to terminal (alt+ctrl+F1) and  :

sudo service lightdm restart

and I was able to log in.

---

### Post by cariboo on 2013-06-29
After the upgrade to the 3.10 kernel, I got an error message stating there was an error compiling the Nvidia 310 driver, I purged the Nvidia drivers, and am currently running nouveau, with apparently very little problem, although I did get a hard lockup about ½ an hour ago, I was running Chromium, Thunderbird, Synaptic, Digikam, Qbittorrent and Gimp. so it could have been any one of them that caused it.

---

### Post by mc4man on 2013-06-29
Re: nvidia &  3.10 kernel, nvidia-319 should be fine, others likely haven't been updated yet (those that  will
If not above then maybe some logs (unless 'no desktop'  means a background that can't be acted on, then enable file manager handling the Desktop in dconf

---

### Post by cariboo on 2013-06-29
+1 to what mc4man said, I installed nvidia-319, and everything is ok.

```
cariboo@alexis:~$ /usr/lib/nux/unity_support_test -p -f
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 210/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 319.32

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

---

### Post by mc4man on 2013-06-29
Before returning to nouveau did notice here that the 3.10/319 combo has awfult restarts, could be local , hopefully not an issue with 3.10/nouveau

---

### Post by grahammechanical on 2013-06-29
> [COLOR=#000000]Same here on a new, fresh install after updates[/COLOR]

For me yesterday's daily image would not install. Ubiquity crashed in the three ways of installing. Also with yesterday's Kubuntu image.

If we only get the background wallpaper then right click select Change Desktop Background and we are at System Settings. I assume that we know how to get to Additional Drivers from there.

I often give that advice out in the wilds of the forum.

Regards.

---

### Post by ventrical on 2013-06-29
> **grahammechanical said:**
> For me yesterday's daily image would not install. Ubiquity crashed in the three ways of installing. Also with yesterday's Kubuntu image.

If we only get the background wallpaper then right click select Change Desktop Background and we are at System Settings. I assume that we know how to get to Additional Drivers from there.

I often give that advice out in the wilds of the forum.

Regards.

 I used an earlier .iso of saucy that was working and updated/dist-upgrade. I'll have to zsync that  and see whats up with the daily.

---

### Post by grahammechanical on 2013-06-29
> **ventrical said:**
> I used an earlier .iso of saucy that was working and updated/dist-upgrade. I'll have to zsync that  and see whats up with the daily.

Today' image has the same problem. Ubiquity crashes BrokenPipeError in command (): ] Err no32] Broken Pipe.

It is a pity. I was going to put in an install of all the flavours and set them up on Xmir just to prove it could be done. There is a video somewhere showing it working on all the flavours. I thought it might be interesting to see how they develop. Kubuntu devs have already decided to stick with Wayland. I wonder how long they will have to wait? I think the Ubuntu Studio will be interesting to watch. The devs there are going to give users the option of choosing which User Interface to choose at log in. I am curious as to how that will work on Xmir.

---

### Post by QDR06VV9 on 2013-06-29
> **grahammechanical said:**
> Today' image has the same problem. Ubiquity crashes BrokenPipeError in command (): ] Err no32] Broken Pipe.

It is a pity. I was going to put in an install of all the flavours and set them up on Xmir just to prove it could be done. There is a video somewhere showing it working on all the flavours. I thought it might be interesting to see how they develop. Kubuntu devs have already decided to stick with Wayland. I wonder how long they will have to wait? I think the Ubuntu Studio will be interesting to watch. The devs there are going to give users the option of choosing which User Interface to choose at log in. I am curious as to how that will work on Xmir.

I have 2 installs one KDE & Gnome-Shell
But Yes I noticed that KDE pulled wayland in, did not notice it on Gnome-Shell though?
But everything is going real smooth here with all updates.
Kernel 3.10-rc7 & Nividia 319.

---

### Post by ventrical on 2013-06-29
I zsynced todays daily (desktop-i386) and it works like a champ. (on one older machine). Performance may vary on different machines of cuurse.

---

### Post by Sef on 2013-06-30
Got my desktop back.  Since I could always get the terminal (with ctrl, alt and T), I typed in ```
sudo update-manager -d
``` and i opted for the partial upgrade after trying continue.  After the partial upgrade completed, I had to reboot, and upon starting, i had my desktop back.
[B]

[SIZE=4][[COLOR=#ff0000]Warning: Partial updates are not recommended.[/COLOR]]("https://wiki.ubuntu.com/U%2B1/partial_upgrade")[/SIZE]  [COLOR=#ff0000][/COLOR][/B]

---

### Post by VinDSL on 2013-06-30
> **Sef said:**
> **[SIZE=4][[COLOR=#ff0000]Warning: Partial updates are not recommended.[/COLOR]]("https://wiki.ubuntu.com/U%2B1/partial_upgrade")[/SIZE]  [COLOR=#ff0000][/COLOR]**
True, for the most part.  Best analogy I can come up with is...

Removing tree stumps from fields using dynamite isn't recommended either.  But, sometimes it's necessary.  ;)

Glad to hear you got your desktop back.

I wanted to mention (if someone hasn't already) if I let the file manager handle my desktop, it disappears.   When I don't allow it, it comes back.  As a matter of fact.  I can turn it off n' on via gnome-tweak-tool and watch my desktop appear/disappear on the fly.  It's pretty amazing to see, really.

Just saying...

---

