---
title: "[IDEA] -- Don't allow any programs to steal the users focus!"
date: 2007-11-01
forum: Ubuntu Brainstorm
---

### Post by altonbr on 2007-11-01
**Summary:**
Pidgin, Synaptic and many other programs pop up over (aka: take focus of) programs that the user is currently using.

**Scope and Use Cases:**
* Stephanie is not a great typer and needs to look down at the keys to type. She gets annoyed when she notices half her e-mail to her father did not get printed because Synaptic finished downloading software, starting installing it and took focus from OpenOffice.org

* Anirudh is typing on a forum in Firefox when a friend messages him in Pidgin. Part of his message starts to write on his friend's Pidgin window and he hits enter to go to the next line, but since the Pidgin window popped up and it happened so fast, he accidentally sent part of a forum message to a friend.

* Anita is a power-user and uses only her keyboard to get around in her Nautilus GUI so she is used to using 'alt' + 'tab' to switch focus of programs. She has many windows open on the bottom panel, including Thunderbird, Firefox, OpenOffice, Gimp and Pidgin. She gets annoyed that every time one of the programs takes focus of her current program, she has to hold 'alt' and hit 'tab' multiple times to get back to her program.

**Implementation Plan:**
Don't allow programs to take a users focus unless specifically requested on a per program basis. Or simply don't allow it at all and use a GTKtooltip to show that a program want focus.

If the former, give programs a weighting on whether they are allowed to take focus over other programs and give a second weighting for if a program will allow its focus to be taken.

Example (1 never; 100 always):
```
Program	 	Steal Focus Rating	  Lose Focus Rating
Pidgin 			1 			1
Synaptic 		1 			100
Firefox 		50 			50
OpenOffice.org		51 			1
```

This will allow Pidgin to always keep it's focus but never steal it, allow Synaptic to never steal focus but always give it up, allow Firefox to steal focus from Synaptic and give it up only to OpenOffice.org and allow OpenOffice.org to steal focus from Firefox but never loose it.

---

### Post by fnjordy on 2007-11-02
Why would you want applications to lose focus?

I understand the need to improve focus handling:  Synaptic is really annoying steeling focus for updates.

---

