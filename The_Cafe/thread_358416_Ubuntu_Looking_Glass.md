---
title: "Ubuntu Looking Glass"
date: 2007-02-10
forum: The Cafe
---

### Post by rucadulu on 2007-02-10
Does anyone know if there is an effort underway to build a ubuntu distro with Looking Glass as the primary desktop environment? If there is how does one get envloved in development and if there is not how does one get the ball started on making a LGubuntu distro? 

Thanks, Russell(rucadulu)

---

### Post by bobbyshafter on 2007-02-10
The live cd is slack...

You can use looking Glass WM ,it working great on dapper.

You need a fast graphic card,i tried it with my onboard intell slooooow....unuseable.

I am now using GeForce 7300 GS,works great.

---

### Post by Sunnz on 2007-02-11
Just wondering, is LG in the repository or do you just to go to Sun's site and download and compile it yourself?

---

### Post by taurus on 2007-02-11
> **Sunnz said:**
> Just wondering, is LG in the repository or do you just to go to Sun's site and download and compile it yourself?

Here you go.

[https://lg3d-core.dev.java.net/binary-builds.html](https://lg3d-core.dev.java.net/binary-builds.html)

---

### Post by Sunnz on 2007-02-11
Wow they got a Windows build as well? Ohh I see it is written in Java...

---

### Post by rucadulu on 2007-02-11
To Load Looking Glass on to your ubuntu distro you need to add the LG3D repsitories to active repsoitories under your favorite package manager.

for Stable:
deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib

for testing:
deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) testing contrib

for unstable:
deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) unstable contrib

after adding repsoitor you need to update your package list either from your package manager or from the terminal: 
"sudo apt-get update"

then install lg3d-core with your package manager or from the terminal: 
"sudo apt-get install lg3d-core"

I have installed the stable version on a PC with 3ghz P4EE, 1024mb dual-channel RAM and a Nvidia 5200 GeForce 256mb Graphics Card. It runs great on this system. I have not been able to get all my apps to come up under it however. Well any how, good luck and have fun.

Russell(rucadulu):)

---

### Post by Klaidas on 2007-02-11
You can easily install it using sun's official guide. 
But Looking Glass is pretty disappointing - looks good in the screenshots, suc kwhen installed :|

---

### Post by pcit on 2007-02-15
Well...
It's simulation in Windows~
I just tried it out today |o|

---

### Post by finer recliner on 2007-02-18
java says the project is still in its infancy. can anyone tell me if the current release is stable enough to try to on a productivity machine, or should i wait?

and when it gets installed, will run as another desktop environment? (like gnome/KDE/...)

---

### Post by %hMa@?b&lt;C on 2007-02-18
> **finer recliner said:**
> java says the project is still in its infancy. can anyone tell me if the current release is stable enough to try to on a productivity machine, or should i wait?

and when it gets installed, will run as another desktop environment? (like gnome/KDE/...)

afaik, it IS a DE, like gnome/kde/etc, just a different DE

---

### Post by rucadulu on 2007-03-04
finer recliner, I have been away for a while so I am  sorry I could not post sooner. Looking Glass can be installed on a any machine you like, however, I would not use it for a primary desktop envoriment due to the fact that it is rather incomplete. With that said it is very fun to play around in and should not afffect your other desktop envoriments like gnome kde or xfce in any way.

rucadulu

---

### Post by old_geekster on 2007-03-07
I installed "Looking Glass" last evening from "Synaptic".  It installed fine.  So, I did a "Ctrl/Alt Backspace" and chose to use Looking Glass as my desktop.

It works fine, however, it sets my screen resolution to 1600 X 1200, which is max for my CRT monitor.  It makes everything too small for these old eyes.:)   The problem, I can't find the secret to changing the resolution.:confused: 

Can anybody help?

---

### Post by MkfIbK7a on 2007-03-07
i tried it and an ubuntu with lg3d as the primary desktop would be all but unusable...

---

