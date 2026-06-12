---
title: "Schwab StreetSmart on WINE"
date: 2009-04-26
forum: Wine
---

### Post by aselus on 2009-04-26
So i'm trying to switch my roommate to fulltiming linux (because he's a virus magnet on windows) and everything seems to be going fine(he's picking it all up well ^_^) except for one thing... there's an essential program he uses called StreeSmart made by Schwab that he daytrades on. So I was wondering if anyone here has gotten it working and/or can help me get it working on his PC.

What I have tried:
Attempt:User Agent switch in Firefox set to pretend the browser is in (I.E.:7 (windows vista))
result: blank screen on launch of the web-app, loads up and then just psheeewwww.

Attempt:install ie6.0 w/ java runtime 1.5
Result: Sort of loads, causes the entire screen to blackout, aside from where it thinks the java is, some things are muffled.


So those are the two things i tried... any help on this would be greatly appreciated so that I can avoid re-installing windows on his machine T_T

btw. new to the forums heh, hio all.:P

---

### Post by asdfoo on 2009-04-26
> **aselus said:**
> So i'm trying to switch my roommate to fulltiming linux (because he's a virus magnet on windows) and everything seems to be going fine(he's picking it all up well ^_^) except for one thing... there's an essential program he uses called StreeSmart made by Schwab that he daytrades on. So I was wondering if anyone here has gotten it working and/or can help me get it working on his PC.

What I have tried:
Attempt:User Agent switch in Firefox set to pretend the browser is in (I.E.:7 (windows vista))
result: blank screen on launch of the web-app, loads up and then just psheeewwww.

Attempt:install ie6.0 w/ java runtime 1.5
Result: Sort of loads, causes the entire screen to blackout, aside from where it thinks the java is, some things are muffled.


So those are the two things i tried... any help on this would be greatly appreciated so that I can avoid re-installing windows on his machine T_T

btw. new to the forums heh, hio all.:P

If he's a virus magnet on Windows, it's still possibly to screw up your system using Ubuntu, so maybe he should learn to be a better user.

Stuff that requires ie is touch and go... but perhaps you could try installing the java 6 runtime (it's backwards compatible) to see if that makes a difference.

which wine version are you using? 1.1.20 is the latest testing release
which video card and drivers?

[http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e](http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e)

---

### Post by aselus on 2009-04-27
> **asdfoo said:**
> If he's a virus magnet on Windows, it's still possibly to screw up your system using Ubuntu, so maybe he should learn to be a better user.

Stuff that requires ie is touch and go... but perhaps you could try installing the java 6 runtime (it's backwards compatible) to see if that makes a difference.

which wine version are you using? 1.1.20 is the latest testing release
which video card and drivers?

[http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e](http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e)

he's not a very experienced computer user, to say the least and doesn't even have the root(su) pass so he'll be fine I think, plus i can upkeep it from day to day a lot easier. Also his mastery of english is limited so that seems to lead him into holes heh.

Gonna try JRE 6 right now and then post on here.

I'm on the latest 'stable' packaged wine (1.0.1)... so if JRE doesn't work will build the test release. 

Video card is a 7800GTX w/ nvidia 180.00 drivers.


Update: JRE 6u13 installer doesn't seem to want to run no matter what i do, updated wine to 1.1.20

---

### Post by aselus on 2009-04-27
well made it work somehow.. reinstall ie6, and installed JSE instead of JRE and it seems to work fine 9still 5.0, 6.0 would not budge) works slow, but eh works. XD

untill I find a way to make this thing opperate under mozilla best I can do I guess.. will keep trying on that front, though seems more futile the more I try.

---

### Post by celem on 2010-03-03
I run StreetSmartPro in VirtualBox.

---

