---
title: "Linux Fonts"
date: 2005-08-26
forum: The Cafe
---

### Post by poofyhairguy on 2005-08-26
One recent thing I have read about many times in web forums is how "fonts suck in Linux." I can't help but wonder how people think that is the case. 

I feel I am very picky with my fonts. Yesterday I bought a new monitor (19" 8ms Samsung with DVI hook ups) and I tried it out in the store. It was the first time I looked at XP on a DVI output, and all I could see was flaws. The fonts looked like crap....like they were bleeding. (not to mention that the default hill backround in XP looks REALLY pixelated with modern technology, and the start bar look sbad as well). I remember thinking "I got to get this home to make sure that these fonts problems are just XP problems". 

Then I got the monitor home, turned on Ubuntu and said "ahhhhhh." The fonts seem so much crisper, Solid to read. The fonts in KDE are just as good (maybe better). It seems to me that one place where Ubuntu kills Windows is the fonts.

Is it just me, or do Linux fonts kick ass?

---

### Post by SKLP on 2005-08-26
Freetype font rendering is great :)

---

### Post by KiwiNZ on 2005-08-26
poofy, Are you sure the the shop one was set at it's native resolution?

---

### Post by KingBahamut on 2005-08-26
Poofy, I felt the same way when I got my vx924 home. 

No question....Linux fonts are much better than Winders.

---

### Post by pmj on 2005-08-26
I haven't really investigated fonts and how they work in Ubuntu yet, but they DO look bad. I have to strain my eyes to even read the text on Slashdot. On small text, parts of letters may just disappear, like the middle line in a z.

---

### Post by darkmatter on 2005-08-26
Fonts on Linux have always been kick-ass, IMHO.

I've been involved in flame wars with self-proclaimed 'experts' on other forms who insist that Windows+Cleartype is the better combo. How anyone can think that is beyond my ability to understand. Cleartype is horrific.

---

### Post by darthsabbath on 2005-08-26
Y'know, I've found fonts in Linux to be odd.  On my 19" Desktop CRT they're utterly beautiful, but on my notebook (15"), they're... ugly.  Granted, Windows fonts don't look great on either, but, I guess something can be said for consistency. ;-)

I'm sure there's something I can do on my notebook, but I'm too lazy to figure it out right now. :D

On the whole, I like Linux' fonts better.

One slightly off topic question... I don't seem to have all my system fonts in Open Office.  Is there any way I can point OOo to the fonts directory?  I 've looked around and pointed it to (forgive me, I'm on a WinXP machine at work, so I can't remember exactly) /usr/lib/X11/$SOMETHING/fonts with no results.

Phil

---

### Post by bored2k on 2005-08-26
On my NEC AccuSync 75F fonts look _much_ better on Linux than on Windows, even the default big font size of Ubuntu. Change Ubuntu's font to Sans 8 and you got yerself pure sweetness.

---

### Post by blastus on 2005-08-26
OK I decided to take poof up on his challenge! :razz:

On every out-of-the-box installation I've done on Red Hat, Fedora Core, Ubuntu, and Mepis...the fonts all look terrible compared to Windows XP. That's right, they look really bad and they are hard on the eyes! There's no arguing about that unless you have vision problems! They look especially bad in a web browser when browsing the web. On many sites I couldn't even make out what the text was on the page without zooming in three or four times!

I have an old CRT monitor. If you have a CRT monitor the first thing that you need to check for (or fix) are the horizontal and vertical refresh rates. You'll have to check the specs for your monitor but for mine the synchronization specs are...

```
Horizontal: 30 kHz to 69 kHz
Vertical: 50 Hz to 160 Hz
```

...so what I did was edit my /etc/X11/xorg.conf file so that the "Monitor" section of the file looks like this...

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-69
	VertRefresh	50-160
