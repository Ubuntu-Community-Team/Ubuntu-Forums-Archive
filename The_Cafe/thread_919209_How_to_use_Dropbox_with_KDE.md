---
title: "How to use Dropbox with KDE?"
date: 2008-09-13
forum: The Cafe
---

### Post by andamaru on 2008-09-13
Does anyone know how to get dropbox to work with out using nautilus

---

### Post by unimatrix on 2008-09-14
I don't think It's possible yet. But they've released the code, so I'm sure somebody will make it work with Konqueror and/or Dolphin.

---

### Post by G@B0 on 2008-09-14
Try launching nautilus from terminal.

---

### Post by unimatrix on 2008-09-14
That would obviously work, but nobody wants Nautilus in KDE.

---

### Post by andamaru on 2008-09-14
sorry, I already figured it out. Start Nautilus with the no desktop switch and install and configure drop box. once that is done manually start up the daemon on login. You don't get the cool little icons but it syncs all your files.

---

### Post by noremac on 2008-09-14
Something like this would be really useful for a smaller netbook. Something with no actual hard drive. I have installed it on my desktop computer running Gnome, but my Eee running Xubuntu cant yet. So I am looking forward to seeing such a thing work. 

-Cameron

---

### Post by chrigu on 2008-10-08
> **andamaru said:**
> sorry, I already figured it out. Start Nautilus with the no desktop switch and install and configure drop box. once that is done manually start up the daemon on login. You don't get the cool little icons but it syncs all your files.
Mhh everytime I run the command "nautilus --no-desktop" a nautilus windows appears.
How can I run nautilus in the background? Without any window?

cheers,
Chrigu

---

### Post by sagen on 2008-10-10
You don't need nautilis at all, you can just run the daemon.

As explained here:
[http://antrix.net/journal/techtalk/dropbox_kde.html](http://antrix.net/journal/techtalk/dropbox_kde.html)

---

### Post by gcranston on 2009-07-26
> **sagen said:**
> You don't need nautilis at all, you can just run the daemon.

As explained here:
[http://antrix.net/journal/techtalk/dropbox_kde.html](http://antrix.net/journal/techtalk/dropbox_kde.html)


Thanks Sagen.  Works brilliantly.  I even get the dropbox icon in my system tray by running the daemon.

---

### Post by dslipp on 2009-08-31
Seriously brilliant! Worked instantly and flawelessly. My deepest thanks.

Dave

---

### Post by diablomarcus on 2009-12-13
> **sagen said:**
> You don't need nautilis at all, you can just run the daemon.

As explained here:
[http://antrix.net/journal/techtalk/dropbox_kde.html](http://antrix.net/journal/techtalk/dropbox_kde.html)


Thank you so much. Very helpful.

---

### Post by infestor on 2009-12-16
any KDE implementation so far?

---

### Post by .ioannis. on 2010-08-22
In case someone arives to this old thread, there is now a new project to bring Dropbox to KDE, called [KDropbox]("http://kdropbox.deuteros.es/"). It's not well integrated yet, with say Dolphin, but I guess it's a start.

---

### Post by rosencrantz on 2010-08-31
Alas, the kdropbox guy has stopped developing the project after getting some kind of cease-and-desist e-mail from dropbox for using their name and logo.

---

### Post by Danny Dubya on 2010-08-31
> **rosencrantz said:**
> Alas, the kdropbox guy has stopped developing the project after getting some kind of cease-and-desist e-mail from dropbox for using their name and logo.

That's very unfortunate... I hope someone else picks up the newly named final version of that project and continues its development, because I doubt that Dropbox will ever do a thing for KDE.

---

### Post by spupy on 2010-08-31
Too bad about KDropBox. But I don't see a huge problem with using the gtk dropbox client. It looks exactly the same thanks to the qt-like gtk theme.
Integration with Dolphin should be done with the so-called "services" for dolphin. I haven't searched for such but I suspect one is available for dropbox.

---

### Post by stafio on 2011-11-14
Again, in case someone arrives to this old thread, there is now a  [_new project to bring Dropbox to KDE_]("http://trichard-kde.blogspot.com/2010/12/introducing-dropbox-integration-for.html").

This one has nice looking Dolphin integration and there is a .deb (64-bit only) available

---

### Post by oldos2er on 2011-11-14
Hitting snooze button....

---

