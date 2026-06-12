---
title: "Mouse gestures in quantal"
date: 2012-09-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Arlanthir on 2012-09-18
I read in [https://wiki.ubuntu.com/Multitouch]("https://wiki.ubuntu.com/Multitouch") that Unity supports touchpad gestures out of the box.

However, I am unable to use any of those besides two-finger scrolling (even after installing ginn). So I decided to search around for gesture support diagnostic and tutorials and keep finding articles about utouch. Unfortunately, while the utouch package itself is available in the quantal repositories, the dependencies are not anymore (see [http://packages.ubuntu.com/search?keywords=utouch&searchon=names&suite=all&section=all]("http://packages.ubuntu.com/search?keywords=utouch&searchon=names&suite=all&section=all")).

So, does Unity still support touchpad gestures? How would I go to enable or diagnose them?

---

### Post by semperfried76 on 2012-09-18
I'm on an Asus N73-SV, and I'm having the exact same issue, no utouch available, only two-finger multitouch (and only scrolling, no pinch-zoom or anything cool like that). I can get three-finger recognition, but only tapping, and all it does is simulate right-click (FAIL). Even if I install easystroke, I cannot get gestures to be recognized. Under Windows 7, all multitouch features were recognized.

---

### Post by Arlanthir on 2012-09-18
> **semperfried76 said:**
> I'm on an Asus N73-SV, and I'm having the exact same issue, no utouch available, only two-finger multitouch (and only scrolling, no pinch-zoom or anything cool like that). I can get three-finger recognition, but only tapping, and all it does is simulate right-click (FAIL). Even if I install easystroke, I cannot get gestures to be recognized. Under Windows 7, all multitouch features were recognized.

Out of curiosity, how do you get the three-finger tap? My three-finger tap does nothing, I can simulate a right click with a two-finger tap only.

---

### Post by semperfried76 on 2012-09-18
Honestly, I don't know, I discovered it worked by accident today. I've been trying to enable three-finger swiping for workspace switching (like on OSX) and not having any luck. I'd also like to get pinch-zoom working.

---

### Post by semperfried76 on 2012-09-18
Have you tried using easytstroke? I've heard that some have had some luck with it (not me, but I may be doing it wrong...)

---

### Post by Arlanthir on 2012-09-18
> **semperfried76 said:**
> Have you tried using easytstroke? I've heard that some have had some luck with it (not me, but I may be doing it wrong...)

I did now. Well, I don't think easystroke is designed to add support for multi-finger gestures, just **mouse** gestures while holding a specific button. It does work for that, though (I used left shift as my gesture button).

---

### Post by semperfried76 on 2012-09-18
> **Arlanthir said:**
> I did now. Well, I don't think easystroke is designed to add support for multi-finger gestures, just **mouse** gestures while holding a specific button. It does work for that, though (I used left shift as my gesture button).

That's what I thought, yet all the googling I did for "multitouch gesture support ubuntu" kept throwing it at me, so I thought I'd give it a try. Oh well...

---

### Post by semperfried76 on 2012-09-19
Bump. Still looking for answers.

---

### Post by semperfried76 on 2012-09-20
Any Ubuntu team devs want to shed some light on this issue? as of yesterday, multitouch support is still being claimed, but honestly, two-fingered scrolling is not really that different an experience from edge scrolling, and I can only see myself using three-finger tap for context menus if my trackpad's buttons stop working- 
As of right now, none of this :
[QUOTE=https://wiki.ubuntu.com/Multitouch]
3 finger pinch to maximize/restore windows
3 finger press and drag to move window
3 finger touch to show grab handles
4 finger swipe left/right to reveal launcher (if the dock autohide is enabled)
4 finger tap to open dash
[/QUOTE]
is working.

---

### Post by semperfried76 on 2012-09-20
I'd also like to hear if anyone else has gotten multitouch working on similar hardware, and how they did it- I'm using an Asus N73-SV with an Elantec PS/2 Touchpad- a device which gets full multi-touch support under Windows 7. I know the touchpad CAN recognize multi-touch because it will do 3-Finger tap and 2-finger scrolling, but so far have found no options to actually configure  multitouch to do anything useful (ie, anything I couldn't do with a regular single-touch touchpad and a mouse-button).

---

### Post by Mr. Picklesworth on 2012-09-20
The gestures are working on my XPS 13 with the Sputnik kernel (patched Ubuntu kernel with a custom driver for the Cypress touchpad). Are you sure the hardware was supported before? Try running geisview and see what happens.

---

### Post by Arlanthir on 2012-09-20
> **Mr. Picklesworth said:**
> The gestures are working on my XPS 13 with the Sputnik kernel (patched Ubuntu kernel with a custom driver for the Cypress touchpad). Are you sure the hardware was supported before? Try running geisview and see what happens.

Thank you for the tool name, it required the installation of the geis-tools packages but that one fortunately existed in the repositories.

geis-view gives me a device touches value of only 2, which seems to indicate that my touchpad lacks the hardware characteristics to detect more than two fingers or the touchpad drivers simply don't support it. I will investigate this further, trying to find what exact model of touchpad I have and its hardware capabilities.

By any chance, do you know if it's possible to configure two-finger drag gestures instead of defaulting to a right-click?

---

### Post by semperfried76 on 2012-09-20
> **Mr. Picklesworth said:**
> The gestures are working on my XPS 13 with the Sputnik kernel (patched Ubuntu kernel with a custom driver for the Cypress touchpad). Are you sure the hardware was supported before? Try running geisview and see what happens.
Here's my output from geisview:
[IMG]http://i.imm.io/F1tc.png[/IMG]
Oddly enough, after running Geisview, 3-finger tap does nothing now, and two-finger tap does right-click menu. Also, two-finger (supposed to be three?) pinch-zoom is now working on images, but not on anything else :(  In other words, geis killed my meager 3-finger support entirely.

---

### Post by semperfried76 on 2012-09-20
Isn't multi-touch gestures supposed to be using GINN in quantal (Gesture Injector: No-GEIS, No-Toolkits)? Why do I still need GEIS?

---

### Post by semperfried76 on 2012-09-20
Here is my output from GINN:
Using wishes file /etc/ginn/wishes.xml
```

ginn
 global
  wish
   action
    trigger
    button
  wish
   action
    trigger
    button
  wish
   action
    trigger
    key
  wish
   action
    trigger
    key
  wish
   action
    trigger
    key
  wish
   action
    trigger
    key
  wish
   action
    trigger
    key
  wish
   action
    trigger
    key
 applications
  application
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
  application
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
  application
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
  application
   wish
    action
     trigger
     button
   wish
    action
     trigger
     button
  application
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
  application
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
  application
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
Button : 4 Button : 5 Button : 4 Button : 5 
Gestures subscribed:
Pinch,touch=2
Drag,touch=2
Rotate,touch=2
Pinch,touch=3
Tap,touch=4
Pinch,touch=4
Drag,touch=4
error subscribing to gestures
```

---

### Post by Arlanthir on 2012-09-20
> **semperfried76 said:**
> Here is my output from GINN:
<snip>
...
Drag,touch=4
error subscribing to gestures

I confirm this behavior. Seems like this bug:
[https://bugs.launchpad.net/ubuntu/+source/ginn/+bug/985121]("https://bugs.launchpad.net/ubuntu/+source/ginn/+bug/985121").

Though it seems some people there have multitouch gestures with 3 and 4 fingers, as long as they're the stock Unity ones.

I have no zoom-thingie whatsoever, just plain old two-click right menu. Two-finger scrolling also works if I enable it.

---

### Post by semperfried76 on 2012-09-20
> **Arlanthir said:**
> I confirm this behavior. Seems like this bug:
[https://bugs.launchpad.net/ubuntu/+source/ginn/+bug/985121]("https://bugs.launchpad.net/ubuntu/+source/ginn/+bug/985121").

Though it seems some people there have multitouch gestures with 3 and 4 fingers, as long as they're the stock Unity ones.

I have no zoom-thingie whatsoever, just plain old two-click right menu. Two-finger scrolling also works if I enable it.

Wow. I'm going to try it in Gnome shell, Loath as I am to give up Unity (I just don't care for how huge everything is in gnome shell, it would annoy me even on a tablet...).

---

### Post by semperfried76 on 2012-09-21
Tried the gestures in gnome-shell, no luck. Still only had the same ones as in Unity.

---

### Post by jbicha on 2012-09-21
> **semperfried76 said:**
> Isn't multi-touch gestures supposed to be using GINN in quantal (Gesture Injector: No-GEIS, No-Toolkits)? Why do I still need GEIS?

No, geis is pre-installed; ginn is in universe now. Everything in the default Ubuntu install has to be in main.

For the rest of you, did multi-touch gestures used to work for you in Precise but stopped working in Quantal? Or are you just trying something new.

---

### Post by Arlanthir on 2012-09-21
> **jbicha said:**
> No, geis is pre-installed; ginn is in universe now. Everything in the default Ubuntu install has to be in main.

For the rest of you, did multi-touch gestures used to work for you in Precise but stopped working in Quantal? Or are you just trying something new.

I'm just trying something new, I wanted at the least to customize two-finger gestures, but everything seems to point at utouch that has missing dependencies in quantal. In light of what you said I'll probably try some older release to see the results.

---

### Post by semperfried76 on 2012-09-25
> **jbicha said:**
> No, geis is pre-installed; ginn is in universe now. Everything in the default Ubuntu install has to be in main.


You guys need to update your wiki, then.

[QUOTE=http://wiki.ubuntu.com/Multitouch]Ginn is installed by default, and provides users with the ability to add gestures for applications that do not directly support gestures. Ginn supports everything from photo viewers and text editors to window managers![/QUOTE]

---

### Post by semperfried76 on 2012-09-25
[QUOTE=http://wiki.ubuntu.com/Multitouch]Unity has support for some system gestures, and you can try those out right away. Here's a list:

3 finger pinch to maximize/restore windows
3 finger press and drag to move window
3 finger touch to show grab handles
4 finger swipe left/right to reveal launcher (if the dock autohide is enabled)
4 finger tap to open dash
Some applications support 2 finger gestures. However, note that 2 finger gestures require extra setup for touchpads in Ubuntu.[/QUOTE]

I also propose that this section of the wiki be edited or removed entirely, it's misleading to say that these features are supported, they should at most be listed as "possible".

---

### Post by semperfried76 on 2012-09-25
Is there any reason behind the removal of utouch from the repos (if geis is installed by default, I'm assuming this was a rename, am I right?) I've tried installing touchegg to get the gestures working, but all the utouch packages it requires have been deprecated.

---

### Post by cariboo on 2012-09-25
You can edit the wiki pages yourself, use you Launchpad login.

---

### Post by semperfried76 on 2012-09-26
> **cariboo907 said:**
> You can edit the wiki pages yourself, use you Launchpad login.

Done, thanks cariboo907.

---

### Post by semperfried76 on 2012-09-27
Still no guidance? Pretty Please?

---

### Post by thorbsd on 2012-10-02
> **Mr. Picklesworth said:**
> The gestures are working on my XPS 13 with the Sputnik kernel (patched Ubuntu kernel with a custom driver for the Cypress touchpad). Are you sure the hardware was supported before? Try running geisview and see what happens.

I just wanted to add that I'm using an XPS15z with the Sputnik kernel on 12.10 beta1, and 3/4 button gestures do not work. The only thing that works is 2-button vertical and horizontal scroll.

---

