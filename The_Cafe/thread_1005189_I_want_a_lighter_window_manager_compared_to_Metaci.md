---
title: "I want a lighter window manager compared to Metacity -- Where should I start?"
date: 2008-12-08
forum: The Cafe
---

### Post by kevdog on 2008-12-08
I need some opinions about where to go since I want to dump Metacity/Gnome.  Fluxbox,Enlightenment,IceWM?  Where should I go?  I really need some opinions and comments.

---

### Post by cardinals_fan on 2008-12-08
**Fluxbox**,** Openbox**, and **Pekwm** are all similar and are all excellent.  Openbox is the easiest to start out with, especially if you install obconf.  I personally feel that **dwm** is the best window manager ever written, but it's a tiling WM (which I like, but you might not).

---

### Post by RiceMonster on 2008-12-08
I really like Xfce and Openbox. Openbox is highly recommended if you want something to play with. It's very configurable, lightweight, and themes are extremely easy to make (and make them look good, at that).

---

### Post by mentallaxative on 2008-12-08
Are you looking to replace Metacity as Gnome's default WM with something else, or are you looking to ditch Gnome altogether?

---

### Post by kevdog on 2008-12-08
> **cardinals_fan said:**
> **Fluxbox**,** Openbox**, and **Pekwm** are all similar and are all excellent.  Openbox is the easiest to start out with, especially if you install obconf.  I personally feel that **dwm** is the best window manager ever written, but it's a tiling WM (which I like, but you might not).

I have to say I love these statements from the dwm website: 

> Because dwm is customized through editing its source code, it's pointless to make binary packages of it. This keeps its userbase small and elitist. No novices asking stupid questions.

I want to get rid of Gnome/Metacity altogether.

---

### Post by aysiu on 2008-12-08
I'd go with IceWM. But really you should go with whatever you're comfortable configuring. All of the ones you mentioned are lighter than Metacity.

---

### Post by cardinals_fan on 2008-12-08
> **kevdog said:**
> I have to say I love these statements from the dwm website: *snip*
Indeed :).  To be honest, the dwm mailing lists are really quite friendly, and I'm always happy to help on these forums.
> **kevdog said:**
> 
I want to get rid of Gnome/Metacity altogether.
Do you need a panel and other DE stuff?  If so, consider:

a) Xfce
b) LXDE (Openbox at heart)
c) A *box with something like pypanel or tint

---

### Post by dannytatom on 2008-12-08
I installed xfce today and am enjoying it. It runs a lot faster than gnome & kde, though not as pretty.

---

### Post by RiceMonster on 2008-12-08
> **dannytatom said:**
> I installed xfce today and am enjoying it. It runs a lot faster than gnome & kde, though not as pretty.

I think Xfce can look just as good as GNOME because it's GTK based, so it can use the same themes (not the WM ones though).

