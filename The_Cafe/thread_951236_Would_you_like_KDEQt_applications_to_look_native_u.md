---
title: "Would you like KDE/Qt applications to look native under Ubuntu (read:GNOME)?"
date: 2008-10-17
forum: The Cafe
---

### Post by LuisAugusto on 2008-10-17
I'm just pasting what I wrote at brainstorm:

[http://brainstorm.ubuntu.com/idea/14516/](http://brainstorm.ubuntu.com/idea/14516/)

> Description
I think it will be quite smart if a Ubuntu user installs a KDE/Qt application could be automatically themed to match the human (or whatever thing being used). This could be done with QGtkStyle ( [http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/](http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/) ).

This, in my humble opinion, would get rid of some integration problems between GNOME and KDE applications (aesthetically) , it will make the user experience less confusing and more consistent.

Just look:
[http://chaos.troll.no/~jbache/human.png](http://chaos.troll.no/~jbache/human.png)
[http://arstechnica.com/journals/linux.media/gtkqt1.png](http://arstechnica.com/journals/linux.media/gtkqt1.png)
[http://chaos.troll.no/~jbache/qt4.png](http://chaos.troll.no/~jbache/qt4.png)

Thanks in advance for your attention.

-Just to clarify (since I can't believe somebody can rate this down...), I meant that KDE/Qt applications installed under Ubuntu (read: Using GNOME as their desktop manager) should get this, I'm not, by any way, trying to say that Kubuntu should use this as their default theme-


---

### Post by MaxIBoy on 2008-10-17
Install KDE (it won't get rid of GNOME, you can have both at once.) There's a theming engine for KDE that allows you to use clearlooks; google for that and you'll find it. Install that theming engine.


After that, things should match up a little bit better, even if you're not using KDE at the time.

---

### Post by barbedsaber on 2008-10-17
I think it needs to be done, compliance is good.
I would also like to see some way to get them to stay the same when you change the default theme. (If the theme engine, whatever it is gtk themes, or metacity, or emerald, I don't understand compleatly) was compatible with qt/Kde, and it would automaticly change the QT/KDE theme when you changed the normal theme.

---

### Post by MaxIBoy on 2008-10-17
The Qt/KDE theme is set by the theming engine. You're not using something else "instead" of Qt.

---

### Post by LuisAugusto on 2008-10-18
> **MaxIBoy said:**
> Install KDE (it won't get rid of GNOME, you can have both at once.) There's a theming engine for KDE that allows you to use clearlooks; google for that and you'll find it. Install that theming engine.


After that, things should match up a little bit better, even if you're not using KDE at the time.

I'm quite aware of that... I don't want to be arrogant, but did you read what I said, or visit the links?

> **MaxIBoy said:**
> The Qt/KDE theme is set by the theming engine. You're not using something else "instead" of Qt.

I'm sorry but you're wrong, this implementation actually uses gtk to render the theme. READ THE LINKS.

---

### Post by Frak on 2008-10-18
I foresee a compat layer being made, endorsed by both, then never developed again.

Welcome to the general nature of increasing compatibility between 2 open source programs.

---

### Post by MaxIBoy on 2008-10-18
> **LuisAugusto said:**
> I'm quite aware of that... I don't want to be arrogant, but did you read what I said, or visit the links?



I'm sorry but you're wrong, this implementation actually uses gtk to render the theme. READ THE LINKS.

I admit that I'd only ever *heard* of clearlooks for KDE and I remembered something about it still using the Qt engine. I also know from personal experience that when applying themes in KDE, Qt apps take on those themes when running under GNOME. I recognized that the QGTKStyle thing did not use Qt, so therefore it would not work. Thus, I was referring to something entirely different (and possibly a product of my sometimes flaky memory) than that which you linked to.


I'm sorry if you misconstrued that as an insult, I definitely could've phrased that better. :(

---

### Post by LuisAugusto on 2008-10-18
> **MaxIBoy said:**
> I admit that I'd only ever *heard* of clearlooks for KDE and I remembered something about it still using the Qt engine. I also know from personal experience that when applying themes in KDE, Qt apps take on those themes when running under GNOME. I recognized that the QGTKStyle thing did not use Qt, so therefore it would not work. Thus, I was referring to something entirely different (and possibly a product of my sometimes flaky memory) than that which you linked to.


I'm sorry if you misconstrued that as an insult, I definitely could've phrased that better. :(

Don't worry, I overreacted a little, sorry for that too.

I guess you were talking about the clearlooks like and the Gtk-Qt (or was it Qt-Gtk?)engines, which both still exist and serve different purposes.

---

### Post by wersdaluv on 2008-10-18
[SIZE="4"]http://labs.trolltech.com/page/Projects/Styles/GtkStyle[/SIZE]

---

