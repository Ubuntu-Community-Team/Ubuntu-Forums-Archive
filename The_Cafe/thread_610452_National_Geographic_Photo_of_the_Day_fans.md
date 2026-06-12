---
title: "National Geographic Photo of the Day fans?"
date: 2007-11-12
forum: The Cafe
---

### Post by Beach on 2007-11-12
I ported my wallpaper changing application called Opal to Linux and it seems to work well here on Gusty Gibbon.  Opal lets you browse the Photo of the Day archive, at NationalGeographic.com, and then you can set the photo as your wallpaper.   There are setup options to randomly pick a new photos on the hour or just change daily to the new photo of the day. 

The web page below has a screen shot and a deb installer.  I just wanted to share it with the community. 

[http://www.penguinbyte.com/software/opal/](http://www.penguinbyte.com/software/opal/)

---

### Post by tgoose on 2007-11-12
There's something iffy with the permissions when installing the deb on my system (it isn't set to executable by default)

---

### Post by rubadub on 2007-11-12
Thanks very much. It was very easy to install. Just got a quick question. Do you need to have the opal program open in the system tray to have the pictures switch randomly?

---

### Post by Beach on 2007-11-12
> **tgoose said:**
> There's something iffy with the permissions when installing the deb on my system (it isn't set to executable by default)

This was my first package so I am sure it is something I missed.  Do you mean the actual file 'opal' in '/usr/bin' is not set to executable?

---

### Post by Beach on 2007-11-12
> **rubadub said:**
> Thanks very much. It was very easy to install. Just got a quick question. Do you need to have the opal program open in the system tray to have the pictures switch randomly?

Thanks!  To adjust the settings, click the middle setup button and select either to change photos on the hour or just once per day.  There is also a setting for large image format which is new for National Geographic.  They just recently started offering photos in 1280x1024 resolution.    Some of the photos are fantastic.

-Beach

---

### Post by TeaSwigger on 2007-11-12
Hello and thanks! :) I'm a NG, webshots etc desktop junkie, and have a massive NG mag collection. Clean interface, plus saves me loading pages etc - bingo, there it is.

I was wondering if you couldn't make it so that one could use at least a limited selection of wallpaper setters. I'm thinking Esetroot, feh and KDE's in particular. The first two may be easy, accepting pretty straightforward commands, but I don't know what's involved in KDE's. Point being it'd make it easily adaptable to pretty much any distro that can use a .deb, not just Gnome. It's working fine on Kubuntu here, but not really automated as I have to use the copy it puts in my folder and manually set it. I still appreciate it. Thanks again! :)

---

### Post by fuscia on 2007-11-12
i've gotten some of my favorite wallpapers from the ng photo of the day, but i always have to mess with them first, especially as i have a widescreen laptop.

---

### Post by rubadub on 2007-11-12
Do you know why some of the days will not load? All that it will say is the photographers name but it will not show the picture. In the month of November it only shows about half of the days.

---

### Post by Exonimus on 2007-11-12
I can confirm the last post. happens to me as well

---

### Post by Beach on 2007-11-12
> Do you know why some of the days will not load? All that it will say is the photographers name but it will not show the picture. In the month of November it only shows about half of the days.

I noticed that also with the Windows version (is it safe to speak of the dark side here? :) ).   Anyway, I will check it out and see what is going on.  Also, I have Opal working with KDE now (thanks for the nudge TeaSwigger).   I'm just using standard KDE commands so you will not need to also load other dependencies.  I try to get it uploaded soon.

---

### Post by TeaSwigger on 2007-11-14
> **Beach said:**
> Also, I have Opal working with KDE now (thanks for the nudge TeaSwigger).   I'm just using standard KDE commands so you will not need to also load other dependencies.  I try to get it uploaded soon.

Most kind of you, thanks! :)

---

### Post by Beach on 2007-11-15
Just uploaded the new version that includes KDE support.   Please give it a test TeaSwigger when you get a chance.   I have tested it on Kubuntu 7.10 and it seems to work fine.  The only issue I see is that the buttons do not display the hover text that tells you what the button does.

Also tested it on openSUSE and some of the text labels did not display correctly.  Not sure why it would be fine on Kubuntu and not on the other, but I was using a pre-made VMware image that might have been a little over tweaked.

Anyway... enjoy
[http://www.penguinbyte.com/software/opal/](http://www.penguinbyte.com/software/opal/)

-Beach

---

### Post by TeaSwigger on 2007-11-15
> **Beach said:**
> Just uploaded the new version that includes KDE support.   Please give it a test TeaSwigger when you get a chance.   I have tested it on Kubuntu 7.10 and it seems to work fine.  The only issue I see is that the buttons do not display the hover text that tells you what the button does.

Also tested it on openSUSE and some of the text labels did not display correctly.  Not sure why it would be fine on Kubuntu and not on the other, but I was using a pre-made VMware image that might have been a little over tweaked.

Anyway... enjoy
[http://www.penguinbyte.com/software/opal/](http://www.penguinbyte.com/software/opal/)

-Beach

Ah thank you :)

I've installed & tested it in Kubuntu. Observed:

- It works! :KS

- Loads apparantly error free.

- Tray icon etc works fine.

- Successfully sets wallpaper.

- As with the previous version, some dates fail to download.

- Even with the "make the same size as my desktop" selected, it doesn't; it seems to be selecting centered rather than scaled.

- The button hover text is working perfectly, so that must be your setup there. :)

So I just have to open the background setting dialog and select scale, and as related some dates won't work. Everything else seems to work perfectly. If you need any more testing or anything let me know. Thanks again for the neat utility. :)

---

### Post by TeaSwigger on 2007-11-16
Even more feedback if you can stand it ;)

About the caption which describes the pic. On most pics it's abbreviated. It's true there's limited space, but if it could wrap perhaps it'd fit most? Also some formatting code is included (try October 7th).

Mentioned a number of dates won't load the pics; an example is Nov. 3rd, if you want to check. Perhaps it's on my end? 

Does it cache anything? So if a page won't show for some reason but comes back up, will it still display the failed cached attempt? 

I've installed it on my 2nd PC, also Kubuntu but with IceWM. I used kubuntu's deb package installer (via Konqueror). After install I had to chown the executable in /usr/bin from my user to root.

Hope it's of interest / helps.

---

