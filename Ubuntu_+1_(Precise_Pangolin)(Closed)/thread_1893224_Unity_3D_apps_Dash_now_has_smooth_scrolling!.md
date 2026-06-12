---
title: "Unity 3D apps Dash now has smooth scrolling!"
date: 2011-12-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-12-09
Way to go Team Ubuntu ! I was wondering if  they would ever get the Unity 3D desktop apps dash to scroll like Unity 2D. I just did a major update and , voila' .. smooth scrolling in Unity 3D!!

Bravo!

---

### Post by ventrical on 2011-12-10
Wow... not so on another system. The latest update even made it more clunkier to use the scroll-wheel!
:(

---

### Post by coffeecat on 2011-12-10
Could this be a graphics driver problem? What are the two in the two systems?

I've not noticed this issue, but that's perhaps because so far I've been testing Pangolin on a laptop and I had to plug a mouse in to test this. I'm getting smooth scrolling in the dash in Pangolin's Unity 3d with Intel graphics.

Out of interest, were you seeing this in Oneiric's Unity 3d? I've not seen poor dash scrolling in Oneiric either.

---

### Post by fjgaude on 2011-12-10
Dash scrolling works just fine with my Intel video, always has as far as I can recall.

---

### Post by ventrical on 2011-12-10
> **coffeecat said:**
> Could this be a graphics driver problem? What are the two in the two systems?

I've not noticed this issue, but that's perhaps because so far I've been testing Pangolin on a laptop and I had to plug a mouse in to test this. I'm getting smooth scrolling in the dash in Pangolin's Unity 3d with Intel graphics.

Out of interest, were you seeing this in Oneiric's Unity 3d? I've not seen poor dash scrolling in Oneiric either.

On this current Precise transition I have the:

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary)

as my display driver .. but I am going to have to re-install FF because now there is a big issue with FF.
^^^^^^^^^^^^^^^^^^
that prob solved.

The laptop is acer 64bit with Ati Radeon Express 1250. Everything else worked fine .. also have two towers with NVidia  graphics .. always had the clunky scrolling with Unity 3D. I'll try to put up a video later about this.

---

### Post by kaldor on 2011-12-10
I'm using the NVIDIA blob and the scrolling has always been useless for me. I rarely click around in the Dash because it's just too slow. Just as bad in Unity 2d. GNOME Shell is better but it still lags. It seems like the proprietary drivers cause the most issues, since it looked fine on the live USB session (Nouveau driver).

I'll give it a go on the open source Radeon driver later and see how it works.

Side note: why is it that composited/3d desktops on Linux are usually clunky and slow, whereas in OS X and Windows 7 it doesn't interfere? I can't even attempt to play games on Linux unless I disable compiz (huge performance hit if I leave it on), and I have a fairly decent and modern PC. 

It's a little bit of a letdown because I really like the direction the Linux desktop is going, but can't use these new things on a regular basis because of the issues I mentioned. Not complaining, it's a genuine question :)

---

### Post by ventrical on 2011-12-10
Perhaps I ought to be more specific. The 3D on all my Precise installs work just great. I am just making a point about  using the mouse <scroll-wheel> in the Unity 3D apps dash. I can get smooth scrolling if I use the side<pull-bar> .. etc.. but not with mouse wheel. However in Unity 2D that is not a problem. Gnome Shell works great also .. Cairo etc.. I'm just beta testing Unity 3D and submitting notes on it.

Thanks for your input.

---

### Post by MacUntu on 2011-12-10
There was no Unity update for over six weeks. ;)

---

### Post by ventrical on 2011-12-11
> **MacUntu said:**
> There was no Unity update for over six weeks. ;)

Umm.... Ok.. :)  but I still only have the smooth scrolling on one  system which is an Acer Extensa 4420 (64bit) PP

---

### Post by ventrical on 2011-12-11
Clunky scroll with Unity 3D:

