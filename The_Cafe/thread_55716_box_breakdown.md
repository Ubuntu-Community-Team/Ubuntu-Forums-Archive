---
title: "*box breakdown"
date: 2005-08-10
forum: The Cafe
---

### Post by TravisNewman on 2005-08-10
I know a lot of you have a lot of opinions about the *box environments. I understand that they're all quite similar, yet quite different. I've used them all, but none to the extent I would like. I admit, I got discouraged by the not-so-easy-to-use customization, but that was a year ago or so, and I've come a long way since, and I want to get back into them. or at least one.

Now, I know of Blackbox, Fluxbox, and Openbox. What are the pros, cons, etc etc of them? High points and low points? Basically, I'm looking for ease of use (the least important), possibility of some sort of desktop (I guess rox might come in there, but would that take away the *box menu?), how customizable they are, how easy it is to get a menu like the debian menu, or the gnome/kde/xfce applications menus so that I don't have to manually add launchers to the menu (another thing that irked me last time), quality of pre-existing documentation, and anything else you think is relevant.

Poofy, I know, E17. I could just never get into it.

---

### Post by poofyhairguy on 2005-08-10
[QUOTE=panickedthumb]
Poofy, I know, E17. I could just never get into it.[/QUOTE]

How about E16 then? Still being developed.....

I like openbox, but all the themes are all small. I would be happy to find one that has close buttons  that are big as your average Metacity theme.

Fluxbox is the only window manager in the GNU world that I can honestly say I'm SCARED of....I tried once and it "put the fear in me."

---

### Post by TravisNewman on 2005-08-10
[QUOTE=poofyhairguy]How about E16 then? Still being developed.....
[/QUOTE]

I meant Enlightenment as a whole actually... but i do plan on trying it out again soon

---

### Post by drizek on 2005-08-10
there is also FVWM, which can be made to look really really nice. FVWM and e17 are actually cool. the *boxes are just performance-oriented.

---

### Post by poofyhairguy on 2005-08-10
[QUOTE=panickedthumb]I meant Enlightenment as a whole actually... but i do plan on trying it out again soon[/QUOTE]

Often I used to think "when is Linux going to stop copying desktop ideas from Windows and OSX and do things that are new?" Those thoughts stopped after messing with E. It leaves you Enlightened.

---

### Post by nocturn on 2005-08-10
[QUOTE=poofyhairguy]Often I used to think "when is Linux going to stop copying desktop ideas from Windows and OSX and do things that are new?" Those thoughts stopped after messing with E. It leaves you Enlightened.[/QUOTE]

I actually ran E16 as my primary desktop for a while.  But when it comes to everyday work, I find Gnome suits better (just an opinion).
E is cool though.

---

### Post by miscz on 2005-08-10
Blackbox - I haven't used it, seems pretty basic
Fluxbox - There are lots of Fluxbox specific menu-editors, configurators, desktop switchers. It supports transparency extensions for x.org but seems kinda slow o_O
Openbox - Very light, very basic, there are some gui menu editors available, I can't stand manual configuration via XML
PekWM - Often overlooked *box wm, there are no tools for configuration so you have to edit it by hand. I found PekWMs config files straight-forward and very flexible.

---

### Post by Lowe on 2005-08-10
Fluxbox isn't standards compliant plus I never liked it, jaggy looking toolbar and menus. Openbox is just great, really nice menu's and themes xml is very easy to edit no need for a menu editor. ;) (oh and openbox is standards compliant.)

