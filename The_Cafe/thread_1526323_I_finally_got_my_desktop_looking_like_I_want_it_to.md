---
title: "I finally got my desktop looking like I want it to!"
date: 2010-07-07
forum: The Cafe
---

### Post by Dustin2128 on 2010-07-07
After being told many times 'it's not possible with anything other than kde' or 'all or none' I finally figured out how to remove window borders from a transparent, scrollbar-less aterm, set it to be embedded in the desktop, and all within the confines of GNOME (pretty much) achieving what I've been attempting to do for 2 months! The funny part was that it was laughably easy, taking only about 2 minutes and involving only two lines of config file changes. First I went to compiz fusion icon and set window manager to kwin. That gives the windows and effects the same behavior as kde but does not force me to use the kde panel or widget system, or in short, any of the things that cause me to dislike it. After that, I changed a few things in the kde compositing manager to give me the same desktop effects I had before (and then some), swap the window decorations to one of my favorite third party themes, and presto! perfect desktop! If anyone's wondering, at the time I took those screenshots I was running a build script from google code's [quake2 html5 project]("http://code.google.com/p/quake2-gwt-port/wiki/BuildingAndRunning").

---

### Post by dragos240 on 2010-07-07
Cool! You got a terminal on your desktop? Tut?

---

### Post by sailthesea on 2010-07-07
Is very nice I wonder if OpenSuse would support those effects?

---

### Post by Lightstar on 2010-07-07
Feels way too busy for me!  And there's barely anything running!  I guess I like my desktop clean and mostly empty :)

But I'm glad you were able to customize it to your need :D  Good job!

---

### Post by Dustin2128 on 2010-07-07
> **dragos240 said:**
> Cool! You got a terminal on your desktop? Tut?
got most the info in the above post, but here's how to do it the with the method I did (probably more efficient methods, but this works for me)
first of all I got aterm, it's in the repos so that was the easy bit.
then ```
[LEFT]
[LIST=1]
[*][FONT=Courier New]$ [COLOR=#000066]echo[/COLOR] -n [COLOR=#ff0000]'Aterm*scrollBar: false'[/COLOR] >> ~/.Xresources[/FONT]
[*][FONT=Courier New]$ xrdb -merge ~/.Xresources [/FONT]
[/LIST]

[/LEFT]



```to remove the scrollbar. After that start with aterm --transparent for pseudo-transparency which is perfectly good for an embedded desktop terminal.
I used a bit of kde integration to accomplish the next bit, so if you don't already have it, get kubuntu-desktop and compiz fusion icon.
After you've got both installed, right click on compiz fusion icon>select window manager>kwin. That should reload it with the kde window manager with which you can still use most or all of your compositing effects, you just have to enable and configure them by right clicking on a window and hitting configure window behavior. After that, you just change the layer of the terminal to 'keep below others', get it to the size you want, then right click>advanced>no border. You have to have disabled shadows on that particular window or, obviously, you see the shadowed outline. That's pretty much what I did. Ungainly? Perhaps. Satisfying? Indeed.

---

### Post by cj.surrusco on 2010-07-07
> **Dustin2128 said:**
>  First I went to compiz fusion icon and set window manager to kwin.

Where is this option? Can't seem to find it.
Edit: Nevermind, Your new post explains it.

---

### Post by steveneddy on 2010-07-07
Too busy for my tastes - and a transparent browser seems like a pain to read.

---

### Post by Dustin2128 on 2010-07-07
> **steveneddy said:**
> Too busy for my tastes - and a transparent browser seems like a pain to read.
Only transparent when I'm moving it, just felt like showing off some compositing features and window decoration options.

---

### Post by chessnerd on 2010-07-08
Which one is the way you want it?

Those screen shots were taken 30 minutes apart. In that time, you moved the indicator applet over the the far left (before it was next to the notification icons). In which instance is it finally the way you like it looking? :D

(Also, the kernel was updated in that time span...)

Question: is that KDE, Gnome, a KDE/Gnome hybrid, or something else?

