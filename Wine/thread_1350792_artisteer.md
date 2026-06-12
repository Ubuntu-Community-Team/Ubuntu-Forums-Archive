---
title: "artisteer"
date: 2009-12-09
forum: Wine
---

### Post by enbilulu on 2009-12-09
How can I run artisteer on ubuntu 9.10?

---

### Post by waterboy0911 on 2010-10-24
I also want to install this artiststeer for ubuntu 10.10

is there any way we can install this to ubuntu?

I tried using wine.. but some bugs came along so I just discontinued to install.. 

I hope there could be a way we can make this happen.

---

### Post by bradmurmz on 2011-03-14
Using winetricks I'm trying to install the necessary add-ons to get artisteer to work and it seems as though winetricks is broken. None of the packages really install correctly or are even remembered when I restart winetricks again...

SO frustrating... When is everything going to 'just work' under linux. I can't wait for that day.

---

### Post by Tweak42 on 2011-03-14
> **bradmurmz said:**
> Using winetricks I'm trying to install the necessary add-ons to get artisteer to work and it seems as though winetricks is broken. None of the packages really install correctly or are even remembered when I restart winetricks again...

SO frustrating... When is everything going to 'just work' under linux. I can't wait for that day.

Winetricks does not "remember" what was installed previously.  It's ["a quick and dirty script to download and install various redistributable runtime libraries sometimes needed to run programs in Wine."]("http://wiki.winehq.org/winetricks") You could find, download, install all the various packages manually you choose.

According to the one report on the [wine appdb](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22513), Artisteer installs but is mostly unusable.  You may have luck trying different versions of wine and different libraries.

By nature getting things to 'just work' in linux takes more than waiting. :D

---

### Post by bradmurmz on 2011-03-14
I actually got it to work now... I just figured out that it doesn't 'remember' things on my own. I guess I was just hoping it would act more like a package manager.  

I've been using linux for years and love it... I just sometimes get frustrated because I end up spending hours trying to get something to work and then wonder if its even worth it sometimes!

I love linux and wish everything would 'just work' and I know it would if it wasn't for the lack of support. Any problem I've ever ran into has always been because some software vendor doesnt make a linux version (which is why I have to then mess with wine for hours) or some hardware manufacturer doesn't make drivers. The community almost always solves these problems buts its just frustrating sometimes... I will be a happy man someday when everything does 'just work'.

:)

---

### Post by bradmurmz on 2011-03-14
Just incase anyone cares I got artisteer 2.6 to work with wine using winetricks and the following commands

winetricks corefonts tahoma fontfix d3dx9 vcrun6 ie6
winetricks dotnet20 
winetricks gecko
winetricks gdiplus

---

### Post by Tweak42 on 2011-03-15
> **bradmurmz said:**
> Just incase anyone cares I got artisteer 2.6 to work with wine using winetricks and the following commands

winetricks corefonts tahoma fontfix d3dx9 vcrun6 ie6
winetricks dotnet20 
winetricks gecko
winetricks gdiplus

You may want to post a updated entry on the wine appdb for other users to find.

---

### Post by rez182 on 2011-04-10
can we use artisteer 2.3 in wine?

---

### Post by abix_adam_pl on 2011-04-13
I can confirm Artisteer 2.6 under Ubuntu 10.10 and wine - works, but it is not exactly the same look as under real Windows ;-(

Adam

---

