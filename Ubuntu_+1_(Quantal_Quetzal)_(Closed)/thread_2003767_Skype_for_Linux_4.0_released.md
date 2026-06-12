---
title: "Skype for Linux 4.0 released"
date: 2012-06-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pressureman on 2012-06-14
[http://blogs.skype.com/linux/2012/06/skype_40_for_linux.html](http://blogs.skype.com/linux/2012/06/skype_40_for_linux.html)

32/64 bits debs available for Ubuntu 10.04 (wtf?), Debian 6.0, and 32 bit packages available for Fedora 16 (again, wtf?) and OpenSuse 12.1.

Hopefully we get this in the partner repos for Quantal (and backported too would be nice).

PS: The 64 bit packages are still actually a 32-bit ELF, and as such need about eleventy billion i386 packages installed on amd64 boxes (multiarch).

---

### Post by cariboo on 2012-06-14
244 extra packages later I have skype 4.0 working here. :)

---

### Post by Gaygerbil on 2012-06-14
A lot of good stuff added but a lot of good stuff were also remove for no reason it seems. And there are bugs in this version.

> There is no pause call option in the new Skype now.

> There is no double size window now, therefore your own cam cannot be resized like before (although you can now stretch the window your cam size cannot be adjusted at all anymore)

> There is no right click menu on the video screen option anymore. :|

> There is a bug right now in Skype which is really annoying, if you set your calls to automatically answer and someone calls you, a notification will pop up and you will pick up automatically. However trying to close the notification closes the call window completely, and hitting the answer button does nothing, while hitting the end button hangs up the call. There is no way to disable the notification as I know of right now as the option has been grayed out. 

> My mic is now randomly going out and making me switch channels on it as well. Not sure what's even going on there.

A lot of good stuff too, I won't go into it but there are many improvements in performance and video calling as well as options. Good job overall to the Skype developers on Linux.

---

### Post by sammiev on 2012-06-14
So far no issues here to report. A few items missing but over all OK. :)

---

### Post by ajgreeny on 2012-06-14
Seems to be working well on my 10.04 box with gnome desktop after downloading from skype direct.

I think sound is clearer than in the old version from the repos, webcam works well, and I can not see anything at fault with it but time will tell how well it really works, after I have used it properly several times.

---

### Post by pressureman on 2012-06-15
If I'm not mistaken, it now supports HD video... it's still just as much a CPU hog as it always was though.

---

### Post by na5h on 2012-06-15
It's nice to see that the Linux version is finally getting some updates...I though that Skype for Linux was dead for sure! :)

---

### Post by ajgreeny on 2012-06-16
> **pressureman said:**
> If I'm not mistaken, it now supports HD video... it's still just as much a CPU hog as it always was though.
How useful is that for a VOIP application which will still depend very much on internet speeds?  Perhaps it will still give a better picture even at the remote end, but HD?

---

### Post by Gaygerbil on 2012-06-17
It would be useful if it actually worked right. I don't think Skype can do anything for certain cams that have Linux drivers that aren't as good as their Window's counterparts. MY video quality is apparently still the same (not sure might be the person's internet) in general though my cam looks better offline in Windows than Linux. 

Some more things I noticed in this new version, you can't double click on the cam window to go fullscreen anymore. WHY!?

Can't turn off other person's cam without ending the call as well like before.

Can't hit numbers really loudly in people's ears like before. :\

---

### Post by mosaic2s on 2012-06-17
And skype 4.0 for ubuntu 12.04?

---

### Post by firekage on 2012-06-17
> **mosaic2s said:**
> And skype 4.0 for ubuntu 12.04?

It's the same i think. As a matter of fact when you download it there is info that 4.0 is for 10.x Ubuntu systems...

---

### Post by mparillo on 2012-06-17
Since Skype (like KDE) is written with the Qt framework, does that mean that KDE distros (like Kubuntu) will seem smoother (less overhead, more responsive, fewer dependencies to load, more consistent window controls, whatever) than Gnome distros?

---

### Post by Simian Man on 2012-06-17
Thank goodness Microsoft bought Skype so that we can finally see it offer better support for Linux systems.

---

### Post by alphacrucis2 on 2012-06-17
> **mparillo said:**
> Since Skype (like KDE) is written with the Qt framework, does that mean that KDE distros (like Kubuntu) will seem smoother (less overhead, more responsive, fewer dependencies to load, more consistent window controls, whatever) than Gnome distros?

Doesn't really make any difference other than cosmetic appearance. Fewer dependencies yes but not for me as I run several qt apps anyway.

---

### Post by Gaygerbil on 2012-06-27
I found that you can still pause the call from the main Skype window for some reason, and pausing it is a work around to closing the notification and bringing the skype call window back when it vanishes. :|

Maybe it'll help someone...

---

### Post by stigb on 2012-06-27
Do you think this update will get to the Skype PPA soon?

---

### Post by cariboo on 2012-06-27
> **stigb said:**
> Do you think this update will get to the Skype PPA soon?

There isn't a skype ppa, the package is usually located in the partner repository, which can be enabled via software sources, either in the software centre or synaptic package manager.

---

### Post by pressureman on 2012-06-27
What would be *really* awesome is if there were an actual 64 bit build available, not just a package with "amd64" in the name :-|

... so that we didn't also have to install half of the i386 repo as multiarch.

---

### Post by stigb on 2012-06-27
> **cariboo907 said:**
> There isn't a skype ppa, the package is usually located in the partner repository, which can be enabled via software sources, either in the software centre or synaptic package manager.
Well, I actually have a /etc/apt/sources.list.d/skype.list and partner repositories disabled. Maybe it got there through Ubuntu Tweak. Is Skype in partner the newest version?

---

### Post by ScislaC on 2012-06-27
> **pressureman said:**
> What would be *really* awesome is if there were an actual 64 bit build available, not just a package with "amd64" in the name :-|

... so that we didn't also have to install half of the i386 repo as multiarch.

Seriously... amen to that!

---

### Post by cariboo on 2012-06-28
> **pressureman said:**
> What would be *really* awesome is if there were an actual 64 bit build available, not just a package with "amd64" in the name :-|

... so that we didn't also have to install half of the i386 repo as multiarch.

With so many people still running i386 on 64-bit capable cpu's, it will be quite a while before we see a purely 64-bit version on many multi-platform programs.
If we could get all the people that are still running 32-bit oses to switch to 64-bit operating systems, we might see pure 64-bit applications, sooner, rather than later

---

### Post by Gaygerbil on 2012-06-28
Unfortunately this is me, I had switched my processor to 64bit just recently and did an upgrade on my distro but forgot about that when downloading and installing the upgrade. :\ Perhaps next time...

---

### Post by pressureman on 2012-06-28
> **cariboo907 said:**
> With so many people still running i386 on 64-bit capable cpu's, it will be quite a while before we see a purely 64-bit version on many multi-platform programs.
If we could get all the people that are still running 32-bit oses to switch to 64-bit operating systems, we might see pure 64-bit applications, sooner, rather than later

Most new PC desktops/notebooks ship with at least 4GB RAM, making the use of i386 suboptimal. Microsoft has 64 bit versions of Office available, Adobe has 64 bit versions of several of their flagship products (eg. Photoshop & co.) available. Apple has had 64 bit app support for years.

I can't understand why Skype can't simply release a 64 bit build. It's not like they're unfamiliar with Linux, since they run their Postgres DB servers on Linux - and I'd be doubtful if they're 32 bit systems with < 4GB RAM.

---

