---
title: "How do you get Monkey Island: The Screaming Narwhal working in wine"
date: 2009-07-14
forum: Wine
---

### Post by Captain_Glen on 2009-07-14
Hi,

I have read that you can play Monkey Island: The Screaming Narwhal on Ubuntu.

I have tried to install it under wine.  It installed ok but when I run it I get a black screen and only sound not video.

The menu works fine but when you click new game it goes all black.  If you wait long enough you can see some stuff but it is mostly just black.

I have ubuntu 9.04 with the default version of wine.

Any help would be appreciated.

---

### Post by PureLoneWolf on 2009-07-15
To get this working for me (managed it yesterday) I downloaded winetricks (right click [HERE]("http://winezeug.googlecode.com/svn/trunk/winetricks") and choose Save Link As)

Then from a terminal ran 

```
sh winetricks d3dx9
```

Tales of MM ran without issue after this.  That said, I got the standalone version, not the steam version, although I would think it might help.

Hope that helps you.  

Also, for the record, before installing anything with winetricks, it is always recommended to backup your .wine folder in your home folder.

---

### Post by Captain_Glen on 2009-07-15
Nope that didn't fix it. :(

---

### Post by GeryonD on 2009-07-21
I tried the tricks thing too to no avail.  I have the latest nvidia drivers installed on Jaunty with Wine 1.1.26.  I have the same results when changing resolution.  I am stuck in 1024x768.  After searching some more, I found a patch for Wine that is supposed to fix this:

[http://bugs2.winehq.org/attachment.cgi?id=22431](http://bugs2.winehq.org/attachment.cgi?id=22431)

I am downloading the git repository for the wine source, I'll apply that patch and see what happens.

---

### Post by GeryonD on 2009-07-21
Just to update my own response.

I pulled the latest code from git for Wine and it actually includes the patch I listed above.  Once compiled, Tales of Monkey Island switched resolutions and ran beautifully.  

Gonna go play :)

---

