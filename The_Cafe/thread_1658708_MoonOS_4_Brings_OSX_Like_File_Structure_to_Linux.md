---
title: "MoonOS 4 Brings OSX Like File Structure to Linux?"
date: 2011-01-03
forum: The Cafe
---

### Post by beastrace91 on 2011-01-03
Ubuntu based [MoonOS]("http://www.moonos.org/") just released their fourth version recently and while they have moved away from the [Enlightenment]("http://www.enlightenment.org/") desktop - they have moved into something else that is radically different: **a unique file structure**

The root of the file system looks like this:

[IMG]http://i.imgur.com/TOcZd.png[/IMG]

Now it still uses maverick as a base and in fact it has Ubuntu still contained in it's sources list, my wondering is how standard Linux packages work in this different file system setup... I have yet to really play around with it, but doing so is now towards the top of my TODO list. I am wondering if this file system layout is useful or just "something different" Whats your take on it? System boots up and seems relatively fast for a Gnome distro.

~Jeff Hoogland

---

### Post by Lucradia on 2011-01-03
**[SIZE="6"]It's not just you! [http://moonos.org](http://moonos.org) looks down from here.[/SIZE]**

;)

---

### Post by LINJEinc on 2011-01-03
it's down from here to

---

### Post by kaldor on 2011-01-03
I like that a lot. Hopefully it keeps working out well.

---

### Post by Barrucadu on 2011-01-03
I assume they're using a similar system to GoboLinux (kernel patch to hide the standard directories, and a tonne of symlinks). It's an interesting way to do it; though it gives the illusion of portability (each app being in its on directory) as symlinks to the standard places are still needed.

Unless they heavily patch everything, which seems unlikely.

---

### Post by HappinessNow on 2011-01-03
looks nice.

---

### Post by alaukikyo on 2011-01-03
It is useless.

---

### Post by beastrace91 on 2011-01-03
Their website is back online now, guess it got hammered after their release.

~Jeff

---

### Post by madjr on 2011-01-03
here are the release notes for the new version, looks very interesting.

-_The New File Hierarchy System_
-_Appshell Framework_

