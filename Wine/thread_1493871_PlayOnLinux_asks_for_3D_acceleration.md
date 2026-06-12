---
title: "PlayOnLinux asks for 3D acceleration"
date: 2010-05-26
forum: Wine
---

### Post by Paddy Landau on 2010-05-26
I run a program on [PlayOnLinux]("http://www.playonlinux.com/") (Wine).

When I start the program, PlayOnLinux says, "You don't seem to have 3D acceleration. We advise you install and enable it."

The program works anyway, so no problems.

However, I wonder whether installing and enabling 3D acceleration would be simple and, if so, how to do it.

If it's complicated, then I won't bother, as it is absolutely **not** important for me (I don't play games on the machine).

I have Lucid 10.04 64-bit running with graphics card Intel GMA950.

---

### Post by Pitosgas on 2010-05-26
I'm not sure, but i think we need to disable compiz in order to have 3d aceleration on POL.

cheers,
Pitosgas

---

### Post by Paddy Landau on 2010-05-26
> **Pitosgas said:**
> I'm not sure, but i think we need to disable compiz in order to have 3d aceleration on POL.
That's interesting. I've made no changes to Compiz, so it does whatever Lucid set it up to do by default. So, to be safe, I'll just leave it alone.

Thanks.

---

### Post by cogadh on 2010-05-26
> **Paddy Landau said:**
> That's interesting. I've made no changes to Compiz, so it does whatever Lucid set it up to do by default. So, to be safe, I'll just leave it alone.

Thanks.
By default, Compiz or desktop effects are enabled as soon as you install the restricted driver for your video card; without the restricted driver, they aren't enabled at all. In order for Wine, and by extension PlayOnLinux, to work properly, you need to turn off desktop effects as it "breaks" OpenGL functionality from Wine's perspective.

---

### Post by Paddy Landau on 2010-05-26
> **cogadh said:**
> By default, Compiz or desktop effects are enabled as soon as you install the restricted driver for your video card; without the restricted driver, they aren't enabled at all.
Thanks for the clarification. I learn something new every day!

I don't have a restricted driver, I believe, because System > Administration > Hardware drivers shows "No proprietary drivers are in use on this system."

> **cogadh said:**
> In order for Wine, and by extension PlayOnLinux, to work properly, you need to turn off desktop effects as it "breaks" OpenGL functionality from Wine's perspective.
Does that mean System > Preferences > Appearance > Visual Effects > None?

If so, that's already the case for me. It seems that when I use a dual screen (nearly all of the time), then my graphics card doesn't cope with visual effects and they turn off automatically. When I use a single screen, the "Extra" visual effects work fine.

---

### Post by cogadh on 2010-05-26
Ah, didn't notice that you have an Intel card. In that particular case, what would be considered the "restricted driver" is already included with Ubuntu by default (Nvidia and ATI drivers are not), hence the "no proprietary drivers..." message. Time to check the basics, then. Open a terminal and run this:
```
glxinfo | grep direct
```
If it comes back saying "Direct Rendering: Yes", then we can stop looking at your graphics card and drivers as the source of the problem.

---

### Post by Paddy Landau on 2010-05-27
> **cogadh said:**
> glxinfo | grep direct
The command returns
```
direct rendering: Yes
```I don't understand the significance of all these things.

---

### Post by cogadh on 2010-05-27
That command, glxinfo, spits out information about about your video card and drivers. Adding the "grep direct" filters out all the info except the part that tells us whether or not you actually have 3D acceleration capabilities. If it comes back saying "direct rendering: No", then you do not have 3D acceleration, if it comes back saying "direct rendering: Yes" then you do have 3D acceleration. 

Basically, we just confirmed that there is nothing wrong with your video card or drivers, so the problem must reside with PlayOnLinux or with some kind of configuration option on your system. The only configuration option that I know of that is capable of screwing up 3D acceleration is the desktop effects and you have already confirmed that you have them disabled. So that leaves PlayOnLinux; either it is having some kind of problem, or it is looking for something on your system that you are missing. In searching around, I found multiple references to the fact that you need to install the mesa-utils package to make that message go away. Apparently in prior versions of Ubuntu, it was installed by default, but now it no longer is and POL depends on that to determine the status of your 3D hardware. Open a terminal and run "sudo apt-get install mesa-utils", when the install finishes, try running POL again.

---

### Post by Paddy Landau on 2010-05-27
> **cogadh said:**
> ... run "sudo apt-get install mesa-utils"
Thank you for all the clarification.

It has solved the problem.

Thank you for taking the time to lead me through this. I'll mark this thread as Solved.

---

### Post by nenadsuperzmaj on 2010-05-27
This helped me too! Thank you!

PlayOnLinx should perhaps suggest installing of mesa-utils or perhaps even depend on it as probably at least of 90% run under POL use 3D capabilities...

---

### Post by efrens on 2010-07-07
installing mesa-utils solved it indeed.

no more "you don't seem to have 3d acceleration we advise you to install and enable it" on PlayOnLinux. Thanks.

---

### Post by marco.cj.org on 2010-08-15
the command "glxinfo | grep direct" also needs mesa-utils. you can install it by opening a terminal and do "sudo apt-get install mesa-utils" (you will be asked for you administrator password).  Thank you for the post, I also had this problem solved here.

---

