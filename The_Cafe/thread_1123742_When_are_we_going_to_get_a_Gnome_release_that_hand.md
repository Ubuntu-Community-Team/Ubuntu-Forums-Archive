---
title: "When are we going to get a Gnome release that handles transparency?"
date: 2009-04-12
forum: The Cafe
---

### Post by detroit/zero on 2009-04-12
Repost of a closed thread.

I think it's a good question and I'm looking forward to some kind of answer, and since I was clearly invited to clutter the database with a second thread, here I am doing as much.

Thanks for the help, guys!

---

### Post by Rocket2DMn on 2009-04-12
Moved to the Community Cafe.

---

### Post by dmizer on 2009-04-12
Using this thread as a platform to complain about your previous thread being closed is unproductive. Please use the resolution center for these things.

---

### Post by saulgoode on 2009-04-12
> **detroit/zero said:**
> ...since I was clearly invited to clutter the database

Was that an [intentional pun]("http://clutter-project.org/")? :)

Nonetheless, transparency is listed as a planned feature on the [GTK+ 3 roadmap]("http://testbit.eu/~timj/blogstuff/GtkRoadmap3Draft2.html") currently being drafted (and I would expect GNOME to continue using GTK+ as its primary GUI toolkit).

---

### Post by detroit/zero on 2009-04-12
> **saulgoode said:**
> Was that an [intentional pun]("http://clutter-project.org/")? :)

Nonetheless, transparency is listed as a planned feature on the [GTK+ 3 roadmap]("http://testbit.eu/%7Etimj/blogstuff/GtkRoadmap3Draft2.html") currently being drafted (and I would expect GNOME to continue using GTK+ as its primary GUI toolkit).
Completely unintentional, I'm afraid.

Thanks for pointing me to that link. My searches on the topic were coming up empty. It's good to know somebody somewhere is at least looking into it.

Thanks again!

---

### Post by bolax on 2009-04-12
> **detroit/zero said:**
> When are we going to get a Gnome release that handles transparency?

year 2020 :lolflag:

---

### Post by CraigPaleo on 2009-04-12
Gnome already handles transparency, no?

---

### Post by sekinto on 2009-04-12
Metacity has supported transparency for awhile now.
[Alt+F2] gconf-editor [Enter]
/apps/metacity/general > check "compositing_manager"

---

### Post by pwnst*r on 2009-04-12
> **CraigPaleo said:**
> Gnome already handles transparency, no?

that's what i'm thinking.  i'm a little confused.

---

### Post by ad_267 on 2009-04-12
The new murrine engine has transparency.

I only noticed it when my terminal windows started to show my background through them. Same thing with the system monitor.

And by my terminal windows, I don't mean the terminal background, I mean the actual gtk widgets like the scrollbar and the tabs. I'm running the metacity compositor.

---

### Post by 3rdalbum on 2009-04-13
> **ad_267 said:**
> The new murrine engine has transparency.

I only noticed it when my terminal windows started to show my background through them. Same thing with the system monitor.

And by my terminal windows, I don't mean the terminal background, I mean the actual gtk widgets like the scrollbar and the tabs. I'm running the metacity compositor.

If you go to the Murrine website, you can get plugins for Eye Of Gnome and Rhythmbox that will enable RGBA support for those programs (transparent backgrounds and widgets).

---

### Post by ad_267 on 2009-04-13
> **3rdalbum said:**
> If you go to the Murrine website, you can get plugins for Eye Of Gnome and Rhythmbox that will enable RGBA support for those programs (transparent backgrounds and widgets).

Thanks, that's awesome. Now I need to figure out how to write a plugin for banshee.

---

### Post by detroit/zero on 2009-04-13
Some apps support it, some don't.. it's really a potluck to get one that does.

From what I've seen (which, granted, isn't all that much), most of the ones that do support it are a pseudo-transparency of sorts.

Take a look at the gnome-panels, for instance.  Those aren't truly transparent; the background directly behind them is read and re-painted onto the panel. This is evident whenever you use the hide buttons to slide on out of the way - the background slides with it, as though it were an image applied to the panel.

I'm sure there are apps that have true transparency - the xterm app is one.

I use compiz-fusion on my desktop, and can achieve transparency that way (it's one of the reasons I even use it). But, my whole point is: Why turn to a 3rd party application to achieve something that should just be part of standard WM behavior?

I'm just asking, is all.

---

