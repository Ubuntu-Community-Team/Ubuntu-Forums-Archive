---
title: "Restart options has been removed from indicator-session"
date: 2013-03-11
forum: Ubuntu Development Version
---

### Post by serdotlinecho on 2013-03-11
But then...

[IMG]http://i.imgur.com/rCoXBC6l.png[/IMG]


And where's the word pc or computer after "...log out from your"?

---

### Post by VinDSL on 2013-03-11
That's the new "Rolling Restart" concept.  They're still discussing it.   :D

I'm jealous!

Hasn't reached my desktop yet...


[[IMG]http://vindsl.com/images/vindsl-desktop-11-mar-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-11-mar-2013-1.png")

---

### Post by kansasnoob on 2013-03-11
[http://www.webupd8.org/2013/03/unity-to-get-new-shutdown-dialogs.html?m=1](http://www.webupd8.org/2013/03/unity-to-get-new-shutdown-dialogs.html?m=1)

---

### Post by philinux on 2013-03-11
> **VinDSL said:**
> That's the new "Rolling Restart" concept.  They're still discussing it.   :D

I'm jealous!

Hasn't reached my desktop yet...



Terminal > setsid unity

If you are up to date you will then have it. :P

---

### Post by grahammechanical on 2013-03-11
What fun! A lock that looks like a handbag. I can imagine the complaints that there isn't a cancel option. Reset + confirm = 2 clicks. Shutdown + confirm = 2 clicks. Shutdown + Reset = 2 clicks. Shutdown + Shutdown = 2 clicks. We get a smaller menu without extra effort needed and we avoid a child's finger or an adult's big fat finger from hitting the wrong menu options. Think touch screen. Think convergence. I just have to laugh at it all.

---

### Post by serdotlinecho on 2013-03-11
> I can imagine the complaints that there isn't a cancel option.

There is X button at the top left corner in case you didn't notice it ;)

---

### Post by VinDSL on 2013-03-11
> **philinux said:**
> Terminal > setsid unity

If you are up to date you will then have it. :P
Okay!  There it is.

It was hiding the whole time...


[[IMG]http://vindsl.com/images/vindsl-desktop-11-mar-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-11-mar-2013-2.png")


**EDIT**

BTW, the button of the left is "Shutdown".

I've tried both buttons (shutdown & restart) and they both work fine.  ;)

---

### Post by VinDSL on 2013-03-11
> **grahammechanical said:**
> What fun! A lock that looks like a handbag.[...]
Looks like a satchel (bag), to me, but...

Why split hairs?!?!?  :D

---

### Post by serdotlinecho on 2013-03-12
> **VinDSL said:**
> Looks like a satchel (bag), to me, but...

Why split hairs?!?!?  :D

Hmm, maybe keybindings like pressing the Esc key to close the shell dialogs, doesn't work atm?

---

### Post by mcellius on 2013-03-12
> What fun! A lock that looks like a handbag.

It's not a purse!  It's European!

---

### Post by mc4man on 2013-03-12
They offer a 4 pack on occasion

---

### Post by VinDSL on 2013-03-12
> **mc4man said:**
> They offer a 4 pack on occasion
LoL!  :D

How did you summon those?

---

### Post by grahammechanical on 2013-03-12
> **serdotlinecho said:**
> There is X button at the top left corner in case you didn't notice it ;)

I also noticed that clicking the desktop causes the dialog to disappear.

---

### Post by mc4man on 2013-03-12
> **VinDSL said:**
> LoL!  :D

How did you summon those?
No way that's really advisable or presently useful.

Somewhat came from yet again getting tired of having the suspend option that I occasionally hit & which on this laptop currently does not work in that I can't come out of, need to do a forced restart. 

So forgetting how I got rid of in the near distant past & with present env of options aren't an option took a look at how 'restart' was just removed in latest indicator-session. (turns out quite easy to remove the suspend option.

For heck of it wanted to see what would happen if I used the previous indicator-session with the new unity deal - that is the result.
Not useful because it's then a 3 click (don't care about that) & somewhat redundant routine, ex.  > click on shutdown  > click on the confirm > 4 option then pops up.

If it was me I'd only have 1 option in indicator for this & pop up the 4 option window directly, may see if I can hack that in.

---

### Post by midfingr on 2013-03-12
@ mc4man
LOL ... 4  Pack :D

Here's a bunch of gibberish you can paste into a terminal or make a script for it...


```
dbus-send --session --dest=org.gnome.SessionManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/SessionManager org.gnome.SessionManager.Shutdown
```

---

### Post by ventrical on 2013-03-12
The new shutdown dialog box (which I cannot sceenshot) is great eyecandy but it is tranparent and very difficult to see. I am assuming it is running off from Unity.

---

### Post by mc4man on 2013-03-12
> **midfingr said:**
> 
Here's a bunch of gibberish you can paste into a terminal or make a script for it...
cool - is there a dbus for logout?

While totally improper used the command to set shutdown to go directly to the 4 pack, Very small vid attached

---

### Post by serdotlinecho on 2013-03-12
We already talking and discussing about [this]("http://ubuntuforums.org/showthread.php?t=2124500") and some screenshots too ;)

---

### Post by cariboo on 2013-03-12
Merged two similar threads.

---

### Post by serdotlinecho on 2013-03-12
The shell dialogs doesn't look good on my netbook, on top of active window.

[[IMG]http://i.imgur.com/zk47Buxl.png[/IMG]]("http://imgur.com/zk47Bux")


> **grahammechanical said:**
> I also noticed that clicking the desktop causes the dialog to disappear.

Also need keyboard keybindings like Esc key to close the shell dialogs. Right now, only Alt+F4 is working.

EDIT: Esc key working now :D

---

### Post by mc4man on 2013-03-13
> **serdotlinecho said:**
> The shell dialogs doesn't look good on my netbook, on top of active window.


It would seem they've got this window set to use the same as Dash so it's colored & also affected by the opacity setting in compiz > Background color

Here i prefer #000000 with opacity so the popup looks fine (a custom color setting is not applied in "Background color" until some opacity is set

---

### Post by stinkeye on 2013-03-13
Don't see why they have to hide the actual names
of the function until I hover over it.
Takes a while for my old brain to join the dots.
Would be worse on a touch screen.

---

### Post by shantiq on 2013-03-14
--dupe---

---

### Post by shantiq on 2013-03-14
may i just say that installing qshutdown and placing it somewhere handy [topbar or docking]  gives you [for the time being] all the termination choices you might wish for and looks nice doing it[]


see


[ATTACH=CONFIG]240155[/ATTACH]

---

### Post by serdotlinecho on 2013-03-14
The user session shell dialog and alt+tab apps switcher should look like unity dash and hud(color and transparency) when open on top of active window. The look and the color not consistent, IMHO. :)

[[IMG]http://i.imgur.com/3cP0SLis.png[/IMG]]("http://imgur.com/3cP0SLi")   [[IMG]http://i.imgur.com/emoXR2ns.png[/IMG]   ]("http://imgur.com/emoXR2n")[[IMG]http://i.imgur.com/dPaV1AXs.png[/IMG]]("http://imgur.com/dPaV1AX")   [[IMG]http://i.imgur.com/tdhSGsGs.png[/IMG]]("http://imgur.com/tdhSGsG")

---

