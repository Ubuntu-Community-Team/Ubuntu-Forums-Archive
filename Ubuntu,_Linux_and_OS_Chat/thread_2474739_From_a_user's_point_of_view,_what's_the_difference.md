---
title: "From a user's point of view, what's the difference between Wayland and X.Org (22.04)?"
date: 2022-05-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Paddy Landau on 2022-05-06
Talking about Ubuntu 22.04…

I know that Wayland has technical improvements over X.Org. However, most "normal" (i.e. non-technical) users don't care about that sort of thing.

From my point of view, there is one glaring difference: Legacy icons don't work in Wayland.

Dropbox's icon (via the deb, not via Flatpak) works. But yad's notification icon is unresponsive on Wayland, whereas it works on X.Org.

Until this is fixed, or I can find an alternative to yad's notification, I have no choice but to use X.Org on 22.04.

On the other hand, I read that some people find that Wayland uses less battery power than X.Org on a laptop.

I was wondering what other differences a user might notice?

---

### Post by sudodus on 2022-05-06
Yes, Wayland is better, or should we say: will be better when it is debugged and polished. But today, several things do no work.  One important problem is the bad cooperation with nvidia graphics. So I switched to Xorg in my Ubuntu 22.04 LTS.

---

### Post by Paddy Landau on 2022-05-06
> **sudodus said:**
> … will be better when it is debugged and polished.
It's good that X.Org works well. I seem to be able to switch between X.Org and Wayland without causing extra problems.

I'm currently testing everything in a virtual machine before making the leap from 20.04 to 22.04. I'm glad that I've done this, because I have found a few gotchas that were easy to research while my current system was running, but that would have been difficult without it.

---

### Post by DuckHook on 2022-05-06
My anecdotal experiences only, but:

[LIST]
[*]I run Wayland exclusively now. On AMD graphics. My experience has been net positive.
[*]It's far more secure. Fewer worries about X giving up my desktop inputs/outputs to some spying scumbag.
[*]On my system at least, it displays better. Switching to X causes not only artifacts but washed out colours. Wayland is brighter, clearer and more consistent.
[*]I can only get 30 Hz on X, but Wayland displays at 60. Go figure.
[*]My setup isn't exactly simple. My LXD containers will only display content if they can properly map a unix socket between container and host. This could have been a deal breaker, but Wayland has handled it nicely. I'm impressed.
[*]Same with Pulse Audio. Mapping container sound to desktop via Wayland has been fine.
[*]A few initial problems for sure, but it's way more stable already and I have no current problems.
[/LIST]
I am aware that nVidia continues to be a problem. Since they are the premier GPU vendor out there, this means that Wayland is a problem for many (if not most). For such people, I can only counsel patience (I know, easy for me to say: I'm on AMD and don't have to deal with the downside).

---

### Post by Paddy Landau on 2022-05-06
> **DuckHook said:**
> … nVidia continues to be a problem. Since they are the premier GPU vendor …
Canonical needs to pay attention to their users. With Firefox taking 10 seconds to start (on a fast machine), and NVIDIA being only partially supported, they're going to alienate a lot of users.

---

### Post by Dennis N on 2022-05-06
> I was wondering what other differences a user might notice? 
There are some things that keep me from using Wayand on my Desktop machines.
In my QEMU/KVM virtual machines, Ubuntu Dock will not appear after hide - moving mouse to edge will not reveal it. A solution would be to always show the dock, rely on the Dash in the activities overview, or use Plank dock. I choose to use Plank, but Plank will not run with Wayland. 
In my QEMU/KVM virtual machines, the cursor hot spot when using Wayland is above and left of the visible cursor. Accurate clicks are not possible.
For those like me who appreciate and want real screensavers to run,  the xscreensaver daemon is unable to blank the screen in Wayland. Xorg is needed for them to run.

---

### Post by grahammechanical on 2022-05-06
Canonical got plenty of criticism when it decided not to support Wayland but to build its own window compositor called Mir. When the Ubuntu phone OS (Unity 8 on Mir) failed to make headway Canonical dropped the plan to use Mir for the desktop and turned to using a Wayland compositor instead. And now some are blaming Canonical for the lack of maturity of Wayland compositors even though Wayland compositors are not Canonical software. Don't blame the Ubuntu developers. Blame the Gnome developers. They are mainly Redhat developers anyway.