---

### Post by Dustin2128 on 2010-07-08
> **chessnerd said:**
> Which one is the way you want it?

Those screen shots were taken 30 minutes apart. In that time, you moved  the indicator applet over the the far left (before it was next to the  notification icons). In which instance is it finally the way you like it  looking? :D

(Also, the kernel was updated in that time span...)

Question: is that KDE, Gnome, a KDE/Gnome hybrid, or something  else?
It's a gnome/kde hybrid. I took the one screenshot, did some major updates then decided to take another  screenshot showing transparent windows.
EDIT: I fixed it with a new screenshot.

---

### Post by chessnerd on 2010-07-08
> **Dustin2128 said:**
> It's a gnome/kde hybrid. I took the one screenshot, did some major updates then decided to take another  screenshot showing transparent windows.
EDIT: I fixed it with a new screenshot.

I figured that that was what happened.

A Gnome/KDE hybrid... Interesting.

There should be a distro that uses a scheme like that, but I don't think there is. Maybe you should make one from your setup. You could call it "Dust, an OS" (like Dustin OS, only less conceited). You could say that it's based on K/Ubuntu. Possible slogans: "All this OS is, is itself in the wind..." or "You'd be surprised how clean Dust can look!"

---

### Post by Dustin2128 on 2010-07-08
> **chessnerd said:**
> I figured that that was what happened.

A Gnome/KDE hybrid... Interesting.

There should be a distro that uses a scheme like that, but I don't think there is. Maybe you should make one from your setup. You could call it "Dust, an OS" (like Dustin OS, only less conceited). You could say that it's based on K/Ubuntu. Possible slogans: "All this OS is, is itself in the wind..." or "You'd be surprised how clean Dust can look!"
Interesting idea... I'd have to decide on the level of integration, but it wouldn't be too hard... I'll have to get back to you on that...
EDIT:
My default theme! (if swapped to black font of course). Motto: The best of both worlds (hardly original, but what the hell?)

---

### Post by Khakilang on 2010-07-08
My desktop is totally empty. Never use any gadget or widget. When I want an application I just go ti Application and select what I want. Maybe I start decorating something and see how it goes.

---

### Post by aeiah on 2010-07-08
i use stjerm bound to F12 for a small pop-up terminal, but it can easily be set to always on, up at the top, transparent and underneath all windows with compiz.

---

### Post by nothingspecial on 2010-07-08
Huh, window borders, backgrounds, panels and docks are for sissys

[ATTACH]162776[/ATTACH] [ATTACH]162777[/ATTACH]

---

### Post by cj.surrusco on 2010-07-08
> **nothingspecial said:**
> Huh, window borders, backgrounds, panels and docks are for sissys


Hah, I really like using panels. It's easier to work when you can monitor everything without typing commands. 

(I have two monitors set up vertically with dualview.)

---

### Post by _Mark_ on 2010-07-08
I followed this and works just fine with the normal gnome terminal and without having to use KDE

[Linky]("http://www.webupd8.org/2009/05/ubuntu-embed-terminal-into-you-desktop.html")

---

### Post by samalex on 2010-07-08
To the OP, awesome you got your desktop perfectly customized to your liking... that's the beauty of Linux is that you can make it fit your needs :)  I do have to say it's more busy than I prefer, instead I like a very clean desktop, but that's probably because of my ADHD.

Here's [a link to a blog post]("http://samalex.blogspot.com/2010/07/moved-to-64-bit-ubuntu-1004-and-loving.html") on my site with a screenshot of my desktop, which is fairly bare bone.

Sam

---

### Post by cj.surrusco on 2010-07-09
> **_Mark_ said:**
> I followed this and works just fine with the normal gnome terminal and without having to use KDE

[Linky]("http://www.webupd8.org/2009/05/ubuntu-embed-terminal-into-you-desktop.html")

Great link! Thanks a lot!

---

### Post by Tristam Green on 2010-07-09
But can it play Crysis?

---