### Post by K.Mandla on 2007-03-07
I set it up a few months ago, just to try it out. 

[http://kmandla.wordpress.com/2006/12/30/hey-wow-looking-glass-3d/](http://kmandla.wordpress.com/2006/12/30/hey-wow-looking-glass-3d/)

I didn't find it terribly cumbersome, but like anything else it would take a little getting used to.

---

### Post by Anthem on 2007-03-07
Seemed like the Looking Glass project has some concepts that would work well in Compiz/Beryl.

But writing a whole DE in Java?  Seems.... odd.

---

### Post by clblanchard on 2007-03-20
Writing  a DE in java does seem odd.  But if you think about java what usually comes to mind?  Everyone I know thinks cell phone games, and very small applications.  I think this may be a way for Sun to show some of the true power of Java.

---

### Post by fakie_flip on 2007-05-02
Could some of you post up your screenshots of Project Looking Glass in Ubuntu? I really want to try it, but I won't be able to for about a week or two.

---

### Post by fakie_flip on 2007-05-02
> **bobbyshafter said:**
> The live cd is slack...

You can use looking Glass WM ,it working great on dapper.

You need a fast graphic card,i tried it with my onboard intell slooooow....unuseable.

I am now using GeForce 7300 GS,works great.

Where can I download that slack live cd with Project Looking Glass? Would you post up some screenshots of Project Looking Glassing running on your computer with the 3d and graphics effects? Thanks.

---

### Post by Sunnz on 2007-06-22
Is there now a Live CD of any sort for it that FF has came out?

---

### Post by rucadulu on 2007-07-15
Here is the url for the live Looking Glass CD from sun.

[https://lg3d-livecd.dev.java.net/Web-Site/Welcome.html](https://lg3d-livecd.dev.java.net/Web-Site/Welcome.html)

---

### Post by rucadulu on 2008-02-09
Here are some Urls for a LG3D distro:

info pages:
[http://distrowatch.com/table.php?distribution=lg3d](http://distrowatch.com/table.php?distribution=lg3d)
[https://lg3d-livecd.dev.java.net/Web-Site/Welcome.html](https://lg3d-livecd.dev.java.net/Web-Site/Welcome.html)

downloads:
[http://sourceforge.net/project/showfiles.php?group_id=144229](http://sourceforge.net/project/showfiles.php?group_id=144229)

---

### Post by bwhite82 on 2008-02-09
Interesting, DLing it now. Will post screenshots.

---

### Post by bwhite82 on 2008-02-09
Update: I've downloaded the LiveCD and while it boots fine, I can only use it in 'kernel driver' mode, ie no accelerated graphics, hence very slow desktop (unusable). Then, I added the repos and installed via dpkg. I tried all three actually (stable, testing, unstable) and depending on which repo I use, I keep getting either:

> E: Sub-process /usr/bin/dpkg returned an error code (1)

Or

> /usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1

It seems the project is pretty outdated, not sure if its being actively developed. Shame, it looks nice and from the little I have used it (un-accelerated LiveCD) I actually was awed at the experience.

---

### Post by bwhite82 on 2008-02-09
Edit: I stand corrected, looks like its still being developed by only 2 people ATM, its no longer a focus of Sun however:

[http://forums.java.net/jive/thread.jspa?messageID=243959](http://forums.java.net/jive/thread.jspa?messageID=243959)

[http://forums.java.net/jive/thread.jspa?messageID=256395](http://forums.java.net/jive/thread.jspa?messageID=256395)

You can snag the very latest .deb here (make sure you have the package sun-java6-jdk installed first):

[https://lg3d-core.dev.java.net/files/documents/1834/84267/lg3d-core_1.0.1_dev_i686.deb](https://lg3d-core.dev.java.net/files/documents/1834/84267/lg3d-core_1.0.1_dev_i686.deb)

The login script (from GDM) isn't working for me but you can run the devel script from CLI and it will run:

> /usr/share/lg3d/bin/lg3d-dev

---

