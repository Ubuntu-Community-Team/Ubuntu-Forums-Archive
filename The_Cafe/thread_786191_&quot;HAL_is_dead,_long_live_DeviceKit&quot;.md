---
title: "&quot;HAL is dead, long live DeviceKit&quot;"
date: 2008-05-07
forum: The Cafe
---

### Post by 23meg on 2008-05-07
*(Thanks to [Martin Pitt]("http://martinpitt.wordpress.com/2008/05/07/hal-is-dead-long-live-devicekit/") for the heads up)*

[David Zeuthen]("http://blog.fubar.dk/") (of HAL and PolicyKit fame) has announced his plans for and unveiled his initial work on DeviceKit:

[http://lists.freedesktop.org/archives/hal/2008-May/011560.html](http://lists.freedesktop.org/archives/hal/2008-May/011560.html)

Looks like he's aiming for at least partial inclusion in GNOME 2.24, which means some exciting changes are ahead for Intrepid, hopefully without big regressions (testers, take note). Perhaps the most directly notable component for non-technical users will be gnome-disk utility (scroll down in the message for screenshot links), which it seems will fulfill the need for a graphical disk manager. 

The pre-release code is already available for testing (with the obvious caveat: it will certainly kill all your disks and you'll lose all your data forever). Zeuthen will be at [FOSSCamp]("http://fosscamp.org") next week, where I expect he will brief the Ubuntu crew on the upcoming changes and discuss how they can be implemented. There are no official plans yet, but we can probably expect the new goods to land in Intrepid in a month or two.

---

### Post by FuturePilot on 2008-05-07
Wow! Sounds cool. Can't wait to see this. :)

---

### Post by atlas95 on 2008-05-09
Seems to be excellent !
Visual smart monitoring is wonderfull :D !
I can't wait for see it too !!

---

### Post by SunnyRabbiera on 2008-05-09
well technically its not dead, just being recoded...
but it looks like development is all going to gnome, wonder how KDE and others will cope as they too use HAL and such

---

### Post by Mr. Picklesworth on 2008-05-09
HAL has always felt in need of some kind of refactoring (it has gone crazy too many times for me...), so this is good news :)

I notice there are user-specified labels in that GNOME disks admin tool, too, which is something that seems oddly difficult in the current situation.

---

### Post by Andrewie on 2008-05-09
KDE doesn't use HAL, they use solid which uses HAL. (if my memory serves me right). They just need to adjust solid to work with DeviceKit and everyone (KDE 4 developers) will be fine.

---

### Post by DoktorSeven on 2008-05-09
I'm just distressed that more and more applications are needing this.  I don't have HAL running on my machine -- don't need it, don't want it.  I can manage things on my own just fine, thanks.  I wish I could get rid of dbus as easily, way too much depends on it for some odd reason.

I can understand why some would want things like this, but I would appreciate it being an option, not a requirement.

---

### Post by Half-Left on 2008-05-09
> **DoktorSeven said:**
> I'm just distressed that more and more applications are needing this.  I don't have HAL running on my machine -- don't need it, don't want it.  I can manage things on my own just fine, thanks.  I wish I could get rid of dbus as easily, way too much depends on it for some odd reason.

I can understand why some would want things like this, but I would appreciate it being an option, not a requirement.

Thats because new users NEED it, you do realize that one of the reason why linux uptake was slow was because of poor interaction with devices. If you want go use Slackware since mostly they mount their devices manually(even Slackware comes with dbus and HAL now).

HAL is a much needed in linux but it seem like something better is coming to replace it, just like Udev.

---

### Post by Andrewie on 2008-05-09
> **DoktorSeven said:**
> I'm just distressed that more and more applications are needing this.  I don't have HAL running on my machine -- don't need it, don't want it.  I can manage things on my own just fine, thanks.  I wish I could get rid of dbus as easily, way too much depends on it for some odd reason.

I can understand why some would want things like this, but I would appreciate it being an option, not a requirement.

you're the first person I've ever seen that hates HAL, 2 e-cookies for you. Jokes aside I don't HAL will ever be an requirement at the very most you'll have to compile binaries with out HAL support but for a tech person like you that shouldn't be too hard.

---

### Post by Mr. Picklesworth on 2008-05-09
> **DoktorSeven said:**
>  I wish I could get rid of dbus as easily, way too much depends on it for some odd reason.
ehawaaht?!
That's like saying you wish you could get rid of bash (and all other shells); d-bus is a key part of integration for GUIs on the modern desktop!

If you don't believe me, then play with RSS feed subscription in Epiphany, or read about upcoming changes to gnome-panel. D-bus is not something that could (or should) just be yanked out. In fact, dbus is becoming one of the critical components for Linux platforms.

---

### Post by DoktorSeven on 2008-05-09
"Thats because new users NEED it"
Thus my admission that yes, I'm sure some will want it.  New users might need all the things HAL/etc provides.  Experienced users, however, might see it as a crutch.

"d-bus is a key part of integration for GUIs on the modern desktop!"
Well, believe it or not, some don't care about "integration".  I want to get something from program A to program B, I'll use X copy/paste for text or some element of program A to save data for program B, or just do it myself.  It's not hard and more natural for me to do.  Thus I see dbus as something unnecessary running in the background, since it's really doing nothing for me.

As I said, what'd be nice is to give users the *option* to disable dbus support if not needed.  I don't like unnecessary stuff running in the background.

---

### Post by Mr. Picklesworth on 2008-05-09
> Thus I see dbus as something unnecessary running in the background, since it's really doing nothing for me.I see where you are coming from, but I feel I should point out that is *not* all dbus does. If you kill the dbus daemon, or check out some of the freedesktop specs, you will see just how much it is used for. Everything from opening a file to running a search query can be (and some day will *ideally* be) done with dbus messages in a beautifully platform-neutral (and system-neutral) way. The notification popups use dbus; I recall reading about lots of dbussery in gvfs; gnome-screensaver, power management and the GNOME settings daemon all use dbus...

That's all inter-process integration, and I think even you would find the lack of those functions quite painful :)
Miles off topic now, but a nice way to poke at the idea is the D-Feet debugger. It's rather interesting to see what uses dbus, and the tool also helps if one is writing a script that triggers things using dbus.

Therefore, I think you can rest easy with the thought that dbus is pretty much synonymous with the Linux platform in general and that it is quite useful. It isn't horribly heavy, anyhow; the alternative would be for every application to implement its own berserk form of IPC, which leads to horrifying redundancy as all manner of standards compete with each other, your desktop being the battle field. It seems to be working out a bit tidier when most of the stuff is already there, under one centralized framework...

---

### Post by DoktorSeven on 2008-05-09
> **Mr. Picklesworth said:**
> I see where you are coming from, but I feel I should point out that is *not* all dbus does. If you kill the dbus daemon, or check out some of the freedesktop specs, you will see just how much it is in charge of. Everything from opening a file to running a search query can be (and some day will *ideally* be) done with dbus messages in a beautifully platform-neutral (and system-neutral) way. The notification popups use dbus; I recall reading about lots of dbussery in gvfs; gnome-screensaver, power management and the GNOME settings daemon all use dbus...

Well, I don't use Gnome, and all the things I use to open files don't rely on dbus at all, so yeah.  All I know is that killing dbus destroys several programs that depend on it and it'd be a pain to recompile all of them without dbus support.

---

### Post by swoll1980 on 2008-05-09
> **Half-Left said:**
> Thats because new users NEED it, you do realize that one of the reason why linux uptake was slow was because of poor interaction with devices. If you want go use Slackware since mostly they mount their devices manually(even Slackware comes with dbus and HAL now).

HAL is a much needed in linux but it seem like something better is coming to replace it, just like Udev.

+1 normal people are not cmd heroes

---

### Post by madjr on 2008-05-10
> **DoktorSeven said:**
> "Thats because new users NEED it"
Thus my admission that yes, I'm sure some will want it.  New users might need all the things HAL/etc provides.  Experienced users, however, might see it as a crutch.

"d-bus is a key part of integration for GUIs on the modern desktop!"
Well, believe it or not, some don't care about "integration".  I want to get something from program A to program B, I'll use X copy/paste for text or some element of program A to save data for program B, or just do it myself.  It's not hard and more natural for me to do.  Thus I see dbus as something unnecessary running in the background, since it's really doing nothing for me.

As I said, what'd be nice is to give users the *option* to disable dbus support if not needed.  I don't like unnecessary stuff running in the background.

don't make me send u back to gentoo mister

---

### Post by Half-Left on 2008-05-10
> **DoktorSeven said:**
> "Thats because new users NEED it"
Thus my admission that yes, I'm sure some will want it.  New users might need all the things HAL/etc provides.  Experienced users, however, might see it as a crutch.

"d-bus is a key part of integration for GUIs on the modern desktop!"
Well, believe it or not, some don't care about "integration".  I want to get something from program A to program B, I'll use X copy/paste for text or some element of program A to save data for program B, or just do it myself.  It's not hard and more natural for me to do.  Thus I see dbus as something unnecessary running in the background, since it's really doing nothing for me.

As I said, what'd be nice is to give users the *option* to disable dbus support if not needed.  I don't like unnecessary stuff running in the background.

I dont understand why it's getting in your way, dbus and hal are very small and are userspace. If you dont want them the option to not install them on Ubuntu is simply not possible because of the integration, sounds like your best off with with another DE.

---

### Post by DoktorSeven on 2008-05-10
> **madjr said:**
> don't make me send u back to gentoo mister

Heh, thanks, no.  Gentoo has its own problems in my experience, and I don't want to return to that.  Ubuntu really seems like the best distro that I can use, even if I have to disable a lot of automatic things I don't use and put up with a few other things.

All I'm saying is that with the design of these things, it would be nice to have the ***option*** to not have to use it via some sort of runtime configuration if it's not needed.  I mean, what's next, putting it on servers where it's really not needed just because something commonly used decides to require dbus?

Linux is about choice, after all, and if I choose not to use dbus, it would certainly be nice to not have to without recompiling every single app that has a compile-time required option for it.

[quote=Half-Left]I dont understand why it's getting in your way, dbus and hal are very small and are userspace. If you dont want them the option to not install them on Ubuntu is simply not possible because of the integration, sounds like your best off with with another DE.[/quote]

I *do* use something other than gnome -- fluxbox.  However, applications that run independently of gnome still require it, and it seems to be spreading out to pretty much every single desktop application, so it will be increasingly difficult to simply avoid.

---

### Post by maninalift on 2009-03-06
> **DoktorSeven said:**
>  Thus I see dbus as something unnecessary running in the background, since it's really doing nothing for me.


OK, I understand the feeling. That icky feeling of unnecessary crap cluttering up your machine. But you can stand back and ask yourself "is it really an issue" because if you have a look at how much CPU and memory it is using... it really isn't significant.

---

### Post by Mr. Picklesworth on 2009-03-06
> **DoktorSeven said:**
> I *do* use something other than gnome -- fluxbox.  However, applications that run independently of gnome still require it, and it seems to be spreading out to pretty much every single desktop application, so it will be increasingly difficult to simply avoid.

Zombie thread, but I am surprised we didn't finish convincing you ;)
The alternative to dbus is having hundreds of little daemons running *continually* in the background. Dbus lets them run on demand and provides a consistent interface by which they communicate.

Further, any Unix system already has piles of userspace daemons. It's part of that "applications do one thing well" philosophy. Dbus just takes that a step further. It replaces older frameworks like CORBA. If it wasn't dbus, there would be something else. (Probably something heavier, uglier and less useful).

---

### Post by gnomeuser on 2009-03-06
[DeviceKit is dead, Long live udev](http://lists.freedesktop.org/archives/devkit-devel/2009-March/000123.html) - no kidding, it's functionality is being folded into udev-extras.

---

### Post by bapoumba on 2009-03-06
> **gnomeuser said:**
> [DeviceKit is dead, Long live udev](http://lists.freedesktop.org/archives/devkit-devel/2009-March/000123.html) - no kidding, it's functionality is being folded into udev-extras.
Thanks, closing then :)

---

