---
title: "Which features would you most like to be put in to GNOME?"
date: 2009-04-23
forum: The Cafe
---

### Post by James_Lochhead on 2009-04-23
As the title says... features do not have to be 100% realistic (I am now sure some of my mine would ever be implemented), however keep it serious :-D. Comments on other peoples "wants" are also welcome.

Here are mine:

[LIST]
[*]**Widgets:** Integrated widget support. i.e. plasma for GNOME.

[*]**Compositing:** Compiz specifically for GNOME. KDE has KWin, it is specifically designed to be easy to use and pre-configured to work with KDE. I want a GNOME version.

[*]**Gnome-Do:** Gnome-Do integration with alt+f2 and Gnome-Do panel applet.

[*]**Nautilus:** Split panels. Multiple side panels. Integrated terminal with tab auto-complete.

[*]**Gedit:** Auto-complete in the terminal extension.

[*]**Contacts application:** An application that will store all my contacts and allow any program I want to use to use them.

[*]**Gnome panel:** Nicer menu applet (more like the KDE one - like an improved slab). More extendibility so the GNOME panel could become a dock.

[*]**Browser:** GTK browser, with no-script, multiple panels, tabs, delicious bookmarks, other add-ons and nautilus integration (i.e. I guess basically Nautilus as an Internet browser).

[*]**Control centre**: Add a front-end to conf-editor. Open everything in the same window. 
[/LIST]

---

### Post by Ms_Angel_D on 2009-04-23
To be honest it sounds like you should using KDE though I do like the idea of split panels for Nautilus

---

### Post by juancarlospaco on 2009-04-23
None, because its lightweight and so easy to use

---

### Post by James_Lochhead on 2009-04-23
> **MetalHellsAngel said:**
> To be honest it sounds like you should using KDE though I do like the idea of split panels for Nautilus

