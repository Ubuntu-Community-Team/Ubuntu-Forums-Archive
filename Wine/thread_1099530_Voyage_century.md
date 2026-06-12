---
title: "Voyage century"
date: 2009-03-18
forum: Wine
---

### Post by Ice799 on 2009-03-18
Alright I've I've tried to run VCO under wine 1.1.17, ive also tried it under the stable 1.0.1

Installstion worked fine. Registered mscoree.dll and streamci.dll as native from windows. I messed with the windows version from windows 98 - Vista, Nothing changes.

At First I get an error that doesnt say anything. (Attached) 

Then when I click update it changes to start game, and goes into the game from there. I choose the ocean to login into and then username and password then select my guy then it crashes back to desktop.

If anyone has got this to to run under wine I would like to if anything what they did or if anyone has any ideas I haven't tried. 

I've tried the steps on winehq under VCO, looked there didn't really find anything useful, I tried setting 256Kb Video Size in my registry. not sure if that helped.... 

Anything that will help me to get this to work?

When I Run it through console I get an error message on the screen that says the files are damage and that I should re-download and I get this in the console:```
$ wine "c:/Program Files/Voyage Century Online/voyagecentury.exe"
fixme:advapi:RegisterTraceGuidsW 0x959f97 0xa94b08 0x849354 1 0x32d9c4 (null) (null) 0xa94b10
fixme:advapi:RegisterTraceGuidsW 0x959f97 0xa94b28 0x849364 1 0x32d9c4 (null) (null) 0xa94b30
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB

```
 
* I think the problem for the game crash is because it hasnt updated its still 0.58... Any1 know how to fix that?```
[CODE]
```[/CODE]

---

### Post by cogadh on 2009-03-18
Its a known bug in Wine with this game:
[http://bugs.winehq.org/show_bug.cgi?id=15548](http://bugs.winehq.org/show_bug.cgi?id=15548)

There is a how-to for earlier versions of the game that might help though:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8265](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8265)

---

### Post by Ice799 on 2009-03-18
The first place i went was to there and none of that helped me...

---

### Post by cogadh on 2009-03-18
Well, the bug shouldn't really have helped, its something that they need to fix in Wine and you may not be able to get the game working until they do. All it really does is explain why the game isn't working for you.

---

### Post by Ice799 on 2009-03-18
I think its something simple im missing... Must be something i can do to get around it

---

### Post by cogadh on 2009-03-18
What you described is precisely what is in that bug: a crash to desktop after logging in. Your crash even has the same uninformative Wine errors. I would find it very hard to believe that you missed something simple that causes an almost identical crash to what is contained in that bug report.

---

