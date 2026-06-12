---
title: "Need a little education about terminology"
date: 2009-06-03
forum: The Cafe
---

### Post by Daremo_06 on 2009-06-03
So I saw the thread about compiz and gnome ect ect and I think I have some misconceptions.

Gnome is the desktop part of the linux package correct?  It comes in various flavors such as Ubuntu, Kbuntu ect ect right?

I was under the impression Compiz, GTK, Emerald were all separate software "modules" (unsure what the correct term is for them is) and that you could install one or more of them to modify the look and functionality of your graphical desktop.  Is this the wrong way to describe them?

---

### Post by nothingspecial on 2009-06-03
Gnome has one flavour, gnome.

Ubuntu uses gnome

There are different desktop environments

Kubuntu uses Kde

Kde is another full featured desktop manager, different to gnome.

Xubuntu uses xfce

Xfce is a lightweight desktop environment useful for lower spec computers.

There are plenty of other eg openbox, fluxbox etc etc

You can use any with ubuntu, try em and see. They are all configurable.

---

### Post by Sublime Porte on 2009-06-03
> Gnome is the desktop part of the linux package correct?

Gnome is a desktop environment. It is just one of many, others are KDE, XFCE, LXDE, Enlightenment. Ubuntu is just one 'flavour' (or what we call Distribution of Linux) and it comes in 3 main varieties that use 3 of the most popular Desktop Environments, Ubuntu uses Gnome, Kubuntu uses KDE and Xubuntu uses XFCE.

> I was under the impression Compiz, GTK, Emerald were all separate software "modules"

Compiz is a compositor, meaning it's a piece of software that can add cool transparencies and other effects to your desktop. Gtk is a toolkit, meaning it's like a module that programmers use to make user interfaces (mostly for Gnome and XFCE) and Emerald is a theming engine for Compiz, that lets you control how window decorations will look when you use Compiz.

---

### Post by Sublime Porte on 2009-06-03
> gnome = ubuntu 
kde....

Whilst I understand you're attempting to simplify it for explanation, that's not such a good idea.

Gnome != Ubuntu.

Making simplified statements like that, can not really lead to better understanding, but actually more confusion.

---

### Post by Bölvaður on 2009-06-03
It's pretty much correct.

Except that GNOME is a DE (desktop environment) which is more than just what you can see, as it has program stack that comes with it and additional programs that base on it.

KDE is also a desktop environment (kubuntu uses it instead of gnome), while fluxbox, openbox and others are window managers. Which can be confusing as you might think all of them just changes the look and feel but not what programs are run. Like with fluxbox you dont have the network manager to auto connect to your wireless network, unless if you do slight tweaking.

GTK is part of gnome which most if not all gnome programs use to get their native gnome look, which changes with different themes.

---

### Post by nothingspecial on 2009-06-03
> **Sublime Porte said:**
> Whilst I understand you're attempting to simplify it for explanation, that's not such a good idea.

Gnome != Ubuntu.

Making simplified statements like that, can not really lead to better understanding, but actually more confusion.

Take a look now ........... does that meet your requirements?

---

### Post by Sublime Porte on 2009-06-03
Yep, much better description of the relationship :)

---

### Post by nothingspecial on 2009-06-03
No problem, only trying to help:D

---

### Post by Daremo_06 on 2009-06-03
> **Sublime Porte said:**
> Gnome is a desktop environment. It is just one of many, others are KDE, XFCE, LXDE, Enlightenment. Ubuntu is just one 'flavour' (or what we call Distribution of Linux) and it comes in 3 main varieties that use 3 of the most popular Desktop Environments, Ubuntu uses Gnome, Kubuntu uses KDE and Xubuntu uses XFCE.



Compiz is a compositor, meaning it's a piece of software that can add cool transparencies and other effects to your desktop. Gtk is a toolkit, meaning it's like a module that programmers use to make user interfaces (mostly for Gnome and XFCE) and Emerald is a theming engine for Compiz, that lets you control how window decorations will look when you use Compiz.

Ok to further break this down then...

Compiz is used to modify the graphical look of the desktop itself.  So thats things like cube desktop or wobbly windows (which btw, I HATE! and is the main reason I took compiz off cause everytime I goofed around with a setting and had to restart compiz, it would default on)

Emerald is used to apply a theme which could be described as a group of various effects/looks across multiple parts of the desktop like border/button colors and looks, window background colors ect ect.  Emerald applies themes through or in partnership with Compiz??  Would that be accurate?

Perhaps I used the wrong acronym for GTK, I was referring to the various themes you could download that state they are GTK or is it GTK+?

Looking at [www.gnome-look.org](www.gnome-look.org), on the left column are various sub catagories.  

GTK 1.x
GTK 2.x
Metacity
Compiz
Beryl (which is Emerald right?)
GDM Themes

Do all of these catagories represent various engines that apply a desktop theme to your linux desktop (whatever it may be)? And within that catagory are various themes which you can download to apply using its engine to your desktop right?

