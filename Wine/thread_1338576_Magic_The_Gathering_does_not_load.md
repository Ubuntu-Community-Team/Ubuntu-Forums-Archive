---
title: "Magic: The Gathering does not load??"
date: 2009-11-26
forum: Wine
---

### Post by pinnacle2009 on 2009-11-26
I finally installed Wine thinking it would solve the MTGO problems. Well, I atleast have it installed, but when I try to open the game client, nothing happens. I don't even get an error message. Anyone able to get it working? :(

---

### Post by Xog on 2009-11-26
> **pinnacle2009 said:**
> I finally installed Wine thinking it would solve the MTGO problems. Well, I atleast have it installed, but when I try to open the game client, nothing happens. I don't even get an error message. Anyone able to get it working? :(

open a terminal and type "wine" followed by the name of the MTGO exe file.

example:
```
wine Magic The Gathering
```

This will display the error.

---

### Post by Gabethebabe on 2009-11-27
> **pinnacle2009 said:**
> I finally installed Wine thinking it would solve the MTGO problems. Well, I atleast have it installed, but when I try to open the game client, nothing happens. I don't even get an error message. Anyone able to get it working? :(

First post!!

Exact same problem here. Unfortunately not in front of my computer, but if I get home I will do what xog suggested (if it has not been done by anyone else).

[IMG]http://www.crunchgear.com/wp-content/uploads/2009/01/microsoft-virus.jpg[/IMG]

---

### Post by Xog on 2009-11-27
it's most likely the fact that the game does not have permissions set to create/delete files. to do so go Browse C:/ and go to program files. you will see your game's folder. right click on it, go to properties and click on permissions. set them to create/delete files and then click enable permissions then click ok. it should run after that.

---

### Post by beastrace91 on 2009-11-27
Just as a heads up, I haven't tried MTGO under Wine with current releases (last time I tried was like 1.1.22) and then it out and out failed... The only solution I had for playing it on Ubuntu was using a VM.

And just as a heads up to run a .exe file with spaces in its name you would need to use quotes or '\'s for example: ```
wine My\ File\ Has\ Spaces.exe
or
wine "My File Has Spaces.exe"
```

I'll have to snag the client later on and see if it works under the latest Wine... I doubt it though >.< if I recall correctly it not working was an issue with .net frame work :-/

~Jeff

---

### Post by beastrace91 on 2009-11-28
I've got MTGO all downloaded and it flat out fails under the latest Wine. It gives a general (non-helpful) error message, with little useful debug in terminal. I'll have to try and play with it some more to see if I can get it working perhaps - but for those who really want to get this working I'd recommend taking a look into [Virtual Box](http://www.virtualbox.org/)

Regards,
~Jeff

---

### Post by pinnacle2009 on 2009-11-28
What is Virtual Box? I glanced around the website but couldnt figure it out. Im new to linux lol

Will probably be getting a new computer for Christmas, so I'll atleast be able to play games on it. Hopefully can get them working on Linux though

---

### Post by beastrace91 on 2009-11-28
Virtual Box allows you to install an operating system inside your operating system (so install Windows inside Linux). It doesn't work for 3D games but for something simple like MTGO it is more than able to run it just fine. (Please note in order to use VB you will need a copy of Windows)

Regards,
~Jeff

---

### Post by pinnacle2009 on 2009-11-29
Ah I see. I should have a Windows CD on the way now. Hopefully anyway. Thanks!

---

