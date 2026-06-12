---
title: "Gnome Global Menu Bar"
date: 2005-08-20
forum: The Cafe
---

### Post by Arktis on 2005-08-20
KDE: Can't live with it, can't live without the global menu feature it has. What I am referring to is an option in KDE that sticks all the menu bars from your applications into a global menu bar at the top of the screen, just as the every Mac I've ever seen does. It's wonderful; in addition to other advantages, you save space in your application windows and things just look all the prettier.

Once upon a time there was a patch that that did this for gnome. Actually, it still exists. Don't get excited. It's only for gnome 1.x. [http://www.carcosa.net/jason/software/obsolete/gnome-globalmenu/]("http://www.carcosa.net/jason/software/obsolete/gnome-globalmenu/")

It took me quite a while to track that down. Like others who have posted on various linux forums, I didn't even know what to search for because I didn't know the proper name for this kind of gui feature. Some of the topics I found were just people trying to describe global menus in an attempt to discover if there was a way to do it from gnome, and failing to convey the idea miserably. If I hadn't been trying to discover the same information, it might have been amusing.

At any rate, I wish to open up discusion on this kind of feature for gnome.  The kinds of things I'd like to discuss are:

1.) How difficult would it be to implement?
2.) Does anyone know if there are plans to do this in the future?
3.) Would it be possible to do this with a pannel applet? Keep in mind it would need to have control over more than just the real estate it takes up on the pannel you put it on; it would have to be able to 'snip' the menu bars out of gtk app windows.
4.) What would be the best way to go about the implementation of such a feature?
5.) Is there anything that can be added on to gnome that would be able to duplicate this effect? 
6.) What other Desktop environments have this besides KDE?

In my opinion, this is the only thing gnome is really lacking other than a lump of minor refinements. What do you think?  Apparently Some people tend to shun the idea altogether.  ( see [http://kasei.us/archives/2005/04/18/menu_bar](http://kasei.us/archives/2005/04/18/menu_bar) ).

---

### Post by Wolki on 2005-08-20
It's planned for Gnome 3.0. More info here: [http://browserbookapp.sourceforge.net/topaz/](http://browserbookapp.sourceforge.net/topaz/)

---

### Post by Lovechild on 2005-08-20
[QUOTE=Wolki]It's planned for Gnome 3.0. More info here: [http://browserbookapp.sourceforge.net/topaz/](http://browserbookapp.sourceforge.net/topaz/)[/QUOTE]

That isn't by any means an official document, those are mockups.

on a sidenote I would love to see global menu bar, so if anyone is keen on programming it, I would love to help out.

---

### Post by Wolki on 2005-08-20
> **Lovechild]That isn't by any means an official document, those are mockups.[/quote]

OK, I was a bit over-enthusiastic ^^ said:**
> http://live.gnome.org/ThreePointZero[/url]) and I hope it will be included.

[quote]on a sidenote I would love to see global menu bar, so if anyone is keen on programming it, I would love to help out.

I'm not a great programmer, but i would like to see this feature too. There's already a bug filed, but it's from 3 years ago... [http://bugzilla.gnome.org/show_bug.cgi?id=82732](http://bugzilla.gnome.org/show_bug.cgi?id=82732)

---

### Post by Lovechild on 2005-08-20
I imagine one could implement this in the existing gnome-applet framework, but I would be greatly interested in partaking in the development of such a feature regardless of my fairly limited coding skills.

---

### Post by Arktis on 2005-08-20
Thanks for the replies. :) 

> I would be greatly interested in partaking in the development of such a feature regardless of my fairly limited coding skills.

I agree. If I had the know-how, I would most certainly try to tackle this. Unfortunately the only experience I've had is in scripting.  On windows.  For web apps.  I wouldn't even know where to get started.

Here's another discussion I dug up about an article from earlier this year.  [http://www.osnews.com/comment.php?news_id=9788&offset=15&rows=30&threshold=-1]("http://www.osnews.com/comment.php?news_id=9788&offset=15&rows=30&threshold=-1")
Makes for a good read imho. The biggest criticism seems to be that in a multi-monitor desktop, a global menu suffers. Seems to me that's a good reason to do this in an applet form if possible. That way it could be made so that on xinerama type desktops the menu could be mirrored on another pannel in the 2nd display, and on non-xinerama type desktops, a separate global menu could be placed on the other display to manage menus for windows on that workspace.