Yea I was recently. KDE 4 is not perfect either though, its got its own problems (namely looks, not many themes available, icons aren't very serious, K branding annoys me, KWin won't fetch my mail, I don't like QT, GTK applications look rubbish and there are is no decent QT equivalent to Synaptic).

Anyway, this is meant to be a light-hearted thread. The features do not necessarily have to be ones you think will ever be implemented.

---

### Post by James_Lochhead on 2009-04-23
If KDE started using GTK and got rid of the annoying K-everything branding I might consider it... like that is ever going to happen though.

---

### Post by gnomeuser on 2009-04-23
The ability to set webmail providers as my preferred email "application". I don't use Evolution anymore, GMail gives me the freedom to read my email anywhere without losing my filters and contact list. However the simple task of clicking a mailto: link still doesn't work.

That kind of integration would be nice to offer and would make GNOME much more fit for the way people use it today.

Aside that I am currently waiting to see where they go with the GNOME-shell, I am still not sold entirely on the idea but I want to see it more fully formed.

I would also like to see MSN webcam/VoIP support along with custom emoticons as I need that. 

Every major desktop comes with a good media player that handles podcasts, music, videos e.g. GNOME ships with totem which is anaemic from a feature point of view. It doesn't do common tasks for users like syncronizing their portable players. For this I would like to see Banshee adopted.

It would be interesting to see where we could take gnome-do, it is a very novel approach to docks, searches and task handling. Nobody really expected docky from gnome-do but that is the kind of thinking we need.

Zeitgest looks interesting, I think we need to start using indexers to allow people to really interact with their work in new ways. We haven't really been good at using indexers so far, we have several really good ones but nobody seems very interested in depending on that functionality despite everyone agreeing that they can solve a lot of problems.

Finally I would like to see the applet situation cleared up - I am not generally a bit fan of applets but yet there seems to be no good solution to this problem.

---

### Post by Simian Man on 2009-04-23
> **gnomeuser said:**
> The ability to set webmail providers as my preferred email "application". I don't use Evolution anymore, GMail gives me the freedom to read my email anywhere without losing my filters and contact list. However the simple task of clicking a mailto: link still doesn't work.


Here is a little script to accomplish exactly that:
```

#!/bin/sh
BROWSER="firefox"

# remove the ? from the uri
uri=`echo "$1" | sed -e 's/subject=/su=/' -e 's/^mailto:\([^&?]\+\)[?&]\?\(.*\)$/\1\&\2/'`

if [ "$uri" ];
 then exec $BROWSER "https://mail.google.com/mail?view=cm&tf=0&ui=1&to=$uri"
 fi
 exec $BROWSER "https://mail.google.com/"

```

Name that gmail-mailto and put that somewhere you can run it (and give it executable permissions). Then go to Preferred Applications and set email to a custom command.  Enter:
```
gmail-mailto %s
```

That should fix this problem.  I found this script somewhere online, but I forgot where.

---

### Post by James_Lochhead on 2009-04-23
> **gnomeuser said:**
> 
For this I would like to see Banshee adopted.


Agreed. Banshee is amazing and is shaping up to be the best media application around.

For the first time ever last week an application succeeded in playing something that VLC could not... and that application was Banshee. Plus it has video library support which is really nice. I think it should eventually replace Rhythmbox and Totem.

I also forgot one thing I would like in my first post and this reminded me...

A few weeks ago I was organizing my videos into directories by genre and came across a problem. What if the video fits in to more than one genre? Therefore, I would like a tag feature that allows you to associate files with specific tags (okay it won't solve the directory problem but it will help to some extent).

---

### Post by Sealbhach on 2009-04-23
In Nautilus, when I'm doing "Save As" from a webpage, I start typing.... but the letters I type do not change the filename, instead they start some kind of search thing going.
 
I have to move the mouse, highlight the name of the file I want to save, then type it in.
 
I don'y know if I've explained that very well, let me know if anyone else has this problem.
 
 
.

---

### Post by MaxIBoy on 2009-04-23
The GNOME project is going to start shutting out Compiz in future versions (as far as I know, GNOME 2.26 is the last version that will work with Compiz.) They're planning on adding Compiz-like features to Metacity the way KDE has done for Kwin.


I don't mind compositing being added to Metacity, but deliberately shutting out other window managers is a Bad Thing. Supposedly it's to fix a bug of some kind, but Compiz developers have said that the bug is fixable without moving the panel into the window manager. I don't know which developers are correct, though.


GNOME already has its own browser. It's called Epiphany. It's more lightweight than Firefox, but it's missing a lot of advanced functionality. 

One of the reasons I like Nautilus is because it is **not** a Web browser. Let's not ruin that. Thank you.


Desktop widgets: just install a third-party program. Plasma should never have been made a component of KDE, when there are other programs to do the same job. More modularity == better.


Control center: I prefer editing text files, but I agree that Gconf-Editor is pretty terrible, and making a control center couldn't hurt.


Split panels: I've been wanting that as well. 


Most of the rest of the suggestions in the original post are already true.

---

### Post by ninjapirate89 on 2009-04-23
> **Sealbhach said:**
> In Nautilus, when I'm doing "Save As" from a webpage, I start typing.... but the letters I type do not change the filename, instead they start some kind of search thing going.
 
I have to move the mouse, highlight the name of the file I want to save, then type it in.
 
I don'y know if I've explained that very well, let me know if anyone else has this problem.
 
 
.

That also happens to me...its very annoying.

---

### Post by gnomeuser on 2009-04-23
> **Simian Man said:**
> Here is a little script to accomplish exactly that:
```

#!/bin/sh
BROWSER="firefox"

# remove the ? from the uri
uri=`echo "$1" | sed -e 's/subject=/su=/' -e 's/^mailto:\([^&?]\+\)[?&]\?\(.*\)$/\1\&\2/'`

if [ "$uri" ];
 then exec $BROWSER "https://mail.google.com/mail?view=cm&tf=0&ui=1&to=$uri"
 fi
 exec $BROWSER "https://mail.google.com/"

```

Name that gmail-mailto and put that somewhere you can run it (and give it executable permissions). Then go to Preferred Applications and set email to a custom command.  Enter:
```
gmail-mailto %s
```

That should fix this problem.  I found this script somewhere online, but I forgot where.


Why not use xdg-open and avoid the whole BROWSER variable

---

### Post by James_Lochhead on 2009-04-23
> **MaxIBoy said:**
> 
GNOME already has its own browser. It's called Epiphany. It's more lightweight than Firefox, but it's missing a lot of advanced functionality.


Yea I do know about Epiphany. I was mostly pointing at the features. If Epiphany improved a bit (more and easier extensions, better UI, cookie management) I would use it. 

> **MaxIBoy said:**
> 
One of the reasons I like Nautilus is because it is **not** a Web browser. Let's not ruin that. Thank you.


Nothing to stop there being two versions though. One with a web browser and one without.

> **MaxIBoy said:**
> 
Desktop widgets: just install a third-party program. Plasma should never have been made a component of KDE, when there are other programs to do the same job. More modularity == better.


I like the idea of integration. The thing about modularity is that it takes time. I just like to install and not have the faff if you know what I mean.

A compromise between the two would be great. A widget program specifically designed and configured for GNOME, that integrates nicely but is not a necessity.  

> **MaxIBoy said:**
> Most of the rest of the suggestions in the original post are already true.

Which ones please?

---

### Post by James_Lochhead on 2009-04-23
> **ninjapirate89 said:**
> That also happens to me...its very annoying.

Thirded.

I hate this and always do it. It is because the Save As menu does not auto-focus on the input box to start with.

---

### Post by Ms_Angel_D on 2009-04-23
> **James_Lochhead said:**
> Yea I was recently. KDE 4 is not perfect either though, its got its own problems (namely looks, not many themes available, icons aren't very serious, K branding annoys me, KWin won't fetch my mail, I don't like QT, GTK applications look rubbish and there are is no decent QT equivalent to Synaptic).

Anyway, this is meant to be a light-hearted thread. The features do not necessarily have to be ones you think will ever be implemented.

I understand what your saying, and I'm sorry if I came across as being brash, It's so hard to express intention in writing...lol

When I first started out with ubuntu I like Kubuntu I think it made it a smoother transition from Windows but then I just became really comfortable with gnome..especially when as you've noted there aren't very many themes availble for KDE. I also find it quite akward trying to customize KDE, though I do enjoy quite a few of the apps.

> **Sealbhach said:**
> In Nautilus, when I'm doing "Save As" from a webpage, I start typing.... but the letters I type do not change the filename, instead they start some kind of search thing going.
 
I have to move the mouse, highlight the name of the file I want to save, then type it in.
 
I don'y know if I've explained that very well, let me know if anyone else has this problem.
 
 
.

This annoys me very much as well perhaps we should take this up with the Gnome people seems it annoys quite a few of us.

---

### Post by MaxIBoy on 2009-04-23
> **James_Lochhead said:**
> Yea I do know about Epiphany. I was mostly pointing at the features. If Epiphany improved a bit (more and easier extensions, better UI, cookie management) I would use it. It's called Firefox. Works fine for me. Epiphany is not designed for power users. The GNOME developers intentionally stripped out a lot of this functionality when they forked it from Galeon.

> Nothing to stop there being two versions though. One with a web browser and one without.Duplication of effort which will slow down development unnecessarily, in my opinion. Nothing to stop someone from starting a project for this, though. If you've got enough developers who are also interested in the idea, you're in business!

> I like the idea of integration. The thing about modularity is that it takes time. I just like to install and not have the faff if you know what I mean.Just because you can replace components doesn't mean  you have to. Modular systems typically come in distros, set up in different ways by different projects. Linux itself is an example. There are a number of Linux distros which come set up in different ways, and you can pick one and not touch it. Firefox is another example. Swiftfox and Iceweasel are both distros of Firefox. 

Overall, though, you're in luck, because GNOME is moving toward an integrated solution. This will probably be why I eventually stop using it. For now though, GNOME is still my favorite desktop.


> A compromise between the two would be great. A widget program specifically designed and configured for GNOME, that integrates nicely but is not a necessity.   In what way, designed and configured for GNOME? Anyway, I'm more worried about the wasted programming effort required to create a program that already exists, when that effort is better spent contributing to existing projects.

I have no objection to starting two projects for similar purposes, as long as the two projects are sufficiently different to justify their separation. However, in the end, use justifies production. If there are two identical projects, and each one has hundreds of users, I'm not really going to complain... unless they **stay** identical.



> Which ones please?GNOME already has a terminal emulator, replete with tab completion. There are plenty of replacement GNOME menu applets, and plenty of panel applets to add dock-like characteristics (I won't say "dock-like functionality," because docks reduce functionality.) The contacts thing is kinda impossible unless you get every project to implement the functionality separately and agree on an API. Your best bet is copy+paste, which actually does the job quite nicely for me.

---

### Post by James_Lochhead on 2009-04-23
> **MaxIBoy said:**
> The contacts thing is kinda impossible unless you get every project to implement the functionality separately and agree on an API.

I think if a simple application using XML files existed by default in GNOME then a lot of developers would build functionality in their projects to support it.

It wouldn't need to be implemented in every project.

---

### Post by 3rdalbum on 2009-04-23
Let's have a feature that Gnome has been tossing around for years.

File type conversions when you rename a file.

We've all seen and heard of newbies trying to convert WAV to MP3 by changing the filename extension... even my father tried it last year, and he's been using computers for longer than me! File conversion should be a function of the file manager, especially as it makes things easy for the newbies who Gnome is trying to target.

I guess things would get a bit hairy when trying to convert between video formats... most people think "I want to convert a .mov to a .avi" without realising that AVI is just a container format and that MOVs don't support many of the same video codecs as AVIs. But there should be some way of doing it.

---

### Post by MaxIBoy on 2009-04-23
> **James_Lochhead said:**
> I think if a simple application using XML files existed by default in GNOME then a lot of developers would build functionality in their projects to support it.

It wouldn't need to be implemented in every project.The best route for this is as a freedesktop.org standard, in which case I'd say it's a good idea. But if GNOME just "Lone Wolf"ed it, I would not be in favor of it.


Conversions when you rename stuff: Good idea, **as long as you can turn it off**.

---

### Post by Sand &amp; Mercury on 2009-04-23
> **James_Lochhead said:**
> 
[LIST]
[*]**Compositing:** Compiz specifically for GNOME. KDE has KWin, it is specifically designed to be easy to use and pre-configured to work with KDE. I want a GNOME version.

[*]**Gnome panel:** Nicer menu applet (more like the KDE one - like an improved slab). More extendibility so the GNOME panel could become a dock.
[/LIST]
Well break out the champagne because Gnome 3 has those things on the road map, specifically referring to gnome-shell and Mutter. 

Metacity actually does have compositing, it's just very barebones.

Re: a control centre, gconf-editor itself is a kind of front end in that respect. I think having a full GUI for controlling every single little option would be moving away from what GNOME is all about, and into KDE territory.

Integrating widgets with Gnome would be great though imo, even if I don't know if I'd use them. We have Desklets, but Desklets is well... crap (nothing against the developers but it does not integrate well with the environment).

Personally what I'd most look forward to is a toolkit that is more robust than GTK+ is at the moment, that can allow for animations, more functionality, customisation, eye candy and so on. I know that's being toyed with for Gnome 3.0 as well.

---

### Post by NightwishFan on 2009-04-23
Epiphany is a fairly good browser. It is basic though, the one thing I like is the gestures plugin that works flawlessly for me.

As for GNOME, I would like to see mainly just changes that make it less Windowsy and OS9..y. I prefer even GNOME to both though.

---

### Post by gnomeuser on 2009-04-23
> **Sand & Mercury said:**
> 
Personally what I'd most look forward to is a toolkit that is more robust than GTK+ is at the moment, that can allow for animations, more functionality, customisation, eye candy and so on. I know that's being toyed with for Gnome 3.0 as well.

Moonlight could easily fit that bill.

---

### Post by chucky chuckaluck on 2009-04-23
> **James_Lochhead said:**
> If KDE started using GTK and got rid of the annoying K-everything branding I might consider it... like that is ever going to happen though.

you can use gtk theming in kde now (and you can still control the colors with kde). with dolphin, dragon, juk, amarok and the like, there is hope of at least lessening the k's. also, in the menu, even k-named apps are given more generic terms like 'terminal', 'audio player', etc.

---

### Post by James_Lochhead on 2009-04-24
Bumpage.

---

