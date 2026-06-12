---
title: "Why cant I find the 'non alternate' download"
date: 2009-12-13
forum: Ubuntu Studio
---

### Post by pgmer6809 on 2009-12-13
OK, I just zipped over the the Ubuntu Studio Download page ready to download and give it a try.
I see references to the 'alternate' iso image for special cases, but no reference to the 'vanilla' iso image.
Where is it?

As a supplementary question, if I already have Ubuntu Karmic installed, do I need the whole Ubuntu Studio ISO or can I just upgrade to the Ubuntu Studio distro from there?

pgmer6809

---

### Post by rafalcieslak on 2009-12-13
You do can upgrade to Ubuntu Studio! Just install all the 'ubuntustudio' packages from the ubuntu repository.
sudo apt-get install ubuntustudio-*  should work, but I am not sure of this command, I'd rather install them manually from Synaptic (about 20 packages to choose, as I did't found anything that would depend on all of them).

---

### Post by trulan on 2009-12-13
It's a little confusing - the alternate install ISO uses a text-based debian installer, the vanilla ubuntu ISO uses a graphical interface.  The Ubuntu Studio ISO is only availabe in 'alternate iso' format.  That's all you can find, because that's all there is.

But absolutely, you can add the studio packages to a regular Ubuntu install.  They are:
ubuntustudio-desktop (the look and feel, etc. - AFAIK you don't really need this)
ubuntustudio-audio (jack, ardour, and a ton of other software, as well as some settings)
ubuntustudio-audioplugins (plugins and more plugins)
ubuntustudio-graphics (graphics software and a ton of free fonts)
ubuntustudio-video (video editing software)

Did I miss anything?

---

