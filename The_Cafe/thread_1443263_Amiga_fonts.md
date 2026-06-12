---
title: "Amiga fonts"
date: 2010-03-30
forum: The Cafe
---

### Post by yester64 on 2010-03-30
Hi,
does someone know how to get amiga fonts working in ubuntu? to copy them into the folder did not work. these are bdf files and from what i googled should work as far as bdf goes.

---

### Post by Chronon on 2010-03-31
In what way do they not work?  Do you get an error of some sort?

(It seems like this should be in a support forum instead of the Cafe.)

---

### Post by Daisuke_Aramaki on 2010-03-31
> **yester64 said:**
> Hi,
does someone know how to get amiga fonts working in ubuntu? to copy them into the folder did not work. these are bdf files and from what i googled should work as far as bdf goes.

May I know where you got them? freakyfonts? I have been looking for a couple of fixed width amiga fonts for quite sometime now. If your source was not freakyfonts, can you provide me a link for download please?

Once you moved the font to the folder, update the font directory listing by issuing the command mkfontdir, then the usual fc-cache -f -v command. Then load the font in X using xset.  If that doesn't work, try converting the bdf to pcf (Loads faster, and takes up less space, architecture dependent though).  You could use bdftopcf utility for that. You could then move the pcf fonts to the appropriate place and use xset to let X load them.

---

### Post by yester64 on 2010-03-31
> **Chronon said:**
> In what way do they not work?  Do you get an error of some sort?

(It seems like this should be in a support forum instead of the Cafe.)

I realize that it is actually the wrong forum. aehem..
But if i rescan the fonts, there are in the list but no font is added. :(

---

### Post by yester64 on 2010-03-31
> **Daisuke_Aramaki said:**
> May I know where you got them? freakyfonts? I have been looking for a couple of fixed width amiga fonts for quite sometime now. If your source was not freakyfonts, can you provide me a link for download please?

Once you moved the font to the folder, update the font directory listing by issuing the command mkfontdir, then the usual fc-cache -f -v command. Then load the font in X using xset.  If that doesn't work, try converting the bdf to pcf (Loads faster, and takes up less space, architecture dependent though).  You could use bdftopcf utility for that. You could then move the pcf fonts to the appropriate place and use xset to let X load them.

I got them from here
[http://umlautllama.com/projects/font/](http://umlautllama.com/projects/font/)

And it did not work:( I will try to use the util for that. Maybe that makes a difference. btw. i understand that these were bitmap fonts. Does it matter where you place them?

---

### Post by Daisuke_Aramaki on 2010-03-31
> **yester64 said:**
> I got them from here
[http://umlautllama.com/projects/font/](http://umlautllama.com/projects/font/)

And it did not work:( I will try to use the util for that. Maybe that makes a difference. btw. i understand that these were bitmap fonts. Does it matter where you place them?


Oh it's from Scott's site. I have the fonts man, and my xfontsel sure sees them. IIRC place them anywhere you want and use xset command to load them. I believe this should be explained in the Readme from the downloaded font folder as well.

---

### Post by yester64 on 2010-03-31
> **Daisuke_Aramaki said:**
> Oh it's from Scott's site. I have the fonts man, and my xfontsel sure sees them. IIRC place them anywhere you want and use xset command to load them. I believe this should be explained in the Readme from the downloaded font folder as well.

Yes, you are right. Xfontsel see's them. I assume i can not load them into the appearance program to use them on the desktop. Because thats what i was trying to do.

---

