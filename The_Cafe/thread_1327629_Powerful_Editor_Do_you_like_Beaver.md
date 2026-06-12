---
title: "Powerful Editor: Do you like Beaver?"
date: 2009-11-15
forum: The Cafe
---

### Post by frenchn00b on 2009-11-15
Here I made a deb for Ubuntu:

```
http://yellowprotoss.ye.funpic.org/pool/contrib/b/beaver0-3-0-1_20091115-1_i386.deb
```

[http://www.nongnu.org/beaver/old/about/Puppy-beaver.jpg](http://www.nongnu.org/beaver/old/about/Puppy-beaver.jpg)

---

### Post by jomiolto on 2009-11-15
I've never used it before, but it looks really nice. According to a quick and very non-scientific test it seems to be about as light as leafpad, but has much more features...

---

### Post by Mornedhel on 2009-11-15
The home page doesn't really explain why I should use it over, say, gedit (not that I would use that, either -- I'm an emacs user).

---

### Post by dragos240 on 2009-11-15
Yes, I like beavers.

---

### Post by jomiolto on 2009-11-15
> **Mornedhel said:**
> The home page doesn't really explain why I should use it over, say, gedit (not that I would use that, either -- I'm an emacs user).

I think this is the main point: "Beaver's only dependency is GTK+2, so no need to install other libraries eating your disk space. These things make Beaver very suitable for old computers and use in small Linux distributions."

Gedit draws in almost half of Gnome (at least in Ubuntu), which is kind of annoying if you're not a Gnome user.

---

### Post by Mornedhel on 2009-11-15
> **jomiolto said:**
> I think this is the main point: "Beaver's only dependency is GTK+2, so no need to install other libraries eating your disk space. These things make Beaver very suitable for old computers and use in small Linux distributions."

Gedit draws in almost half of Gnome (at least in Ubuntu), which is kind of annoying if you're not a Gnome user.

Good point.

---

### Post by ZankerH on 2009-11-15
> **jomiolto said:**
> I think this is the main point: "Beaver's only dependency is GTK+2, so no need to install other libraries eating your disk space. These things make Beaver very suitable for old computers and use in small Linux distributions."

Gedit draws in almost half of Gnome (at least in Ubuntu), which is kind of annoying if you're not a Gnome user.

An editor that depends on gtk? No thank you. Give me one good reason why I should need a *graphical* environment to edit *text*.

Vim for me.

---

### Post by Mornedhel on 2009-11-15
> **ZankerH said:**
> An editor that depends on gtk? No thank you. Give me one good reason why I should need a *graphical* environment to edit *text*.

Vim for me.

At some point advanced features in text editors start to resemble graphical environments anyway. Sure, you can implement drop-downs, multiple windows, tabs, syntax highlighting, etc., in a terminal, but then what's the difference with a graphical application ?

