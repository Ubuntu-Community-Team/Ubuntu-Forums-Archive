---
title: "Request: gdesklets 0.35"
date: 2005-06-11
forum: Ubuntu Backports
---

### Post by foxy123 on 2005-06-11
gDesklets 0.35 out now, actually has been out already for a couple of weeks. Any way to get it in backports any time soon?

---

### Post by garnertr on 2005-06-11
I've now moved from my beginner stage to gdesklets, these are fun and way cool to play with...

Have you been able to get 35 ver running?

---

### Post by Mez on 2005-06-11
35 is sitll a Release candidate.... so it's not stable yet.

---

### Post by foxy123 on 2005-06-12
[QUOTE=Mez]35 is sitll a Release candidate.... so it's not stable yet.[/QUOTE]

I guess it is a final release:

```
gDesklets 0.35 out now!
Posted By: chrisime
Posted on May 26 2005 @ 23:31 GMT

Hi!

gDesklets 0.35 has been released with some fixes which have been discovered in 0.35rc1.
You can download gDesklets 0.35 at the usual location.
See you at GUADEC in Stuttgart!

Have fun,
The gDesklets Development Team
```

---

### Post by Seth on 2005-06-13
Well, I gave it a go, but no Hoary system to test it on, so you get to test

I'm sure Mez will let me know if it doesn't work, probably in the most public and humiliating way possible, but meh... learn by doing!

Let me know if it doesn't work and I'll either fix my error or somebody else will make you one.

Download gDesklets 0.35-1

---

### Post by Seth on 2005-06-13
[QUOTE=foxy123]I guess it is a final release:

```
gDesklets 0.35 out now!
Posted By: chrisime
Posted on May 26 2005 @ 23:31 GMT

Hi!

gDesklets 0.35 has been released with some fixes which have been discovered in 0.35rc1.
You can download gDesklets 0.35 at the usual location.
See you at GUADEC in Stuttgart!

Have fun,
The gDesklets Development Team
```[/QUOTE]
 Here you go :)

