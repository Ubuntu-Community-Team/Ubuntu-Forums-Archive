---
title: "gnome-screensaver settings"
date: 2007-02-18
forum: The Cafe
---

### Post by kevinlyfellow on 2007-02-18
Have the gnome devs finally given up and put in a way to change the settings for screensavers?  I know this was a big controversy when it was first released, and quite frankly, I'm getting tired of hoping that our gnome overlords implement it.  I love gnome and I think they have made much better decisions than others when developing a de, but sometimes the choices they make are incredibly poor and we all suffer from their refusal to change things.  Sorry about the rant... but I know when this first came out the dev was very upset that people didn't see things his way, and it appeared like nothing was going to change.  I really would like to have this option!

---

### Post by yabbadabbadont on 2007-02-19
I don't think so.  That is one of the things I hate about Gnome, the "we know best", attitude of the devs.  Still, they are the ones writing it, so they get to decide how it works.  :lol:

In the meantime see this:

[http://ubuntuforums.org/showthread.php?t=198809](http://ubuntuforums.org/showthread.php?t=198809)

---

### Post by Wolki on 2007-02-19
I'm not 100% sure, but I think the necessary pieces are in place now (ie. since edgy). You should be able to create new screensaver themes as a normal user as well as enable/disable them. There is no UI for it, though; it shouldn't be too hard to write one but it seems noone was interested in writing it yet.

---

### Post by ssam on 2007-02-19
if you are not a programmer yourself, you cold always make a bounty for it.

---

### Post by kevinlyfellow on 2007-02-19
> **Wolki said:**
> I'm not 100% sure, but I think the necessary pieces are in place now (ie. since edgy). You should be able to create new screensaver themes as a normal user as well as enable/disable them. There is no UI for it, though; it shouldn't be too hard to write one but it seems noone was interested in writing it yet.

That's excellent news!  I would love a gui, but as long as there isn't a hackish way of solving the problem, I'll be happy.  I've tried the whole xscreensaver replacement, but there were too many drawbacks.

---

### Post by IYY on 2007-02-19
I'm pretty sure that the settings will be implemented soon enough. They were not actually "removed" as most people here believe, but rather the entire screensaver application was rewritten, and the settings feature was not implemented.

---

### Post by Wolki on 2007-02-19
IYY: While it is ture that gnome-screensaver was completely rewritten, I'm not so sure about the options dialogs. While the developer may change his mind about it, gnome-screensaver is supposed to work with themes rather than config options. This is an interesting idea and has several benefits for users (like the ability to easily have more than one configuration per screensaver available in random mode, and the ability to easily share cool themes with other people through art&theme sites like art.gnome.org or gnome-look). So far it doesn't seem to work out, but I hope this will change. The approach wouldn't be incompatible with options directly in gss-config, but it might make sense to have theme creation as a separate program which can be a bit more crack in the ui department since the only people who will run it are those who really care about screensavers (unlike me, for example).

kevinlyfellow: OK, here's a brief explanation of how to do it.

Step 1: Go to /usr/share/applications/screensavers, you will find a lot of files, one for each default screensaver. Find the one you want to modify it, and copy it somewhere you have write access (for example, your home dir)

Step 2: Open that file with the text editor of your choice. The line starting with "Exec:" is the command used to start the screensaver, add the options you want there. The options are described in the screensaver engine's man page. (Note that some options might not be possible to change this way; I'm not really sure. You can change a lot of settings, though)
As an example, here's a complete theme for the gltext screensaver:

```

[Desktop Entry]
Encoding=UTF-8
Name=GLText
Comment=Displays a few lines of text spinning around in a solid 3D font. Written by Jamie Zawinski.
TryExec=gltext
Exec=gltext -text "boring text la la la" -root
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver
X-Ubuntu-Gettext-Domain=xscreensaver

```

Step 3: If you want your new theme to replace the default for that screensaver, leave the names as they are; if you want to have your new theme in addition to the default one, change the name entry (and likely the filename too, I'm too lazy to check right now).
Step 4: Start the gnome-screensaver preferences applet. Drag the theme you created to it, close the window and start it again. Your customized screensaver should be available now.

These are the steps to add/change screensavers for a single user. To change the default for all users, edit the .desktop file in /usr/share/applications/screensavers directly, you will need to have administrative access to do this, though.

Disabling certain screensavers without removing them should be possible too, but the way that used to work doesn't seem to any more. If I figure out a way to do it reliably, I'll add it. This is something that is planned for the screensaver preferences applet though.

---

### Post by kevinlyfellow on 2007-02-19
Thanks Wolki   had only half of that figured out.  I think the theme idea could work, but we need an easy way to create the theme (and one that is obvious to users to know that they can create it).  I've been trying out different programming languages to see if I can find one that right for me so that I can start making my own stuff.  Anyways its clear that some screensavers were not built for the theming mentality and deal better with configuration than theming.  Case in point, gltext.  One that really annoys me is glslideshow because it doesn't provide a commandline option to change the directory it reads, so editing the 'Exec=' line won't help.  Does anyone know how to change the directory for glslideshow?

I've also found a ton of xml files in /usr/share/xscreensaver/config  What relation does this with theming?

---

### Post by Wolki on 2007-02-20
> **kevinlyfellow said:**
> Thanks Wolki   had only half of that figured out.  I think the theme idea could work, but we need an easy way to create the theme (and one that is obvious to users to know that they can create it).  I've been trying out different programming languages to see if I can find one that right for me so that I can start making my own stuff.

Yeah, I'm sure a theme creator would be well appreciated. The basic stuff shouldn't be that hard, though if you want things like preview it could get complicated.
If you want to work on it, I'm sure you'll find a lot of help and support.

> Anyways its clear that some screensavers were not built for the theming mentality and deal better with configuration than theming.  Case in point, gltext.  One that really annoys me is glslideshow because it doesn't provide a commandline option to change the directory it reads, so editing the 'Exec=' line won't help.  Does anyone know how to change the directory for glslideshow?

I've also found a ton of xml files in /usr/share/xscreensaver/config  What relation does this with theming?

 I guess those config files have something to do with it, some screensavers are a bit weird.I'd recommend using one of the several picture screensavers that is more easily configurable.

---

### Post by MasonM on 2007-04-22
Changing the image directory for GLSlideshow is pretty simple.

Create a file in your home directory called .xscreensaver

with this entry:

imageDirectory: /path/to/your/images

and GLSlideshow will look there for the images.

---

### Post by jiminycricket on 2007-04-22
The other one that bugs me the most is gnome-power-manager settings.  It's so impoverished; even though all the settings are in gconf, they're in numbers and not easy to understand.  I can't even set it to hibernate when I press the power button when I go in there, or to set it to sleep (hibernate's not an option there either...) at a time greater than an hour, grr...

---

