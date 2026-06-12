---
title: "GASP... a BACKPORT????"
date: 2005-07-25
forum: The Cafe
---

### Post by jdong on 2005-07-25
[http://ubuntuforums.org/showthread.php?p=271702](http://ubuntuforums.org/showthread.php?p=271702)


Did everyone catch that? The Ubuntu Security Team released firefox 1.0.6 for Ubuntu as an.... OFFICIAL PACKAGE?

---

### Post by TravisNewman on 2005-07-25
Rock on, this shows that they can see the need for new packages in certain situations.

I must admit I'm a bit surprised, but woohoo!

---

### Post by Kvark on 2005-07-25
Uhh, yes, they do release security fixes and updates even for releases that are already "released". Otherwise it would kinda suck for the users, to have to wait until the next release to get up to date security. ...whats the surpricing part here?

---

### Post by DJ_Max on 2005-07-25
[QUOTE=Kvark]Uhh, yes, they do release security fixes and updates even for releases that are already "released". Otherwise it would kinda suck for the users, to have to wait until the next release to get up to date security. ...whats the surpricing part here?[/QUOTE]
 They patch security updates only, without features, so thats why the version number doesn't change. But in this case, they were having problems due to the API change, so they had no choice.

---

### Post by poofyhairguy on 2005-07-25
Kick ass.

Probably a rarity though.

---

### Post by bored2k on 2005-07-25
A day after I whiped Ubuntu Firefox and got the official package. Grr

---

### Post by jdong on 2005-07-25
[QUOTE=bored2k]A day after I whiped Ubuntu Firefox and got the official package. Grr[/QUOTE]

ya know, a bit of patient saves a lot of hassle!

---

### Post by bored2k on 2005-07-25
[QUOTE=jdong]ya know, a bit of patient saves a lot of hassle![/QUOTE]
 Apparently, patience is a virtue I still haven't developed throughly.

---

### Post by jdong on 2005-07-25
[QUOTE=bored2k]Apparently, patience is a virtue I still haven't developed throughly.[/QUOTE]

well, THAT explains a lot!

(j/k ;) )

---

### Post by NeoChaosX on 2005-07-25
Word of warning: if you have Backports enabled, downgrade the mozilla-firefox packages and get rid of the current firefox Backport packages, because this update [causes havoc](http://ubuntuforums.org/showthread.php?t=51931) if you don't.

---

### Post by poofyhairguy on 2005-07-25
[QUOTE=NeoChaosX]Word of warning: if you have Backports enabled, downgrade the mozilla-firefox packages and get rid of the current firefox Backport packages, because this update [causes havoc](http://ubuntuforums.org/showthread.php?t=51931) if you don't.[/QUOTE]

Damn. Hey jdong, can you just delete your old package to prevent future problems?

---

### Post by jdong on 2005-07-25
[QUOTE=poofyhairguy]Damn. Hey jdong, can you just delete your old package to prevent future problems?[/QUOTE]

Too late, takes an uninstall+reinstall to fix.


I did bump a newer firefox to stable, which should in theory solve this. I'm not at a Ubuntu box right now. Is there still a conflict after an apt-get update and a dist-upgrade?

If so, reply back with full error.

---

### Post by ubuntu_demon on 2005-07-25
[QUOTE=jdong]Too late, takes an uninstall+reinstall to fix.


I did bump a newer firefox to stable, which should in theory solve this. I'm not at a Ubuntu box right now. Is there still a conflict after an apt-get update and a dist-upgrade?

If so, reply back with full error.[/QUOTE]

It's really cool that they backported firefox!!!

I got backports + staging enabled and I don't have any problems

---

### Post by TravisNewman on 2005-07-25
So is this new package in backports the same as the official Ubuntu package, just in backports format?

---

### Post by NeoChaosX on 2005-07-25
jdong: The new stable firefox package worked for me.

---

### Post by UbuWu on 2005-07-26
Great! Everything secure and working at the same time again!

---

### Post by benplaut on 2005-07-26
am i missing something? i haven't gotten wind of either the faulty or legit updates...

something is wrong...

---

### Post by bored2k on 2005-07-26
[QUOTE=benplaut]am i missing something? i haven't gotten wind of either the faulty or legit updates...

something is wrong...[/QUOTE]
 I thought I was the only one _not_ getting any errors at all. Me and the french cookie monster who eats Croissants have not :D.

---

### Post by Burgundavia on 2005-07-26
They backported the package because FF is so screwed anyway that they might as well. 

Mainly this is a mozilla issue with out-of-tree extensions.

Corey

---

### Post by Ubunted on 2005-07-26
After hearing about problems with conflicts, I took the following steps when updating to 1.0.6:

1: Open and reload Update Manager
2: Removed Firefox from the Add or Remove Programs menu.
3: Applied the updates in Update Manager without closing it.
4: Verified FIrefox was indeed marked as installed again in Add or Remove Programs
5: Booted it up and came here.

Everything's working just dandy so far. :)

---

### Post by thecrimsonking on 2005-07-26
Firefox 1.06 did not show up until this morning in the backports mirror I use.  I did not uninstall Firefox before I used Ubuntu Update Manager and have had no problems.

---

### Post by wmcbrine on 2005-07-26
Hooray! And, about time! See how easy that was? Now, why oh why didn't they do this for 1.0.3, 1.0.4 and 1.0.5?

BTW, Ubuntu's security patches for Firefox were never complete. I know because one of the security changes in mainstream FF broke the "Remove Selection" functionality of the Nuke Anything extension, but it never broke in the Ubuntu version, until now. (There's an updated NA to restore it.)

---

### Post by poofyhairguy on 2005-07-26
[QUOTE=wmcbrine]Hooray! And, about time! See how easy that was? Now, why oh why didn't they do this for 1.0.3, 1.0.4 and 1.0.5?
[/QUOTE]

If you think this is establishing precedent, you will b disappointed.

---

### Post by poofyhairguy on 2005-07-26
[QUOTE=wmcbrine]Hooray! And, about time! See how easy that was? Now, why oh why didn't they do this for 1.0.3, 1.0.4 and 1.0.5?
[/QUOTE]

If you think this is establishing precedent, you will be disappointed.

---

### Post by UbuWu on 2005-07-26
[QUOTE=wmcbrine]BTW, Ubuntu's security patches for Firefox were never complete. I know because one of the security changes in mainstream FF broke the "Remove Selection" functionality of the Nuke Anything extension, but it never broke in the Ubuntu version, until now. (There's an updated NA to restore it.)[/QUOTE]

Or the Ubuntu team did a better job integrating the security patches... (don't know which one is true...)

---

### Post by mike998 on 2005-07-27
This is sweet!

Good work ladies and gents!

---

### Post by DJ_Max on 2005-07-27
[QUOTE=UbuWu]Or the Ubuntu team did a better job integrating the security patches... (don't know which one is true...)[/QUOTE]
 I'm thinking the samething. It's not always that developers just update or patch security fixes, Firefox is open source, so you can fix bugs and 'port' the software for your system.

---