### Post by yabbadabbadont on 2007-11-02
Preventing focus stealing is a function of the window manager.  So it would be up to the upstream devs (for Gnome/KDE/XFCE/*box/...) to decide whether or not they will implement it.  I believe that KDE already has some settings dealing with focus stealing, but I don't know about the others.

---

### Post by altonbr on 2007-11-02
> **fnjordy said:**
> Why would you want applications to lose focus?

I understand the need to improve focus handling:  Synaptic is really annoying steeling focus for updates.

Yeah, that last part was a conjecture on how it could be safely and conveniently implemented with user input. I prefer to not have focus taken at all.

---

### Post by smartboyathome on 2007-11-02
I would not like this for all situations. When I am working with the panel/menus, it is annoying that the properties NEVER come up, while other things do. It would be good to have this when playing a full screen game though (it always freezes my computer when a popup comes up while playing :().

---

### Post by altonbr on 2007-11-03
> **smartboyathome said:**
> I would not like this for all situations. When I am working with the panel/menus, it is annoying that the properties NEVER come up, while other things do. It would be good to have this when playing a full screen game though (it always freezes my computer when a popup comes up while playing :().

So then do you think my rating system would be worthwhile to implement?

---

### Post by Hairy_Palms on 2007-11-03
i think it should be a given that the application the user is focusing is the one he wants focused, so no stealing at all, they can give a visible signal by making their taskbar entry flash as pidgin does at the moment when you get a new message in an already open window.

---

### Post by amiga_os on 2007-11-03
Since this is popular, is it worth filing a bug report?

I don't know what we'd file it under... Gnome maybe?  Saying something like "unexpected behaviour: programs steal focus uneccesarily, this potentially causes crashes"

Can you describe how you'd recreate your computer crashing when this happens, then I can file a bug report.

(describing easy ways to recreate the bug makes it more useful)

---

### Post by smartboyathome on 2007-11-03
> **Hairy_Palms said:**
> i think it should be a given that the application the user is focusing is the one he wants focused, so no stealing at all, they can give a visible signal by making their taskbar entry flash as pidgin does at the moment when you get a new message in an already open window.

If this happened, you would see me on XFCE. I don't ALWAYS want to be using the program that is up. If this was implimented, then you would have to go down to the desktop in order to open up the program you want in front. And about the rating system, maybe instead of that, have a thing which makes it so only certain programs cannot steal focus, and maybe certain programs that can not have their focus stolen.

---

### Post by amiga_os on 2007-11-03
> **smartboyathome said:**
> If this happened, you would see me on XFCE. I don't ALWAYS want to be using the program that is up. If this was implimented, then you would have to go down to the desktop in order to open up the program you want in front. And about the rating system, maybe instead of that, have a thing which makes it so only certain programs cannot steal focus, and maybe certain programs that can not have their focus stolen.

Can I ask when you would like the system to steal focus?  Can I suggest that there are two factors involved here that make this complicated: the program you are using and the program that wants to steal focus.

Maybe you would like synaptic to steal focus when you are using open office, but not when you are playing a game.  It would be quite complicated for a system to ascertain when a program can and can't steal focus.

The way around that problem is actually the method that's already been suggested - a rating system, that allows open office to be trumped by synaptic, but a full screen game is never interrupted.

---

### Post by yelo3 on 2007-11-03
for sure I don't want that the focus is stolen when I'm writing a password...

---

### Post by aysiu on 2007-11-03
I can't think of a single situation in which I want focus stolen from my current app.

I wouldn't mind the window list item flashing to let me know that another application needs my attention, though.

---

### Post by yabbadabbadont on 2007-11-03
Let me reiterate.  Focus handling is controlled by the window manager and **not** the running applications.  The apps can set hints for the WM to tell it that they need attention (hence the flashing task bar entry with some WM's), but it is the WM's decision as to who gets focus.  Therefore, it is up to the developers of the various window managers, and not the Ubuntu devs (except for ones who are also WM devs) to add/modify this feature.  If you have focus issues with a particular window manager, then file a proper bug about it were it may do some good.  ;)

---

### Post by altonbr on 2007-11-05
> **yabbadabbadont said:**
> Let me reiterate.  Focus handling is controlled by the window manager and **not** the running applications.  The apps can set hints for the WM to tell it that they need attention (hence the flashing task bar entry with some WM's), but it is the WM's decision as to who gets focus.  Therefore, it is up to the developers of the various window managers, and not the Ubuntu devs (except for ones who are also WM devs) to add/modify this feature.  If you have focus issues with a particular window manager, then file a proper bug about it were it may do some good.  ;)

So if I use GNOME and have based this idea on GNOME, I *have* to file a bug with GNOME? Why can't Ubuntu devs make a program a focus controlling program in Python (or a similar language, permitted they have time). I don't think this has to be implemented at the low level of Nautilus, but could be a specific Ubuntu program.

Of course, that being said, I don't *want* this to be a Ubuntu-only project because any advancement in Linux should be shared freely and this is most easily implemented if it were put into Nautilus code.

But how to implement it? I'm not sure code wise, but you could easily have something in "System > Preferences > Program Focus" (rough example) that says "What program would you like to edit?" > "OpenOffice.org". "Programs that can steal focus" > "None". "Programs you'd like OpenOffice.org to steal focus from" > "All".

Or, when the user doesn't want "None" or "All", give the user a drop-down list of all the programs available. When he or she selects a program, another drop down list opens up in case they'd like a second program, and so on.

Doesn't sound too efficient at the moment, but at least we're thinking.

If we had a interface for at least the Ubuntu devs to use to set for all of the program focus settings (which then each user could edit in gconf) then I think that would be the most efficient (so far). Or use sqlite but I'm not sure how efficient that is.

---

### Post by smartboyathome on 2007-11-05
> **altonbr said:**
> So if I use GNOME and have based this idea on GNOME, I *have* to file a bug with GNOME? Why can't Ubuntu devs make a program a focus controlling program in Python (or a similar language, permitted they have time). I don't think this has to be implemented at the low level of Nautilus, but could be a specific Ubuntu program.

Yes, (or metacity, if you want  to get technical). Also, you would have to file a bug with Compiz Fusion, as it is a different Window Manger.

---

### Post by 23meg on 2007-11-06
> **altonbr said:**
> So if I use GNOME and have based this idea on GNOME, I *have* to file a bug with GNOME? 

I wouldn't say that you have to, but it can be useful. A good thing to do at this point would be to do a search at the GNOME bug tracker under the product Metacity; it's very likely that someone has had a similar idea before.

> **altonbr said:**
> Why can't Ubuntu devs make a program a focus controlling program in Python (or a similar language, permitted they have time). I don't think this has to be implemented at the low level of Nautilus, but could be a specific Ubuntu program.

No, the best way to go about this kind of thing is to get it implemented upstream. Note that it doesn't matter who implements it; I'm talking about *where* it's implemented. It could be Ubuntu developers, GNOME developers, or just a random citizen wandering in the bug tracker looking for things to fix.

With that said, Metacity has always been about simplicity, and has often been criticized for being over-simplistic; I doubt that advanced configuration settings that are advertised upfront will be considered.

---

### Post by Hairy_Palms on 2007-11-07
> If this happened, you would see me on XFCE. I don't ALWAYS want to be using the program that is up. If this was implimented, then you would have to go down to the desktop in order to open up the program you want in front. And about the rating system, maybe instead of that, have a thing which makes it so only certain programs cannot steal focus, and maybe certain programs that can not have their focus stolen.
id be curous to what the situation you would want focus stolen is, you wouldnt have to go do the desktop, you can click on its taskbar entry or alt-tab to it, currently alt-tab gets broken by focus stealing causing you to need to switch away and back to your current app to let it gain focus.

---

### Post by smartboyathome on 2007-11-07
> **Hairy_Palms said:**
> id be curous to what the situation you would want focus stolen is, you wouldnt have to go do the desktop, you can click on its taskbar entry or alt-tab to it, currently alt-tab gets broken by focus stealing causing you to need to switch away and back to your current app to let it gain focus.

(Like I said before) Full screen games get broken by focus stealing (just like they were broken by compiz before during Gutsy development), and also when I am working on a paper, and pull up the web browser, I usually type while it is coming up, and if it covers the paper, I can loose my train of thought (which can get pretty frustrating at times).

---

### Post by Hairy_Palms on 2007-11-07
> (Like I said before) Full screen games get broken by focus stealing (just like they were broken by compiz before during Gutsy development), and also when I am working on a paper, and pull up the web browser, I usually type while it is coming up, and if it covers the paper, I can loose my train of thought (which can get pretty frustrating at times).
i think you misread my question, i said when would you WANT this behaviour, you mentioned that if focus stealing was stopped youd move to xfce, those above are all situations when focus stealing is bad.

---

### Post by CrazyGuy123 on 2007-11-09
A complex way of deciding if focus should be stolen makes the system appear inconsistant to the user.  (ie. imagine explaining to your parents that "when the window pops up updates are done, unless you're using firefox, in which case when the taskbar flashes updates are done")

Either focus stealing should be allowed, or it should be disallowed - no inbetween.

One option that could be considered, is that an application should be able to pop on top, but not steal the focus - ie. crazy things won't happen when you're typing.

---

### Post by hotani on 2007-11-22
this has been at the top of my short list of major complaints with WMs. The ones I use most often all do it: metacity, compiz and xfwm.

No window should ever steal focus or pop up in front of what the user is doing. Show an alert in the notification area (e.g. when firefox is updated it shows a subtle but noticable icon that when clicked shows information about the last update.). Another option would be to flash the item in the window list in the panel. Anything but jumping in front of the current window would be a plus.

---

### Post by 23meg on 2007-12-12
[http://ejohn.org/blog/bad-background-browser/](http://ejohn.org/blog/bad-background-browser/)

---

### Post by altonbr on 2007-12-13
> **23meg said:**
> [http://ejohn.org/blog/bad-background-browser/](http://ejohn.org/blog/bad-background-browser/)

Good article, thanks.

Go Firefox 3 :)

---

