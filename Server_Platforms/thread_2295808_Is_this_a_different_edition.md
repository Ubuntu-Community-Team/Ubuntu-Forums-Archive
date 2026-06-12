---
title: "Is this a different edition ?"
date: 2015-09-21
forum: Server Platforms
---

### Post by soamz on 2015-09-21
Is the normal ubuntu and server edition different ?
How different?

---

### Post by CharlesA on 2015-09-21
Server edition has no GUI installed by default.

---

### Post by soamz on 2015-09-21
I see. 
So, how does someone do the actions ?

---

### Post by v3.xx on 2015-09-21
> **soamz said:**
> I see. 
So, how does someone do the actions ?
With much difficulty if you do not know how to use the command line.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[https://help.ubuntu.com/lts/serverguide/serverguide.pdf](https://help.ubuntu.com/lts/serverguide/serverguide.pdf)

---

### Post by deadflowr on 2015-09-21
> **soamz said:**
> Is the normal ubuntu and server edition different ?
How different?

Their quite different, beyond gui issues.

The server edition has a far more advanced installation process, for one.
You set various configurations like hard drive space used, ubuntu archives to connect to, networking settings, etc etc,
and you pick and customize what packages you want to install.

The desktop version automates (or makes them easy to setup) most of those functions, and packs it with a slew of packages that will be installed, regardless of how you feel about them.

The installers are also both different in that the desktop version is more user friendly and easy to understand.
(The server installer needs your attention from time to time. Where as once you get past a certain point with the desktop version, you can sit back and let it go)

But if any significant difference can be found between the two it would be that server versions tend to allow you to make the system server-side heavy, while the desktop version is built client-side heavy.

But come post-installation, either can be turned into the other. If one wants.

Hope it helps.

---

### Post by CharlesA on 2015-09-21
Pretty much nailed it ^.

The server installer is text-based while the desktop install is GUI based.

I can't think of any reason for someone to use the server ISO to do an install unless it was actually going on a server.

If you want to pick which packages and whatnot you want to install, there is always the mini iso.

---

### Post by alxhoff-d on 2015-09-22
The server install not installing a GUI is particularly helpful for low cpu or gpu power/memory systems

---

### Post by CharlesA on 2015-09-22
> **alxhoff-d said:**
> The server install not installing a GUI is particularly helpful for low cpu or gpu power/memory systems

Minimal CD would be a better idea in that case. [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by sudodus on 2015-09-22
> **CharlesA said:**
> [QUOTE=alxhoff-d;13360466]The server install not installing a GUI is particularly helpful for low cpu or gpu power/memory systems

Minimal CD would be a better idea in that case. [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)[/QUOTE]

In many cases, yes. I use the mini.iso

But if the user has a slow or unreliable internet connection and/or wants to install more than once, the server iso is better, because more of the system can be installed from the CD/DVD/USB drive, and less must be downloaded via the internet each time.

I have tested and compared. The final result is almost the same (for a minimal text based system). Not exactly the same. And installing from the server iso is faster (much faster if the internet connection is slow).

---

### Post by TheFu on 2015-09-23
I always install the "server" version.
Tried the mini.iso version and networking worked for the installation, but not later. I don't need that hassle.
Dropped the desktop distro when "Unity" became standard and Canonical decided to make a little extra money be sending every "lens" query to 3rd parties without asking me to opt-in. Plus Unity didn't run in a VM very well.  I moved to XFCE, then LXDE, and now run plain openbox or fvwm-crystal for the desktops (where I want a desktop).  Plus I find network-manager to suck huge-ones and never, ever, want to see that thing again in my life.  Server doesn't have it.  Server is still bloated with stuff I don't want.  I do manage about 20 systems, so having all of them from the same base is more convenient.

The CLI is better for me anyway. For me, Point-n-Click just means I haven't automated the task yet.  A GUI is just a way to have more terminals available ... and a necessary evil for email and browsing.  Right now, on my netbook, there are 9 "windows" - 3 are GUI programs (thunderbird, firefox, keepassx) and the rest are xterms - most connected to other systems around the world.

I am not a typical user, probably.

If I want a truly minimal system (perhaps for an email gateway, not a full email server), the Debian mini-installer is much, much, lighter.  That means a cheaper VPS in the cloud can be used, since they charge mainly by RAM amount-disk and CPU speed don't matter for us, for this purpose.

Lastly, a reason to install a server is to keep the noobs away.  Lots of "IT professionals" will feel comfortable using a mouse to point-n-click around, but when confronted with a text screen with 1 word ...
> Login:
on the console, they keep walking.  I don't want some bored admin to decide to play some flash game on my server. If they don't know how to install the GUI, good. The box can do what it is supposed to do.

---

