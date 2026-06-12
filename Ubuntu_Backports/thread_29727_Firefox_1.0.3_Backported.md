---
title: "Firefox 1.0.3 Backported"
date: 2005-04-25
forum: Ubuntu Backports
---

### Post by jdong on 2005-04-25
OK, I got the latest FF 1.0.3 from Sid and backported. It's currently uploading as Revision 125 to the tree [being the first commit to the BSD-powered tree], and will take a bit of time.

A few things to remember:
[list]
[*]This is a **Debian** style Firefox 1.0.3, which may not match with Ubuntu's Firefox. Watch for settings/plugins that have trouble (I don't expect any)   
[*]GNOME integration is unavailable -- those GNOME2 style file selectors aren't in Debian's source, and as a result will NOT be available for Firefox. Besides, I found them unstable [segfaults when using autocomplete] and bothersome [KDE fan here :)] 
[/list] Please test and report back.

---

### Post by jdong on 2005-04-25
Confirmed by me to work :)

---

### Post by Turin Turambar on 2005-04-25
But there's a gnome-support 1.0.3 package available on debian site?!

---

### Post by jdong on 2005-04-25
The firefox-gnome-support package integrates Firefox as a GNOME browser by allowing it to be set as the default browser and associating html files and URL's with Firefox from Nautilus.

The f-g-s package does **NOT** provide the GNOME2 file selector dialogs -- that's compiled into the mozilla-firefox package. It add unnecessary GNOME dependencies into Firefox.

---

### Post by TravisNewman on 2005-04-25
Personally, I'm happy that it doesn't have the gnome2 file selector dialogs. I love gnome, but between warty and hoary, those dialogs got screwy, as I've posted elsewhere. Trying this out now :)

---

### Post by Virtual DarKness on 2005-04-25
[QUOTE=panickedthumb]Personally, I'm happy that it doesn't have the gnome2 file selector dialogs. I love gnome, but between warty and hoary, those dialogs got screwy, as I've posted elsewhere. Trying this out now :)[/QUOTE]
 me too ;)

bye,
Giovanni.

---

### Post by TravisNewman on 2005-04-25
Huh. All the fonts seem to look better in this one.

---

### Post by NeoChaosX on 2005-04-25
Wait, I just did an apt-get update, and I can't upgrade. Is it only avalible in staging, or what?

---

### Post by ow50 on 2005-04-25
Epiphany doesn't work anymore.

```
$ epiphany
epiphany: error while loading shared libraries: libgtkembedmoz.so: cannot open shared object file: No such file or directory
```

It can be verified with that locate that the file indeed doesn't exist anymore after upgrading.

I built firefox from the same debian source myself earlier today and had the same problem.

Note that the latest version of Epiphany is 1.6.2 while Hoary has 1.6.1. Also, Ubuntu's Epiphany depends on mozilla-firefox while Debian's Epiphany seems to depend on mozilla-browser.

---

### Post by TravisNewman on 2005-04-25
Same here-- no more epiphany. I DO have mozilla-browser installed as well.

Epiphany had the same security issue though, any chance of getting that one backported jdong?
No benefit to me, as I only have epiphany for testing things, but others who want to use both may need it.

---

### Post by jdong on 2005-04-25
1.0.3 is still Staging. As shown by the last two people, there are issues (reverse dependency breakage) with this backport.


Ok, I'm investigating on the Epiphany issue. It seems to be a classic reverse dependency breakage, but usually you don't get missing stuff in that case.


I'll also try to get the latest Epiphany while I'm at it!

---

### Post by XDevHald on 2005-04-25
Some one call the webulances;! I think we have a connector down on the backports!!!

This thing is SO SLOW! lol, it's running anywhere from 915 bs to 1400 bs, that is REALLY slow.

I think I have enough to time to go out to eat for a few hours lol, that's not e ajoke either :p

---

### Post by ubuntu-geek on 2005-04-25
[QUOTE=BB]Some one call the webulances;! I think we have a connector down on the backports!!!

This thing is SO SLOW! lol, it's running anywhere from 915 bs to 1400 bs, that is REALLY slow.

I think I have enough to time to go out to eat for a few hours lol, that's not e ajoke either :p[/QUOTE]
 lol I seem to be causing some rucas with my traffic shaping rules eh? :P

---

### Post by ubuntu-geek on 2005-04-25
Do you notice any speedy increase now?

---

### Post by XDevHald on 2005-04-25
[QUOTE=ubuntu-geek]Do you notice any speedy increase now?[/QUOTE]