How would one go about setting up one of those "bounty" things I've heard about? I'd be willing to donate some money towards it.

---

### Post by Kvark on 2005-08-20
Whatever you guys are talking about it sounds extreamly weird and I completely fail to imagine what/how it is, looks like and works. But it does sound insteresting. Please point out some screenshots or a video clip demonstrating it. For those who have no idea what 'global menu bar' is.

---

### Post by Arktis on 2005-08-20
It's really quite a simple concept. Instead of having a separate set of menus within each window for each individual application, you have only one menu bar in a fixed location (presumably at the top of the screen, though it would be better to be able to place it anywhere IMHO, like the bottom or either side of the screen). This menu would change depending on the window that is in focus. For example, if I click on a nautilus window, the menu options for nautilus are shown. If I click on my email client, the menu options for it is shown. If I click on the desktop, then I get a default set of menus which would have a bunch of general functions. I definately think it's much more elegant. If you've ever used a mac, then you've used a global menu bar. They have no menus in their application windows and instead the menu's are displayed in the bar at the top of the screen depending on which window is in focus. As I stated earlier, KDE has this feature as optional, but it's got known bugs as well as issues with multiple displays as I discovered when I tried it out. And there's also the fact that I can't stand using KDE, but that's a personal preference. :wink:

---

### Post by aysiu on 2005-08-20
[QUOTE=Kvark]Whatever you guys are talking about it sounds extreamly weird and I completely fail to imagine what/how it is, looks like and works. But it does sound insteresting. Please point out some screenshots or a video clip demonstrating it. For those who have no idea what 'global menu bar' is.[/QUOTE] Yes. I, too, have no idea what a global menu is supposed to look like. I didn't know Mac had one... (and I'm using a Mac right now!)

---

### Post by Wolki on 2005-08-20
[QUOTE=aysiu]Yes. I, too, have no idea what a global menu is supposed to look like. I didn't know Mac had one... (and I'm using a Mac right now!)[/QUOTE]