openbox + pypanel is great. Here is a screenshot of my desktop. [http://xs40.xs.to/pics/05315/openbox.png](http://xs40.xs.to/pics/05315/openbox.png)

---

### Post by egon spengler on 2005-08-10
What are these standards fluxbox does not conform to?

Out of the various *box on linux I've only used flux, been meaning to give openbox a try but not as of yet. I think it's pretty easy to set up, there's a command to create a menu automatically create a menu so you don't need to do it all manually first time (can't remember the command right now but check the latest flux thread on 5.04 desktop support). Fluxmenu theoretically makes the menu easier to tweak but peronally I find it easier to just use gedit, especially when you want to alter the order of menu items. Gedit's drag + drop is much easier to use. Another drawback of fluxmenu is that it overwrites any icons in your menu when it saves.

---

### Post by Lowe on 2005-08-10
[QUOTE=egon spengler]What are these standards fluxbox does not conform to?
[/QUOTE]

These [http://freedesktop.org](http://freedesktop.org). Openbox only has 2 config files one for the menu and one for the main config, openbox also has obconf that helps do most stuff.  :razz:

---

### Post by Stormy Eyes on 2005-08-10
[QUOTE=Lowe]openbox + pypanel is great. Here is a screenshot of my desktop. [http://xs40.xs.to/pics/05315/openbox.png](http://xs40.xs.to/pics/05315/openbox.png)[/QUOTE]

Dude, what's that display at the top of your screen that you're using to show what's currently playing? Is that torsmo, by any chance? If so, would you mind posting your .torsmorc?

---

### Post by Stormy Eyes on 2005-08-10
[QUOTE=drizek]the *boxes are just performance-oriented.[/QUOTE]

What's wrong with that? Openbox *is* cool. It does its job, does it well, and can be made to look very elegant. It's the Harley-Davidson of window managers.

And Harleys f---ing rule.

---

### Post by kvidell on 2005-08-10
[QUOTE=Stormy Eyes]What's wrong with that? Openbox *is* cool. It does its job, does it well, and can be made to look very elegant. It's the Harley-Davidson of window managers.

And Harleys f---ing rule.[/QUOTE]
 I knew I was crazy thinking I was the only linux geek that liked Harley's and Buells too.
I think you're the only other one I know of now >.> Are we really this sparse?

As for the topic at hand:
I like FluxBox a lot. The first time I ever used Debian, I used Flux. It was great, I didn't do a lot of tweaking but I did have fun with it.
I haven't had the patience to get it going the same again, though. It took a _lot_ of fandangling. There's quite a few configs as was mentioned, but I don't really mind that.

Although sometimes I find things aren't in logical places (Not in the config file I thought they'd be in, etc...)

I played with OpenBox for a bit and I found that I liked that just right.
It was a nice environment. Easy to configure, easy to maintain.
Just make sure you write your XML perfectly the first time.... I left out a bracket in my menu once and it was completely lost. Right clicking at that point resulted in... nothing.

Dig around BoxWhore.org and look at different desktops. Aside from customizability, see if one appears to be able to do what you want it do aesthetically.
- Kev

---

### Post by somuchfortheafter on 2005-08-10
i was in the spirit of change today so I changed out my media player from rythmbox to amarok and before that I saw this thread and decided to convert to openbox as I have used every other *box. I must say this fits me the best and it works very well with gnome.

---

### Post by Lowe on 2005-08-10
[QUOTE=Stormy Eyes]Dude, what's that display at the top of your screen that you're using to show what's currently playing? Is that torsmo, by any chance? If so, would you mind posting your .torsmorc?[/QUOTE]

Not torsmo, but the OSD for the quodlibet music player.

Quodlibet: [http://www.sacredchao.net/quodlibet](http://www.sacredchao.net/quodlibet)
[OSD](http://www.sacredchao.net/quodlibet/file/trunk/plugins/osd.py?rev=1544) 

Some quodlibet screenshots. [http://www.sacredchao.net/quodlibet/wiki/Screenshots](http://www.sacredchao.net/quodlibet/wiki/Screenshots)

It's great.  ;-)

---

### Post by az on 2005-08-10
I only would use fluxbox, but that is because if i wanted to use a *box, it is because I would not want to configure anything.  I would just want it to run fast.

Less is more.  It just runs.

---

