---
title: "A conky request"
date: 2010-01-05
forum: The Cafe
---

### Post by PuddingKnife on 2010-01-05
Total Conky newb here ..

I was wondering if someone would be willing to help me configure my Conky to look like this version of Rainmeter (minus the dock part of course):

[ATTACH]142585[/ATTACH]

I will be eternally grateful to anyone that helps me achieve this level of desktop awesomeness.

---

### Post by Dark Aspect on 2010-01-05
> **PuddingKnife said:**
> Total Conky newb here ..

I was wondering if someone would be willing to help me configure my Conky to look like this version of Rainmeter (minus the dock part of course):

[ATTACH]142585[/ATTACH]

I will be eternally grateful to anyone that helps me achieve this level of desktop awesomeness.

Conky is not hard to learn your self, for a list of commands use:

```
man conky
```

There is also a beginners guide that not too hard to follow [here]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628").

---

### Post by Bruce M. on 2010-01-05
> **PuddingKnife said:**
> Total Conky newb here ..

I was wondering if someone would be willing to help me configure my Conky to look like this version of Rainmeter (minus the dock part of course):

[ATTACH]142585[/ATTACH]

I will be eternally grateful to anyone that helps me achieve this level of desktop awesomeness.

Sure, I'll help, Dark Aspect already pointed you to my little HowTo and that's a decent start.  Keep in mind you will want two conkys when you read that post.  One for the top_left or tl and one for the top_right or tr.

If you put some effort into starting as per the HowTo, I'll be here, along with others I'm sure, to give you a helping hand.  It is however difficult for someone to do what your want not knowing your equipment and screen size.  Also people don't generally write conkys for other people, but will help those struggling to get one going.  :)

Give it a try, we'll be here.
Bruce

---

### Post by PuddingKnife on 2010-01-05
Many thanks.

Im reading and reading. I didnt even know you could have 2 conkys.. but thats definitely going to help me in getting a HUD style conky going soon.

My res is 1280x800 btw

---

### Post by Bruce M. on 2010-01-05
> **PuddingKnife said:**
> Many thanks.

Im reading and reading. I didnt even know you could have 2 conkys.. but thats definitely going to help me in getting a HUD style conky going soon.

My res is 1280x800 btw

JAJAJAJAJAJAJAJAJAJA ... that's ... HAHAHAHAHAHAHAHA in Spanish.

*Didn't know you could have two conkys* - oh that soooooo good!

I have 8 and I'm working on 2 more.  :)

Please **do not take that the wrong way**, it's 35.6°C here and my brain is cooking slowly!  However that are saying we are about to get the mother of all storm soon.  :)

I remember [my first conky question]("http://ubuntuforums.org/showthread.php?t=281865&page=116"): "Is the bottom part of the attached image (I found it here) "cronky" as well?"  - Nope, that's some sort of desklet.  I didn't even know the name: **cronky** indeed. :popcorn:

And my first conky said I was "C-64" because I "borrowed" his code. :lolflag:  Nostalgia is so nice.  :)

Did you install "conky" yet?

Have a GREAT day.
Bruce

---

### Post by PuddingKnife on 2010-01-05
Yes, and this is what Ive achieved so far:

[ATTACH]142603[/ATTACH]


Someone else's code of course. But at least its up and running  :)

---

### Post by koleoptero on 2010-01-05
> **PuddingKnife said:**
> Yes, and this is what Ive achieved so far:

[ATTACH]142603[/ATTACH]


Someone else's code of course. But at least its up and running  :)

Add before the TEXT the line: own_window_type override

---

### Post by PuddingKnife on 2010-01-05
Whats that do?

---

### Post by koleoptero on 2010-01-05
> **PuddingKnife said:**
> Whats that do?

Make it blend with the desktop better (no shadow, no offset in the background, test it and see).

---

### Post by Bruce M. on 2010-01-05
> **PuddingKnife said:**
> Yes, and this is what Ive achieved so far:

[ATTACH]142603[/ATTACH]


Someone else's code of course. But at least its up and running  :)

That how over 90% of the people start with a conky.  They borrow one and "customize" it.

Two links for you:
[The stuff that goes Above TEXT]("http://conky.sourceforge.net/config_settings.html")
[The stuff that goes Below TEXT]("http://conky.sourceforge.net/variables.html")

I word them that way because for a reason:

They BOTH have a Variables column, but the last one is "variables.html" with a tab lable of "Conky Objects".

The first one is "config_settings.html" with a tab label of "Lua API"

**Above TEXT** and **Below TEXT** is much easier to understand.  :)

> **koleoptero said:**
> Add before the TEXT the line: own_window_type override

Sage advice!

From Above TEXT:

> own_window_type
 	if own_window is yes, you may specify type normal, desktop, dock, panel or override (default: normal). Desktop windows are special windows that have no window decorations; are always visible on your desktop; do not appear in your pager or taskbar; and are sticky across all workspaces. Panel windows reserve space along a desktop edge, just like panels and taskbars, preventing maximized windows from overlapping them. The edge is chosen based on the alignment option. Override windows are not under the control of the window manager. Hints are ignored. This type of window can be useful for certain situations.

Night all.
Bruce

---

### Post by PuddingKnife on 2010-01-10
UPDATE:

Ok, I kind of gave up with Conky since Ive accomplished most of what I want w/ Screenlets. I feel that one has to be a programmer to understand how conky works and how to manipulate it. Since these are skills I do not have, Ive had to fall back on Screenlets.

This is what Ive got so far:
[ATTACH]143143[/ATTACH]

This bright white clock in the bottom right corner is all thats left of my original conky. I want to keep it but change the font (which I think I can handle on my own) and make it as transparent as the Screenlets.

Does anyone know how I can make the clock more transparent?

---

