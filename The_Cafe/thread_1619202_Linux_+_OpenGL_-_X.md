---
title: "Linux + OpenGL - X"
date: 2010-11-11
forum: The Cafe
---

### Post by anark10n on 2010-11-11
[SIZE=2]I'm pretty sure this the place to start this thread, [SIZE=1](at the very least pretty safe) [SIZE=2]but i had this idea bouncing around in my head for quite some time though, pretty sure i'm not the only one, but would it be feasible to compile a Linux distro that uses opengl as its graphics API rather than X and not need Mesa or anything similar. My apologies if there has been a previous thread on this subject, couldn't find it.[/SIZE][/SIZE][/SIZE]

---

### Post by del_diablo on 2010-11-11
MESA == openGL
X11 = A gigantic thingy which also provides GUI interface......
And I would recommend reading this page: [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

---

### Post by Austin25 on 2010-11-11
oops- double post :oops:

---

### Post by Austin25 on 2010-11-11
I get what you're thinking: a non-window based gui for pc's, but X is still a good idea. I was thinking a video game type of user interface, but I'm nowhere skilled or informed enough to implement it.

---

### Post by Dustin2128 on 2010-11-11
it wouldn't be eliminating x, but you could always configure a tiling window manager to look kinda like a game console. If you actually want to replace X with opengl, besides being royally screwed if compositing (did I spell that correctly?) isn't available on your card, I think it'd be rather difficult.

---

### Post by anark10n on 2010-11-12
I got all the stuff working okay on my pc, i wasn't asking out of some issue i had, just wondering if it would be feasible and more practical to to implement a graphics system for Linux based on opengl. I was thinking it would at least eliminate some runtime overheads by eliminating X, (studying software development), any clarity on this topic would be appreciated.

---

### Post by MasterNetra on 2010-11-12
> **anark10n said:**
> [SIZE=2]I'm pretty sure this the place to start this thread, [SIZE=1](at the very least pretty safe) [SIZE=2]but i had this idea bouncing around in my head for quite some time though, pretty sure i'm not the only one, but would it be feasible to compile a Linux distro that uses opengl as its graphics API rather than X and not need Mesa or anything similar. My apologies if there has been a previous thread on this subject, couldn't find it.[/SIZE][/SIZE][/SIZE]

Just wait for Wayland. Suppose to run on OpenGL.

---

### Post by moma on 2010-11-12
Hello,
I do agree with MasterNetra: Wait for Wayland.

The old X (or Xorg) is command/instruction based and network transparent. It can send drawing commands through a local socket or network; Which? It does not matter. Wayland will be different. Wayland will use shared memory areas where client applications draw directly via OpenGL. The Wayland's composer will then read these memory blocks (graphics) and combine them to a desktop picture. So Wayland will be very fast, no frame tearing or flickering to see!

I have already tested some of the Waylands features. I found a helper script on: [http://www.chaosreigns.com/wayland/](http://www.chaosreigns.com/wayland/)

But first, I had to uninstall Nvidias commercial driver and installeds "libgl1-mesa-dri-experimental" package instead. Ref. this [posting...]("http://lists.freedesktop.org/archives/wayland-devel/2010-November/000121.html") 
The script needs also the [aptitude]("apt://aptitude") tool/package. 

Then the Wayland _demo_ worked fine. The last few lines of the script will start the Wayland and demos.
[[img]http://bildr.no/thumb/757064.jpeg[/img]](http://bildr.no/view/757064)
Thanks to her/him who made the script.

Neither Nvidia or AMD/ATI support Wayland yet by their commercial drivers. [COLOR="Red"]We should put press on them![/COLOR]

Learn more about Wayland: [http://wayland.freedesktop.org/](http://wayland.freedesktop.org/) It's absolutely an awesome piece of technology.

**EDIT**: Also Fedora embraces Wayland and will have it in Fedora 15/16.
Ref. [http://www.osnews.com/story/24029/Fedora_To_Eventually_Move_to_Wayland_Too](http://www.osnews.com/story/24029/Fedora_To_Eventually_Move_to_Wayland_Too)

**EDIT**: Wayland demo video:
[http://www.phoronix.com/scan.php?page=news_item&px=ODgwMw](http://www.phoronix.com/scan.php?page=news_item&px=ODgwMw)

---

### Post by anark10n on 2010-11-15
Following question may seem retarded to those in the graphics-know, i'm not quite there yet.

Perhaps somebody could better explain what wayland is and what it isn't, like X or not, will it replace X, the issue of overheads (hate to bring it up again, but not everybody has hardware that will make overheads a moot point).

Thanks to anyone who understands better than i...

---

### Post by anark10n on 2010-11-17
oops double post!

didn't see the link that moma put up, got the info and thanks...

but still not quite what i had in mind, but close and good enough i say

anybody know how to close threads?

---

