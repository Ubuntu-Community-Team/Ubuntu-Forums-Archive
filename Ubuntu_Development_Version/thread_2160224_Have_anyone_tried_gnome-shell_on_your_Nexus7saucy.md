---
title: "Have anyone tried gnome-shell on your Nexus7/saucy?"
date: 2013-07-06
forum: Ubuntu Development Version
---

### Post by tista on 2013-07-06
Hi all,

For a couple of weeks I've been fighting for Ubuntu Gnome on armhf... ;)

The reference article is here:
[https://live.gnome.org/MichaelHill/Nexus7]("https://live.gnome.org/MichaelHill/Nexus7")

As known well, the saucy preinstalled image of nexus7-team is so hard to install into our nexus7, so I also suggest that we should install raring 1st via preinstalled image and then do dist-upgrading. So why? Yeah the Unity of saucy preinstalled image seems too buggy.  As we know Ubuntu enhances touch interface for phablet devices, but wait a moment! we actually need standard GUI interfaces on such small devices to develop codes, maintain servers, and much more things wherever we go...

I've already built some packages for armhf saucy on my Google drive:
[https://drive.google.com/folderview?id=0B9cS96ptLZMeWHFyUS0zdWRYVHc&usp=sharing]("https://drive.google.com/folderview?id=0B9cS96ptLZMeWHFyUS0zdWRYVHc&usp=sharing")

And here is my desktop of Nexus7/saucy with gnome-shell 3.9.3:
[IMG]http://s15.postimg.org/pc1xigma3/Screenshot_from_2013_07_06_15_19_03.png[/IMG]

The openGLES2 implementations seems to be completed around 50% to run mutter/clutter on this git sources. Surely still gnome-shell crashes frequently though... :p  Basically since a nvidia-tegra3 kernel-space driver couldm't get any "hardware cursor" features, so we might not solve the visual glitch around the area of mouse pointer maybe... this artifact also appears on the compiz based desktop, and Unity.

Then I've found that gnome-session 3.8 series were caused in fail of gdm login on our armhf. Seemed those version tries to find 3D accel drivers which handles DRI2/GLX on user-space driver. But how nvidia-tegra3  should be? no... this driver basically were built without any DRI/AIGLX implementations you know... So I've downgraded gnome-session series to 3.6, I had no choice. And even if we applied gnome-shell 3.9.3 series on our Neuxs7, we should make gnome-session to stop "accel-helper" check running before kicking gnome-shell.

Finally I strongly recommend that we should keep our eyes open to "cogl" upstream. So it makes sense to follow git upsream codes and build from those sources. Anyway Thanks ricotz and jbicha for keeping armhf sources up!! :)

Best regards,
Tista

---

### Post by wojox on 2013-07-06
What app did you use to screenshot that with?

---

### Post by tista on 2013-07-06
@wojox

The gnome's stock "screenshot" app. ;)
works perfectly!

Regards,
Tista

---

### Post by wojox on 2013-07-06
I'll try this today. Nice all I have to do is upgrade from the terminal, sweet. :)

---

### Post by cariboo on 2013-07-07
Removed double post.

---

### Post by Michael_Hill on 2013-08-16
Tista, great to see the progress; I'll update the wiki page. I haven't tried building gnome-shell since the later 3.8 packages (May?), but thanks to you I have 3.9.5 running. I have what I think are some Ubuntu-specific issues (for one, my .xsession-errors shows an upstart problem)... is there anything special required for the upgrade to Saucy?

---

### Post by tista on 2013-08-17
> **Michael_Hill said:**
> Tista, great to see the progress; I'll update the wiki page. I haven't tried building gnome-shell since the later 3.8 packages (May?), but thanks to you I have 3.9.5 running. I have what I think are some Ubuntu-specific issues (for one, my .xsession-errors shows an upstart problem)... is there anything special required for the upgrade to Saucy?

Hi Michael !! ;)

Yeah we still might recommend raring as base platform to run gnome stuffs.. But if guys really want to play with bleeding-edge gnome-applications on our Nexus7(grouper), I could suggest the "Partial Upgrading", not means "fully dist-upgrading"... ;)

Some unexpected cahges would come into our stable environments:

**#1. Ubuntu-touch android kernel on saucy repository**
It's completely different system with our "core" kernel on Nexus7 (grouper). If it come onto our system, we can't boot anymore... So I strongly recommend we should stay with stock kernel on raring (means "don't do upgrading linux-image package!!")

**#2. Xorg with abi14**
I've seen some ugly glitches on gnome-desktop... As known well, we could see newer nvidia-tegra3 package on saucy repository what were built with such new abi14, it works but it leads some visual glitches. So I suggest that "Pin the most of Xorg packages". But don't worry, we could build newer nvidia-tegra3 with raring's abi13 packages manually.

**#3. Cogl with libwayland**
Now Cogl packages can implement the wayland pipeline with some build options, but the problem is the huge complex between raring's wayland pakcages and saucy's one. so we might need some tricks to upgrade some wayland packages with doing "dpkg-ing" via downloaded packages by hand. So my pre-built pakcages already ignored some dependencies to wayland. Because wayland, mir and some newer display-servers today works with compeletely open-sourced display-driver (means both sides in kernel-space kms, user-space drm).
And soon I would update my cogl packages with Ricotz's 1.16 pre-released version...

**#4. Cogl crashes on "multiple sliced textures"**
I think this is the mainly problem that we can't get much stable gnome-shell session yet... nvidia-tegra3 seems to put many objects as "sliced" buffer. A couple of weeks ago, the developers of cogl (Intel stuffs) seemed to do some tweaks to enhance some sliced texture overlays, but soon those commits were "reverted", omg...

**#5. Still kernel stoled with cpu codes in reboot/shutdown**
We saw some trace dump messages on reboot/shutdown in raring, On saucy, I suppose we may see such stacks much more frequently.. Worst case, we can't reboot/shutdown without hard-reset (pressing both of buttons POWER, VOLUME UP and VOLUME DOWN), after boot into bootloader menu, select "Power-off"...

Anyway really thanks for you and your Wiki! ;)

Best Regards,
Tista

---

### Post by f-jandl91 on 2014-07-18
Hello, I am struggling to get this running on the Transformer TF700T and since it is a Tegra 3 device I would like to know if there is any progress!
What version of gnome-shell are you running right now and could you provide the debs?

---

### Post by kansasnoob on 2014-07-18
> **f-jandl91 said:**
> Hello, I am struggling to get this running on the Transformer TF700T and since it is a Tegra 3 device I would like to know if there is any progress!
What version of gnome-shell are you running right now and could you provide the debs?

Probably best to open a new thread since that is quite dated - circa Saucy which is now EOL.

---

### Post by cariboo on 2014-07-18
Thanks kansasnoob, thread closed.

---

