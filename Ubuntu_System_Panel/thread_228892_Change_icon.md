---
title: "Change icon?"
date: 2006-08-03
forum: Ubuntu System Panel
---

### Post by _simon_ on 2006-08-03
Where does the icon need to be and what needs to be entered in gconf?

Each time I try all I get is a box with a red x in - I assume because it can't find the icon.

Could the answer be added to the HOW TO? [http://www.ubuntuforums.org/showthread.php?t=224992](http://www.ubuntuforums.org/showthread.php?t=224992)

and shouldn't the HOW TO be a sticky? :)

---

### Post by cantormath on 2006-08-03
> **_simon_ said:**
> Where does the icon need to be and what needs to be entered in gconf?

Each time I try all I get is a box with a red x in - I assume because it can't find the icon.

Could the answer be added to the HOW TO?

what are you trying to do exactly?

are you trying to change all of the icons, just one, or create a launcher?

If you are try to change all the icons, go to
System>Preferences>Theme
Click on Theme Details, then Icons tab.
you can select new icons.
If you want new icons, try gnome-art
its in the repository, just look for it.
it will help you find more if you dont like the ones you have.

---

### Post by _simon_ on 2006-08-03
I want to change the USP icon...

I think you posted without checking which part of the forum you are in ;)

---

### Post by gruvsyco on 2006-08-03
gconf-editor

apps > usp

applet_icon_name

just add the name of your icon leaving off the extension, it seems to auto-detect the format at least, png and xpm

**edit* also it appears to look in /usr/share/icons by default.*

---

### Post by _profox on 2006-08-03
Sorry, I will clarify :)
applet_iconname uses icons from your current theme! So browse to /usr/share/icons/name-of-your-theme/ and find icons there. Then just enter the name of the icon, without the extension.

We might add the possibility to use custom .png or .xpm files later

---

### Post by gruvsyco on 2006-08-03
> **_profox said:**
> We might add the possibility to use custom .png or .xpm files later
Not sure, what you mean by this.  I can already change the icon to a custom icon and it will stick through changes in icon themes.

---

### Post by _profox on 2006-08-03
> **gruvsyco said:**
> Not sure, what you mean by this.  I can already change the icon to a custom icon and it will stick through changes in icon themes.

Can you give an example?
The way I programmed it, it uses the iconname you provide to get that icon from your current theme..

ps: you have to re-add the applet for the text/icon change to take effect, this is a little bug that is caused by manual patching, it will be fixed in the next release.

---

### Post by chanders on 2006-08-03
> **_profox said:**
> Can you give an example?
The way I programmed it, it uses the iconname you provide to get that icon from your current theme..

ps: you have to re-add the applet for the text/icon change to take effect, this is a little bug that is caused by manual patching, it will be fixed in the next release.

GNOME uses standard names for certain icons. So as long as you use a STANDARD GNOME NAME it will work. One way to find out the list of icon names is to look in a theme folder. You can use any name you see there, just leave out the extension such as .png or xpm...

Eg. gnome-logout is a standard GNOME name so using gnome-logout as the icon name in /apps/usp/applet_icon_name will just fine.

---

### Post by gruvsyco on 2006-08-03
> **_profox said:**
> Can you give an example?
The way I programmed it, it uses the iconname you provide to get that icon from your current theme..

ps: you have to re-add the applet for the text/icon change to take effect, this is a little bug that is caused by manual patching, it will be fixed in the next release.

I put an icon name mymenu.png in /usr/share/icons and just pointed to it.  Regardless of what my theme is it seems to stay.  Perhaps because it's not named after any system icon.

---

### Post by chanders on 2006-08-03
> **gruvsyco said:**
> I put an icon name mymenu.png in /usr/share/icons and just pointed to it.  Regardless of what my theme is it seems to stay.  Perhaps because it's not named after any system icon.

Or maybe all icons in /usr/share/icons work also ;)

---

### Post by bulldog on 2006-08-04
Yes you could use any icon in your icon map.
You can copy any icon that you wish to use to that folder and use it.
And you can give your menu any name that you wish.
I have a Dutch version of Ubuntu and called my menu very original "Startmenu" and did used a variety of icons.
No problems there :D

---

### Post by chanders on 2006-08-04
> **bulldog said:**
> Yes you could use any icon in your icon map.
You can copy any icon that you wish to use to that folder and use it.
And you can give your menu any name that you wish.
I have a Dutch version of Ubuntu and called my menu very original "Startmenu" and did used a variety of icons.
No problems there :D

Post a screenie in the screenshots thread ;)

---

### Post by LordMau on 2006-08-05
Before the gconf key was made, the way I did it was to provide a file named

**distributor-logo (usually .svg, not sure if .png works)**

within my used icon theme.

USP automagically uses that file as the logo on its button.

---

### Post by bulldog on 2006-08-05
> **chanders said:**
> Post a screenie in the screenshots thread ;)
Done!
I put one with a different name and icon too.

---

### Post by jason.b.c on 2006-08-19
Well i don't know  , I sure can't get it to work...](*,) :(

---

### Post by Uncle Spellbinder on 2006-08-20
[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/USP-ICON.png[/IMG]

---

### Post by chanders on 2006-08-20
> **jason.b.c said:**
> Well i don't know  , I sure can't get it to work...](*,) :(

See [this]("http://www.ubuntuforums.org/showpost.php?p=1335183&postcount=8") post

---

### Post by Eman64 on 2006-09-24
I tried it and it came out really really tiny. Anyone know the solution to this?

---

### Post by diggity on 2006-09-26
> I tried it and it came out really really tiny.I'm getting the same result.
I placed the png file into the /usr/share/icons dir changed the applet_icon_name to the file (w/out the .png). The image is displayed, but very small. Btw the image dimensions are (114px x 41px) and the panel height is 24px.

---

### Post by Uncle Spellbinder on 2006-09-26
> **diggity said:**
> I'm getting the same result.
I placed the png file into the /usr/share/icons dir changed the applet_icon_name to the file (w/out the .png). The image is displayed, but very small. Btw the image dimensions are (114px x 41px) and the panel height is 24px.


Same here. Regardless of the image I choose, or it's size, it always shows up as a USP icon very tiny.

---

### Post by Eric_T on 2006-12-14
Same here....any solution to this?

---

### Post by chanders on 2006-12-14
Will try to get to the bottom of this for USP2

---

### Post by apapww on 2007-01-03
Thanks ever so much[.](http://hk.yahoo.com)[.](http://www.ec2biz.com)[.](http://www.rthk.org.hk)[.](http://www.ads28.com)[.](http://www.ec2biz.com)[.](http://www.top1.com.hk)[.](http://www.ads28.com)

---

### Post by boneyjellyfish on 2007-05-18
Did anything ever come of this? I'd like to change my USP icon to [this](http://www.natewelch.com/postnuke/ubuntumenu.png) but it gets cut off. Although the applet_icon_size key does make the icon larger, it doesn't actually increase the space allotted for icons, so they still get cut off.

---

### Post by mid_night gypsy on 2007-07-19
Howdy,
 I to am having this problem, and can't figure it out (head banging on monitor sounds). I have  seen  some screen pics where the menu icon fits right, But no luck on my part tried quite a few. Any help would be great.
 P.S. USP is awesome keep up the good work.
 Thanks,gypsy

---

