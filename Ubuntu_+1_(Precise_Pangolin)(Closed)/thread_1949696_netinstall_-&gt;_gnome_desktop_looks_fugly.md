---
title: "netinstall -&gt; gnome desktop: looks fugly??"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2012-03-30
Hello All

I'm experimenting with a 'gnomebuntu' install of just gnome-shell on top of the 12.04 netinstall command line environment, along with nvidia restricted drivers on this HP xw6200 pc with nvidia graphics.

[LIST]
[*]Netinstall from the 30th March daily i386-pae went fine.
[*]Rebooting left me with screen artifacts
[*]Did an Ctrl-Alt-F1 to get a console, logged in fine
[*]Ran sudo apt-get gnome
[*]Got a fairly basic Gnome shell desktop, which booted into Gnome Classic 
[*]Installed and used jockey-gtk to load the nvidia drivers
[*]Rebooted into Gnome Shell
[*]Looks kind of fugly with a mis-matched theme and fisher-price icons
[*]Only had Epiphany Web browser, and Abiword/Gnumeric along with Rhythmbox, but also Inkscape and GIMP
[*]Installing LibreOffice, Firefox and Ubuntu Restricted Extras now
[/LIST]

Anyone any ideas on how to get extra themes?

The default one looks totally out of place.

[http://dl.dropbox.com/u/8403291/gubuntu-from-netinstall.jpg](http://dl.dropbox.com/u/8403291/gubuntu-from-netinstall.jpg)

PS:had to add libreoffice spelling and alsa-utils using synaptic (nostalgia).

---

### Post by NHclimber on 2012-03-30
Interesting take on Kandinsky...

I ended up editing the icon theme because I'm not a fan of the '*-symbolic' icons.

---

### Post by jbicha on 2012-03-30
Your icon theme is the default for upstream but the window theme isn't right. Do you have gnome-themes-standard installed?

The missing icons next to Personal, Hardware, and System when you don't use Ambiance or Radiance is a bug.

Alternatively, you can install light-themes if you want Ambiance and Radiance.

---

### Post by keithpeter on 2012-03-31
> **jbicha said:**
> Your icon theme is the default for upstream but the window theme isn't right. Do you have gnome-themes-standard installed?

@jbicha

No, I didn't, but then I installed gnome-tweak and that brought in the theme package as a dependency, thanks for pointing out the package name.

@NHclimber

> Interesting take on Kandinsky...

Alas, not my work

[http://www.andrewblakedesign.com/?p=77](http://www.andrewblakedesign.com/?p=77)

I'll be fiddling with icon sets when the testing period is over, I don't especially like the default ones either.

Gnomebuntu :twisted:

Just gnome-shell on top of a netinstall is currently...

```
sudo apt-get install gnome gnome-themes-standard ubuntu-restricted-extras libreoffice libreoffice-l10n-en-gb alsa-utils
```

Installing alsa-utils was my way of getting the right sound outputs working on this old HP box, might be better ways.

NB: installing gnome-standard-themes does not add themes to the appearance setting. Still the odd light blue theme.

---

