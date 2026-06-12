---
title: "OpenOffice 2.0.0 final out!"
date: 2005-10-19
forum: The Cafe
---

### Post by topcop on 2005-10-19
[ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/stable/2.0.0/](ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/stable/2.0.0/)

:)

---

### Post by tseliot on 2005-10-19
Are you sure it's not  a Release Candidate (RC)?

---

### Post by benplaut on 2005-10-19
whoa... that's... sudden!

if it's true

---

### Post by Sirin on 2005-10-19
Check out their official website.

[http://www.openoffice.org/](http://www.openoffice.org/)

It's just a hoax. [img]http://ubuntuforums.org/images/icons/icon12.gif[/img]

---

### Post by BWF89 on 2005-10-19
You had me all excited when you said that. Oh well, atleast Firefox 1.5 will be coming out later this month.

---

### Post by topcop on 2005-10-19
[QUOTE=Sirin]Check out their official website.

[http://www.openoffice.org/](http://www.openoffice.org/)

It's just a hoax. [img]http://ubuntuforums.org/images/icons/icon12.gif[/img][/QUOTE]
No its not necessarily a hoax, the announcement may come later, a lot of times a RC is labeled as a final if its stable. if you check this is the stable folder, RC is in another folder here: [ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/contrib/rc/2.0.0rc3/](ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/contrib/rc/2.0.0rc3/)

and they seem to be the same size so infact RC3 may be labelled as final

---

### Post by MakubeX on 2005-10-19
I have a team which is building/recompiling OO 2.0 Beta source for my university..

We are monitoring this site: [http://blog.janik.cz/archives/cat_1.html](http://blog.janik.cz/archives/cat_1.html)

So is that it? I can't wait to get the source! rofl.

---

### Post by Lovechild on 2005-10-19
To late, I switched to GNOME Office, it's faster, prettier and provides me with the features I need. Now all I need is a presenter application, crawips looks promising.

---

### Post by Goober on 2005-10-19
Just wondering, will the Ubuntu Update thingie (the little red button that comes up when there are Updates) have the Udate for OOo2 for us to just DL and install automatically when it comes out?  Or will we have to do it through the Command Line or Synaptic?

What about Firefox 1.5?

---

### Post by Lovechild on 2005-10-19
OpenOffice might be a tad bit to update in deployed and tested environments - backports might carry it, if you bribe jdong I guess.

---

### Post by jdong on 2005-10-19
[QUOTE=Lovechild]OpenOffice might be a tad bit to update in deployed and tested environments - backports might carry it, if you bribe jdong I guess.[/QUOTE]

The chances of Ubuntu releasing official breezy-updates for Openoffice are slim to impossible.

As far as Backports, this depends on many factors:

(1) The opening of the Dapper Tree
(2) How long it takes the devs to upload 2.0 to Dapper
(3) Whether or not that will compile well under Breezy
(3a) The time to accept/review patches towards the successful backporting of Openoffice
(4) How stable the compiled package will be.


Again, the incentive to update has to be measured -- are the last few bugfixes trickling in worth the man-hours in backporting and (more significantly) maintaining the backports against security fixes and such? Only time will tell :)

---

### Post by benplaut on 2005-10-19
any way to backport a patch, or does the entire behemoth have to be uploaded?

---

### Post by jdong on 2005-10-19
[QUOTE=benplaut]any way to backport a patch, or does the entire behemoth have to be uploaded?[/QUOTE]
whole thing... we don't have the architecture to generate differential patches ("hotfixes"), unlike SuSE's deltarpms.

---

### Post by fsman on 2005-10-20
Why wouldn't 2.0 final be issued as part of the standard distribution a la firefox going 1.05 - 1.07?

The difference between the version supplied by the offical breezy and final will be bug fixes so surely. Given that the reason OOo delayed was due to a major bug I would hope that Breezy is updated to avoid showstoppers identified by OO.

If Ubuntu is going to make it as a desktop replacement, then a fully functional office suite is going to be essential.

---

### Post by GeneralZod on 2005-10-20
[QUOTE=jdong]whole thing... we don't have the architecture to generate differential patches ("hotfixes"), unlike SuSE's deltarpms.[/QUOTE]

Just out of interest, do you happen to know if Ubuntu has any plans to incorporate this kind of technology into future releases? I know it is would be a major change, but developing nations that have only slow dial-up connections could benefit greatly from it.

---

### Post by UbuWu on 2005-10-20
It is now official on th [http://www.openoffice.org](http://www.openoffice.org) front site.  Also a nice read:
[http://www.madpenguin.org/cms/?m=show&id=5370](http://www.madpenguin.org/cms/?m=show&id=5370)

---

### Post by Lovechild on 2005-10-20
[QUOTE=GeneralZod]Just out of interest, do you happen to know if Ubuntu has any plans to incorporate this kind of technology into future releases? I know it is would be a major change, but developing nations that have only slow dial-up connections could benefit greatly from it.[/QUOTE]

It's not my impression that Debian has this kind of functionality on the drawing board - and I'm told the SuSE delta rpm patch is really ugly so I'm betting that's why.

Sad for people in the developing world without broadband, but if that's a general issue bundling tested upgrade CDs might be an option.. that's a nice little project for someone.

---

### Post by Hg80 on 2005-10-20
Nice to see its offical, been using beta version with no problems

---

### Post by Master Shake on 2005-10-20
Is it in the repositories yet?  If so, I know what I'm doing tonight. :)

---

### Post by poofyhairguy on 2005-10-20
[QUOTE=fsman]Why wouldn't 2.0 final be issued as part of the standard distribution a la firefox going 1.05 - 1.07?

The difference between the version supplied by the offical breezy and final will be bug fixes so surely. Given that the reason OOo delayed was due to a major bug I would hope that Breezy is updated to avoid showstoppers identified by OO.

If Ubuntu is going to make it as a desktop replacement, then a fully functional office suite is going to be essential.[/QUOTE]

Firefox was upgraded for security problems, not bug fixes. Outside of backports, applications are only updated in Ubuntu because of security problems.

Unless the new version fixes a security flaw, I can almost promise you won't see the final version in the main Breezy repo. But its ok, the version included works fine and Dapper is only six months away and it WILL have the newest OO.org.

By the way, what is Ubuntu a replacement for?

---

### Post by jdong on 2005-10-20
[QUOTE=GeneralZod]Just out of interest, do you happen to know if Ubuntu has any plans to incorporate this kind of technology into future releases? I know it is would be a major change, but developing nations that have only slow dial-up connections could benefit greatly from it.[/QUOTE]

No, I don't know of any plans. I do know they plan to switch .debs over from gzip compression to bzip2 compression, which definitely reduces sizes of packages significantly.


As a SuSE user, too, I do agree with you that delta packages are very valuable for updates -- an OOo security patch that's 80MB under Ubuntu is fixed in SuSE as a 500KB patch.


The complicity of implementing this on Ubuntu shoudn't be that bad -- just some more work at the apt-get level (dpkg+1 level abstraction)

---

### Post by bugmenot on 2005-10-23
I think this aspect of debianess (no updates, and even if someone actually does it, it's friggin big) is what ubuntu should drop first (i heard they are going to be binary incompatible anyway). Those things are of much more consequence to desktop users than LVM and the like. 
It has happened to firefox, now it happens to OOo. I think it might kill the whole project, especially in the light of SuSE going open.
I mean, come on, desktop replacement with beta office software that was delayed because of a bug?
I don't think so.
And as a developer I'd like to add that the java support leaves much to be desired, GCJ is not something a serious project can put up with.
GCJ is not better for running up-to-date Java apps (which will be using Swing) than mono is for Windows.Forms (=bad, hardly ever runs).
Also the sound in UT needs to be fixed. But I disgress.

---

### Post by poofyhairguy on 2005-10-23
[QUOTE=bugmenot]I think this aspect of debianess (no updates, and even if someone actually does it, it's friggin big) is what ubuntu should drop first (i heard they are going to be binary incompatible anyway). [/QUOTE]

1. We have backports.

2. Many Ubuntu users have broadband.

---