[http://www.youtube.com/watch?v=x324PADu3wQ](http://www.youtube.com/watch?v=x324PADu3wQ)

Smooth scroll with Unity 2D:

[http://www.youtube.com/watch?v=7lRFmrsEEMc](http://www.youtube.com/watch?v=7lRFmrsEEMc)

---

### Post by effenberg0x0 on 2011-12-11
> **ventrical said:**
> Clunky scroll with Unity 3D:

[http://www.youtube.com/watch?v=x324PADu3wQ](http://www.youtube.com/watch?v=x324PADu3wQ)

Smooth scroll with Unity 2D:

[http://www.youtube.com/watch?v=7lRFmrsEEMc](http://www.youtube.com/watch?v=7lRFmrsEEMc)


Wild guessing:

At Ubuntu Session (3D): 
On ccsm/ubuntu_unity_plugin, deactivate Blur totally. 
sudo service lightdm restart / select Ubuntu (3D) Session. Still clunky?

Also check at... 
cd /usr/lib
ls -la libGL*

cd /usr/lib32
ls -la libGL*

...if soft-links are not broken _and_ pointing to correct nvidia lib*.so, or if you may have some other mesa GL in-between and/or broken links. If so manual fix is needed (remove soft-links, make new links point to nvidia lib*290*.so, restart lightdm service, etc.

---

### Post by ventrical on 2011-12-11
It works much better. In this one instance I am using ATi card. I did not know we could get rid of that blur :) 

thanks ! :)

ventrical@ventrical-P4M266A-8237:~$ cd /usr/lib
ventrical@ventrical-P4M266A-8237:/usr/lib$ ls -la libGL*
lrwxrwxrwx 1 root root     18 Nov 18 19:20 libGLEWmx.so.1.5 -> libGLEWmx.so.1.5.2
-rw-r--r-- 1 root root 251144 Aug  4 18:51 libGLEWmx.so.1.5.2
lrwxrwxrwx 1 root root     16 Nov 18 19:20 libGLEW.so.1.5 -> libGLEW.so.1.5.2
-rw-r--r-- 1 root root 283912 Aug  4 18:51 libGLEW.so.1.5.2
------------------------------

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary)

---

### Post by mc4man on 2011-12-11
At least here scrolling in unity-3d works fine but is 'better' in unity-2d. The difference would be similar to the difference in FF - unity-3d is like normal scrolling in FF, unity-2d is like FF with 'smooth scrolling' option enabled

What are you using now for the unity-3d Dash, no blur or static blur?
(i preferred the no blur for the short time in OO when it used a solid color background. That was broken & never fixed or never intended & fixed, either way I find the current 'no blur' to be worthless

---

### Post by ventrical on 2011-12-11
> **mc4man said:**
> At least here scrolling in unity-3d works fine but is 'better' in unity-2d. The difference would be similar to the difference in FF - unity-3d is like normal scrolling in FF, unity-2d is like FF with 'smooth scrolling' option enabled

What are you using now for the unity-3d Dash, no blur or static blur?
(i preferred the no blur for the short time in OO when it used a solid color background. That was broken & never fixed or never intended & fixed, either way I find the current 'no blur' to be worthless

  The scroll in Unity 2D has this very "springy" type effect.. sort of like how a video slot machine would scroll - it is very lucid. I disabled the 'blur' but then when I moved windows about they got all milky and fuzzy , but the scrolling did work a bit better for 3D.

  I am just curious because Mark Shuttleworth had more or less declared that he is very intimate as a dev with Unity desktop..etc... and I can only wonder why a lot of legacy and ancient bugs are still allowed to persist with Precise. (no pun intended :)

---

### Post by mc4man on 2011-12-11
> **ventrical said:**
> The scroll in Unity 2D has this very "springy" type effect.. sort of like how a video slot machine would scroll - it is very lucid. I disabled the 'blur' but then when I moved windows about they got all milky and fuzzy , but the scrolling did work a bit better for 3D.

  I am just curious because Mark Shuttleworth had more or less declared that he is very intimate as a dev with Unity desktop..etc... and I can only wonder why a lot of legacy and ancient bugs are still allowed to persist with Precise. (no pun intended :)

You may find that the static blur option works the best, keeping in mind that it's set the first time the Dash is opened, then that is what's used the the rest of the session so take some care on what is opened over.

Otherwise they've been fixing things like this, apparently some "testers" are confused by the nautilus launcher icon having an H on it, never mind that it always opens the Home folder.
(and certainly there is nothing 'confusing' about the unity panel always reporting "Home Folder" no matter where nautilus is when using unmaxed windows

[https://bugs.launchpad.net/ayatana-design/+bug/874265](https://bugs.launchpad.net/ayatana-design/+bug/874265)

---

### Post by effenberg0x0 on 2011-12-12
I'm far from being any sort of specialist in Graphics/GPUs and OpenGL performances, but I think there probably is some way to test / measure what the impact of opening the dash / each blur routine on the system? Does GPU cycles increase significantly? VGA Memory usage? What can we measure? Maybe a good way to start monitoring this (if it is improving / getting worse) until PP release is to establish some numbers / range / what would be a decent performance, etc? I'd like to hear from someone with more experience in graphics.

---