[http://moonos.org/news/20/27-moonos-4-neake-release-note](http://moonos.org/news/20/27-moonos-4-neake-release-note)

---

### Post by Queue29 on 2011-01-03
> Neak is currently available with the GNOME only, in 32 bits.

Suddenly a lot less interesting.

---

### Post by Lucradia on 2011-01-03
> **Queue29 said:**
> Suddenly a lot less interesting.

if it has PAE, then it is basically the same as 64-bit in terms of RAM.

---

### Post by marl30 on 2011-01-03
This has got to be one of the best looking distros I've seen. It looks quite nice.

---

### Post by alexan on 2011-01-03
As the website says.. it come with the mythical ~200 lines patch.

It does improve any _real_ user feel?

---

### Post by pinguy on 2011-01-05
I am pretty sure they are using [http://www.gobolinux.org/?page=doc/articles/gobohide](http://www.gobolinux.org/?page=doc/articles/gobohide)

I can see the reasoning behind doing it. But I think it will course more problems then it will help.

---

### Post by cgroza on 2011-01-05
Whats the point of changing the structure anyway? Many people don't even leave their Home Folder anyway.

---

### Post by dh04000 on 2011-01-05
A filesystem that would allow a user to simply drop a program into a folder and then remove it the same way would be amazing. Imagine being able to download pidgin.deb and just dropping it into a application folder found in PLACES, and that would be all that's need to install. Then the application self adding itself to your menu's after the drop. Removing would be just as easy as removing it, causing it self to removed from the menu. Truly an amazing idea. If the software center installed everything that same folder, that would be great.

I can't tell you how many times I have installed an application and been unable to remove it.

---

### Post by Legendary_Bibo on 2011-01-05
> **dh04000 said:**
> A filesystem that would allow a user to simply drop a program into a folder and then remove it the same way would be amazing. Imagine being able to download pidgin.deb and just dropping it into a application folder found in PLACES, and that would be all that's need to install. Then the application self adding itself to your menu's after the drop. Removing would be just as easy as removing it, causing it self to removed from the menu. Truly an amazing idea. If the software center installed everything that same folder, that would be great.

I can't tell you how many times I have installed an application and been unable to remove it.

Really? I've never had an issue with removing software, and I've added and removed a lot of software through synaptic, apt-get, and the software center.

---

### Post by madjr on 2011-01-05
> **pinguy said:**
> I am pretty sure they are using [http://www.gobolinux.org/?page=doc/articles/gobohide](http://www.gobolinux.org/?page=doc/articles/gobohide)

I can see the reasoning behind doing it. But I think it will course more problems then it will help.

i dont think they are using gobohide

[http://www.webupd8.org/2011/01/moonos-is-linux-distribution-based-on.html](http://www.webupd8.org/2011/01/moonos-is-linux-distribution-based-on.html)

---

### Post by kaldor on 2011-01-05
I agree with one of the above posters. When not installing software from the Ubuntu Software Centre, it can sometimes be very annoying. 

The Mac way of doing it is probably the easiest possible way; what's easier than downloading a file, clicking on it, then dragging the Icon to the Applications folder (or wherever you want to store it)?

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-01-05
> **kaldor said:**
> what's easier than downloading a file, clicking on it, then dragging the Icon to the Applications folder (or wherever you want to store it)?

A common sense file structure that uses stronger associations than "these files are generally used by the same application, most of the time". The Unix file hierarchy is simply superior on every way to the windows/mac way of doing things, and replacing it (or, as in this case, hiding it with a thousand symlinks) just for familiarity reasons is just idiotic.

Besides, if you're using a package manager, it can tell you where every file installed by a package is. And if you aren't, then you should know that on your own. This is a non-fix of a non-existent problem.

---

### Post by MisterGaribaldi on 2011-01-05
I've always felt the way that Linux stores its resources are very arbitrary and extremely inaccessible to those who aren't extremely hard-core users or developers.

Even after 10-odd years of use, I have a hard time whenever I need to find where something has been installed.

Both Microsoft and Apple to their credit have a fairly straight-forward organizational structure for software, system software, and other resources.

On the flip side, apt knows where everything is so when I need to remove or re-install something, it handles everything. But I admit to wishing I had a better grip on where everything goes and what the rationale behind the organizational structure is.

---

### Post by Chronon on 2011-01-05
> **MisterGaribaldi said:**
> I've always felt the way that Linux stores its resources are very arbitrary and extremely inaccessible to those who aren't extremely hard-core users or developers.

Even after 10-odd years of use, I have a hard time whenever I need to find where something has been installed.

Both Microsoft and Apple to their credit have a fairly straight-forward organizational structure for software, system software, and other resources.

On the flip side, apt knows where everything is so when I need to remove or re-install something, it handles everything. But I admit to wishing I had a better grip on where everything goes and what the rationale behind the organizational structure is.
You can, as pointed out previously, get a list of every file and its location from the package entry in your package manager.

---

### Post by beastrace91 on 2011-01-05
> **madjr said:**
> i dont think they are using gobohide


I asked on their forums - they are indeed using Gobohide. Should have figured as much.

Cheers,
~Jeff

---

### Post by Spr0k3t on 2011-01-06
I see problems a foot with this gobledegook.

---

### Post by MisterGaribaldi on 2011-01-06
> **Chronon said:**
> You can, as pointed out previously, get a list of every file and its location from the package entry in your package manager.

No doubt. And as no doubt you've guessed, if it hasn't been enough of a PIA for me after 10 years, it's probably not that big a PIA in the first place.

---

### Post by dh04000 on 2011-01-06
> **Legendary_Bibo said:**
> Really? I've never had an issue with removing software, and I've added and removed a lot of software through synaptic, apt-get, and the software center.


Still to this day, I can not get Wolfenstein:Enemy Territory removed.

---

### Post by Mr. Picklesworth on 2011-01-06
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> A common sense file structure that uses stronger associations than "these files are generally used by the same application, most of the time". The Unix file hierarchy is simply superior on every way to the windows/mac way of doing things, and replacing it (or, as in this case, hiding it with a thousand symlinks) just for familiarity reasons is just idiotic.

Besides, if you're using a package manager, it can tell you where every file installed by a package is. And if you aren't, then you should know that on your own. This is a non-fix of a non-existent problem.

It really, really depends on the application. I agree with you that the package manager is basically what you should use to edit files that aren't in /home except in some funny cases. The fancy file hierarchy makes a lot of sense, for the reason you mentioned, when we're talking about a major component other applications depend on. Libraries, dbus, udev, grub, apache, etc.

However, I think it is a Very Bad thing when we get to extra applications of the sort that depend on those components. This would be Firefox, OpenOffice, the *front end* for Evolution, a Calculator. I think it's bad for a bunch of reasons.
It doesn't make sense because these apps *are* self contained. More seriously, every time one of these apps dumps a file somewhere like /usr/bin, there is a very real risk of a name collision. We work around the problem now by having a lot of dedicated package maintainers working hard to keep these collisions from happening, but that workaround does not scale.

With a hierarchy that puts application binaries and data files in the same place (that would be installing to /opt/ApplicationDomain.ApplicationName), with a few extras elsewhere (.desktop file in /usr/share/applications, symlink somewhere in $PATH if people complain), that risk of collision is much smaller and the underlying problem can be addressed properly.

---

### Post by rvchari on 2011-01-06
looks and feel seems to be good, time will tell on the apps performance and resource utility.... some day will try to run from cdrom...

---

### Post by beastrace91 on 2011-01-07
> **rvchari said:**
> some day will try to run from cdrom...

DVDROM* Its a 832meg download :-/

~Jeff

---

### Post by Pogeymanz on 2011-01-07
Most people just don't understand the Unix filesystem hierarchy. I'm not saying that it should never be changed. I'm not dogmatic like that, but reducing some 20 important directories (/boot; /etc; /usr/bin; /bin; /usr/sbin; /sbin; /var/spool; /home; /tmp; /dev; /sys; ...) to about five is ridiculous.

You can already install applications to different directories such as /opt or your /home so that you can run different versions concurrently.

I agree that the filesystem has vestigial parts (/var/tmp needs to go, and /media, /mnt, /dev can be combined).

Your "App Files" is basically /usr/bin.

Just my two cents. I will be very interested to see how GoboLinux and MoonOS evolve.

---

### Post by 3Miro on 2011-01-07
The Unix directory structure is very logical from system point of view. Changing it would make more sense to a less savvy user, but it doesn't really make much sense on the system level. On the other hand:

Apps = /usr + /opt
System = /lib /etc /dev /proc /var ...
Users = /home

so what's the big difference, you just have to type more in a terminal.

---

### Post by dead_knight on 2011-01-14
@madjr
hey man!
sorry to bother you like this sudden, what is the name of the anime in your profile picture. I'm sure i watched it but could not remember (driving me nuts). (and sorry for using the forum like this :D)

---

