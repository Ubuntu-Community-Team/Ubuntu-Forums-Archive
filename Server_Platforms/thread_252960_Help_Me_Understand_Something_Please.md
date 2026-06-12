---
title: "Help Me Understand Something Please"
date: 2006-09-07
forum: Server Platforms
---

### Post by inthewayboy on 2006-09-07
Okay, so I'm a Win32 geek trying to get comfortable with linux for various reasons, mostly LAMP. I've been using the server distro for a while and have gotten pretty used to it, doing everything from the shell.

However I'm still feeling a little out of place with no GUI, so I started researching that on the forums. Thanx to a few posts I've managed to get what I think is a rather lite GUI installed using Xfce. Here are the packages I install:

x-window-system-core xfce4 wdm synaptic firefox thunar mousepad

That gives me the basics...a desktop, a menu, and a few tools to handle the easy stuff. I'm pretty content with this too!

However, I like to know whats happening as much as possible. I think I know how things work, but then I start getting a little confused.

I looks like the x-window-system-core gives you the ability to run GUI stuff, but it's not actually a desktop environment right? That's where the Xfce comes in, along with wdm to handle the logon GUI.

My questions are:

1. Once x-window-system-core is installed I still have to choose a desktop environment (That may be the wrong term). Currently I use Xfce, but what other options are there? Is Xcfe similar to KDE and GNOME? It sounds like KDE and GNOME are much more advanced and integrated, which would mean more resources being used.

2. I see a lot of applications that seem to require either GNOME or KDE. There might even be two versions of a tool, one for each. Is this correct?

3. Let's assume I stick with Xfce, what kinds of applications can that run? I see options to start GNOME or KDE services, so can it handle applications from either environment? Or is that something totally different?

4. Seeing as this is a server, if I had to choose between KDE or GNOME is there any reason to pick one over the other?

5. wdm handles the logon GUI, and I see gdm but I think that requires GNOME. Are there any other options if I stick with Xfce?

I guess I'm just trying to get a bigger picture of it all. I don't wanna load up the server with a bunch of useless packages just so I can run a few applications.

BONUS QUESTION: In Xfce I'm trying to add a menu item for synaptic. When I create the menu item to run the application it loads it in read-only mode, most likely cause there is no sudo tied to it. I tried adding that to the command and then nothing happens. How do I handle situations like that?

Thanx in advance, and I apologize if this has been discussed to death. The search terms are just too generic to get anywhere with. Also, if anyone has any links to sites that might help explain this better (But not from a desktop/idiot point of view) I'm more than willing read and re-read things. Thanx!!!

---

### Post by skymt on 2006-09-07
1. You're absolutely right about the relationships between XFCE, KDE, and GNOME. XFCE is lightweight but also light on features. KDE and GNOME both have loads of features and applications integrated with them, but run slower and take up more resources.

There are basically three desktop environments, but there are more window managers than you can shake a stick at. A window manager is technically the program that manages windows (duh!), but many of them offer ways to launch and switch applications, so some people run a plain window manager instead of a real "desktop environment." Popular window managers to run "vanilla" include fluxbox, windowmaker, openbox, and icewm.

2. In general, applications for any desktop environment will run on any other. They just run best, look best, and have more features on their native desktop. KDE applications, however, have a little more trouble running on non-KDE desktops then GNOME apps on non-GNOME desktops. XFCE apps will run anywhere.

3. Stick mostly with GNOME apps for XFCE. KDE apps bring a lot more daemons and libraries with them.

4. It depends on how busy your server gets. If it's often under a high load, you want as light a desktop as possible. In that case, use something like Fluxbox. If it gets less traffic than that, you can use something heavier, like XFCE or GNOME. KDE also, I guess. I just don't like it. :cool: 

5. GDM was made for GNOME, but only requires the regular GTK libraries. It will work fine with XFCE.

Bonus answer: Use 'gksudo synaptic'. This will bring up a window for you to enter your password. Also, look into aptitude. It's like synaptic, but text-based. It's also much more powerful, with better broken package handling and dependency tracking.

---

### Post by az on 2006-09-07
It is stacked like this:

Your running application (firefox)
Window Manager
Desktop Environment
Login Manager (Session manager or desktop manager)
X server
Kernel

---

### Post by inthewayboy on 2006-09-07
Nice, very good info. Coming from a Win32 world it's a little different to have all these components just to run the desktop and applications. But I can see the benefit of the flexability.

The more I'm investigating I'm seeing a pattern, with the gksudo being the gui version of sudo. I've seen it on other apps, it looks like it's not standard but kinda common at least. Anywho, I'm doing a reload now with some of that new info just to sharpen up and I'll see how that works.

And thanx again, I always hate having to ask these easy questions. I can find the answeres to the hard ones, but these kinds always stump me.

---

### Post by rastilin on 2006-09-08
You might also want to pull in the "xubuntu-desktop" package, which should autoconfigure menus, themes and miscellaneous other stuff like the xubuntu distribution is.

Incidentally one of the reasons kde pulls more resources in xfce is because both gnome and xfce are built with the gtk+ libraries while kde is built with qt. With gnome apps the libraries are already loaded but kde needs to use it's own.

---

