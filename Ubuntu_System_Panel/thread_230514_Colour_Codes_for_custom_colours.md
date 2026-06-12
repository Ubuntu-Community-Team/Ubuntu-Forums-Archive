---
title: "Colour Codes for custom colours"
date: 2006-08-06
forum: Ubuntu System Panel
---

### Post by Oppi on 2006-08-06
[FONT="Tahoma"][SIZE="2"]Hi

Can somebody tell me where to get the colour-codes if I want to set custom colours in USP?

Is it a 6-digit code or do I have to type in just the colour I want? 

Because by default the colours in gconf/apps/usp are set like "999999" or "4d4d4d"

greets, Oppi[/SIZE][/FONT]

---

### Post by moma on 2006-08-06
I think that USP uses colors of the current theme.
System -> Preferences -> Theme.

Anyway,
the colors are written as hexadecimal values in $HOME/.gconf/apps/usp/%gconf.xml

Start GIMP and use its color selector to choose a color. It will show you the color number too as hex value.  Or install gcolor2 package.
$ gcolor2 

You can file a bug-report if USP does not obey custom colors.

BTW: How did s{he} changed the colors?
[http://ubuntuforums.org/showthread.php?t=230439&highlight=USP]("http://ubuntuforums.org/showthread.php?t=230439&highlight=USP")

---

### Post by Oppi on 2006-08-06
Thank you for your fast answer. I will try it when i am home again in front of my beloved ubuntu-system :p  

I have to play around some more hours with the gconf apps/usp definitions, especially with the colours. Let's see if it works

Greets, Oppi

---

### Post by chanders on 2006-08-06
> **Oppi said:**
> Thank you for your fast answer. I will try it when i am home again in front of my beloved ubuntu-system :p  

I have to play around some more hours with the gconf apps/usp definitions, especially with the colours. Let's see if it works

Greets, Oppi

Colors are set using this system

Red, Green, Blue
#RRGGBB

Where RR stands for red, GG for green and BB for blue and values of each letter can be from 0 to F with #000000 being black and #FFFFFF being white.

eg.
#3FC12A is valid but #G52AC2 is not because of the 'G'

---

### Post by Uncle Spellbinder on 2006-08-06
[**Color Codes**]("http://www.webmonkey.com/webmonkey/reference/color_codes/")

---

### Post by chanders on 2006-08-06
Thanks! I will put the link in the HowTo..

---

### Post by Uncle Spellbinder on 2006-08-06
> **chanders said:**
> Thanks! I will put the link in the HowTo..

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/wink.gif[/IMG]

---

### Post by Oppi on 2006-08-06
Thanks ! Great help :p

---