(If you need to edit files in an X-less environment, either you don't need advanced features, or your editor needs remote edition capabilities.)

---

### Post by ZankerH on 2009-11-15
> **Mornedhel said:**
> At some point advanced features in text editors start to resemble graphical environments anyway. Sure, you can implement drop-downs, multiple windows, tabs, syntax highlighting, etc., in a terminal, but then what's the difference with a graphical application ?




It doesn't have a metric fuckton of redundant dependancies.

Let's see:

-drop-downs: entirely useless. Keyboard shortcuts are superior in accessibility and ease of instruction
-tabs: irrelevant in a CLI environment, you can either log in on another terminal, or use a terminal multiplexer like GNU screen
-syntax highlighting: can be done perfectly fine without X

---

### Post by hessiess on 2009-11-15
Don't know anything about it, if it isn't modal(like Vim/Gvim), im not interested.

> 
At some point advanced features in text editors start to resemble graphical environments anyway. Sure, you can implement drop-downs, multiple windows, tabs, syntax highlighting, etc., in a terminal, but then what's the difference with a graphical application ?


Just because an application is graphical dousen't mean it has to be mouse driven. mouse driven applications are clunky and slow. Having everything on the keyboard provides a much better interface. If everything is on the keyboard, menus are useless.

---

### Post by Mornedhel on 2009-11-15
> **ZankerH said:**
> -drop-downs: entirely useless. Keyboard shortcuts are superior in accessibility and ease of instruction
-tabs: irrelevant in a CLI environment, you can either log in on another terminal, or use a terminal multiplexer like GNU screen
-syntax highlighting: can be done perfectly fine without X

Agreed for the dependencies, although "only GTK" is a rather light dependency -- you're going to be needing it anyway, or some other toolkit, unless you go really minimalist, which is fine.

Tabs, irrelevant ? Have you ever coded for large projects ? At some point you'll need to have several files open at the same time so you can switch between them easily. Using screen implements this (with tabs outside your editor instead of inside). Logging in multiple terminals implements this. With tabs built-in, you only need one instance of your editor. (Vim users ridicule Emacs for needing more than one second to start; this is because you only start Emacs once per boot.)

Syntax highlighting can be done perfectly fine without X (although you do lose a few options, you keep enough to make it perfectly usable), but if you have X, why not use that for syntax highlighting ?

Dropdowns : I'm not talking about the ones you click here, I'm talking about for instance code completion (Intellisense-style, for lack of a better word). You still get to keep your hands on the keyboard. Even vim has overlays to do that (probably in a plugin).

---

### Post by hessiess on 2009-11-15
> 
Tabs, irrelevant ? Have you ever coded for large projects ? At some point you'll need to have several files open at the same time so you can switch between them easily. Using screen implements this (with tabs outside your editor instead of inside). Logging in multiple terminals implements this. With tabs built-in, you only need one instance of your editor. (Vim users ridicule Emacs for needing more than one second to start; this is because you only start Emacs once per boot.)


(G)Vim has both tabs and splits, personally I find splits to be vastly superior as you can see 2 or more files at the same time. Plus having a tiling WM is also nice.

---

### Post by Pogeymanz on 2009-11-15
You certainly aren't going to convert any vim or emacs users, but this text editor does look nice without having a crap-ton of dependencies.

And yeah, if you are running X at all, chances are you've installed gtk anyway, so that hardly counts as a dependency. I use emacs in terminal mode all the time, but I still always startx when I'm at my computer.

---

### Post by jomiolto on 2009-11-15
> **ZankerH said:**
> An editor that depends on gtk? No thank you. Give me one good reason why I should need a *graphical* environment to edit *text*.

Vim for me.

I'm also a Vim user 95% of the time, but sometimes I just want to use a graphical text editor for some unknown reason (split personality? :P).

---

### Post by frenchn00b on 2009-11-16
> **jomiolto said:**
> I'm also a Vim user 95% of the time, but sometimes I just want to use a graphical text editor for some unknown reason (split personality? :P).

sometimes I newly use the 
```
mc -e file.c
```
mc is quite colorful

---

### Post by Tibuda on 2009-11-16
> **jomiolto said:**
> I'm also a Vim user 95% of the time, but sometimes I just want to use a graphical text editor for some unknown reason (split personality? :P).

Me too, at those times I use GVim.

---

### Post by Exodist on 2009-11-16
I just used Gedit while using Gnome for convenience and good markup. But on the CLI with no X or DE I just use Nano.

---

### Post by Praxicoide on 2009-11-16
I haven't tried this, but yes I do. ;)

People who don't like text editors on x, don't use one. Those of us who do, well, we might like another choice (I currently use mousepad).

---

### Post by Icehuck on 2009-11-16
I use it Beaver all the time when I want to save portions of text from websites.  It's part of my minimal(light weight) GUI setup for one my boxes.

---

### Post by yanom on 2011-05-08
> **ZankerH said:**
> An editor that depends on gtk? No thank you. Give me one good reason why I should need a *graphical* environment to edit *text*.

Vim for me.

Where would the Linux world be without purists?

---

### Post by Lucradia on 2011-05-08
> **ZankerH said:**
> It doesn't have a metric fuckton of redundant dependancies.

Let's see:

-drop-downs: entirely useless. Keyboard shortcuts are superior in accessibility and ease of instruction
-tabs: irrelevant in a CLI environment, you can either log in on another terminal, or use a terminal multiplexer like GNU screen
-syntax highlighting: can be done perfectly fine without X

Tell me how to close VIM or VI, or whatever, by pressing two keys, without modifying the vim config.

---

### Post by overdrank on 2011-05-08
Please start a new thread. Thread closed. :)

---

