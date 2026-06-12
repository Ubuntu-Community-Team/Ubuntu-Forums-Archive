---
title: "Parabolic Predictive mouse movement for Ubuntu..."
date: 2008-10-07
forum: The Cafe
---

### Post by Mazza558 on 2008-10-07
(I fully expect very few replies as the thread title will scare people off, but here goes...)

I thought of a concept which predicts mouse movement for the desktop. I thought of this when I realised how small a space people have to click in to achieve something. Here's a few situations where you might get this happening:

- clicking the "close tab" button in firefox 
- clicking on panel applets
- clicking any close buttons
- clicking links
- clicking to open a menu

There's loads of examples. Now, wouldn't it be more sensible for commonly used buttons to enlarge slightly as you approach them with your mouse? Such program could learn which areas of the screen you click on most, enlarging the interface slightly as you move the mouse towards them. The back button, for example, would grow quite large before you reached it. This could also happen for web links. But rather than enlarging the text, make a small glow appear around it - if anyone clicks within the area of the glow, the link is clicked, meaning people don't have to just click on text any more. If you think about it, most of the time using the mouse is actually spent trying to get the cursor into exactly the right position - simply moving the mouse across the screen is very, very easy.

I believe that these ideas would improve productivity so much more than moving buttons around and slightly tweaking interfaces. Compiz plugin perhaps?

---

### Post by schauerlich on 2008-10-07
What happens in you click on the back button so many times that its glow gets too big to hit the buttons around it?

---

### Post by Mazza558 on 2008-10-07
> **EDavidBurg said:**
> What happens in you click on the back button so many times that its glow gets too big to hit the buttons around it?

There'd be a limit to how big it could get - buttons around it would move out of the way slightly in a parabolic effect anyway.

---

### Post by sicofante on 2008-10-07
Your idea sounds bright to me. Maybe you should propose to the Gnome devs? I promise I'll support you.

---

### Post by schauerlich on 2008-10-07
> **Mazza558 said:**
> There'd be a limit to how big it could get - buttons around it would move out of the way slightly in a parabolic effect anyway.

So basically make all of the icons bounce around like the Apple Dock's magnify effect, sizing based on number of clicks?

---

### Post by Mazza558 on 2008-10-07
> **EDavidBurg said:**
> So basically make all of the icons bounce around like the Apple Dock's magnify effect, sizing based on number of clicks?

erm... not quite like that. I actually think parabolic's the wrong word. The button grows as you move your mouse towards it but the other buttons stay the same size and move away slightly.

> **sicofante said:**
> Your idea sounds bright to me. Maybe you should propose to the Gnome devs? I promise I'll support you.

Compiz development is a lot faster and it would probably require a code rewrite for gnome as opposed to a visual plugin for compiz.

---

### Post by schauerlich on 2008-10-07
> **Mazza558 said:**
> erm... not quite like that. I actually think parabolic's the wrong word. The button grows as you move your mouse towards it but the other buttons stay the same size and move away slightly.

Yeah, that's what I meant.

---

### Post by aaaantoine on 2008-10-07
> **Mazza558 said:**
> erm... not quite like that. I actually think parabolic's the wrong word. The button grows as you move your mouse towards it but the other buttons stay the same size and move away slightly.

Compiz development is a lot faster and it would probably require a code rewrite for gnome as opposed to a visual plugin for compiz.

This wouldn't be just visible.  You want the expanded area to also be clickable, correct?  That could require a tweak to X.org, I think.

It would probably be better to submit this to the Gnome project.

---

### Post by Mazza558 on 2008-10-07
A very quick mockup (apologies for paint), but this would be the parabolic idea.

[IMG]http://dl.getdropbox.com/u/29948/parabolic1.JPG[/IMG]

---

### Post by Mazza558 on 2008-10-07
And another mockup which would probably work better...

[IMG]http://dl.getdropbox.com/u/29948/parabolic2.JPG[/IMG]

---

### Post by snova on 2008-10-07
Sounds like a WM thing to me, in which case you'd propose this to the developers of Metacity (isn't that the one Gnome uses?) and Kwin (don't leave us out!).

It's a neat idea. I suggest changing the color of the button when the mouse gets close enough where clicking would press it anyway, or by making it obvious that clicks are no longer going where you think they are in some other manner.

---

### Post by Mazza558 on 2008-10-07
...and a better mockup, showing what it would probably look like (obviously with no mouse trails)

[IMG]http://dl.getdropbox.com/u/29948/mockup2.jpg[/IMG]

---

### Post by mysticrider92 on 2008-10-07
Thats a pretty cool idea, but it would take some work. Compiz is a little unstable (for me atleast), and would probably end up hiding the other buttons or something. It sounds like a cool extra for usablity and fun. 

Not to get this off topic, but it would be kinda cool if the menus did something similar. Like you click on the "Applications" menu, and as you scrolled over each catagory, it would balloon up (like the Mac dock). Or is there already a program to do this?

---

### Post by Mazza558 on 2008-10-07
> **mysticrider92 said:**
> Thats a pretty cool idea, but it would take some work. Compiz is a little unstable (for me atleast), and would probably end up hiding the other buttons or something. 

I would be all for the idea, though. It sounds like a cool extra for usablity and fun. 

Not to get this off topic, but it would be kinda cool if the menus did something similar. Like you click on the "Applications" menu, and as you scrolled over each catagory, it would balloon up (like the Mac dock). Or is there already a program to do this?

This could be done with a combination of Xorg and Compiz - compiz to show the fancy effects, and a code to trick xorg into thinking the mouse is in a different position when you click.

---

### Post by Canis familiaris on 2008-10-07
Nice idea. But don't you think it would be bit heavy on the resources?

---

### Post by geoken on 2008-10-07
It's a good idea. We've done it before with Flash sites.

Basically, there was a listener for mouse movement. When a mouse move was initiated we captured and stored the position. The we used the previous position and current position to extrapolate trajectory. We would then take the trajectory, figure out which menu items it intersected, then either expand the hit area invisibly (although the expanded hit area was invisible, the mouse over feedback would occur if you were within the expanded hit area) or use an all out OS X style menu.

The technique is common in flash sites.
[http://theflashblog.com/?p=413]("http://theflashblog.com/?p=413")

---

### Post by Mazza558 on 2008-10-07
> **geoken said:**
> It's a good idea. We've done it before with Flash sites.

Basically, there was a listener for mouse movement. When a mouse move was initiated we captured and stored the position. The we used the previous position and current position to extrapolate trajectory. We would then take the trajectory, figure out which menu items it intersected, then either expand the hit area invisibly (although the expanded hit area was invisible, the mouse over feedback would occur if you were within the expanded hit area) or use an all out OS X style menu.

The technique is common in flash sites.
[http://theflashblog.com/?p=413]("http://theflashblog.com/?p=413")

I thought it might be in use somewhere. Why it's never spread to everyday usage is beyond me.

> **Anurag_panda said:**
> Nice idea. But don't you think it would be bit heavy on the resources?

No more than any other compiz plugin or low-level program.

---

