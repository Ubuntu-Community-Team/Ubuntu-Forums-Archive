---
title: "Unity Continuity for Ubuntu 17.10"
date: 2017-09-28
forum: Ubuntu, Linux and OS Chat
---

### Post by xabaom on 2017-09-28
Hi people.

Considering Unity won't be the standard interface in Ubuntu 17.10, I would like to know if Unity will be continued?

I thought about the possibility of some enthusiasts rewrite Unity code for Wayland without Compiz dependencies.

Someone knows some news in this way?

Hugs and Cheers.

---

### Post by xabaom on 2017-09-28
Some answers:

Unity Alternative for Ubuntu 17.10 and after that
[https://askubuntu.com/questions/922808/unity-alternative-for-ubuntu-17-10-and-after-that](https://askubuntu.com/questions/922808/unity-alternative-for-ubuntu-17-10-and-after-that)

Is there a way to install Unity 7 or 8 in Ubuntu 17.10?
[https://askubuntu.com/questions/956025/is-there-a-way-to-install-unity-7-or-8-in-ubuntu-17-10](https://askubuntu.com/questions/956025/is-there-a-way-to-install-unity-7-or-8-in-ubuntu-17-10)

Thanks.

---

### Post by rosswmcgee on 2017-10-01
I switched to kde plasma using Unity but also using Antergos Plasma. After getting acquainted with Plasma I see no advantage to Unity. If I want a program or file I just right click on the desktop
a window opens and I type in what I want. Example type sol and Solitaire appears as an option. I never like gnome, but in Antergos as well  as unity I can use any desktop I want be it Mate or what ever you prefer. Not only that Plasma seems more stable, the libre office works better, oh and I like the fact that that when using calc it will open in the same spot I left it, etc sold on Plasma after
using it for 3 months I don't even bother with Unity.

---

### Post by vasa1 on 2017-10-01
Please keep this thread on the rails even though it's in Chat. Thanks!

---

### Post by grahammechanical on 2017-10-07
> Is there a way to install Unity 7 or 8 in Ubuntu 17.10?

Unity 7 = Yes. I have done it. I used Synaptic Package Manager to install Unity7 and all its dependencies. But something was missing. The UI used the Adwaita theme and it looked horrible. The UI would freeze when resizing application windows. The fix was to also to install ubuntu-desktop. That will get the familiar look and smoothness of Unity 7. As well as the Unity system utilities to replace the Gnome utilities.

Unity 8 = Not a good idea to try. Unity 8 was built to run on the MIr display manager and it never progressed far from being a UI for a phone or tablet.

How long can we use Unity 7? How long will it be in the repositories? It is there in 17.10 but will it be in the 18.04 archives? I am thinking that to keep using Unity 7 a person would have two options.

1) Install Ubuntu 17.04 (to get Unity) and then continue upgrading to 17.10 & 18.04 and hope the upgrade to 18.04 does not remove Unity.
2) Install 17.10 and add Unity 7 + ubuntu-desktop and then upgrade to 18.04.

Regards

---

### Post by mastablasta on 2017-10-09
since i never really used Unity i am not sure what was so special about it (other than HUD + global ? menus).

from what it seems to me the Gnome in Ubuntu is going to look very similar. after they get the look, surely they will be able to move the most used features of unity to it.

I think the look itself is easy enough to do (i did something similar to XFCE back in the days). it's the extra features that users might miss. while in my opinion no one from the users is really interested in background or how it all works :)

---

### Post by xabaom on 2017-10-17
Hi Ubuntu people.

Follow a little resume about the next Unities:

Unity 7 Continuity: Artemis Project
Wayland + Qt + Swiftly. Looks great.
[https://artemis-project.github.io](https://artemis-project.github.io)

Unity 8 Continuity: YUnity
UBPorts + MIR acting as a Wayland client
[https://yunit.io](https://yunit.io)

And I believe I can predict the future: Ubuntu Artemis 18.04...

Hugs and Cheers.

---

### Post by ventrical on 2017-10-19
> **xabaom said:**
> Hi people.

Considering Unity won't be the standard interface in Ubuntu 17.10, I would like to know if Unity will be continued?

I thought about the possibility of some enthusiasts rewrite Unity code for Wayland without Compiz dependencies.

Someone knows some news in this way?

Hugs and Cheers.

unity7 will be in the /universe for 18.04 for installation and testing. if all goes well it may become an offical flavor.

regards..

---

### Post by Chanath on 2017-10-19
> **xabaom said:**
> Hi Ubuntu people.

Follow a little resume about the next Unities:

Hugs and Cheers.

If you search around in Sourceforge, you might find a Unity Remix...

---

### Post by xabaom on 2017-10-23
> **Chanath said:**
> If you search around in Sourceforge, you might find a Unity Remix...

Great! Thank you! 

Unity 7 Remix Project
[https://sourceforge.net/projects/unity7sl/](https://sourceforge.net/projects/unity7sl/)

---

