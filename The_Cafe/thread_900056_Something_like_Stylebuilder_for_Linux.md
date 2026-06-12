---
title: "Something like Stylebuilder for Linux??"
date: 2008-08-24
forum: The Cafe
---

### Post by Twitch6000 on 2008-08-24
I was wondering if there is anything like stylebuilder(a fun easy style editing program for windows) for Linux.

I know the default tool does some stuff,but nothing like stylebuilder.

StyleBuilder is one tool that let me have alot of fun with windows lol.

I just put gimp in the editing tool list clicked what I wanted to edit and off I go :).

So  anyways is there a tool like this or not?

If not is there a tool like the freeware alternative to it that is text based <.<.

The reason why I ask is I am really wanting to make my own Linux window borders and icons :).

---

### Post by Polygon on 2008-08-25
why not just make your own theme? you can make your own borders and icons with themes

---

### Post by Twitch6000 on 2008-08-25
> **Polygon said:**
> why not just make your own theme? you can make your own borders and icons with themes

In order to fully make my own theme I would need a program for it :p.

---

### Post by smartboyathome on 2008-08-25
Good luck with finding the program. Right now teh only one is Murrine's configurator, which only changes colors. :(

---

### Post by days_of_ruin on 2008-08-25
I am working on one.Its still in the early stages but 
you can check it out [here]("https://launchpad.net/mct")

---

### Post by Twitch6000 on 2008-08-27
Thank you I will look into it :).

Now a related question,how do the current theme you get off of lets say gnome art get made?

I looked around and seen something about gconf(I think) other then that I was lost.

So uhh yeah any help there?

---

### Post by smartboyathome on 2008-08-27
Look at the GNOME Themes link in my signature. Also, check out your ~/.themes folder (it is hidden), it contains all your themes. Just try changing some of the stuff in there and see what happens. This is how most themes are made.

---

### Post by Twitch6000 on 2008-08-29
> **smartboyathome said:**
> Look at the GNOME Themes link in my signature. Also, check out your ~/.themes folder (it is hidden), it contains all your themes. Just try changing some of the stuff in there and see what happens. This is how most themes are made.

Hummm ok will do :).

---

### Post by geoken on 2008-08-29
There are two main ways to make a theme, using a theme engine and it's options or using the pixbuf (pixmap) engine.

Using a theme engine is the method that involves code. You basically edit a GTKRC file which contains instructions on what colors buttons will be, how much roundness, what kind of gloss, etc.

Using a pixmap theme is the method that would be more familiar to a Windows themer. With a pixmap theme you don't have to touch a line of code. A pixmap theme is exactly like a windows theme except instead of having all the images compressed into a msstlye file, the images are just sitting there in normal folders. You can simply open the scrollbar image in gimp, edit it, then save and refresh the theme and you'll see you changes.

You can download this theme ([http://www.gnome-look.org/content/show.php/Glory-Simplex?content=60326]("http://www.gnome-look.org/content/show.php/Glory-Simplex?content=60326")) to get an idea of how pixmap themes work. Extract the theme and browse through the folders.

---