(Incidentially, this is probably one of the significant reasons why its difficult to market the various linux products to people.  There is great flexibility and choice, but things are rarely intuitive as you can see by my misconceptions.  I by no means am a newbie to computers having been playing around with them since the days of the Trash-80, but this is my first real foray into something other than a MS OS and a brief stint using MAC back in the 80s.  That's a separate discussion though and I don't want to derail my current topic.  I would be happy to start another thread about it though..)

---

### Post by stwschool on 2009-06-03
GDM themes affect the login screen.
Beryl has since merged into compiz, it was a separate project.
Metacity is Gnome's window manager. It puts windows on your screen and decorates them.
GTK is a toolkit used to keep things consistent in Gnome apps. A theme applied to gtk will bring all gtx apps into line.

---

### Post by forrestcupp on 2009-06-03
The base level of your operating system is the Linux kernel.  The kernel handles low level things like interfacing with your hardware.  

After that, you'll go to a login manager, such as GDM for Gnome or KDM for KDE.  

Then, you'll go to your DE, or desktop environment, such as Gnome, KDE, etc.  Your DE is pretty much your user interface to graphically communicate with your system.  It usually has a lot of small programs associated with it to allow you to control things or even do some productive things, and generally direct how the desktop environment is used.  It also includes programs that do some behind the scenes things to make things work together that we just take for granted.

The DE requires another "module" called a WM (Window Manager) to deal with the windows.  The WM draws the windows to your screen and handles the calls back and forth between the system.  If you click a button or even slightly move your mouse, the window manager sends that information to your system and receives instructions from your system on what to do.  Windows can be many things, not just the standard window with the title bar, menus, etc.  In the Gnome desktop environment, Metacity is the current default window manager.  You can also replace Metacity with an optional window manager like Compiz or the dead Beryl.  Compiz is a compositing window manager, which means it uses your video card to process the windows instead of your CPU.  Compiz is not the effects like wobbly windows, that is the Fusion part of Compiz.  Compiz is a WM that merely uses a different, more modern way of drawing the windows.

A window manager uses a programming toolkit to run things.  Gnome uses GTK and KDE uses Qt.  They're basically just different ways to program how things happen.  Since they're different toolkits, they will act and look differently.

A window manager can also use a theming engine.  Emerald is one theming engine that you can use with compiz.  You can also use the default Metacity one if you're in Gnome.  The theming engine is also called a window decorator.  It configures how your windows look with the appearance of your title bar, buttons, borders, shadows, etc.  You'll download Compiz or Beryl themes if you're using Emerald, or Metacity or GTK themes if you're using Metacity's window decorator.  You can download GDM themes to change your login screen appearance.  There is a whole other web site for KDE theming.

Of course under the hood things are actually way more complicated than this.

---

### Post by billgoldberg on 2009-06-03
> **stwschool said:**
> 
Metacity is Gnome's window manager. It puts windows on your screen and decorates them.


Yes, but not in Ubuntu. 

Compiz Fusion is the default Window Manager in Ubuntu *(if your pc can handle compositing)*.

---

### Post by rookcifer on 2009-06-03
> **forrestcupp said:**
> The base level of your operating system is the Linux kernel.  The kernel handles low level things like interfacing with your hardware.  

After that, you'll go to a login manager, such as GDM for Gnome or KDM for KDE.  

Then, you'll go to your DE, or desktop environment, such as Gnome, KDE, etc.  Your DE is pretty much your user interface to graphically communicate with your system.  It usually has a lot of small programs associated with it to allow you to control things or even do some productive things, and generally direct how the desktop environment is used.  It also includes programs that do some behind the scenes things to make things work together that we just take for granted.

The DE requires another "module" called a WM (Window Manager) to deal with the windows.  The WM draws the windows to your screen and handles the calls back and forth between the system.  If you click a button or even slightly move your mouse, the window manager sends that information to your system and receives instructions from your system on what to do.  Windows can be many things, not just the standard window with the title bar, menus, etc.  In the Gnome desktop environment, Metacity is the current default window manager.  You can also replace Metacity with an optional window manager like Compiz or the dead Beryl.  Compiz is a compositing window manager, which means it uses your video card to process the windows instead of your CPU.  Compiz is not the effects like wobbly windows, that is the Fusion part of Compiz.  Compiz is a WM that merely uses a different, more modern way of drawing the windows.

A window manager uses a programming toolkit to run things.  Gnome uses GTK and KDE uses Qt.  They're basically just different ways to program how things happen.  Since they're different toolkits, they will act and look differently.

A window manager can also use a theming engine.  Emerald is one theming engine that you can use with compiz.  You can also use the default Metacity one if you're in Gnome.  The theming engine is also called a window decorator.  It configures how your windows look with the appearance of your title bar, buttons, borders, shadows, etc.  You'll download Compiz or Beryl themes if you're using Emerald, or Metacity or GTK themes if you're using Metacity's window decorator.  You can download GDM themes to change your login screen appearance.  There is a whole other web site for KDE theming.

Of course under the hood things are actually way more complicated than this.

Don't forget X11.  Without it, there would be no GDM, Gnome, Metacity, etc.

---

### Post by forrestcupp on 2009-06-03
> **rookcifer said:**
> Don't forget X11.  Without it, there would be no GDM, Gnome, Metacity, etc.

Right!  I knew I was missing something very important.

---

