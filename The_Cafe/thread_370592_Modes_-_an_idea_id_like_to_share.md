---
title: "Modes - an idea id like to share"
date: 2007-02-25
forum: The Cafe
---

### Post by uzusan on 2007-02-25
Recently while digging through menus looking for a particular application (RapidSVN if your at all interested), I started to think of an idea which i think could be really useful.

I got to thinking about the way the menu in gnome was organised. There were applications there that i just didn't use all that often. There are applications that i use on occasion, when I'm doing something specific, like programming. However i realised that there are groups of applications that i use when doing specific things. Take programming again as an example. I might use programs like monodevelop, anjuta, glade and a whole host of other related applications. 

The key word that sparked this idea was related. When im engaging in a specific task, there are a core set of applications that i like to use for each task. There are also some programs that i would use at any time, such as the terminal, music players and so on.

The basic idea of modes would be to set up the window manager, be it Gnome or KDE or Enlightenment etc in such a way that you could customise what options are in use, depending on what type of task you are doing. (I'm going to explain this idea based on gnome as its the one im most familiar with, I'm not sure how applicable some of this could be to other window managers, though i think the main premise could be used with any window manager).

The menu items idea would just be the start. You could have different properties for almost anything depending on what "mode" you were currently in. Let me explain further with examples: (Ignore the specifics, these are just to illustrate the idea)

[B][U]Development mode:
[/U][/B]
(Programming, Web Development an so on.)

Menu Items:
Monodevelop
MonoDoc
Anjuta
Glade
...

Menu Properties:
Icons set to off (Faster loading)
...

Panel properties:
Change layout to one panel at top with menu at left and tasklist in center
...

Desktop Icons:
Projects Directory Icon
...

Compiz / Beryl:
Settings Off

Workspaces:
4

**_Web Browsing Mode:_**
(Anything Internet related.)

Menu Items:
Firefox
Thunderbird
Gaim
...

Menu Properties:
Icons set to on

Panel Properties:
Change layout to two panels, one top, one bottom with menu at top and task list on bottom.
...

Desktop Icons:
Downloads Directory
...

Compiz / Beryl:
Settings On

Workspaces:
2

**_Minimal Mode:_**
(When you want to run an app with the most resources available, in this example for running a game through WINE)

Menu Items:
Wine (Set up for the game)
...

Menu Properties:
Icons set to Off

Panel Properties:
Change layout to one panel at top with menu at left.
...

Desktop Icons:
None

Compiz / Beryl:
Settings Off

Workspaces:
1

and other resource saving options.

The idea is that everyone would be able to customize the settings to suit for each mode. I had the idea of a combo box that could be placed on one of the panels that has a list of modes. You would click the combo box to change between modes and all of the settings would change to suit whatever task you are doing.

For this idea to work you would need to choose which mode a particular setting was applicable to. I thought of having something like 3 options for choosing which mode:

This mode.
All modes.
Specific modes. (which would then list each mode and you could choose just them modes you wanted the property to be applicable in)

It would be good if you could have this choice for each setting in both a central config utility and in the properties of each of the affected applications. For example if you clicked on an icon, there would be an extra tab where you could choose which mode it was available in, or you could go to the config utility and look at all the icons on the desktop and choose the icons for each mode.

I would love to start making something like this myself, but i don't have enough technical knowledge of linux yet to know where to begin. Let me know what you think.

---

### Post by Adamant1988 on 2007-02-25
I have to say, I think I could see the use in this.  It would be nice to have applications I wasn't looking for sort themselves out for me.  Narrowing my choices down to the applications I need for the task I'm doing at this particular moment. 

However, may I suggest some changes? 

Perhaps these "modes" should be user created and editted, so as not to pre-define anything and alienate anyone.   The modes could also be specific to a certain desktop, for example:

"John creates a new user mode called "kids"  that sorts out applications that John would rather his kids not mess with.  John then assigns this user mode to desktop #4."

So now, the menu in "desktop #4" would (until otherwise instructed) be permanently sorted to the "Kids" mode.

---

### Post by uzusan on 2007-02-25
I agree that the modes shouldn't be limited in anyway by what other people might think is useful but may not necessarily be useful to you.  I was thinking that perhaps it would start off with some pre-defined modes that some people might find useful (like some of the ones I mentioned) but allow the editing of all of the modes and all of the options.

such as adding new modes / changing existing ones.

I was thinking of a mode type similar to what you have suggested about the kids mode. I had the idea of a restricted mode, with limited access to certain applications (and no terminal) and then have the combo box ask for the admin password to change from that mode into any other so that anyone could use the computer without accidentally changing something they shouldn't.

---

### Post by Adamant1988 on 2007-02-25
> **uzusan said:**
> I agree that the modes shouldn't be limited in anyway by what other people might think is useful but may not necessarily be useful to you.  I was thinking that perhaps it would start off with some pre-defined modes that some people might find useful (like some of the ones I mentioned) but allow the editing of all of the modes and all of the options.

such as adding new modes / changing existing ones.

I was thinking of a mode type similar to what you have suggested about the kids mode. I had the idea of a restricted mode, with limited access to certain applications (and no terminal) and then have the combo box ask for the admin password to change from that mode into any other so that anyone could use the computer without accidentally changing something they shouldn't.