EndSection
```

Now you need to install the msttcorefonts package and turn off antialiasing! msttcorefonts is the Microsoft TrueType fonts package. To install it enter...

apt-get install msttcorefonts

...I'm not sure what repository it is in but it's probably in restricted. This font package doesn't come with the Tahoma font but Tahoma is used throughout Windows XP. To install the Tahoma font, copy the tahomabd.ttf and tahoma.ttf files from c:\windows\fonts (I think) on Windows XP to your ~/.fonts directory in Ubuntu. Note; this will only install the Tahoma font for your account--it will not make it available for all users. I'm not sure how to install it systemwide.

Now in Ubuntu goto System -> Preferences -> Font and change all the fonts except the "Terminal font" to "Tahoma." I run at 1024x768 and used Tahoma size 9 on Windows XP so I set all my fonts to Tahoma size 9 in Ubuntu. Now the key is to set Font Rendering to "Monochrome." If you click on the "Details..." button, you'll notice that the "Monochrome" font rendering setting set Smoothing = None and Hinting = Full. I've tried messing with the other settings and the "Monochrome" is the best.

Now the fonts in Ubuntu should look just like they do in Windows XP. You'll notice that sites like [www.cnn.com](www.cnn.com) and pretty much everything you browse on the web looks as good as it does in Windows XP. Why is that? Well I think it's because almost everyone uses Windows and almost every single website ever built uses Microsoft's TrueType fonts.

Now to put poofs claim to the test and so that my eyes weren't playing tricks on me, I went into Windows XP and opened WordPad. I selected Tahoma size 9 and typed in some text. Then I took a screenshot and saved it as a PNG file. Then I went into Ubuntu and opened up the GIMP. I then opened the screenshot I saved in Windows XP. I turned off antialiasing in the GIMP and selected Tahoma size 12 as the text font. I'm not sure why Tahoma size 12 pt/px/pc or whatever in the GIMP is the same as Tahoma size 9 but whatever. Then I typed in the same text underneath the existing text on the image. Then I moved the text so that it was aligned underneath the existing text that was typed in Windows XP. Then I zoomed in 800% and compared the two texts character by character and pixel by pixel. 

What I found was the texts were identical, pixel for pixel! The only difference I could find was that the two texts were off by one pixel--the Ubuntu text was one pixel shorter in width than the Windows XP text. I had the word "Tahoma" in both texts. In the Windows XP text, there was one extra space between the "T" and the "a" but that was the only difference between the texts.

---

### Post by benplaut on 2005-08-26
i use veranda for everything... still looking for good system fonts, soemthing unique  :mad:

---

### Post by drizek on 2005-08-26
[QUOTE=KiwiNZ]poofy, Are you sure the the shop one was set at it's native resolution?[/QUOTE]
 ya, most likely they were running it at 1024x768 or something, and it got skewed at 1280x1024.

however, that does not mean that fonts in linux are bad. they are just as good as windows(which does a damn good job with them as well).

---

### Post by Mishura on 2005-08-27
I dualboot WIndows XP and Kubuntu Linux Hoary.  (Let the firing squad commence!)

Fonts in XP freaking SUCK.  No antialiasing, at all.  What "Nice looking" fonts are these trolls talking about?!  Is there something they installed?  A setting?  What?

Fonts in Linux RULE.  With KDE, I click on the "If its a font, antialias it!" checkbox and all is well.  I install GTK-Qt engine, and the same goes to my GTK apps.  And I'm only using the Bitstream ones, and other default fonts.

Sure, SOME fonts in Linux suck..  but not as horrible as my XP setup.

*I honestly don't care about fixing the fonts in XP.. I never stay long on the desktop to warrant it.  Go Linux!

*oh, 17" CRT monitor if your wandering.. 32bit colors all the way at 1024x768.. due to higher resolutions operate at below 70hz refresh rate..  hurts my eyes..

---

### Post by luca_linux on 2005-08-27
Just set BitStream Vera fonts as the default for all the system and in Firefox. Everything will look better.
Yeah, Ubuntu, like Fedora, has been already set up for better font rendering, but try a Debian or Slackware: the fonts don't look fine...these distros need some tweaking for making fonts good.

---

### Post by drizek on 2005-08-27
if you use windows xp, this is how you set up font antialiasing. AA is disabled by default.

[http://www.microsoft.com/typography/cleartype/tuner/Step1.aspx](http://www.microsoft.com/typography/cleartype/tuner/Step1.aspx)

---

### Post by benplaut on 2005-08-27
[QUOTE=luca_linux]Just set BitStream Vera fonts as the default for all the system and in Firefox. Everything will look better.
[/QUOTE]

sweet... much better than Veranda  :)

---

### Post by haakon on 2005-08-27
I have installed Bitstream Vera, but Firefox will only let me choose between "Serif" and "Sans Serif" for proportional font. In the other font categories, I can pick the Bitstream fonts, but not there. The "Serif" font is extremely grainy and makes sites like slashdot.org look really bad. How do I fix this?

---

### Post by mstlyevil on 2005-08-27
[http://ubuntuguide.org/#extrafonts](http://ubuntuguide.org/#extrafonts)

  First try downloading all these fonts available to Ubuntu users in the unofficial guide.  If this doesn't fix your problem then download the windows fonts from a previous post.  Personally, I like times new roman over the default XP fonts.

---

### Post by Rogee on 2005-08-27
I honestly don't understand how people think that Linux fonts are good.  That has been one of the things keeping me from using Linux 100% of the time.

Right now I'm using ClearType on Windows XP on my LCD screen.  I've never seen better fonts on any OS, including OSX.
[http://www.microsoft.com/typography/ClearTypeInfo.mspx](http://www.microsoft.com/typography/ClearTypeInfo.mspx)

To be honest though, it looks pretty bad without ClearType.  Either way, reading web sites has driven me crazy in Linux, even after installing MS core fonts.

---

### Post by blastus on 2005-08-28
[QUOTE=Rogee]I honestly don't understand how people think that Linux fonts are good.  That has been one of the things keeping me from using Linux 100% of the time.[/QUOTE]

I totally agree with you! But if you go back to my post on the first page of this thread you can make your fonts look just like in Windows XP. And in my post, I proved that there was nothing wrong with the TrueType font renderer in Linux...it's at least just as good as the one in Windows XP.

> Right now I'm using ClearType on Windows XP on my LCD screen.  I've never seen better fonts on any OS, including OSX.
[http://www.microsoft.com/typography/ClearTypeInfo.mspx](http://www.microsoft.com/typography/ClearTypeInfo.mspx)

To be honest though, it looks pretty bad without ClearType.  Either way, reading web sites has driven me crazy in Linux, even after installing MS core fonts.

ClearType is only for the benefit of LCD. I don't have an LCD. But there was a post quite a while ago on these forums on how to enable ClearType for fonts in Linux, check it out right here [http://www.ubuntuforums.org/showthread.php?t=20976&highlight=ClearType](http://www.ubuntuforums.org/showthread.php?t=20976&highlight=ClearType). 

I totally agree with you about viewing web pages with the default Linux fonts. One would have to have bad eyesight not to notice how bad web pages look by default in Linux! On a default installation, some web pages are hardly even legible without zooming in several times. But once the Microsoft TrueType fonts are installed, everything magically looks good!

---

### Post by glandula on 2005-09-02
i always thought linux fonts look really ugly compared to windows, but ive discovered  that they only look ugly when the fonts are black. if u use fore example this theme [http://www.gnome-look.org/content/show.php?content=22989&PHPSESSID=1ffdcef2b42938d2e6d28dc733f97ebe](http://www.gnome-look.org/content/show.php?content=22989&PHPSESSID=1ffdcef2b42938d2e6d28dc733f97ebe)
which has an oliveish background and i guess dark grey or maybe dark olive fonts it looks way better, just as good as in windows

---

### Post by poofyhairguy on 2005-09-02
[QUOTE=Rogee]
Right now I'm using ClearType on Windows XP on my LCD screen.  I've never seen better fonts on any OS, including OSX.[/QUOTE]

I guess fonts are a more subjective thing. I'm in XP right now on an LCD with tweaked Cleartype settings and it still hurts my eyes.

---

### Post by poofyhairguy on 2005-09-02
I have to say, after getting used to it the fonts in Breezy rule. Very very very nice.

---

### Post by endy on 2005-09-02
To everyone complaining about the fonts: POST SCREENSHOTS to back up your claims and show us where they look so bad.

I just took a shot of Slashdot in Firefox from Ubuntu for an example. Personally, I think the fonts in linux are good if not better than Windows. Do you see anything wrong with my fonts?

[[IMG]http://img232.imageshack.us/img232/5417/linuxfonts3ch.th.png[/IMG]](http://img232.imageshack.us/my.php?image=linuxfonts3ch.png)

---

### Post by aysiu on 2005-09-02
[QUOTE=endy]To everyone complaining about the fonts: POST SCREENSHOTS to back up your claims and show us where they look so bad.[/quote]

Here you go.
[This ](http://i22.photobucket.com/albums/b337/psychocats/linux_fonts.png)is one page in Ubuntu's Firefox.
[This ](http://i22.photobucket.com/albums/b337/psychocats/windows_fonts.png)is the same page on the same computer in Windows XP's Firefox.

They seem comparable to me.

---

### Post by poofyhairguy on 2005-09-02
[QUOTE=aysiu]Here you go.
[This ](http://i22.photobucket.com/albums/b337/psychocats/linux_fonts.png)is one page in Ubuntu's Firefox.
[This ](http://i22.photobucket.com/albums/b337/psychocats/windows_fonts.png)is the same page on the same computer in Windows XP's Firefox.

They seem comparable to me.[/QUOTE]

Not at all to me. The Windows fonts seem WAY worse in those pictures.

---

### Post by aysiu on 2005-09-02
[QUOTE=poofyhairguy]Not at all to me. The Windows fonts seem WAY worse in those pictures.[/QUOTE] Sorry. You're right. I took a second look, and the Windows ones are a bit pixelated.

---

### Post by Lux Perpetua on 2005-09-02
[QUOTE=poofyhairguy]Not at all to me. The Windows fonts seem WAY worse in those pictures.[/QUOTE]
 That's because ClearType is not enabled in the XP version. How does it look with ClearType?

---

### Post by poofyhairguy on 2005-09-02
Use this:

[http://www.microsoft.com/typography/ClearTypePowerToy.mspx](http://www.microsoft.com/typography/ClearTypePowerToy.mspx)

Then post again.

---

### Post by aysiu on 2005-09-02
Okay, [here](http://i22.photobucket.com/albums/b337/psychocats/windows_cleartype.png)'s the ClearType version.

And [here](http://i22.photobucket.com/albums/b337/psychocats/linux_fonts.png)'s the Ubuntu version again.

---

### Post by endy on 2005-09-02
Apart from the Window's font's being slightly smaller I think they both look fine. I can't see why anyone would complain about Linux fonts unless they have a broken setup, crappy monitor or just want to troll :)

Personally, I still prefer the fonts on Linux, although there doesn't seem much difference in the screenshots but that's my honest opinion.

---

### Post by aysiu on 2005-09-02
[QUOTE=endy]
Personally, I still prefer the fonts on Linux, although there doesn't seem much difference in the screenshots but that's my honest opinion.[/QUOTE] I'm not sure I care. They both seem fine to me. The only fonts I hate are the default ones for Mepis, but for Linux in general, I think the fonts are just fine.

---

### Post by urlwolf on 2008-04-04
> **aysiu said:**
> Okay, [here](http://i22.photobucket.com/albums/b337/psychocats/windows_cleartype.png)'s the ClearType version.

And [here](http://i22.photobucket.com/albums/b337/psychocats/linux_fonts.png)'s the Ubuntu version again.

I think windows fonts look better. Look at the word RSS. In linux, there are parts of the S that are not even white. This is unacceptable.

I wonder why that is.

---

### Post by jespdj on 2008-04-04
urlworlf, congratulations on waking up a thread that has been dead since September 3rd, 2005 (more than 2.5 years ago).

Have you tried with the current version of Ubuntu? Things might have changed in the last 2.5 years. If you don't like the default fonts, install something different, for example the [Red Hat Liberation fonts](apt://ttf-liberation).

---

### Post by the_darkside_986 on 2008-04-04
Lol@thread necromancy. On topic: I remember when I first saw Ubuntu on an LCD screen. Previously, that laptop had Windows XP and LCD + MS Sans Serif is not a very pretty sight. Well, there's nothing pleasant about MS fonts IMO, too mechanical. But then my friend installed Ubuntu on his laptop and everything looks so nice on the screen, especially compared to XP. So that day I was determined to replace my ugly CRT with an LCD for the desktop so I could have an excellent looking Ubuntu.

In fact, whenever I install Windows XP, I tend to replace the default theme fonts with Bitstream Vera, to make it look less ugly and more like Gnome. But sadly, I can't figure out how to replace the widget fonts (buttons, etc.) with Bitstream Vera instead of MS Sans Serif. I hope there are step-by-step registry editing instructions for doing that, and that I someday find them. (Not that I've booted Windows in over a month.)

---

### Post by z0mbie on 2008-04-04
I've seen a big improvement in Ubuntu fonts in particular. Out of the other distros I've tried out, Ubuntu has very lushes font. A lot of people don't have their displays setup right in the beginning and don't have the Free type substitutes either. You're right clear type does bleed, every time I come home from work, I always notice how refreshing the fonts are in Ubuntu compared to XP. I hope we keep moving in this direction.

---

