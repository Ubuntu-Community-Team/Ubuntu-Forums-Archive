---
title: "funny &amp;wierd stuff with libertine containers"
date: 2016-08-01
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-08-01
I am just hacking and playing around with libertine.

 Here is a test I did.

I created 4 containers.
I installed firefox into each contianer.
I ran all instances of firefox, opened up youtube and played the classic hey Jude video, all simutaneously, but a various stages:)

---

### Post by ventrical on 2016-08-01
You can also "pin" each session of firefox to the unity panel, then close, yes CLOSE you sessions and when you click on the icon in the unity8 panel it will open firefox then where you left off, including tabs.. so no more worrying about closing a session and losing tabs :)

regards..

---

### Post by ventrical on 2016-08-01
Google Chrome and firefox running side by side from different containers. Chrome will not start if firefox is running but firefox will start if chromium is running fist. Chromium seems a little flickerty.. but thats chromium :)

regards..

---

### Post by ventrical on 2016-08-01
synaptic will not open at all.

---

### Post by ventrical on 2016-08-01
I was able to install 'sysinfo'  and got some interesting information. I installed sysinfo on container chrome2 (which is the 4th container) I created and so sysinfo reports the hostname as yakkety-4 which is very  interesting I think and is news to me. So we get to take a peek under the hood.


regards..

---

### Post by ventrical on 2016-08-01
This, hopefully, where we will be headed..

[https://ubuntuforums.org/showthread.php?t=2271655&page=4&p=13264665#post13264665](https://ubuntuforums.org/showthread.php?t=2271655&page=4&p=13264665#post13264665)

---

### Post by grahammechanical on 2016-08-01
I would like to see Libertine patched to work on Unity 7 so that all X apps can be run in LXC containers. I would need to be re-written to put the application icon in the Dash and not in the Unity 8 scope. Libertine itself is a snap that runs on both Unity 7 & 8. But doing what I would like would be a distraction from the present task.

Regards.

---

### Post by ventrical on 2016-08-01
> **grahammechanical said:**
> I would like to see Libertine patched to work on Unity 7 so that all X apps can be run in LXC containers. I would need to be re-written to put the application icon in the Dash and not in the Unity 8 scope. Libertine itself is a snap that runs on both Unity 7 & 8. But doing what I would like would be a distraction from the present task.

Regards.

X11 apps was there .. and now it's gone.

Regards..

---

### Post by ventrical on 2016-08-02
bwahahaha .. I can't believe it. My hi-lite for the day:) glxgears running in xterm from container on unity8. They said it couldn't be done :)

regards..

---

### Post by QDR06VV9 on 2016-08-02
> **ventrical said:**
> bwahahaha .. I can't believe it. My hi-lite for the day:) glxgears running in xterm from container on unity8. They said it couldn't be done :)

regards..

Is this with the Nvidia Driver installed?:o

---

### Post by ventrical on 2016-08-02
> **runrickus said:**
> Is this with the Nvidia Driver installed?:o

Nouveau! :)

Maybe I should try Nvidia  :)

regards..

---

### Post by deadflowr on 2016-08-02
> **ventrical said:**
> bwahahaha .. I can't believe it. My hi-lite for the day:) glxgears running in xterm from container on unity8. They said it couldn't be done :)

regards..

curiously, what was the framerate for it?

---

### Post by ventrical on 2016-08-02
> **runrickus said:**
> Is this with the Nvidia Driver installed?:o

There is still the bounce-back to lightdm with nVidia driver installed.
Regards..

---

### Post by QDR06VV9 on 2016-08-02
Yep Uninstalled the Nvidia blob...Unity8 is at least usable now for me.:)

---

### Post by ventrical on 2016-08-02
> **deadflowr said:**
> curiously, what was the framerate for it?

The caveat was that it did not display any framerate. Just the whirling gears. What was noticeable was that as you enlarged the the xterm window the gears would get bigger in a sort of smooth xmir sort of way.  There are a lot of bugs with the current terminal.click which will not not run glxgears. I am trying several differentdeb apps. Some work really well but other just won't work at all , ie; gnome-disk-utility, gnome-system-monitor etc.. but there are plenty of other apps to try out and that work very well.

regards..

edit : btw .. you could not quit the terminal in the usual sense with Ctrl+c or +x. You have to close the xterm window to stop the program..

---

### Post by grahammechanical on 2016-08-02
> I am trying several different deb apps. Some work really well but other  just won't work at all , ie; gnome-disk-utility, gnome-system-monitor  etc..

I am not surprised about that. The container has ubuntu core but does it have Gnome 3 DE? I do not think that it does. I have no proof but I suspect that Unity 8 is its own DE and interacts directly with Mir.

Regards

---

### Post by ventrical on 2016-08-02
> **grahammechanical said:**
> I am not surprised about that. The container has ubuntu core but does it have Gnome 3 DE? I do not think that it does. I have no proof but I suspect that Unity 8 is its own DE and interacts directly with Mir.

Regards

Yes.. I agree. But when running htop I can see the unity-system-compositor and xorg running concurrently. Also upstart and systemd. But I think that is if you have unity8 as the DE and libertine containers running also. We have done a lot of work on the early containers and I liked the concept back then . I like it even more now the way that regular deb apps can run side by side with mir. The mir apps and framework is doing the mir thing that it does while allowing xorg to pop in a portal concurrently which is what we are expecting with convergence. So my meaning is that there is no STOP state with mir while xorg is running and vis a versa. Rather impressive.

regards..

---

### Post by grahammechanical on 2016-08-03
> So my meaning is that there is no STOP state with mir while xorg is running and vis a versa. Rather impressive.

I agree. I learnt something from yesterday's Ubuntu on Air session. Systemd starts & stops the OS services but Upstart is still being used to start & stop user services. It explains why we still see upstart code. But work is being done to make the switch to systemd complete.

Regards.

---

### Post by ventrical on 2016-08-03
I got a bunch of libclucene... packages and now the graphics in containers are gone buggy. The glxgears looks like it has astigmatism!. it must be a mir refit. 
Regards..

---

### Post by ventrical on 2016-08-03
As unity8 , mir and libertine containers develop you can expect mild to total breakage at any time.  If you have a good working install of unity8+libertine then do not upgrade it.  Start another fresh install if you have to.  This way you can epxperiement with a working libertine for a little while to see what .deb packages work for you.

Regards..

---

### Post by ventrical on 2016-08-03
You can go out of Desktop mode and get a full screenpanel thingy which is kewl and weird (or effervescent). Notice when out of desktop mode the unity8 panel icos are repositioned at the bottom of the panel.

---

### Post by ventrical on 2016-08-05
GImp works pretty good.

Ok.. won't upload attatchment.

regards..

---

### Post by ventrical on 2016-08-20
ehehehehehe .... I really did it now :)  As I am going along , trying gout different apps I tried this little program called evilwm. It is a minimalist windows manager. Installed and then lost all my scopes. pppppffft! .. just like that ! But still have unity7.

---