[https://docs.fedoraproject.org/en-US/fedora/f34/system-administrators-guide/Wayland/#_additional_resources](https://docs.fedoraproject.org/en-US/fedora/f34/system-administrators-guide/Wayland/#_additional_resources)

> Major desktops such as KDE Plasma and Gnome  have implemented their own Wayland compositors. 

[https://wiki.debian.org/Wayland](https://wiki.debian.org/Wayland)

Regards

---

### Post by #&amp;thj^% on 2022-05-06
> **DuckHook said:**
> My anecdotal experiences only, but:

[LIST]
[*]I run Wayland exclusively now. On AMD graphics. My experience has been net positive.
[*]It's far more secure. Fewer worries about X giving up my desktop inputs/outputs to some spying scumbag.
[*]On my system at least, it displays better. Switching to X causes not only artifacts but washed out colours. Wayland is brighter, clearer and more consistent.
[*]I can only get 30 Hz on X, but Wayland displays at 60. Go figure.
[*]My setup isn't exactly simple. My LXD containers will only display content if they can properly map a unix socket between container and host. This could have been a deal breaker, but Wayland has handled it nicely. I'm impressed.
[*]Same with Pulse Audio. Mapping container sound to desktop via Wayland has been fine.
[*]A few initial problems for sure, but it's way more stable already and I have no current problems.
[/LIST]
I am aware that nVidia continues to be a problem. Since they are the premier GPU vendor out there, this means that Wayland is a problem for many (if not most). For such people, I can only counsel patience (I know, easy for me to say: I'm on AMD and don't have to deal with the downside).

It's like you read my mind. :)
```
Graphics:
  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: qxl resolution: 1920x1080~60Hz
  OpenGL: renderer: llvmpipe (LLVM 13.0.1 256 bits) v: 4.5 Mesa 22.0.1

```
this has been a good run on Gnome now, response is very close to flawless, out side of the few remaining quirks everyone here has noted.
I do have Nvidia, but that's fine as well.
```
CPU: AMD Ryzen 5 4600H with Radeon Graphics (12) @ 3.000 
                                           GPU: NVIDIA GeForce GTX 1650 Ti Mobile 

```

---

### Post by DuckHook on 2022-05-06
> **grahammechanical said:**
> Canonical got plenty of criticism when it decided not to support Wayland but to build its own window compositor called Mir. When the Ubuntu phone OS (Unity 8 on Mir) failed to make headway Canonical dropped the plan to use Mir for the desktop and turned to using a Wayland compositor instead. And now some are blaming Canonical for the lack of maturity of Wayland compositors even though Wayland compositors are not Canonical software. Don't blame the Ubuntu developers. Blame the Gnome developers. They are mainly Redhat developers anyway.
There is an ongoing undercurrent of chronic griping within the Ubuntu ecosystem in which no direction is ever good enough. It's too bad but that's the nature of geeks, I suppose. X has to go at some point. It is kludgy, decrepit and security challenged. It's been held together with spit, prayers and duct tape for years now and can't keep blindly going on as if it is business as usual.
> **1fallen said:**
> …I do have Nvidia, but that's fine as well.
Since I don't use nVidia I'm only going by hearsay, but my understanding is that the nVidia issues crop up when trying to sleep or hibernate. Since I don't use those functions even with AMD, I have no direct experience of such shortcomings.

---

### Post by #&amp;thj^% on 2022-05-06
> **DuckHook said:**
> There is an ongoing undercurrent of chronic griping within the Ubuntu ecosystem in which no direction is ever good enough. It's too bad but that's the nature of geeks,
you should hear the, rants, different thought's, and directions, i witness right now as a tester. (not for the soft hearted)
everyone here keeps me sane.

---

### Post by r3vd3l0x3 on 2022-06-13
Well why dont just exclude Nvidia. As a Tester and Debugger Wayland is not ready. for Beta testing. The apps are already saying it. plus idk if the Xwayland even work. because if it is 'SimpleScreenRecorder' should be running fine but it's not and i hate it. reverting to Xorg manually is a hassle. Hopes the Next update reverts to X11.

Running On:
Form Factor: Laptop
CPU: Intel Celeron N3060 2x 2.40ghz
iGPU: Intel Graphics HD 400(braswell)
RAM: 4GB DDR4
HDD: 500gb (Budget Performance HDD)
WLAN: 2.4GHz 
Resolution: 800p 1366 x 768 (16:9) 40hz-60hz
There's no cooler but there's active cooling on it. (Fans and Heat Sink both pressured for efficiency)

---

### Post by Paddy Landau on 2022-06-13
> **r3vd3l0x3 said:**
> 'SimpleScreenRecorder' should be running fine but it's not…
Ubuntu 22.04 comes with a built-in screencast, a really nice one, that works in both X.Org and Wayland. [Try it out]("https://help.ubuntu.com/stable/ubuntu-help/screen-shot-record.html#:~:text=Make%20a%20screencast&text=Press%20Ctrl%20%2B%20Alt%20%2B%20Shift%20%2B,again%20to%20stop%20the%20recording.")!
> **r3vd3l0x3 said:**
> reverting to Xorg manually is a hassle.
It's dead easy. When you go to the login screen, after you select your user but *before* you enter your password:

[LIST=1]
[*]Select the settings (cogwheel) at the bottom-right corner > Ubuntu on Xorg
[*]Enter your password and log in
[/LIST]
You only have to do this once!

---

### Post by vanadium on 2022-06-13
The one-to-one touch gestures on Wayland constitute a remarkable difference between Wayland and Xorg. The opening of the overview follows the speed of your fingers. It is a nice and spectacularly different experience opening the overview with gestures on Wayland than on Xorg (saw this in action with a live session of Fedora - wow!).

That said, I continue to use Xorg, for three reasons.

1. I critically rely on keyboard automation tools (text snippets and macro's to do repetitive things on websites) and Wayland does not support such functionality (it even does not support application specific global shortcut keys, e.g. a shortcut key to start and stop recording in OBS). It looks like Espanso may fill the gap for text snippets, as it appears to support Wayland now, but else, my first attempts to use "ydotool"

2. Wayland also took away the little control on window positioning a linux user had left. I want new Evince windows (and some others) to always open maximized. Not full screen (there is an option for that), but maximized (there is no option for that). Devilspie2 does the job in a setup-and-forget-about way, but alas, also these tools do not anymore work on Wayland.

3. I setup application shortcut keys that launch an application only if it is not running, else switches to a running instance. You can do that (in Xorg) with wmctrl, but I use jumpapp, a bash script that uses "wmctrl" under the hood. Yes, that does not work anymore under Wayland. This could be worked around by adding/changing keybindings in Gnome Shell to switch to application N on the dash, and better, there is a good extension "run-or-raise", but then, that may stop working on the next version.

---

### Post by Paddy Landau on 2022-06-13
> **vanadium said:**
> 1. … my first attempts to use "ydotool"
I'd not heard of ydotool. There's no man page for it! How are you finding ydotool?
> **vanadium said:**
> 2. Wayland also took away the little control on window positioning a linux user had left…
This is upsetting.
 > **vanadium said:**
> "wmctrl" … does not work anymore under Wayland.
Again, upsetting!

I haven't converted to Ubuntu 22.04 yet (I'm only experimenting with it, and probably won't move my day-to-day work there until the point-1 release), but it looks as though I'll be using X.Org, not Wayland. The nice thing is that you seem to be able to switch between the two without hiccups.

---

### Post by Paddy Landau on 2022-06-13
I've been experimenting further, and of course xdotool and wmctrl, which I depend on for a couple of scripts, don't work at all in Wayland.

The intended replacements also don't work (I can't get ydotool to work).

I've [asked a question]("https://ubuntuforums.org/showthread.php?t=2475972") on the forum.

---

### Post by zebra2 on 2022-06-13
I use Wayland on 22.04 and also 22.10 because Wayland and Gnome 4 is default on those releases.  I did try a X boot a while back just to compare and I really couldn't tell any difference between X and Wayland.  Even the video on X seemed just fine to me.  In the beginning Wayland wasn't supporting a couple of apps that I use and I had to implement work-around's but eventually Xwayland caught up with it all and everything works as needed so I use Wayland exclusively because that is the default. I might add that I don't have a very discriminate or perfectionist mindset so I might be missing something. There is one software that I use that requires my Windows partition and if that was ported to Linux I would be 100% Ubuntu/Gnome/Wayland. Overall, I think the current release is the best it has been since 1986 when I bought my first computer.  Can't wait to see what's next.

---

### Post by Paddy Landau on 2022-06-13
> **zebra2 said:**
> … I really couldn't tell any difference between X and Wayland.
I have certainly found that they look and feel identical. As already discussed, Wayland has some technical problems, but probably nothing that would hold back the "average" computer user.
> **zebra2 said:**
> Overall, I think the current release is the best it has been since 1986 when I bought my first computer.  Can't wait to see what's next.
Ubuntu 22.04 is a polished desktop. It's just a pity that Wayland comes as default when it has such problems.

---

