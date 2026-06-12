---
title: "Aggravating Scrollbar Behavior"
date: 2015-08-29
forum: Ubuntu Development Version
---

### Post by sgage on 2015-08-29
Hello All,

I have been using Ubuntu Gnome for some time now, and I really like the way Gnome Shell has developed. But there is one issue that has been bugging me for a while (not sure when it started). It involves the behavior of the scroll bar.

In every other environment I have ever used, when you click in the scroll bar below or above the 'thumb', the disply scrolls down or up one screenful. Indeed, that's what happens if you're using a 'native' Gnome app, such as gedit or nautilus. However, in Firefox and LibreOffice, two of the apps I spend the majority of my time in, it doesn't work that way.

If you click in the scroll bar below the thumb, the display scrolls to the position in the document/webpage corresponding to how far down below (or above) the thumb you've clicked. So if you want to scroll one screenful with the mouse, you basically have to drag the thumb (which is especially awkward in a large document/webpage, where a tiny drag results in major scrollage). Or use the mouse wheel to scroll.

It is aggravating to click on the scrollbar and have the display go rocketing off to points unknown. Is there any way to fix this? If anyone has any suggestions, I'd be most appreciative!

[edit: Should I perhaps post this in General Help?]

---

### Post by ventrical on 2015-08-29
Yes.. I see that too. I wonder if it can be adjusted using gnome-tweak tool.

nope! It looks like it is a fixed feature. On the other distros there is that small radio button  at the bottom and top of the scroll dialog slider that will 'slow scroll' when you click on it. gnome-desktop does not have that feature. Why?  No idea.  But good point you have brought up. Smooth scroll works so well I do not even think about it :)

Regards..

---

### Post by sgage on 2015-08-29
I'm glad you see what I mean. It's not a show-stopper or anything, especially if I remember that's how it works. It's when I forget, and it goes zinging off to wherever, and then I have to find my place in the document. There must be a tweak somewhere, though I've gone through things with dconf-editor with a fine-toothed comb. Maybe someone knows the secret...

---

### Post by ventrical on 2015-08-29
It does the same thing in unity (as you described it with gnome-desktop) but with the exception that unity has those radio buttons on the scroll bar dialog area hence the slow-smooth scroll. I looked for a gizzmo  but could find none.

Regards..

---

### Post by mc4man on 2015-08-29
It appears related to the theme used. So if gnome-shell > ambiance,  clicking anywhere in scroll bar goes 1 screen up or down.
With adwaita theme it goes relative to clicked spot in scrollbar.
(- at least in Firefox

---

### Post by ventrical on 2015-08-30
> **mc4man said:**
> It appears related to the theme used. So if gnome-shell > ambiance,  clicking anywhere in scroll bar goes 1 screen up or down.
With adwaita theme it goes relative to clicked spot in scrollbar.
(- at least in Firefox

I am using that theme (default) and it is still jumpy - but then it is jumpy on all distros. Difference is that other distros have slider button  on top and bottom of vertical scroll bar. Curious as to why gnome  (running firefox) does not have this button.

---

### Post by sgage on 2015-08-30
Well spotted! Ubuntu Gnome comes with a theme called 'Numix', and the effect is the same as with Ambance. Works for LibreOffice as well. It must be possible to tweak the Adwaita theme... I'm not very experienced with themes in Gnome, but if I have time later I'll poke around...

---

### Post by sgage on 2015-08-30
> **ventrical said:**
> I am using that theme (default) and it is still jumpy - but then it is jumpy on all distros. Difference is that other distros have slider button  on top and bottom of vertical scroll bar. Curious as to why gnome  (running firefox) does not have this button.

Same thing with LibreOffice...

---

### Post by mc4man on 2015-08-30
It's been a while but last I checked adwaita was a 'compiled' scheme so any adjustments would have to be done in source (gnome-shell source iirc which can be a stretch at times

---

### Post by sgage on 2015-08-30
> **mc4man said:**
> It's been a while but last I checked adwaita was a 'compiled' scheme so any adjustments would have to be done in source (gnome-shell source iirc which can be a stretch at times

Yes, I was poking around in /usr/share/themes, and it looks like the Adwaita folder just has a couple of placeholders. Maybe someone will make an Adwaita II with 'correct' scrollbar behavior. Maybe it's just time for me to learn about gtk-3 themes. :KS

---

### Post by sammiev on 2015-08-30
> **sgage said:**
> Hello All,

I have been using Ubuntu Gnome for some time now, and I really like the way Gnome Shell has developed. But there is one issue that has been bugging me for a while (not sure when it started). It involves the behavior of the scroll bar.

In every other environment I have ever used, when you click in the scroll bar below or above the 'thumb', the disply scrolls down or up one screenful. Indeed, that's what happens if you're using a 'native' Gnome app, such as gedit or nautilus. However, in Firefox and LibreOffice, two of the apps I spend the majority of my time in, it doesn't work that way.

If you click in the scroll bar below the thumb, the display scrolls to the position in the document/webpage corresponding to how far down below (or above) the thumb you've clicked. So if you want to scroll one screenful with the mouse, you basically have to drag the thumb (which is especially awkward in a large document/webpage, where a tiny drag results in major scrollage). Or use the mouse wheel to scroll.

It is aggravating to click on the scrollbar and have the display go rocketing off to points unknown. Is there any way to fix this? If anyone has any suggestions, I'd be most appreciative!

[edit: Should I perhaps post this in General Help?]

I really like the way I can go from top to bottom in 1/2 second or any where I want on the page.

It's been like that on the last version or two.

---

### Post by sgage on 2015-08-30
> **sammiev said:**
> I really like the way I can go from top to bottom in 1/2 second or any where I want on the page.

It's been like that on the last version or two.

If you know what percentage of the document the place you want to go to is at, and you can eyeball that, OK. I really don't like it. Plus, it works that way on FF and LibreOffice, but not on the 'native' Gnome apps. I find myself cursing at it all the time. But whatever works for you.

---

### Post by mc4man on 2015-08-30
Having a predefined action that can reveal all of a window in an orderly fashion is certainly useful, if purposely removed seems rather wasteful with all of the other & likely more popular  page scrolling methods.
(my most used here are a free-wheeling mouse scroll wheel & the arrow keys

---

### Post by sgage on 2015-08-31
> **mc4man said:**
> Having a predefined action that can reveal all of a window in an orderly fashion is certainly useful, if purposely removed seems rather wasteful with all of the other & likely more popular  page scrolling methods.
(my most used here are a free-wheeling mouse scroll wheel & the arrow keys

Except no other platform does it that way. I like the 'Fitt's Law' aspect of just being able to click anywhere on the bar and get the next page. Sure, there are keys, but there are times when I don't want to drop the mouse to hit a key. The scroll wheel is less precise.

Even in Gnome/Adwaita, it works differently in different apps, which is just wrong, IMO.

---