Yeah :grin: much better! but...

I have this ---> Error W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages)

I'll let you slide on this error, for now [-X

---

### Post by jdong on 2005-04-25
Ok, there appears to be a "mozilla-firefox-dev" package that Ubuntu's Firefox package creates.

Now, we have some options:

(1) Find the patchcode responsible for generating the mozilla-firefox-dev package

(2) Forcibly apply the Ubuntu 1.0.2 patch onto Firefox 1.0.3, and worry about build issues as they come.

(3) Wait for 1.0.3 in Breezy.

In the meantime, what should we do with this Firefox package:

(1) Keep it in staging and don't promote it, as it breaks Epiphany and any other m-f-dev reliant packages.
(2) Pull it from staging
(3) Promote it because the security benefits outweigh the broken browser


I'm also considering adding "Conflicts: epiphany-browser" to the control file, which would remove epiphany if you upgraded to this backport.

---

### Post by jdong on 2005-04-25
I've gone with forced patching for now.... Rebuilding.

---

### Post by Turin Turambar on 2005-04-25
After the mess I had with FF when manually tried to install debian packages, I decide to stick with 1.0.2....

---

### Post by jdong on 2005-04-25
I'm pleased to announce that patching 1.0.2 Ubuntu diffs onto 1.0.3 did compile cleanly. I'm currently uploading this backport to the Staging area for testing.


I anticipate this will be just as stable as Firefox 1.0.2 official. Please also advise if epiphany is still broken.

Currently uploading, may take a few minutes before it hits the server.

---

### Post by TravisNewman on 2005-04-25
Well, it seems to work quite well, and epiphany now works.

---

### Post by jdong on 2005-04-26
Yep, likewise. I'll promote this today if nobody complains.

---

### Post by ow50 on 2005-04-26
Works well, Epiphany too.

---

### Post by donar73 on 2005-04-26
Works well for me too!  \\:D/  (Haven't installed Epiphany - so I couldn't test this)

Thank's alot for your great work!!!

---

### Post by jdong on 2005-04-26
bumped to stable. Security fixes do not have to go through the mandatory 7-day staging period. All you Hoary users, your Firefox is safe to use once again :) :)

---

### Post by XDevHald on 2005-04-26
Ah, such a lovely day for backports, great job as usual jdong!!

---

### Post by Turin Turambar on 2005-04-26
Great job indeed! Thanks! :)

---

### Post by IdoMcFly on 2005-04-27
I've tried the Secunia test and it seems to be ok though I got "XXXXXX" output in the test. (In windows, 1.0.3 don't output anything)

---

### Post by jdong on 2005-04-27
Hmm, I have no idea what causes that.


Does anyone else have this issue?

---

### Post by Turin Turambar on 2005-04-27
I also got a XXXX displayed...

---

### Post by wolovids on 2005-04-27
If the bug is fixed, you WILL get XXXXX outputted.  Otherwise, you'd see random printable characters from firefox's memory.  

I'm using Firefox 1.0.3 under WinXP right now and it displays XXXXX's.

In other words, the bug is fixed in the backport.  Things seem to be working great.  Thanks jdong!

---

### Post by IdoMcFly on 2005-04-27
ok my bad : I got *white* XXX on XP... :D

---

### Post by Turin Turambar on 2005-04-27
[QUOTE=wolovids]If the bug is fixed, you WILL get XXXXX outputted.  Otherwise, you'd see random printable characters from firefox's memory.  

I'm using Firefox 1.0.3 under WinXP right now and it displays XXXXX's.

In other words, the bug is fixed in the backport.  Things seem to be working great.  Thanks jdong![/QUOTE]

But I also got XXXXX displayed in 1.0.2 !  :? 

I just opened the JavaScript console and found this message:

XML Parsing Error: no element found
Location: jar:resource:///chrome/toolkit.jar!/content/mozapps/update/updates.xml
Line Number 1, Column 1:

What is that? Maybe that's why I had XXXX displayed in 1.0.2.

---

### Post by wolovids on 2005-04-27
[QUOTE=Turin Turambar]But I also got XXXXX displayed in 1.0.2 !  :? 

I just opened the JavaScript console and found this message:

XML Parsing Error: no element found
Location: jar:resource:///chrome/toolkit.jar!/content/mozapps/update/updates.xml
Line Number 1, Column 1:

What is that? Maybe that's why I had XXXX displayed in 1.0.2.[/QUOTE]
Try it a few times.  After a while it'll change and start outputting stuff in Firefox's memory.

The XML parsing error (I believe) is an error due to the removal of the automatic update mechanism in ubuntu/debian's build of Firefox.  It's nothing to worry about.

---

### Post by deathburger on 2005-04-28
[QUOTE=jdong]All you Hoary users, your Firefox is safe to use once again[/QUOTE]

And Warty? I thought backports for it were going to continue...?

---

### Post by deathburger on 2005-05-10
[QUOTE=deathburger]And Warty? I thought backports for it were going to continue...?[/QUOTE]
Anyone? Bueller?

---

### Post by jdong on 2005-05-11
[QUOTE=deathburger]Anyone? Bueller?[/QUOTE]

I made it quite clear before that Backports will only be provided for the **latest stable Ubuntu release**. I don't have the time to do twice the amount of compiling, not mentioning that new library dependencies make it increasingly more difficult to support older releases. Sorry.

---

### Post by deathburger on 2005-05-11
[QUOTE=jdong]I made it quite clear before that Backports will only be provided for the **latest stable Ubuntu release**. I don't have the time to do twice the amount of compiling, not mentioning that new library dependencies make it increasingly more difficult to support older releases. Sorry.[/QUOTE]
1.0.4 compiled fine and dandy for me. And no need to get pissy with me about it, I wasn't rude to you.

Thank you for the reply though, at least I know the official support stance, that being I'm on my own.

---

### Post by jdong on 2005-05-11
Sorry, I wasn't trying to be rude :)

You got to understand, I simply don't have the time to support two releases.

---

### Post by deathburger on 2005-05-11
[QUOTE=jdong]Sorry, I wasn't trying to be rude :)

You got to understand, I simply don't have the time to support two releases.[/QUOTE]
No problem. I don't mind doing FF myself, I just needed to know what the Warty backports stand on it was before replacing it with one I've compiled... until I can upgrade to the newer Ubuntu release, that is.

In case I haven't mentioned it previously, the backports rock. Thanks. :)

---

### Post by kleeman on 2005-05-11
Sorry if this has already been covered: Today there was a security release in Ubuntu for 1.0.2 fixing two "critical" vulnerabilities. As I understand it 1.0.3 in backports is also affected by these vulnerabilities. Will this security fix be implemented in backports or for safety should we revert to the updated 1.0.2?

---

### Post by nocturn on 2005-05-12
The security fixes that went into 1.0.2 where taken from 1.0.3, so you are fine.
It seems 1.0.4 released today (fixing a new, currently non-exploitable issue).

---

### Post by hda on 2005-05-12
[QUOTE=nocturn]The security fixes that went into 1.0.2 where taken from 1.0.3, so you are fine.
It seems 1.0.4 released today (fixing a new, currently non-exploitable issue).[/QUOTE]

Not quite. With the current version in backports that exploit [here](http://www.heise.de/security/dienste/browsercheck/demos/nc/mozdemo3.shtml)  still works. :-(

---

### Post by nocturn on 2005-05-12
[QUOTE=hda]Not quite. With the current version in backports that exploit [here](http://www.heise.de/security/dienste/browsercheck/demos/nc/mozdemo3.shtml)  still works. :-([/QUOTE]

Well, I didn't understand much of it (it's in German), but this seems the vuln with the software install in FF.  This issue was recenty discovered after the 1.0.3 release (is not exploitable any more thanks to the mozilla.org site maintainers).

The fix for this is in 1.0.4 (released today).

Jdong will probably have a backport within days.

---

### Post by deathburger on 2005-05-12
[QUOTE=nocturn]The fix for this is in 1.0.4 (released today).[/QUOTE]
I'm using a CVS build, which I pulled just a couple days ago.. still vulnerable. Maybe something made it in in the last second?

---

### Post by fishfork on 2005-05-12
I'm using the backported 1.0.3 at the moment. Automatic Update has just told me there are two new packages available of libnspr4 and libnss3, which seem to be related to firefox. Is it OK to install them, or will they cause proplems?

Ben

---

### Post by fng on 2005-05-12
I instelled them, didnt experience any problems.

---

### Post by A-star on 2005-05-12
[QUOTE=fng]I instelled them, didnt experience any problems.[/QUOTE]
Same here, no problems at all.

---

### Post by kleeman on 2005-05-12
Oh by the way Happy Birthday John and thank you for all your efforts with backports!  :smile:  :smile:  :smile:

---