[http://www.sethkinast.com/ubuntu/hoary/backports/gdesklets_0.35.1-1~5.04ubp1_i386.deb](http://www.sethkinast.com/ubuntu/hoary/backports/gdesklets_0.35.1-1~5.04ubp1_i386.deb)
**Updated - now in Breezy**

---

### Post by matthew on 2005-06-13
Running beautifully on my machine. Thank you!

Screenshot: [http://photos13.flickr.com/19232055_edb1cca495_b.jpg](http://photos13.flickr.com/19232055_edb1cca495_b.jpg)

---

### Post by foxy123 on 2005-06-14
[QUOTE=Seth]Here you go :)

[gdesklets_0.35-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gdesklets_0.35-1~5.04ubp1_i386.deb)[/QUOTE]

thanks a lot. works perfectly. as i noticed it uses less resources than the previous version.

---

### Post by acascianelli on 2005-07-06
Why isn't this version of GDesklets in backports yet?

---

### Post by foxy123 on 2005-07-06
0.35.1 is already out with some bugs fixed...

---

### Post by Kyral on 2005-07-06
I concur!

---

### Post by Seth on 2005-07-06
Because it's not in Breezy yet. I'll see about getting .35.1 into Breezy today.

---

### Post by C.B. on 2005-07-09
How _exactly_ do I install the new version (.35) over the older Synaptic installed leaky memory version?

---

### Post by Seth on 2005-07-09
[QUOTE=C.B.]How _exactly_ do I install the new version (.35) over the older Synaptic installed leaky memory version?[/QUOTE]
 Download the file here.

Open a terminal and **cd** to the location you downloaded (e.g. **cd Desktop**)

Type **sudo dpkg -i gdesklets*.deb**

---

### Post by Seth on 2005-07-09
gdesklets 0.35.1-1 has now entered Breezy. Here is an updated backport for Hoary.

[http://www.sethkinast.com/ubuntu/hoary/backports/gdesklets_0.35.1-1~5.04ubp1_i386.deb](http://www.sethkinast.com/ubuntu/hoary/backports/gdesklets_0.35.1-1~5.04ubp1_i386.deb)

---

### Post by C.B. on 2005-07-09
Seth,

Thank you for instructions. Worked fine. Now, however, a couple of my desklets no longer work, but I think I read someting about possible compatibility issues with the newer gDesklets manager.

One other thing, not a big deal, but I've never been able to have desklets start automatically after bootup. I put "gdesklets" under  the Start tab of System/Prefs/Session as prescribed. The daemon seems to run but none of the desklet apps start. Any clues?
[color=red]edit: add  "gdesklets shell" to System/Preferences/Session
[/color]
Alright, two other things. When I'm running xcompmgr for 3D shadow and fading effects all desklet apps have borders and shadows even if I've deselected them individually in pref's. Is there a way to suppress?
[color=red]edit:
1. rt. click on gDesklet daemon in Notification Area.
2. Under Configuration, check the XComposite 'Translucency support' box
Note: If above is checked but XComposite isn't running, all your backgrounds will be dark/black.[/color]

Okay, three other things . . . but this really has to stop! I don't see any good gDesklet resources, forums, etc. even on gdesklets.org. Can anybody recommend?
[color=red]ed: Okay, found the forum . . . right there under my nose. :roll:[/color]

---

### Post by Seth on 2005-07-09
[QUOTE=C.B.]Seth,

Thank you for instructions. Worked fine. Now, however, a couple of my desklets no longer work, but I think I read someting about possible compatibility issues with the newer gDesklets manager.

One other thing, not a big deal, but I've never been able to have desklets start automatically after bootup. I put "gdesklets" under  the Start tab of System/Prefs/Session as prescribed. The daemon seems to run but none of the desklet apps start. Any clues?

Alright, two other things. When I'm running xcompmgr for 3D shadow and fading effects all desklet apps have borders and shadows even if I've deselected them individually in pref's. Is there a way to suppress?

Okay, three other things . . . but this really has to stop! I don't see any good gDesklet resources, forums, etc. even on gdesklets.org. Can anybody recommend?[/QUOTE]
 I can only answer the second question.

**gdesklets --translucent** will allow you to use xcompmgr and not have it apply to gDesklets.

---

### Post by neanderthal // anarchism on 2005-07-16
for some reason my firefox browser opens up with the homepage of some college and not google, like i had it on.

---

### Post by Chareos on 2005-07-27
[QUOTE=neanderthal // anarchism]for some reason my firefox browser opens up with the homepage of some college and not google, like i had it on.[/QUOTE]
 What about 0.35.2 ? It has the useful float feature, which makes StarterBar finally useful.

---

### Post by umdzig on 2005-07-29
[QUOTE=neanderthal // anarchism]for some reason my firefox browser opens up with the homepage of some college and not google, like i had it on.[/QUOTE]

I have the same issue with my starter bar. Anyone know how to fix this?

---

### Post by graabein on 2005-07-29
Oh, I know the answer to this one. Check your properties for the Firefox icon and remove the %u (or something) parameter after the execute command for Firefox. I did this at home for my moms account and that did the trick.

---

### Post by Stallone on 2005-08-06
Can anyone, like Seth, make a .deb file for the new version of 0.35.2?

Quote from [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/) :

> New in release 0.35.2:

[U][B]
   [COLOR=Red] * Float mode. Press a configurable key to bring your desklets to front temporarily![/COLOR][/B][/U]

    * Fixed the issue with broken "shelve" module on some systems (gentoo, *BSD)

    * Bug fixes

:)

---

### Post by Seth on 2005-08-06
[QUOTE=Stallone]Can anyone, like Seth, make a .deb file for the new version of 0.35.2?

Quote from [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/) :



:)[/QUOTE]
 Is that my name I hear?

[http://sethkinast.com/ubuntu/hoary/backports/gdesklets_0.35.2-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gdesklets_0.35.2-1~5.04ubp1_i386.deb)

Breezy-fresh. Do you need the -data package too? I remember it being buggy...
EDIT: Here it is anyway.
[http://sethkinast.com/ubuntu/hoary/backports/gdesklets-data_0.35.2-3_all.deb](http://sethkinast.com/ubuntu/hoary/backports/gdesklets-data_0.35.2-3_all.deb)

---

### Post by Kyral on 2005-08-06
Seth's version is more "official" than mine, so I'm gonna be (finally) clearing out my /workspace dir :D

GO WITH HIS PEOPLE!!

---

### Post by foxy123 on 2005-08-07
Thansk Seth. Just a word of warning, a new version breaks some of gdesklets, so I had to roll back to 0.35.1.

---

### Post by Seth on 2005-08-07
[QUOTE=foxy123]Thansk Seth. Just a word of warning, a new version breaks some of gdesklets, so I had to roll back to 0.35.1.[/QUOTE]
 Yeah, but that's the desklets' fault, so the backport is safe :)

---

### Post by graabein on 2005-08-11
I can't understand why gdesklets needs an icon in the notifier bar... Anyone?  :neutral:

---

### Post by Mastodront on 2005-08-11
Thanks for 0.35.2 Seth :)

Is anyone else besides me experiencing problems with the very nice float feature?
It works a couple of times but then it stops working. Doesn't freeze or anything, just nothing happens when I press the combination :/

---

### Post by Stallone on 2005-08-11
[QUOTE=Mastodront]Thanks for 0.35.2 Seth :)

Is anyone else besides me experiencing problems with the very nice float feature?
It works a couple of times but then it stops working. Doesn't freeze or anything, just nothing happens when I press the combination :/[/QUOTE]

Yeah, me too.... I suppose it is still a buggy version....

---

### Post by escariot on 2005-08-15
[QUOTE=graabein]I can't understand why gdesklets needs an icon in the notifier bar... Anyone?  :neutral:[/QUOTE]

Write it like this under sessions, to automagically start gdesklets without icon.

```
gdesklets --no-tray-icon
``` 

-Escariot

---

### Post by cutOff on 2005-08-15
[QUOTE=graabein]I can't understand why gdesklets needs an icon in the notifier bar... Anyone?  :neutral:[/QUOTE]
If you do right-click on the icon, you will see the 'preferences' item. Click it and you will be able to turn off the tray icon.

BTW thanks a lot Seth for the packages  ;-)

---

### Post by cutOff on 2005-08-15
[QUOTE=Mastodront]Thanks for 0.35.2 Seth :)

Is anyone else besides me experiencing problems with the very nice float feature?
It works a couple of times but then it stops working. Doesn't freeze or anything, just nothing happens when I press the combination :/[/QUOTE]
For the present never happened to me.

---

### Post by maxdevis on 2006-02-19
i still get a message by every gdesklet i install that he can't find the sensor, whil e it is there.

---

### Post by steve101101 on 2007-03-01
thanks for the advice to get gdesklets to work on the start up. it worked great.

---

