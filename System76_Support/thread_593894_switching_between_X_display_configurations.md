---
title: "switching between X display configurations"
date: 2007-10-27
forum: System76 Support
---

### Post by dnarnold on 2007-10-27
I need to change my X configuration quite frequently.  For
example, when at home, I want to use a large external display
and the laptop LCD as two displays to get extra real estate.  When
I'm in an airplane, of course, I only want the laptop LCD.
When I am giving a presentation I want to use the resolution of
the projector, and I want to clone that on the laptop LCD
so I can see my presentation without turning around to view
the screen.  Etc.

What is the recommended way to handle this?  My approach has
been to make a whole bunch of xorg.conf files and point
to one of them with a symlink from /etc/X11/xorg.conf .  For
convenience I have a script to change the symlink on demand.

Does anyone have experience with a better way?

This is on a white Darter 1 with Kubuntu 7.10 (gutsy).
Thanks for any help -- Doug

---

### Post by thomasaaron on 2007-10-29
I'm not sure of any native ways of doing this.

What would be cool, though, is to have a few custom launchers on your toolbar, each of which pointed to a shell script that dumped in the appropriate xorg.conf for your needs. Or maybe one icon that pointed to a shell script that cycled the xorg.conf files.

You could even make a simple python app with a button for each xorg.conf.

---

