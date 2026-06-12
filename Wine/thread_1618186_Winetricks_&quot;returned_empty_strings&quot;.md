---
title: "Winetricks &quot;returned empty strings&quot;"
date: 2010-11-10
forum: Wine
---

### Post by Redgrieve on 2010-11-10
Hey ho :)

I´m new in Ubuntu. I´m using windows since 17 years, but I wanted to test something new.

Ubuntu looked ok, so I installed it. I´m REALLY impressed. Smooth, fast, straight.
But there things annoying me. I can´t open some sites in Mozilla for example. 
So I downloaded Wine and saved Winetricks. I´m trying to open "gecko" and "gecko-dbg", but I just get this error:

cmd.exe /c echo ´%ProgramFiles%´ returned empty string

It  appears on every "program" I´d like to install. I found some stuff  here, but either I´m doing it wrong, or it just won´t work.

Thank you :)

---

### Post by dankegel on 2010-11-11
What do the following commands output?

 wine --version

 winetricks -V    (or sh winetricks -V, depending on how you installed it)

 cmd.exe /c echo "%ProgramFiles%"

---

### Post by YokoZar on 2010-11-11
Best way to get winetricks is to just add the Ubuntu Wine PPA -- did you do that?

---

### Post by abdusamed on 2010-12-28
I can't run powerpoint 2007 because I need to install certain file through winetricks. But winetricks itself is not working

Whenever I try to install something via
```

sh winetricks

```I'm always reading the error in my terminal output
```

wine cmd.exe /c echo '%ProgramFiles%' returned empty string

```
Please fix it... i need office powerpoint 2007...2010 doesn't work yet :'(

btw
```

sh winetricks -V
Winetricks version 20101008.  (C) 2007-2010 Dan Kegel et al.  LGPL.

```

and on ubuntu 10.04 altest kernal..update 2 days ago from the date of this post posted on

---