Take a look at a OSX Screenshot... like this one:
[http://images.apple.com/downloads/macosx/apple/images/macosxupdate1038_200502091436.jpg](http://images.apple.com/downloads/macosx/apple/images/macosxupdate1038_200502091436.jpg)

Neither the File Manager nor the Email program have a Menu bar. Insted, the Menu entries for the currently focused application are on the top panel, in the Screenshot the File Manager menu.

---

### Post by Arktis on 2005-08-20
See my previous post.  You must have hit 'send' right after I first did. =p

---

### Post by aysiu on 2005-08-20
[QUOTE=Wolki]Take a look at a OSX Screenshot... like this one:
[http://images.apple.com/downloads/macosx/apple/images/macosxupdate1038_200502091436.jpg](http://images.apple.com/downloads/macosx/apple/images/macosxupdate1038_200502091436.jpg)

Neither the File Manager nor the Email program have a Menu bar. Insted, the Menu entries for the currently focused application are on the top panel, in the Screenshot the File Manager menu.[/QUOTE] Oh, *menu bar*! Now I know what you're talking about. Well, I hope they get that soon. My fake Mac Gnome environment won't be complete without that.

---

### Post by Arktis on 2005-08-20
Do I detect sarcasm? If you are saying this isn't a necesary feature, neither is a desktop environment necesary. I for one, am not interested in creating some kind of OSX clone DE. For the most part, I can't even stand to use a mac. Apple computers and mac users 'think different' in a way I don't much like. What I am interested in is what I consider to be a more comfortable and in some ways advantageous way of handling menus, one more suited to my tastes. However, since you mention it, how many features of KDE, gnome, or any other open source desktop environment are borrowed from osx and windows? How about vice versa? What about next-step? **How about LINUX itself being created as a very meticulous clone of UNIX?** Talk about hypocrasy.

---

### Post by drizek on 2005-08-20
the only way is to go to "run application" in gnome and then type in "kicker" and then you have to set up the uni menubar in kcontrol nad use only kde apps(cause gtk apps arent compatible with it). otherwise youre SOL.

---

### Post by aysiu on 2005-08-20
Sometimes I really hate the written word. No, I didn't intend it to be sarcastic at all. Now that I go back and read the post, it does sound that way, though. I'm completely serious, actually. I have Mac icons, a Mac window border, Mac controls, etc. If I had that global menu, it would be complete.

---

### Post by Arktis on 2005-08-20
Oh.  Sorry.  Well, just because features are there doesn't mean you have to use them.

---

### Post by Kvark on 2005-08-20
Ahh, interesting place to put the menubar at. Can't see any advantage since it still takes up screen space and it still fills the same function. But being able to customize where yet another thing should be would be fun!

---

### Post by SKLP on 2005-08-20
[QUOTE=Kvark]Ahh, interesting place to put the menubar at. Can't see any advantage since it still takes up screen space and it still fills the same function. But being able to customize where yet another thing should be would be fun![/QUOTE](Quoted from 
[http://mpt.net.nz/archive/2005/04/11/ubuntu](http://mpt.net.nz/archive/2005/04/11/ubuntu))

"Every window that has menus puts them in a separate menu bar inside the window. This (a) wastes screen real estate, (b) is confusing (even experts occasionally click the wrong menu bar by accident), (c) does not work for narrow windows (as demonstrated by the Gimp), (d) works badly for windows near the bottom or right of the screen (for which menus unexpectedly open upward or leftward), and (e) works even worse if those menus have submenus.

Worst of all, because under Fitt’s Law their vastly smaller target size outweighs their somewhat closer proximity, (f) menu bars inside each window are several hundred percent slower to use than a menu bar at the top of the screen.
"

---

### Post by pmj on 2005-08-20
I'm of the opinion that programs shouldn't have menu bars at all if it can be avoided.

But if there has to be a bar I'd rather have it in the application window. It makes far more sense for items that clearly belong to the application to be grouped with the application and not be mixed with things that are global and affects more/other things than the application.

Also, global menus could really mess things up for you if the wrong window has focus, something that happens to me frequently.

Wastes screen real estate? If anything is wasting screen real estate it's a menu at the top of the screen that you would hardly ever use.

---

### Post by basse1989 on 2005-08-20
[QUOTE=pmj]I'm of the opinion that programs shouldn't have menu bars at all if it can be avoided.

But if there has to be a bar I'd rather have it in the application window. It makes far more sense for items that clearly belong to the application to be grouped with the application and not be mixed with things that are global and affects more/other things than the application.

Also, global menus could really mess things up for you if the wrong window has focus, something that happens to me frequently.

Wastes screen real estate? If anything is wasting screen real estate it's a menu at the top of the screen that you would hardly ever use.[/QUOTE]
So you mean one menu bar in EVERY window uses less space than one global menu bar for all windows, huh? :P

btw. I'd like a global menu bar applet, and IMO it would fit very good into GNOME's standard panel layout since there's a lot of empty space on the top panel.

---

### Post by pmj on 2005-08-20
[QUOTE=basse1989]So you mean one menu bar in EVERY window uses less space than one global menu bar for all windows, huh? :P

btw. I'd like a global menu bar applet, and IMO it would fit very good into GNOME's standard panel layout since there's a lot of empty space on the top panel.[/QUOTE]
The top part of the screen is more valuable than any other part. And no, I don't want a menu bar in every window. I don't want any menu bars at all except in things like word processors that has a million functions and would absolutely need one.

I often interact with the top border of windows, such as right clicking, double clicking and dragging. Having a panel on top of the screen makes this much more time consuming. I ended up clicking on the panel several times a day when I meant to click on the window border. Since I had filled the panel with program shortcuts, often a program would start whenever I did this mistake. Highly annoying!

---

### Post by poofyhairguy on 2005-08-20
[QUOTE=pmj]
I often interact with the top border of windows, such as right clicking, double clicking and dragging. Having a panel on top of the screen makes this much more time consuming. I ended up clicking on the panel several times a day when I meant to click on the window border. Since I had filled the panel with program shortcuts, often a program would start whenever I did this mistake. Highly annoying![/QUOTE]

The trick is to add "show/hide" button to the top panel and get the panel to hide when you don't need it!

---

### Post by cowlip on 2005-08-20
[QUOTE=pmj]The top part of the screen is more valuable than any other part. And no, I don't want a menu bar in every window. I don't want any menu bars at all except in things like word processors that has a million functions and would absolutely need one.

I often interact with the top border of windows, such as right clicking, double clicking and dragging. Having a panel on top of the screen makes this much more time consuming. I ended up clicking on the panel several times a day when I meant to click on the window border. Since I had filled the panel with program shortcuts, often a program would start whenever I did this mistake. Highly annoying![/QUOTE]

Yep, that's why I don't even use it in KDE where you can! lol.  I am addicted to closing windows by throwing the mouse to the top right corner of the screen...both  follow fitt's law, too!

But hey if it's a choice, I don't mind :)

---

### Post by sethmahoney on 2005-09-13
I would also be very much interested in seeing this feature implemented.  Another thread here suggests that GTK isn't equipped to handle this kind of feature, but it does seem like it would be possible to implement, if difficult, by somehow intercepting the call to draw menus or whatever (or maybe I'm thinking too much like a Windows programmer).  Then again, I'm not much of a programmer, and certainly not much of a Linux programmer.

 Another useful feature (that may already be implemented) to consider in relation to global menus would be the option to reduce the "Applications", "Places", etc. menus to icons with no text, thereby allowing more room for something like a global menu.

I'm also wondering if it would be easier to program a panel replacement rather than an applet-dealey.

---

### Post by Perfect Storm on 2005-09-13
Wouldn't it be better with an applet that allow people to add their own menu bar instead? So people can choose how many bar menus to have, call them whatever they like etc. etc.

---

### Post by cowlip on 2005-09-13
[QUOTE=sethmahoney]

 Another useful feature (that may already be implemented) to consider in relation to global menus would be the option to reduce the "Applications", "Places", etc. menus to icons with no text, thereby allowing more room for something like a global menu.
[/QUOTE]

Well there's always "main menu" instead of "menu bar" applet.

---

### Post by sethmahoney on 2005-09-13
[QUOTE=Artificial Intelligence]Wouldn't it be better with an applet that allow people to add their own menu bar instead? So people can choose how many bar menus to have, call them whatever they like etc. etc.[/QUOTE]

Well, a panel replacement wouldn't exclude that possibility.  The reasons I suggest this route rather than the applet route are:

1.  We wouldn't be subject to the panel's limitations.  Skinning, arbitrary configurations, and a whole host of other features all become possible.

2.  I've heard panel applets can be difficult to program.  Never tried myself, so I dunno, but that's what I've heard.

3.  There's no guarantee that an applet will be forward-compatible.  Of course, there's no guarantee that a GTK app will be forward-compatible either, but it *seems* more likely.

There is one major limitation, which is that it would likely be difficult to program in support for adding applets to the menu bar, but I don't see that as a huge thing - its not like most people will want tons of crap clogging their menu bars.

---

### Post by IMELucky on 2006-10-15
I agree that there should be some way to add a global menu bar into GNOME. I'm a java programmer, so I really wouldn't be able to implement my own ideas, but I think that a panel applet would be a great idea. That way, the user can place the menu bar anywhere they want, or not have a global menu bar at all.

---

### Post by aktiwers on 2006-10-15
I saw someone post is one "gnome hack" here on the Ubuntuforums, that did this exact thing. Hold on.. I will look if I can find it.

EDIT:
Hmm..  couldnt find it - but im sure I saw it here somewhere.
Anyways I found this in my search (as I rememberd that the guy who posted it here, also posted it on ArchLinux forum, or so he said.).
It isnt the same thing as I saw here but looks like what you are talking about.
[http://bbs.archlinux.org/viewtopic.php?t=25749&highlight=gnome+mac+menu+panel](http://bbs.archlinux.org/viewtopic.php?t=25749&highlight=gnome+mac+menu+panel)

---

### Post by Guy_AD on 2009-04-12
For a global menu applet in GNOME 2:

[http://code.google.com/p/gnome2-globalmenu/]("http://code.google.com/p/gnome2-globalmenu/")

I tried it and it works a treat.

---

### Post by CraigPaleo on 2009-04-12
> **Guy_AD said:**
> For a global menu applet in GNOME 2:

[http://code.google.com/p/gnome2-globalmenu/]("http://code.google.com/p/gnome2-globalmenu/")

I tried it and it works a treat.

What a perfect day to resurrect an old post! On Easter! I've done it before myself without realizing it.

---

