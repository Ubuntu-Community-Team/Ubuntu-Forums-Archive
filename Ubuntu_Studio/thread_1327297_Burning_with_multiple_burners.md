---
title: "Burning with multiple burners"
date: 2009-11-15
forum: Ubuntu Studio
---

### Post by oldsam on 2009-11-15
Hi,

I am using multiple burners with brasero. I want to access brasero from
an external application and here's what i found out until now:

with 'brasero -a' I can create my project i want.
With 'brasero -r' I can burn this project directly.

What I miss is that I can specify a burner (Sometimes I use 5 burners
simultaneously) and then I've got a list like that when I want to choose
my burner in brasero:
"Empty CD-R 700MB"
"Empty CD-R 700MB"
"Empty CD-R 700MB"
"Empty CD-R 700MB"
"Empty CD-R 700MB"

How do I know which burner it is? Can I perhaps specify the burner as a
parameter to brasero (that would be the best solution)?
By the way, K3B puts the name of the drive in brackets if is are more
than 1 burner. But I cannot use K3b because it can be started only
once...

What suggestion do you have how to manage these burnings? Maybe with another program.

Regards,
Samuel

---

### Post by fanum on 2010-01-31
Have you considered using the commandline? 

[http://www.ghacks.net/2009/01/27/burn-cds-from-command-line/]("http://www.ghacks.net/2009/01/27/burn-cds-from-command-line/")

---

### Post by LuridCinema on 2010-01-31
[http://sourceforge.net/projects/turbojet/](http://sourceforge.net/projects/turbojet/)

I have used turbojet2 works like a charm !!!!

---

### Post by oldsam on 2010-02-03
Thank you for your answers. In the meantime I've contacted the developers of Brasero and they added a feature that you can specify a drive with the command line.
It will be in the next GNOME release, 2.30 ([https://bugzilla.gnome.org/show_bug.cgi?id=602181](https://bugzilla.gnome.org/show_bug.cgi?id=602181)).

---

### Post by Grenage on 2010-02-03
That's what I call service!

---

### Post by oldsam on 2010-02-03
Yeah, that's how Open Source projects (should) work.

---

### Post by wkulecz on 2010-02-03
Are you burning five different iso images to five different drives? or the same iso to five drives for "production"?  The later is what I would like to know how to do.

--wally.

---

### Post by LuridCinema on 2010-02-03
YES Im doing that w/ Turbojet2 you can burn the same image to all 5 at same time or 5 different images at same time. All w/ a GUI

---

### Post by oldsam on 2010-02-03
I burn recordings to an Audio disk, every burning process is seperate.
Sometimes I have different recordings for each burner and sometimes it's all the same.
But using 5 burners is an exception, mostly I use 2 or 3.

I don't know if it is possible to burn one image to all drives without starting a seperate burning process for each burner.
Maybe someone else can help.

EDIT:
LuridCinema was faster.. I think I really should take a closer look at TurboJet2, the first view scared me a bit (UI not so user-friendly)

---

### Post by LuridCinema on 2010-02-03
> **oldsam said:**
> 
LuridCinema was faster.. I think I really should take a closer look at TurboJet2, the first view scared me a bit (UI not so user-friendly)

You are correct, the UI and docs seemed cryptic, but once you get it down it is simple. tell ya what I'll post a how to on burning w/ TJ2 on Youtube & get back w/ ya

---

### Post by LuridCinema on 2010-02-03
Here ya go folks a Youtube How To tutorial on how to setup & use turbojet2
[http://www.youtube.com/watch?v=BNuCcZ0aLuU](http://www.youtube.com/watch?v=BNuCcZ0aLuU)

enjoy !

---

### Post by &#5097;&#5103;waya on 2010-05-15
64-bit deb anytime soon?

---

### Post by pezgordo on 2011-03-02
Tried using Turbojet2. for burning same image to several DVD using 4 burners.


I always get an error message:

"unable to reload tray: No such file or directory"

I suppose is not critical since every disk works fine.

Also Since I have to do hundreds of copies, is there a way to add a number of copies parameter? couldn't find it on the GUI or man

---