The possibilities are certainly there.  However, you need to be talking to developers about this to see how difficult it would be to implement, etc.

---

### Post by Tomosaur on 2007-02-26
Actually, I really like this idea. It could even be implemented as a seperate project from Gnome - allowing other Desktop managers to take advantage of it and use it in other distrobutions. All it'd take would be to alter that desktop manager's environment / menu configuration files. It wouldn't even be a complex thing to implement, you'd just need to know how each desktop manager configured it's menus, and that is probably one of the easiest things you could find out.

---

### Post by Adamant1988 on 2007-02-26
> **Tomosaur said:**
> Actually, I really like this idea. It could even be implemented as a seperate project from Gnome - allowing other Desktop managers to take advantage of it and use it in other distrobutions. All it'd take would be to alter that desktop manager's environment / menu configuration files. It wouldn't even be a complex thing to implement, you'd just need to know how each desktop manager configured it's menus, and that is probably one of the easiest things you could find out.

There are a lot of desktop managers.  Loving the idea though, anyone know a good mailinglist/forum to take this too?

---

### Post by Deathshrimp316 on 2007-02-26
I agree its a very good idea. I usually end up with a desktop for working in and a desktop for firefox/gaim etc. Could really see this being useful if it were able to be applied on a per-desktop basis.

---

### Post by uzusan on 2007-02-26
thanks for the replies everyone. I think i might have a go at trying to pull something (very basic) together to try it out. At least on the menu icons side of things.

I was looking at the menu editor alacarte for gnome and it sounds as if it would be ideal for this use, only problem being i dont know python (or much xml for that matter).

I think it may be worth a bit more investigation. (The ability to hide specific icons is exactly what i was thinking would be needed for this.)

---

### Post by 23meg on 2007-02-26
Check out the GNOME Panel Switcher, which lets you switch to preset panel configurations easily. It's not working very reliably at the moment, but the code can be reused in implementing your idea:

[https://wiki.ubuntu.com/PanelSwitcher](https://wiki.ubuntu.com/PanelSwitcher)

---

### Post by Tomosaur on 2007-02-26
The gnome menu configuration files are in /etc/xdg/menus. You'd only need to write a simple XML parser (there are loads of libraries for this already, so you can do it in whatever language you find best). There doesn't even really need to be a complex frontend - an idea would be a small applet to quickly switch modes, similar to the workspace switcher.

Not sure how KDE configures it's menus, but fluxbox also follows a text based approach. I don't think it uses XML, but the amount of code this project would involve is still very small, it's just parsing rules really.

---

### Post by Wolki on 2007-02-26
I don't really see the point - I'd guess that managing modes will take up most of the time you might save, and it complicates things a lot.

I guess one could use different user accounts for this, and the fast user switch applet to change modes. Only problem would be to share configuration between modes where relevant, so you'd have to play with permissions a bit.

---

### Post by Tomosaur on 2007-02-26
> **Wolki said:**
> I don't really see the point - I'd guess that managing modes will take up most of the time you might save, and it complicates things a lot.

I guess one could use different user accounts for this, and the fast user switch applet to change modes. Only problem would be to share configuration between modes where relevant, so you'd have to play with permissions a bit.

I dunno - there'd probably be a few preset modes available, but you can extend or shorten those as you see fit. The end user probably wouldn't have to manage the modes themselves unless they really wanted to - the way it works now is that categories are already recognised by the package manager. However, for Ubuntu, there's no 'real focus' on what it's targeted at, it's more or less a generic operating system. With other distributions, they're specifically targeted at certain audiences. For example, one may be targeted at web developers, one at artists, one at audio producers etc. This modes idea would enable users of generic distributions to temporarily reconfigure their machine for a certain use, without having to mess around with removing packages etc. It'd certainly help me - I usually get distracted by other apps than those I'm using to work. If I could switch to the right 'mode' for the job - then all of those potential distractions would dissappear. It could also be extended to configure the desktop in general. For example, if I wanted the background to become a terminal (using devilspie, for example), and I wanted some IDE or text editor to open, then this could happen. Yes, I could just use a shell script for this, but I still think it's a nice idea - it certainly wouldn't detract from anything, and it'd be nice to be able to set this kind of thing up without spending a while setting up a shell script.

---

### Post by prizrak on 2007-02-26
That's actually an interesting idea. Would be even more valuable if modes can be set on per workspace basis so that you will have different sets of applications in different workspaces and perhaps opening certain applications will automatically put on the correct workspace regardless of where and how it was open. 

Would be pretty useless for regular users but I think power users will be happy about it.

---

### Post by H.E. Pennypacker on 2007-02-26
Sounds like a great idea.  Excellent idea.

---

### Post by Adamant1988 on 2007-02-26
> **prizrak said:**
> That's actually an interesting idea. Would be even more valuable if modes can be set on per workspace basis so that you will have different sets of applications in different workspaces and perhaps opening certain applications will automatically put on the correct workspace regardless of where and how it was open. 

**Would be pretty useless for regular users but I think power users will be happy about it.**

I don't know, I'd be happy to not have to sort through all of the applications my friends/girlfriend install on my computer while I'm working.  I'm sure Jess (My girlfriend) isn't too fond of digging through my applications either.

---

