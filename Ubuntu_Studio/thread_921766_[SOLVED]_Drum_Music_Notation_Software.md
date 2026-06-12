---
title: "[SOLVED] Drum Music Notation Software"
date: 2008-09-16
forum: Ubuntu Studio
---

### Post by tgerbert on 2008-09-16
I'm looking for music notation software, specifically for drums (so I need special note heads, like diamond, cross, etc). Anybody have any suggestions?

MuseScore seems okay, but is a bit buggy yet...

Can't really figure out how to use Rosegarden for notation without also recording.

NoteEdit is also a little weird (starts up without window decorations...ie. no maximize/minimize buttons or title bar, maybe because it's a KDE app and I use gnome?)

I'd prefer to not enter text (I think)...will abc or lilypond even do the drum note heads?

---

### Post by Stochastic on 2008-09-17
I **know** lilypond will do it, take a read through the /usr/share/doc/lilypond/examples/input/regression/note-head-style.ly
file for more info on it.  It's not the most elegant way of doing things, but it's bug free.

---

### Post by angelsguitar on 2008-09-18
Check out Mup from [http://www.arkkra.com/]("http://www.arkkra.com/").  Although not free (costs $29) it's cheap, does drum notation and much more, and its syntax is a lot easier than Lilypond's.

---

### Post by tgerbert on 2008-10-16
Well, after having poked around for a bit with the various programs I've decided that Lilypond is my best bet.

I still think the syntax is slightly non-sensical, and the documentation could be a little clearer, but it's not so bad once you get the hang of it.

---

### Post by angelsguitar on 2008-10-16
> **tgerbert said:**
> Well, after having poked around for a bit with the various programs I've decided that Lilypond is my best bet.

I still think the syntax is slightly non-sensical, and the documentation could be a little clearer, but it's not so bad once you get the hang of it.

If you are into Lilypond, there are a couple of GUI front end tools or that export to Lilypond format that can make it easier, like Rosegarden, Denemo, NoteEdit, NtEd (this one looks great; highly recommend, look for it in [http://vsr.informatik.tu-chemnitz.de/staff/jan/nted/nted.xhtml]("http://vsr.informatik.tu-chemnitz.de/staff/jan/nted/nted.xhtml")), MuseScore.  Just do a quick search on google or your prefered search engine, or even in the forums for more info.

Edit: I believe you've tried some of the above, except NtEd.  It's a nice program from the creator of NoteEdit.  I've used it, and is very intuitive, the latest version has drum notation, and very easy to learn,  Check it out, maybe is what you are looking for.  I'm not sure if there's a package for it on Ubuntu's repos, and if it is, I would probably be a little outdated.  I would recommend you install the one from the website.  You'll have to install a few dependencies first, and then compile it, but everything is explained in the website.  Let me know if you need any help.

---

### Post by tgerbert on 2008-10-17
Took a look at NtEd, and it does seem very good ... but can't help but notice the drum bar doesn't have an X note head. ;)

I think I'll keep my eye on that one though.

Will Rosegarden let you edit scores without recording?  I've mucked around the notation editor, but can only seem to get it after having recorded something.

---

### Post by Bucky Ball on 2008-10-17
The bad news here is that I have Vista on my laptop for one reason and one reason only ... Sibelius 5. In my opinion, nothing comes close.

---

### Post by angelsguitar on 2008-10-17
> **tgerbert said:**
> Took a look at NtEd, and it does seem very good ... but can't help but notice the drum bar doesn't have an X note head. ;)

I think I'll keep my eye on that one though.

That's funny, I'm using NtEd version 1.3.3 right now (and I believe there are newer versions) and mine has it.  Maybe you have an older version installed?

> Will Rosegarden let you edit scores without recording?  I've mucked around the notation editor, but can only seem to get it after having recorded something.[/QUOTE]

I'm not that familiar with writing music with Rosegarden; only use it for recording MIDI.  Sorry, frankly, I don't know. :confused:

---

### Post by angelsguitar on 2008-10-17
> **Bucky Ball said:**
> The bad news here is that I have Vista on my laptop for one reason and one reason only ... Sibelius 5. In my opinion, nothing comes close.

To be honest, I too have a copy of Sibelius 5, which haven't used for months... been using Mup lately.  

By the way, I believe you can run Sibelius 5 in wine, using winetricks.

---

### Post by Bucky Ball on 2008-10-17
> **angelsguitar said:**
> 

Will Rosegarden let you edit scores without recording?  I've mucked around the notation editor, but can only seem to get it after having recorded something.


Angel, create a blank sequence then open that in Lilypond (the Rosegarden notation editor), and start composing! :)

---

### Post by Dufangoer on 2008-10-19
I'm going to bump the tread up.cheap wow power leveling --------------------------------**buy [eq2 plat](http://www.epaxx.com),  [eq2 gold](http://www.epaxx.com), [everquest platinum](http://www.epaxx.com), [rs gold](http://www.favgames.com/rs-gold/), [silkroad gold](http://www.favgames.com/silkroad-gold/),**

---

### Post by angelsguitar on 2008-10-19
> **Bucky Ball said:**
> Angel, create a blank sequence then open that in Lilypond (the Rosegarden notation editor), and start composing! :)

Thanks for the tip! I forgot: you can create empty fragments in Rosegarden by double-clicking on the desired area.  Once created, you can open that fragment in the score editor and begin adding notes to it.

---

