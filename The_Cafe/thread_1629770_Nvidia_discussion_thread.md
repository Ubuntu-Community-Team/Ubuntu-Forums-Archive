---
title: "Nvidia discussion thread"
date: 2010-11-24
forum: The Cafe
---

### Post by Oxwivi on 2010-11-24
I'm creating this thread to discuss issues faced by Nvidia users in the Linux world.

The most pressing issue in my mind is Nvidia's stance on Wayland. They've already announced that they will not support it, which is concerns me because Ubuntu is going to use Wayland in the future, what of us?

The second thing is Compiz. Compiz requires Nvidia drivers, which we can't install during Ubuntu installation, so we won't be able to use Unity right off the bat with Natty. I don't like the idea of using GNOME-Shell just to install the drivers.

And finally, a little papercut - before driver installation I have the graphical loading screen - y'know that Ubuntu logo with the four dots. But after installing the driver the logo is replaced by monospace ASCII-type characters. Don't like that.

So Nvidia users, speak up!

---

### Post by surfer on 2010-11-24
i had a lot of trouble lately with an ubuntu 10.04 installation and my nvidia card. [here]("http://ubuntuforums.org/showthread.php?t=1623870")'s the thread that at least answered my questions for this one...

but the questions you address... makes you think, doesn't it?

---

### Post by smellyman on 2010-11-24
Wouldn't worry about it now.  Wayland is a long way off.

They did not say they will not support it.  It was also one dude saying they have no plans on supporting Wayland which I am sure is 100% true.  They have no plans to support Wayland.....now.

Fedora and Ubuntu are on board now and as we get farther down the line Nvidia will look into it.  As I bet they are right now.

---

### Post by Spice Weasel on 2010-11-24
Doesn't Ubuntu use Plymouth for its splash screen? I could never get it to work with a Nvidia card either.

---

### Post by everytimeref on 2010-11-24
Gave up trying to install 10.10 on my old laptop with a 4200go graphic card there were loads of graphical glitches with the older driver.

The new Plymouth manager has helped with the splash screens on both my laptop and my desktop running a 7600gs
see OMGubuntu for the link.
[http://www.omgubuntu.co.uk/2010/11/plymouth-manager-lets-you-change-boot-theme-resolution-in-ubuntu/](http://www.omgubuntu.co.uk/2010/11/plymouth-manager-lets-you-change-boot-theme-resolution-in-ubuntu/)

If Ubuntu is now going to require Compiz out of the box then the drivers to run Compiz will have to be installed at installation or there won't be anything to see...

---

### Post by Oxwivi on 2010-11-24
> **everytimeref said:**
> If Ubuntu is now going to require Compiz out of the box then the drivers to run Compiz will have to be installed at installation or there won't be anything to see...
There will be GNOME-Shell to see, or the current GNOME interface, they'll still be supported.

---

### Post by Oxwivi on 2010-11-24
> **smellyman said:**
> Wouldn't worry about it now.  Wayland is a long way off.

They did not say they will not support it.  It was also one dude saying they have no plans on supporting Wayland which I am sure is 100% true.  They have no plans to support Wayland.....now.

Fedora and Ubuntu are on board now and as we get farther down the line Nvidia will look into it.  As I bet they are right now.
As far as I know, they don't have any 'plans to support it'. They might look into it in the future, but Linux is minority, Wayland is even more of a minority within Linux...

---

### Post by Shining Arcanine on 2010-11-24
> **Oxwivi said:**
> I'm creating this thread to discuss issues faced by Nvidia users in the Linux world.

The most pressing issue in my mind is Nvidia's stance on Wayland. They've already announced that they will not support it, which is concerns me because Ubuntu is going to use Wayland in the future, what of us?

The second thing is Compiz. Compiz requires Nvidia drivers, which we can't install during Ubuntu installation, so we won't be able to use Unity right off the bat with Natty. I don't like the idea of using GNOME-Shell just to install the drivers.

And finally, a little papercut - before driver installation I have the graphical loading screen - y'know that Ubuntu logo with the four dots. But after installing the driver the logo is replaced by monospace ASCII-type characters. Don't like that.

So Nvidia users, speak up!

When Wayland is ready for general use, Nvidia will likely support it.

---

### Post by LowSky on 2010-11-24
Why should Nvidia need to directly support Linux. Same for ATI. The open source drivers are moving further foward. By the time WAyland takes over we might see full 3D support from these drivers. I want to see more companies supporting VDPAU, but right now only Nvidia supports it which annoys me because find ATI makes better fanless cards.

---

### Post by Oxwivi on 2010-11-24
> **LowSky said:**
> Why should Nvidia need to directly support Linux. Same for ATI. The open source drivers are moving further foward. By the time WAyland takes over we might see full 3D support from these drivers. I want to see more companies supporting VDPAU, but right now only Nvidia supports it which annoys me because find ATI makes better fanless cards.
Let's hope that this statement proves prophetic.

---

### Post by cariboo on 2010-11-24
There is already basic 3D support available using the nouveau drivers, and libgl1-mesa-dri-experimental. The combination works well enough that it makes Unity pretty usable, even at this early stage of development.

I'm currently running Natty on 5 systems, 3 with Unity 1 with gnome-shell and 1 with the standard desktop, all but one system uses nvidia graphics. I can't really see any performance difference between the system using Nvidia drivers and the system using Nouveau drivers, in normal day to day usage.

---

### Post by cariboo on 2010-11-24
There is already basic 3D support available using the nouveau drivers, and libgl1-mesa-dri-experimental. The combination works well enough that it makes Unity pretty usable, even at this early stage of development.

I'm currently running Natty on 5 systems, 3 with Unity 1 with gnome-shell and 1 with the standard desktop, all but one system uses nvidia graphics. I can't really see any performance difference between the system using Nvidia drivers and the system using Nouveau drivers, in normal day to day usage.

---

### Post by cariboo on 2010-11-24
There is already basic 3D support available using the nouveau drivers, and libgl1-mesa-dri-experimental. The combination works well enough that it makes Unity pretty usable, even at this early stage of development.

I'm currently running Natty on 5 systems, 3 with Unity 1 with gnome-shell and 1 with the standard desktop, all but one system uses nvidia graphics. I can't really see any performance difference between the system using Nvidia drivers and the system using Nouveau drivers, in normal day to day usage.

---

### Post by Oxwivi on 2010-11-24
That is great news! I haven't been Maverick's Unity without the proprietary driver. :(

> **Spice Weasel said:**
> Doesn't Ubuntu use Plymouth for its splash screen? I could never get it to work with a Nvidia card either.
From [OMG! Ubuntu!]("http://www.omgubuntu.co.uk/2010/11/nvidia-have-no-plans-to-support-wayland/"): *NVidia have often been tepid at best when it comes to adding support for open-source technologies. They already &#8216;declined&#8217; to add support for Kernel Mode Setting (KMS, the thing which gives many Ubuntu users a pretty boot screen and the rest of us a lame one).*

---

