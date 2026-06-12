---
title: "re-install ubuntu and keep wine software?"
date: 2010-09-07
forum: Wine
---

### Post by jfreak_ on 2010-09-07
I know the topic is a bit vague, but couldn't phrase it better. Anyway, I have a legit copy of MS office installed (its actually the last of the 3 licences that you get with home&student), and I want to reinstall ubuntu. As you are well aware, installing office required some winetricks stuff and some dll over-rides. So when I re-install ubuntu, is there any way to retain MS office flawlessly? Will simply copying back /.wine work?

---

### Post by howefield on 2010-09-07
> **jfreak_ said:**
> Will simply copying back /.wine work?

I believe it will.

If you don't get confirmation here, you could also try if you haven't already,  the support at winehq, where you'll find a well populated irc channel, wiki, and forum ect.

[http://www.winehq.org/help/](http://www.winehq.org/help/)

---

### Post by cwwilson721 on 2010-09-07
> **jfreak_ said:**
> I know the topic is a bit vague, but couldn't phrase it better. Anyway, I have a legit copy of MS office installed (its actually the last of the 3 licences that you get with home&student), and I want to reinstall ubuntu. As you are well aware, installing office required some winetricks stuff and some dll over-rides. So when I re-install ubuntu, is there any way to retain MS office flawlessly? Will simply copying back /.wine work?If you backup entire ~/.wine, and copy that back, yes

---

### Post by cheekyangel on 2010-09-10
Hey jfreak! Just some words of encouragement for you.
howefield and cwwilson742 are right.
Those are the exact thing i did with my ubuntu and wine.
And i never had a problem with it, in fact i am enjoying it up to this far.

Hope this confirmation will help you decide.

---

### Post by YokoZar on 2010-09-12
Please note you'll be missing the start menu entries if you just copy ~/.wine

---

### Post by onemyndseye on 2010-09-12
Copying your wine prefix to another install/machine *should* work.  But as noted above youll be missing the menu entries although this isnt exactly a deal breaker.. Infact I think winemenubuilder may fix this on first run after the copy

if not the you can search for exe's later with:
```


find ~/.wine -name "*.exe" -not -wholename ~/.wine/drive_c/windows/* 


```

However it should be noted that not *ALL* software will work OK this way.  I cant personally speak for MS Office but Winamp does not like having its prefix transported to a new machine.  YMMV.
 
At any rate the WINE wiki states that *most* software should work as intended this way.  If ur in doubt create a Ubuntu install inside VirtualBox and try copying your Wine prefix in and running office.  If it works then your golden :)

---

