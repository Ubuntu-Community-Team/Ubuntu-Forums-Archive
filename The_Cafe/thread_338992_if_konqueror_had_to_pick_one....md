---
title: "if konqueror had to pick one..."
date: 2007-01-15
forum: The Cafe
---

### Post by fuscia on 2007-01-15
...either browser or file manager (but not both), which would you want it to be? 

i'd go with browser, myself. i like it a lot as a browser and find it lacking when compared to thunar, especially, as a file manager (not that it's bad. i just like thunar better). hopefully, dolphin will become what thunar is.

---

### Post by Verminox on 2007-01-15
I like Konqueror as a file manager - does exactly what I want it to do.

Just prefer Firefox for browsing.

---

### Post by G Morgan on 2007-01-15
Konqueror is just a KPart viewer. You could build 45 different web browsers and file managers out of it. Same as how in the past Konqueror used to be able to run KATE or Vimpart as it's text editor.

It's important to make this distinction. Many criticise Konqueror of being IE6 like, the reasons for IE6 being bad are it tries to be everything to everyone (and has ActiveX). Konqueror does one thing well, it's a great KPart viewer. As a result it is only as good as it's KParts though. The KHTML browser is probably the best on the planet though, very efficient and good standards support.

The file manager depends heavily on settings, you can turn it into practically any file manager out there.

---

### Post by fuscia on 2007-01-15
> **G Morgan said:**
> The file manager depends heavily on settings, you can turn it into practically any file manager out there.

ok, so one of the things i like about both thunar and nautilus is that i can right-click on whatever directory i'm in and open it as root. how can i do this in konqueror? or. right-click on a file and open it in whichever text editor i'd want to use, as root?

---

### Post by zerhacke on 2007-01-15
I'd stick with file manager.  I love how you can click tools and get a terminal in the current direcotry with it.

Useful when the directory is named some-package-name-x.x.x_x.x-i386.src.

---

### Post by G Morgan on 2007-01-15
> **fuscia said:**
> ok, so one of the things i like about both thunar and nautilus is that i can right-click on whatever directory i'm in and open it as root. how can i do this in konqueror? or. right-click on a file and open it in whichever text editor i'd want to use, as root?

There's a section [[COLOR="Red"]here[/COLOR] ]("http://developer.kde.org/documentation/tutorials/dot/servicemenus.html")on altering the context menus by mimetype.

//edit - perhaps this is something you should put to the Kubuntu developers. It would be a simple enough alteration.//

---

### Post by fuscia on 2007-01-15
> **G Morgan said:**
> There's a section [[COLOR="Red"]here[/COLOR] ]("http://developer.kde.org/documentation/tutorials/dot/servicemenus.html")on altering the context menus by mimetype.

even though that looks like a nightmare for an end user like me, it's nice to know that kind of thing is possible.

> //edit - perhaps this is something you should put to the Kubuntu developers. It would be a simple enough alteration.//

i use kde-core in ubuntu.

---

### Post by G Morgan on 2007-01-15
This is a major difference between KDE and GNOME though. GNOME wants to provide a consistent desktop wherever it is used which is why they get so uppity when someone dares to customise. KDE is about providing the technology and either the users or the distro maintainers are supposed to configure it into an ideal set up for you. Most distro maintainers just leave it as default because its traditional to let users configure it.

---

### Post by MkfIbK7a on 2007-01-15
I dont use konquerer at all anymore but when i browsed with it it used to break my xserver...
so i would say file manager

---

### Post by Lord Illidan on 2007-01-15
Filemanager...

---

### Post by Extreme Coder on 2007-01-15
Web  browser, let Dolphin take the crown of the file-management!

---

### Post by Erunno on 2007-01-15
Well, to make Konqueror either Filemanager or Browser the KParts would suddenly have to be taken out of the KDE architecture and something tells me that is not likely.

I'm content with the filemanager functions so far but I wish they would work on the khtml kpart a bit to bring it up to the standard of other modern browsers like Firefox and Opera. For instance, back and forward in khtml is annoyingly slow (I think it's due to Konqueror not caching websites in memory) and there's the issue with the missing session management (no, the general session management isn't a substitute for me).

---

### Post by fuscia on 2007-01-15
i should have asked this before, but what *is* a _kpart_?

---

### Post by kuja on 2007-01-15
tough call ... I use it for everything from web browsing and ftp to file viewing & management. I suppose if I had to pick it being one or the other, I'd say file manager, because I'd still have Opera around for web browsing, especially seeing as Konqueror is hurting when it comes to web browsing in the caching area (in terms of both the documents/media and DNS caching(had to set up dnsmasq to fix that issue)) As a web browser it also lacks some of the features that I like too ... I guess Opera has me spoiled :D

---

### Post by maniacmusician on 2007-01-15
> **fuscia said:**
> i should have asked this before, but what *is* a _kpart_?
kpart is the structure used to embed one application in another...it could be explained better than I'm doing it right now. For instance, in konqueror, if you double click on a text file, it opens it right inside Konqueror. What it does is takes an application such as kate (dont know what it really uses) and embedds it inside itself.

There was once a super cool project that embedded the Gecko rendering engine into Konqueror using kparts; it was dropped because they couldn't maintain it, but it was awesome.

---

### Post by kuja on 2007-01-15
> **fuscia said:**
> i should have asked this before, but what *is* a _kpart_?
Basically, an embeddable component. Konqueror is a good example ... you could for example preview a kword document in the same konqueror window, or have a konsole part along the bottom. Kontact is another good example, as it embeds kmail, akregator, knotes, as well as several other pim apps in it.

---

### Post by Erunno on 2007-01-15
I did a quick google search as I don't want to give inaccurate information.

First of all, KParts explained by the developers themselves:

[http://developer.kde.org/documentation/tutorials/kparts/index.html]("http://developer.kde.org/documentation/tutorials/kparts/index.html")

This is a documentation for the KDE 2 framework so while the implementation details have most likely changed for KDE 3 I guess that the fundamental idea still applies.

Here's another good explanation (also for KDE2, the web seems to be void of general KParts descriptions or I'm just inept at using google):

[http://phil.freehackers.org/kde/kpart-techno/kpart-techno.html]("http://phil.freehackers.org/kde/kpart-techno/kpart-techno.html")

> Gui components are a very powerful technology. Basically, a component allows an application to provide its features and its interface not only as an application but also as an embedded frame into any other application of the desktop. Each component can be improved separately, and you can assign preferred components for certain tasks. Typical examples: a mail reader requests a Text editor component to compose a new mail; an IDE requests a Text editor to edit the code (not necessarily the same one), a spreadsheet requests a Chart builder to analyse its data; an application requests a html browser for its need, etc. 

Components increase code reuse and modularity, thus should be used as much as possible. To turn components into a reality, KDE made them very simple to write and use. 

In Gnome, the component technology is provided by Bonobo, which is built upon Corba. KDE also used Corba in the past, but eventually dumped it for an home-made technology: KPart.

---

