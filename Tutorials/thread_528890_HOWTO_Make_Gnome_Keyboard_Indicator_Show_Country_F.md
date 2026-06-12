---
title: "HOWTO Make Gnome Keyboard Indicator Show Country Flags"
date: 2007-08-18
forum: Tutorials
---

### Post by Ingla on 2007-08-18
This was written with Ubuntu Feisty (Gnome) in mind (See the NOTE in #6 below for a comment on Edgy).

I found out about this (mostly) on a Russian language Ubuntu site at:
[http://www.nabble.com/%D0%A4%D0%BB%D0%B0%D0%B6%D0%BA%D0%B8-%D1%81%D1%82%D1%80%D0%B0%D0%BD-%D0%B2-%D0%BF%D0%B5%D1%80%D0%B5%D0%BA%D0%BB%D1%8E%D1%87%D0%B0%D1%82%D0%B5%D0%BB%D0%B5-%D1%80%D0%B0%D1%81%D0%BA%D0%BB%D0%B0%D0%B4%D0%BE%D0%BA-GNOME.-t3639724.html](http://www.nabble.com/%D0%A4%D0%BB%D0%B0%D0%B6%D0%BA%D0%B8-%D1%81%D1%82%D1%80%D0%B0%D0%BD-%D0%B2-%D0%BF%D0%B5%D1%80%D0%B5%D0%BA%D0%BB%D1%8E%D1%87%D0%B0%D1%82%D0%B5%D0%BB%D0%B5-%D1%80%D0%B0%D1%81%D0%BA%D0%BB%D0%B0%D0%B4%D0%BE%D0%BA-GNOME.-t3639724.html).

1**. If you haven't got a language indicator**, right click on a panel and select "Add to Panel", find "Keyboard Indicator" near the bottom of the pop up dialogue, highlight it and click "Add", then "Close".

2. When the indicator appears on the panel, right click it and choose "Keyboard Preferences". Select the "Layouts" tab and use the "Add" button to **choose your languages** (Gnome only allows four). Put a check by the language you want as default. Close the dialogue. You should have a language indicator showing some not terribly esthetic text. Click on it to change languages.

3. **Now, you need flag images**. The above mentioned site links to two images, one for the US flag and one for the Russian. These are at: 

[http://forum.ubuntu.ru/index.php?action=dlattach;topic=6303.0;attach=1226](http://forum.ubuntu.ru/index.php?action=dlattach;topic=6303.0;attach=1226) - us.png
[http://forum.ubuntu.ru/index.php?action=dlattach;topic=6303.0;attach=1227](http://forum.ubuntu.ru/index.php?action=dlattach;topic=6303.0;attach=1227) - ru.png 

I don't need Russian, but since these folks had done the work, I downloaded the images to find out the proper sizes. The images are (width) 64 x (height) 43 pixels.

If you can't find suitable flags, going to Wikipedia and searching for a country name will bring you to a page which includes the country's flag. It can be downloaded by right-click>Save image as... I didn't take these myself, but someone told me he got some there. A brief look at their site didn't seem to reveal any legal problem downloading - especially since it's only for your own desktop. It's even OK for your web site (with acknowledgment of the source [see their page for details]).

These are much larger images than you need*****, so right click the image and select "Open with > the Gimp". When the image opens in the Gimp, right click it and select "Image>Scale Image". In the dialogue box, change the width to 64. The height should take care of itself and come out around 42-47 (as mentioned, theirs are 64x43). Hit the "Scale" button and close. 

Then, in the File menu, choose "Save as..." and, leaving the .png format, name the image according to the standard two letter country code, e.g., us.png, es.png, fr.png etc. (Use the country names as found in the keyboard indicator as in #2 above ... the system recognizes languages by those country names. So, for Spanish, you must use "es.png", not "Spanish.png" or "mx.png", etc... country names - not language names: "us", not "en" [you could use a Mexican flag as long as the image were named "es.png"]). Close the Gimp.

*****_Noamr wrote_,"You actually don't need all this GIMP stuff. You can just download the SVG file from wikipedia and put it in /usr/share/pixmaps/flags/XX.svg."  I haven't tried that but, if it works for you, go for it!

4. **Place your flag images in /usr/share/pixmaps or ~/.icons/flags **(I only tried the first). If cut and paste won't work because of permission issues, move them with the command line (example: sudo mv -i Desktop/cn.png /usr/share/pixmaps/cn.png).

5.** Go to Applications>System Tools>Configuration Editor**. It seems to ship with Feisty but was not visible in my menu. If that's the case with you, try System>Preferences>Main Menu to open the Menu Editor. Find Applications>System Tools and see if it's there just waiting for you to put a check mark by it (and do that). Then you should see it in the Applications menu. You can also open it from a terminal by typing " gconf-editor" (no quotes). As a last resort, you can install it from Synaptic or apt-get (gconf-editor, gconf2-common, and gconf2).

6.** After you have the Configuration Editor open,** go to Desktop>Gnome>Peripherals>Keyboard>Indicator and check the box on the right side that says "showFlags". Close the editor and you should have flags instead of text in your keyboard indicator. (The Russian page cited above gives different instructions, but they seem to be for another keyboard indicator applet).

**NOTE:** Nanogeek, posting on the original thread for this howto, found that the above Configuration Editor selection did not work for Edgy, but was able to get the flags working by using this instead: Apps->gswitchit->Applet->showFlags (the selection mentioned on the Russian site). I have not tried this personally.

When I first did this, the flags appeared quite small. After a reboot, they came back in a better size (maybe refreshing the panel would have done that).

Also, at one point, my keyboards wouldn't switch. A reboot might have fixed that, but I was in the middle of a download, so I removed the indicator from the panel (AFTER removing all languages but one!). I then added the indicator back to the panel and put back the languages and it's been fine).

Hope this is of help to someone.

---

### Post by smoocat on 2007-10-26
Thank you!  This is just what I needed :)

As for Noamr's tip, I can confirm that that method works great, running Gutsy Gibbon--just googled "svg wiki flag [country name]" and the first result was invariably the one i wanted.

A simple rename to the two-letter country code was all I need to do before copying to /usr/share/pixmaps/flags/ .

For those frustrated at finding the correct two-letter combination, [this site]("http://www.iso.org/iso/support/country_codes/iso_3166_code_lists/iso-3166-1_decoding_table.htm") helped me tremendously, as Gnome uses ISO 3166-1 for its naming scheme.

---

### Post by Red Khan on 2008-01-31
Thank you! Worked nicely for me.
I have one more question though. Is there a way to choose different flags/icons for different variants of the same layout?

---

### Post by roadrocket13 on 2008-03-05
excellent!

quick question though, where are the Keyboard Layout .png's kept? i can't seem to find them in /usr/share

thanks in advance.

---

### Post by Ingla on 2008-03-05
Place your flag images in /usr/share/pixmaps or ~/.icons/flags (I only tried the first). If cut and paste won't work because of permission issues, move them with the command line (example: sudo mv -i Desktop/cn.png /usr/share/pixmaps/cn.png).

---

### Post by kostkon on 2008-03-05
Thank you for this how-to! Very nice! It works perfectly, even when putting the icons in the *~/.icons/flags* folder.

I used flag icons [from this collection at the *IconArchive*]("http://www.iconarchive.com/category/culture/no-patriot-icons-by-mayosoft.html"). They are pretty good.

---

### Post by zorkerz on 2008-04-23
anyone have an idea what i should do for dvorak?
I switch between a standard us qwerty and the standard us dvorak. 
I have named dvorak us.png and my image shows up nicely I do not know what to name the qwerty image because it cannot also be us. Normally they show up as USA and USA2 with the two as a little subscore.

---

### Post by iheartubuntu on 2008-05-26
Works great, thank you very much!

---

### Post by zorkerz on 2008-05-26
It appears that both US english and US dvorak look to the same image for their icon (/usr/share/pixmaps/us.png). I believe then that this method will not work for layouts from the same region.

---

### Post by pressureman on 2008-06-12
Another good collection of flag icons - PNG format. Sizes : 16x16, 24x24, 32x32, 48x48.

[http://www.icondrawer.com/free.php](http://www.icondrawer.com/free.php)

---

### Post by notanotherone on 2008-06-26
see below

---

### Post by notanotherone on 2008-06-26
I have my flags in both the 'icons' folder and the 'pixmaps' folder but my indicators for keyboards (GBr and Fr) are both showing a 'no entry' sign. Has anyone any ideas please?

---

### Post by CinemaFoto on 2008-07-05
Thank You a lot! I wish all tutorials were written like this one! Thanks again.

---

### Post by mellowtothemax on 2009-11-03
Thanks, it works great.  Ubuntu Karmic 9.10. I noticed that the icons can be any size.

---

### Post by armag.info on 2009-11-24
Thanks, man! For those who use GIMP: I advise to set canvas to 64x43, but crop layer to 50x33 to have the icon smaller.

---

### Post by NetFreeDiver on 2010-02-26
Hi notanotherone,
You should change your flag names to small letters, like "tr" instead of "Tr"or like "fr" instead of "Fr".

Cheers,

---

### Post by fortguy on 2010-02-27
What would be the code for Latin American (Spanish)?

---

### Post by pressureman on 2010-02-28
> **fortguy said:**
> What would be the code for Latin American (Spanish)?

There is a fairly thorough list here :)

[http://www.i18nguy.com/unicode/language-identifiers.html](http://www.i18nguy.com/unicode/language-identifiers.html)

---

### Post by misGnomer on 2010-09-29
Has anyone managed to figure out what (flag) icon names to use in case of keyboard variants?

I often need to use accents on US international keyboards and while toggling with the GNOME keyboard indicator between "us" and "us&#8322;" layouts works fine, those two layouts share the same flag icon.

I'd much rather have the us&#8322; (or "US international (with dead keys)" layout have its own descriptive flag icon, but I haven't been able to find out what icon filename the US-intl variant might be looking for.

I've tried us2.png, us_intl.png, us-intl.png and even "us    intl.png" (as indented in gconf-editor) but the icon doesn't get picked up and both layouts use whatever is titled "us.png/svg".

[FONT="Fixedsys"]
[COLOR="Silver"]— — — — — — — — — — —[/COLOR]
**[[COLOR="SeaGreen"]Mint-flavoured[/COLOR]]("http://forums.linuxmint.com/viewforum.php?f=141") [[COLOR="DarkRed"]Debian[/COLOR]**]("http://debian.org")[/FONT]

---

### Post by Jacknjellify on 2010-12-05
For those who need to switch from US Qwerty to US Dvorak, I noticed that Canada Qwerty is identical to US Qwerty, so they are interchangeable. :D

Hence,
Qwerty icon = ca.png
Dvorak icon = us.png

Ah, but then GDM adds the "USA" Qwerty keyboard layout at every login.

---

### Post by swmail on 2011-03-21
Collection of the 246 iso country coded "flag" icons for the keyboard indicator in the SVG format.
[https://bugs.launchpad.net/ayatana-ubuntu/+bug/628015/comments/9](https://bugs.launchpad.net/ayatana-ubuntu/+bug/628015/comments/9)

---

### Post by GrouchyGaijin on 2011-10-18
Anyone get the flags to show up on a clean install of 11.10?

---

