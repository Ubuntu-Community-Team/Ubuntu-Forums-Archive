---
title: "Font Suggestions?"
date: 2009-05-10
forum: The Cafe
---

### Post by sports fan Matt on 2009-05-10
Im having a terrible time sticking to a font..Any suggestions?

It seems like there isnt one thats crisp and just so clear on the eyes..even for one's eyes that arent the strongest like mine

---

### Post by monsterstack on 2009-05-10
I'm quite fonf of *Minya Nouvelle*. It's a serif font that isn't too huffy and is easy on the eyes. I can't stand sans serif fonts.

---

### Post by chucky chuckaluck on 2009-05-10
urw gothic l is pretty clean, though kind of thin. dejavu sans bold is what i'm using now. it pretty much says "hi. look at me."

---

### Post by Sealbhach on 2009-05-10
HandelGotDLig for me.

[IMG]http://www.fontica.com/utile/create_preview.php?id=2234&nume=[/IMG]

.

---

### Post by raymondh on 2009-05-10
> **sox fan Matt said:**
> Im having a terrible time sticking to a font..Any suggestions?

It seems like there isnt one thats crisp and just so clear on the eyes..even for one's eyes that arent the strongest like mine

Matt, these are for mac fonts ....

[http://forums.msiwind.net/viewtopic.php?f=39&t=6545](http://forums.msiwind.net/viewtopic.php?f=39&t=6545)

---

### Post by sports fan Matt on 2009-05-10
Ray, wow..what a difference..what exactly did that do?

---

### Post by raymondh on 2009-05-10
> **sox fan Matt said:**
> Ray, wow..what a difference..what exactly did that do?

If you ask me, I think it's in the smoothing of the subpixels and the no-hinting. That and I have always liked the "roundness" of lucida's

My prescriptions are getting close to 5 and 6 so every little thing helps :)

---

### Post by bashveank on 2009-05-10
Helvetica Narrow Bold

---

### Post by Pasdar on 2009-05-11
The Lucidia fonts (Mac) are by far the best fonts.

---

### Post by itreius on 2009-05-11
Absolutely loving Calibri (and Consolas as fixed-width). :P

---

### Post by glotz on 2009-05-11
You sure you got the **font rendering** set up properly?

```
gconf-editor /desktop/gnome/font_rendering
```

---

### Post by etnlIcarus on 2009-05-11
Mac fonts really are all a person needs.

---

### Post by Saint Angeles on 2009-05-11
whenever i put "hinting" at "none" instead of "slight" it looks all pizelated and crappy.

+1 for "HandelGotD"

also, i like "World of Water" available in one of the many font collection packages in the repos.

---

### Post by sports fan Matt on 2009-05-11
Glotz, im not sure..what should they be set at?

---

### Post by sports fan Matt on 2009-05-11
Here is a screenshot of my desktop..Am i just not thinking right when I feel the fonts are a tad messed up, even after applying the tweak by raymond?

---

### Post by RPG Master on 2009-05-11
I really like the Liberation fonts. They are what I am using curently. Check 'em out :)

---

### Post by Incense on 2009-05-11
> **pasdar said:**
> the lucidia fonts (mac) are by far the best fonts.

+1.

---

### Post by forrestcupp on 2009-05-11
I just pulled my Segoe UI fonts from my Vista install.  I've never found a font in Linux that compares.

---

### Post by raymondh on 2009-05-11
Hi Matt,

Here's my desktop for/as a font comparison.  Note this is on the MSIWind 10-inch screen

---

### Post by leus on 2009-05-11
> **raymondhenson said:**
> Matt, these are for mac fonts ....

[http://forums.msiwind.net/viewtopic.php?f=39&t=6545](http://forums.msiwind.net/viewtopic.php?f=39&t=6545)

Great!! and for the firefox?? what settings for the same theme for mac?

---

### Post by Sealbhach on 2009-05-11
> **sox fan Matt said:**
> Here is a screenshot of my desktop..Am i just not thinking right when I feel the fonts are a tad messed up, even after applying the tweak by raymond?

I think the hinting is supposed to be slight. My dpi is 101, I don't know if that's right or not. Your fonts look the same as mine after applying the Mac settings.

.

---

### Post by dragos240 on 2009-05-11
[Visitor.]("http://www.dafont.com/visitor.font")

---

### Post by etnlIcarus on 2009-05-11
> **sox fan Matt said:**
> Here is a screenshot of my desktop..Am i just not thinking right when I feel the fonts are a tad messed up, even after applying the tweak by raymond?

If you're referring to the massive fonts:

[img]http://img354.imageshack.us/img354/941/screenshotv.png[/img]

Otherwise, they look fine. You might just be suffering from *MS Sans Serif withdrawal*. It happens to the best of us.

---

### Post by ShodanjoDM on 2009-05-11
[Droid Sans]("http://www.stefanoforenza.com/get-androids-fonts-on-ubuntu-how-to/")

---

### Post by glotz on 2009-05-11
> **sox fan Matt said:**
> Glotz, im not sure..what should they be set at?
Try selecting those items and it will show you a quick help. Theoretically it depends on what kind of a display you have but in practice it's really a personal preference.

---

### Post by sports fan Matt on 2009-05-11
Raymond, what are your font settings if I may ask?

---

### Post by ice60 on 2009-05-12
i'm using a very old version of gnome so maybe things have changed, but i put this, named as **.fonts.conf**, in my home directory -
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```
you need to logout and back in, or restart the desktop to see the effects.

i also did this to get my fonts looking better -
[http://forums.opensuse.org/archives/sf-archives/archives-tips-tricks-tweaks/341943-how-make-fonts-look-good.html](http://forums.opensuse.org/archives/sf-archives/archives-tips-tricks-tweaks/341943-how-make-fonts-look-good.html)

i changed the dpi in xorg.conf and in gconf-editor to 96dpi. i think screenshots of fonts don't always show up the way they look.

---

### Post by raymondh on 2009-05-12
> **sox fan Matt said:**
> Raymond, what are your font settings if I may ask?

This are my settings on a 15-inch screen

For the MSI 10-inch, font size is 9

The 24-inch monitor (desktop), I use a font size of 11

Hope this helps.

---

### Post by LowSky on 2009-05-12
Comic Sans is the best font ever! :-({|=


Flame Suit on...lol
\\:D/

---

### Post by RPG Master on 2009-05-12
I am disappointed that no one else has mentioned Liberation Sans :|

---

### Post by raymondh on 2009-05-12
> **leus said:**
> Great!! and for the firefox?? what settings for the same theme for mac?

Hello leus

I use lucida grande as well .... size 14

I'll check my mac and see what safari has (when I get home) and post back if you wish.

---

### Post by Firestem4 on 2009-05-12
Ive been using DejaVu Sans ever since I upgraded to 9.04 (kubuntu), and I am loving it. The font is very smooth and comfortable to look at.

---

