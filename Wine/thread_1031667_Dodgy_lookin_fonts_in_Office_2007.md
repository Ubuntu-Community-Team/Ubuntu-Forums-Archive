---
title: "Dodgy lookin fonts in Office 2007"
date: 2009-01-05
forum: Wine
---

### Post by connel on 2009-01-05
hi i am using Ubuntu 8.04 and wine version 1.1.12.
I succesfully installed M$ Office 2007 (i need it for college im afraid :()
However i have notcied that all the fonts are weird they look kinda pixelated. I have copied my fonts folder from my Windows Vista partition c:/windows/Fonts into my wine c driver and still no luck :( i can use microsoft fonts like Calibri in Office 2007 they just dont look good. I can also use these fonts in open office no problem so im gessing they are installed. any help would be greatly appreciated as atm this is the only thing stopping me from deleting my windows partition :D lol

---

### Post by connel on 2009-01-05
oooh shhhhhugar i just realised that when i zoom in at 140% they look a lot better is there a reason for this as they look rather poor at 100%? thanks again

---

### Post by Daminvar on 2009-01-05
Hmm.  I'm having the same problem; it's good to know that I'm not the only one.  Fonts like Calibri and Cambria look terrible.  The ones that come with the system (default Ubuntu fonts) look okay, though.

---

### Post by Ng Oon-Ee on 2009-01-06
Has to do with anti-aliasing, I believe. Try searching with that and see what that turns up.

---

### Post by connel on 2009-01-06
i have tried searching but i have found nothing that helps me, i found a page that says i could edit some text somewhere in a wine file to enable anti aliasing for fonts less than 16 and another that says you have to change the settings of your graphics card im really confused lol any help how i can turn on anti aliasing would be much appreciated :)

---

### Post by connel on 2009-01-08
bump

---

### Post by Jonathan Moerman on 2011-06-14
[FONT="Arial"]This is very easy to fix: 
1. install FontForge
2. navigate to the fonts directory.
3. open the font you want (Calibri) and _do NOT import the bitmaps  fonts_
4. file -> generate fonts : save as TrueType and with the option _"No Bitmap Fonts"_ (and I recommend to disable the validate before saving option)
5. rename and replace the font
6. repeat this with the Italic and bold variants[/FONT]

I hope this helps!!

---