This is what my Xfce desktop looks like:
[http://ubuntuforums.org/showpost.php?p=6328839&postcount=245](http://ubuntuforums.org/showpost.php?p=6328839&postcount=245)

---

### Post by ChanServ on 2008-12-08
openbox or wmii i say.

---

### Post by dannytatom on 2008-12-08
> **RiceMonster said:**
> I think Xfce can look just as good as GNOME because it's GTK based, so it can use the same themes (not the WM ones though).

This is what my Xfce desktop looks like:
[http://ubuntuforums.org/showpost.php?p=6328839&postcount=245](http://ubuntuforums.org/showpost.php?p=6328839&postcount=245)

I was wandering how you got yours like that, and does it run just as smoothe as the default themes?  

I, for some reason, can't get themes to install.  If I could do that, and stop being too lazy to edit the menu, I'd be 100% happy with it.  The default menu is too unorganized for me. :/

---

### Post by RiceMonster on 2008-12-08
> **dannytatom said:**
> I was wandering how you got yours like that, and does it run just as smoothe as the default themes?  

I, for some reason, can't get themes to install.  If I could do that, and stop being too lazy to edit the menu, I'd be 100% happy with it.  The default menu is too unorganized for me. :/

Yep, it runs just as fine, no difference at all. If you want to install a theme, download the tarball and extract it to ~/.themes/

For icons, extract them to ~/.icons/

Then, you can go to the user interface settings and you can select the theme from there.

---

### Post by kevdog on 2008-12-08
I want lighter than xcfe

Preferably I want a dock, tray/panel.  That's about all.

---

### Post by p_quarles on 2008-12-08
> **kevdog said:**
> I need some opinions about where to go since I want to dump Metacity/Gnome.  Fluxbox,Enlightenment,IceWM?  Where should I go?  I really need some opinions and comments.
It's important to note, first of all, that Fluxbox, Enlightenment and IceWM are replacements for Metacity, and **not** for Gnome. A window manager will never replace all of the things that a complete graphical environment does. 

That said, I use Fluxbox. It's extremely flexible, it's in active develepment, and it looks good. I would recommend it above Enlightenment for stability, and above IceWM for configurabilty. Above Openbox and PekWM for features.

---

### Post by Rokurosv on 2008-12-08
Openbox or Fluxbox are good choices, IceWM and JWM are also good choices.

---

### Post by -grubby on 2008-12-08
I used Fluxbox for quite some time, it was nice and comes with some graphical configuration tools (though the config files are quite simple; I'd must rather edit them by hand then by a GUI tool). I use wmii, but it took me about 3 or 4 tries to finally get to like the tiling. I wouldn't recommend it unless you want to try something radically new.

---

### Post by mentallaxative on 2008-12-08
> **kevdog said:**
> I want lighter than xcfe

Preferably I want a dock, tray/panel.  That's about all.

Look up lxde. It's basically Openbox with a couple of other apps like a panel, terminal and file manager (Pcmanfm) added to flesh it out.

---

### Post by zmjjmz on 2008-12-08
Have you ever tried twm?
That's close to as light as it gets.

---

### Post by bobbocanfly on 2008-12-08
I'd highly recommend Openbox. The stock Openbox is very plain and you need to config it all your self, so I'd recommend checking out a LiveCD of it, before you download the packages etc. (CrunchBang Linux has one of the nicest default Openbox setups I have foubd).

---

### Post by Chilli Bob on 2008-12-08
I had JWM replacing Metacity for a while and it looked great (if a bit retro for some tastes).  After a few weeks it all fell apart though and Metacity took over again.  I never worked out what happened.

I also recommend openbox and IceWM.  Or drop Gnome altogether and use LXDE, it's a very sweet little DE.

---

### Post by acelin on 2008-12-08
Windows Aero is pretty light from my experience. At least the toolbar shows up on every login, unlike Gnome, and the interface is intuitive, unlike KDE.

---

### Post by renzokuken on 2008-12-08
openbox gets my vote. its very easy to do. just follow **urukrama's** extensive and thorough guide. its excellent.

if you are using intrepid you can simply install everythng you need via

```
sudo apt-get install openbox obconf obmenu
```

this will give you the latest version (no need to compile anything as the installation procedure in that guide was actually written for previous versions of ubuntu.........everything else is valid though)

here is my desktop using openbox and pypanel
[http://ubuntuforums.org/showpost.php?p=6313080&postcount=163](http://ubuntuforums.org/showpost.php?p=6313080&postcount=163)

---

### Post by 3rdalbum on 2008-12-08
Openbox is fine if you're planning to run it without Gnome.

Metacity itself is so insignificant in terms of weight, that there's almost no difference between Metacity on Gnome and Openbox on Gnome.

---

### Post by kevdog on 2008-12-08
Any dock application you would prefer over others?

---

### Post by urukrama on 2008-12-08
Try Openbox. It is the best window manager to start, and the best window manager to stick with :p Have a look at my guide if you need help getting started with Openbox (link in signature).

---

### Post by chucky chuckaluck on 2008-12-08
openbox and fluxbox are very similar. obmenu makes openbox's menu even easier to configure than fluxbox's. flubox comes with a panel, openbox does not (you can use tilt, pypanel, bmpanel, perlpanel, xfce4-panel, etc). dwm is my favorite and, imltho, the fastest tiling wm. icewm is pretty zippy, but i hate trying to work its menu (it can get pretty cheesy looking, too). e17 is beautiful, but psychotic.

---

### Post by kevdog on 2008-12-08
> e17 is beautiful, but psychotic.

I mean this truthfully, but could you provide a little bit more details on this?

---

### Post by chucky chuckaluck on 2008-12-08
> **kevdog said:**
> I mean this truthfully, but could you provide a little bit more details on this?

trying to get the menus setup is where it all goes wrong for me with e17. in trying to add apps to a menu, i've had everything happen from the app never showing up to showing up multiple times. or, if i change the icon of an app, it disappears from all the menus, for no apparent reason. it sure is pretty, though, and worth at least trying.

---

### Post by igknighted on 2008-12-08
> **kevdog said:**
> Any dock application you would prefer over others?

Since you are looking for light, I would say wbar is the way to go.

---

### Post by mikjp on 2008-12-09
Try openbox, pekwm, enlightenment or lxde. 

mikko

---

