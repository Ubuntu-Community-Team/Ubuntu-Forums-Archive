---
title: "making a color transparent"
date: 2009-07-12
forum: Ubuntu Studio
---

### Post by johnh10000 on 2009-07-12
Hi gang,  I'm looking for a graphics editor to make the bjgnd color transparent.  this is for webdesign.  Any ideas as to what to use ?

If the gimp has this capibility, err where is it?

Or a nice simple webdesign graph ed.

Any suggestions welcome

---

### Post by lykeion on 2009-07-12
If I understand your question correct, you want to make a transparent background for an image.

As far as I know all image editors are capable of this. In GIMP you could proceed like this...
* Open the image and select the area that you would like to keep, or if it's easier to select the background (perhaps with Magic Wand Tool or Select by Color Tool), select background and then invert the selection. 
* Cut it out (ctrl + x) and paste into into a new layer (ctrl + v). 
* Delete the old background layer. 
* Save the image as png or gif.

Hope that this helps

---

### Post by johnh10000 on 2009-07-12
> **lykeion said:**
> If I understand your question correct, you want to make a transparent background for an image.

As far as I know all image editors are capable of this. In GIMP you could proceed like this...
* Open the image and select the area that you would like to keep, or if it's easier to select the background (perhaps with Magic Wand Tool or Select by Color Tool), select background and then invert the selection. 
* Cut it out (ctrl + x) and paste into into a new layer (ctrl + v). 
* Delete the old background layer. 
* Save the image as png or gif.

Hope that this helps

I tried to cheat, and used psp on a windoz box on the network.  And it's still not right :(

Is there just a see through colour?

Take a look, ebassy.isa-geek.org

---

### Post by Stochastic on 2009-07-12
The feature in GIMP you're trying to use is under the Colours menu, in the bottom portion, called Colour to Alpha...  (Alpha is the transparency colour).  This will open a dialogue for you to pick which colour, how precise it should be, etc..

---

