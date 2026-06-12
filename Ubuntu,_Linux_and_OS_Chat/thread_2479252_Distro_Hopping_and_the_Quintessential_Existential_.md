---
title: "Distro Hopping and the Quintessential Existential Crisis"
date: 2022-09-19
forum: Ubuntu, Linux and OS Chat
---

### Post by Shibblet on 2022-09-19
I recently decided to give Fedora 36 KDE Spin a try.

I "daily drive" Kubuntu, and have for years.  But decided to make a drive image of Kubuntu, and load up a non-VM of Fedora KDE Spin like a good ol' fashioned Distro Hopper!

These two distributions are mostly the same as far as the desktop is concerned, of course... but there are a few differences that I noticed.

Fedora KDE is using Wayland, Kubuntu 22.04 is still using K11.
Fedora uses Flatpak's, Kubuntu uses Snaps.  There are some serious fundamental differences here.
In order to get most of the software I use, I had to enable the Fedora "Non-Free" repositories, or use FlatPak's.
There are a couple of PPA's I use in Kubuntu and the software is just not available in Fedora.  Ubuntu Cleaner is one I can think of off hand.
Fedora takes longer to boot than Kubuntu...  Not sure why.

I am starting to believe the people who are saying that there's not much difference between the main distributions... For most people.

But, ultimately, I did reload my Kubuntu image to have my quicker booting and PPA's.

The oi' "Snappers" out there could take a lesson from the "FlatPaks."  There doesn't seem to be much of a problem with FlatPaks...
They don't have drive access issues, or missing fonts, and the like.  If you didn't know it was a FlatPak, you'd think it was a regular package.

It seems as if there will always be "subtle" differences between Distros.  Fedora has multple-input selection.  For example: I can set the mouse sensitivity differently on my BlueTooth Trackball, as opposed to my wireless mouse.  Subtle, but not a deal breaker.

Are these the things that cause people to Distro-Hop so many times?  Always looking for the "perfect" distro?

---

### Post by grahammechanical on 2022-09-19
> The oi' "Snappers" out there could take a lesson from the "FlatPaks."   There doesn't seem to be much of a problem with FlatPaks...
They don't have drive access issues,

How come when flatpak apps are sandboxed/confined as much as snap packaged apps?

> One of Flatpak&#8217;s main goals is to increase the security of desktop systems by isolating applications from one another. This is achieved using sandboxing and means that, by default, applications that are run with Flatpak have extremely limited access to the host environment. This includes:

 
[LIST]
[*]No access to any host files except the runtime, the app, ~/.var/app/$FLATPAK_ID, and $XDG_RUNTIME_DIR/app/$FLATPAK_ID. Only the latter two being writable. 
[*]No access to the network. 
[*]No access to any device nodes (apart from /dev/null, etc). 
[*]No access to processes outside the sandbox. 
[*]Limited syscalls.  For instance, apps can&#8217;t use nonstandard network socket types or ptrace other processes. 
[*]Limited access to the session D-Bus instance - an app can only own its own name on the bus. 
[*]No access to host services like X11, system D-Bus, or PulseAudio. 
[/LIST]
 Most applications will need access to some of these resources in order to be useful. This is primarily done during the finishing build stage, which can be configured through the finish-args section of the manifest file (see [Manifests]("https://docs.flatpak.org/en/latest/manifests.html")).

[https://docs.flatpak.org/en/latest/sandbox-permissions.html](https://docs.flatpak.org/en/latest/sandbox-permissions.html)

If a user wants an app to break out of confinement then surely that user will have issues with flatpaks. In my opinion a web browser that can access the root partition (and deb packaged browsers can) is a security risk for the user and everyone else that accesses the internet.

P.S. Distro hopping might have been necessary when Ubuntu was the only distro with the Unity Desktop Environment. But with most distros offering the full range of Desktop Environments there seems little point in distro hopping. Not that I have done much of it.

Regards

---

### Post by zebra2 on 2022-09-19
Good luck on your search for perfection.  You may want to look outside of the OS time space continuum to find it.

---

### Post by Shibblet on 2022-09-19
> **zebra2 said:**
> Good luck on your search for perfection.  You may want to look outside of the OS time space continuum to find it.

When did I say I was looking for perfection?

---

### Post by Frogs Hair on 2022-09-19
I find distro hopping educational especially in regards to package management outside of apt. I don't know of any new desktop environments other than cutefish and the customized KDE environment on Nitrux OS at the moment.

---

### Post by qyot27 on 2022-09-19
> **Frogs Hair said:**
> I find distro hopping educational especially in regards to package management outside of apt. I don't know of any new desktop environments other than cutefish and the customized KDE environment on Nitrux OS at the moment.
This, especially when having to write guides on installing or building software.  Having at least a little familiarity with the target distro makes sense, and in some cases, you may need to rely on a particular distro if the hardware you want to use is niche enough.  There's only a handful of modern distros that still support PPC64 (big endian) or SPARC, for instance.

---

### Post by lammert-nijhof on 2022-09-22
Ubuntu, right or wrong, my distro :)

---

