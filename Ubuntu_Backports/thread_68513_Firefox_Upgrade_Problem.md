---
title: "Firefox Upgrade Problem"
date: 2005-09-23
forum: Ubuntu Backports
---

### Post by acascianelli on 2005-09-23
Firefox 1.0.7 was just released into backports.  When I try to upgrade to it thru synaptic I get these errors...


---------------------------------
E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support
---------------------------------

...Anybody else getting these errors?  It broke firefox, I can not start it at all now.  I'm forced to use epiphany for now.

---

### Post by mtrythall on 2005-09-23
[QUOTE=acascianelli]Firefox 1.0.7 was just released into backports.  When I try to upgrade to it thru synaptic I get these errors...


---------------------------------
E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support
---------------------------------

...Anybody else getting these errors?  It broke firefox, I can not start it at all now.  I'm forced to use epiphany for now.[/QUOTE]

I'm having the same problem, and came here to see if anyone had a fix. Being as I have the DOM inspector, I also get a message about that (same thing, trying to overwrite it). Anyone have any suggestions?

---

### Post by sk545 on 2005-09-23
Yep, i had the same problem just now.  Its really stupid that they changed their package name from 'firefox' and 'firefox-gnome-support' to 'mozilla-firefox' and 'mozilla-firefox-gnome-support'.  I have no idea as to why they did this, but the update manager is telling you that you are trying to overwrite something in one package onto another which has the same files, and they just need to be updated.  The update manager isn't smart enough to tell that they are both the same packages.  Why they change the names?  Well, its Linux.  Its how things are sometimes.

Anyhow, to fix this mess, you have to remove the packages 'firefox' and 'firefox-gnome-support' first before installing the the update.  Don't expect that to go so easily if you already tried to update, since it messes up apt, and you will get errors.  Took me quite a while, and at the end i had to do this:

```
$ cd /var/cache/apt/archives
$ sudo dpkg -i --force-overwrite mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
$ sudo dpkg -i --force-overwrite mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb
$ sudo apt-get remove --purge firefox firefox-gnome-support 
```

Extremely dumb on the package maintainers part to change the names of the packages all of a sudden.

---

### Post by mtrythall on 2005-09-23
Just tried it, it works. I'm working through the DOM inspector problem now. Like I said, I got this error message:

> E: /var/cache/apt/archives/mozilla-firefox-dom-inspector_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/extensions/{641d8d09-7dda-4850-8228-ac0ab65e2ac9}/components/libinspector.so', which is also in package firefox-dom-inspector

I tried the commands you provided, replacing the package names (.debs) with the one the DOM inspector used. And then I just ran the purge using the old names. Worked like a charm, I'm now up-to-date.

Thanks again!

---

### Post by acascianelli on 2005-09-23
Worked here too...But now Epiphany is broken :(  But it's ok cause I got Firefox working again.

---

### Post by debaser13 on 2005-09-23
Alright, well, I ran the commands issued above and now Firefox in apt-get and symantic say it is up-to-date but I can't get it to work.  I can't install the dom-inspector stuff because it says it has unmet dependencies...any suggestions?

Thanks.

Carl

---

### Post by NabsS on 2005-09-23
I did something which worked. Here's what I did.
```
 
sudo apt-get update
sudo dpkg -r --force-all firefox
sudo dpkg -r --force-all firefox-gnome-support
sudo apt-get upgrade
*and, if asked*
sudo apt-get -f install

```

---

### Post by xavierh on 2005-09-23
[QUOTE=NabsS]I did something which worked. Here's what I did.
```
 
sudo apt-get update
sudo dpkg -r --force-all firefox
sudo dpkg -r --force-all firefox-gnome-support
sudo apt-get upgrade
*and, if asked*
sudo apt-get -f install

```[/QUOTE]

good post... I tested in on my of my vmware sessions and it works....

---

### Post by nubbe on 2005-09-23
[QUOTE=xavierh]good post... I tested in on my of my vmware sessions and it works....[/QUOTE]
 Worked for me on a "real" install...

---

### Post by petrol on 2005-09-23
I had to kill the firefox-bin process for it to work.

---

### Post by tag on 2005-09-23
@petrol: yep - looks like this is the key to success here. Killing the process after performing all above mentioned remove steps is the way to go.

Now - imagine the outcry if something like this would have happened on Microshaft.
Don't get me wrong, everybody makes mistakes, and i love ubuntu - but shouldn't there be at least an email warning about this issue? Or even better a rollback on the servers?

---

### Post by nubbe on 2005-09-23
[QUOTE=tag]@petrol: yep - looks like this is the key to success here. Killing the process after performing all above mentioned remove steps is the way to go.

Now - imagine the outcry if something like this would have happened on Microshaft.
Don't get me wrong, everybody makes mistakes, and i love ubuntu - but shouldn't there be at least an email warning about this issue? Or even better a rollback on the servers?[/QUOTE]
 I killed it before, and it worked fine.
Anyone know if this problem affects only "backports FF" or not?
(I had backports version)

---

### Post by coxc24 on 2005-09-23
This problem completly killed my Firefox. I ended up booting into Windows to see if there were any posts here.

Found this and now Firefox is sorted!

Thanks  :smile:

---

### Post by camp on 2005-09-23
Hi all!

What a wonderful community we are living in... we Linux nerds!

Thank you all, I got my running too now... from a little help of here and there...
I must confess, I had been touching on a lot of things to get it to work. But I knew that wasn't going to be a problem at all... we are a lot of brains here, and we always find our ways to help each other!

Why use another OS!?!?... Why even use another flavor of Linux!?   \\:D/  :grin: 

Have a nice weekend all!
/J.Camp

---

### Post by Mustard on 2005-09-24
Beautiful.  This worked like a charm

```
sudo apt-get update
sudo dpkg -r --force-all firefox
sudo dpkg -r --force-all firefox-gnome-support
sudo apt-get upgrade
and, if asked
sudo apt-get -f install
```
Kill firefox process
Restart firefox

---

### Post by chatuser on 2005-09-24
I completely agree Ubuntu marketing: "Linux for human beings"


What kind of human beings ?

---

### Post by vinx on 2005-09-24
I was not able to see this page because my browser ended up broken. 
I couldn't startup firefox 1.0.7 with 'firefox' but could with ' firefox --g-fatal-warnings'  :-?

---

### Post by nianhbg on 2005-09-24
[QUOTE=Mustard]Beautiful.  This worked like a charm

```
sudo apt-get update
sudo dpkg -r --force-all firefox
sudo dpkg -r --force-all firefox-gnome-support
sudo apt-get upgrade
and, if asked
sudo apt-get -f install
```
Kill firefox process
Restart firefox[/QUOTE]
 I did the long way removed the old firefox and restarted ubuntu then installed firefox 1.07 and its working

---

### Post by mlomker on 2005-09-24
> Extremely dumb on the package maintainers part to change the names of the packages all of a sudden.

It probably wasn't a mistake.  Backports are not quality tested to the same degree as the packages that are released with the operating system itself, so it'd be inappropriate to name it the same until it was thoroughly tried out on a lot of machines.  Otherwise you could have a lot of disabled PC's due to a bad package and forcing a package downgrade doesn't always work--I had to reinstall my machine once due to that very issue.

I ended up in this thread because one of the KDE users did this upgrade and now his system has problems.

---

### Post by GeneralZod on 2005-09-24
[QUOTE=mlomker]It probably wasn't a mistake.  Backports are not quality tested to the same degree as the packages that are released with the operating system itself, so it'd be inappropriate to name it the same until it was thoroughly tried out on a lot of machines. [/QUOTE]

According to Synaptic, and if I'm reading this right, 1.0.7 actually comes from hoary security.  Or does backports have its own security repository...?  Confusing! :D

[img]http://etotheipiplusone.com/firefox107.png[/img]

---

### Post by mlomker on 2005-09-24
[QUOTE=GeneralZod]According to Synaptic, and if I'm reading this right, 1.0.7 actually comes from hoary security. [/QUOTE]

That's true now, but if you read the original post of this thread it was in backports and has now been widely released through security.  Installing anything from backports has at least a modest risk because it hasn't been tested in a widespread manner yet (and that's assuming that the same people manage the repositories...often they may be entirely different packages because some backports projects are community managed while security is Ubuntu).

---

### Post by GeneralZod on 2005-09-24
[QUOTE=mlomker]That's true now, but if you read the original post of this thread it was in backports and has now been widely released through security.  Installing anything from backports has at least a modest risk because it hasn't been tested in a widespread manner yet (and that's assuming that the same people manage the repositories...often they may be entirely different packages because some backports projects are community managed while security is Ubuntu).[/QUOTE]

Ah, I see - thanks for the info! :)

---

### Post by ppl on 2005-09-24
[QUOTE=NabsS]I did something which worked. Here's what I did.
```
 
sudo apt-get update
sudo dpkg -r --force-all firefox
sudo dpkg -r --force-all firefox-gnome-support
sudo apt-get upgrade
*and, if asked*
sudo apt-get -f install

```[/QUOTE]

It works now, great!
But I am such a fool!, I forget backup my bookmarks, and by doing so ,I lost all my books marks ](*,)

---

### Post by mlomker on 2005-09-24
[QUOTE=ppl]It works now, great!
But I am such a fool!, I forget backup my bookmarks, and by doing so ,I lost all my books marks ](*,)[/QUOTE]

Naw, they're probably just in the wrong directory now because the backports version of Firefox installs to a different place.

Try this:

```

sudo updatedb
locate bookmarks.html

```

---

### Post by jadugarr on 2005-09-24
[QUOTE=NabsS]I did something which worked. Here's what I did.
```
 
sudo apt-get update
sudo dpkg -r --force-all firefox
sudo dpkg -r --force-all firefox-gnome-support
sudo apt-get upgrade
*and, if asked*
sudo apt-get -f install

```[/QUOTE]

I did this and it fixed my firefox problem like everyone else.  It also broke epiphany though, which I use occasionally.  Anyone have any idea how to reinstall ephiphany?

---

### Post by ppl on 2005-09-24
[QUOTE=mlomker]Naw, they're probably just in the wrong directory now because the backports version of Firefox installs to a different place.

Try this:

```

sudo updatedb
locate bookmarks.html

```[/QUOTE]

Sorry, I gave the wrong information, the bookmarks are back again after a soft restart of Ubuntu. But you probably right about different place, because after I successfully updated my Firefox, before restart, I can't run it by click the icon on the gnome panel, buy I can start it  from command line. Anyway I am happy again, :grin: !

---

### Post by ppl on 2005-09-24
[QUOTE=jadugarr]I did this and it fixed my firefox problem like everyone else.  It also broke epiphany though, which I use occasionally.  Anyone have any idea how to reinstall ephiphany?[/QUOTE]

What happed if u try to reinstall Epiphany by command line or synaptic?

---

### Post by xavierh on 2005-09-24
[QUOTE=mlomker]Naw, they're probably just in the wrong directory now because the backports version of Firefox installs to a different place.

Try this:

```

sudo updatedb
locate bookmarks.html

```[/QUOTE]

this is strange I did not loose my bookmarks....

---

### Post by jadugarr on 2005-09-24
[QUOTE=ppl]What happed if u try to reinstall Epiphany by command line or synaptic?[/QUOTE]
It says that ephiphany-browser depends on firefox.  I haven't tried doing a force install though.

---

### Post by Cloud[01] on 2005-09-24
Here is my walk-through:

```

sudo apt-get remove mozilla-firefox mozilla-firefox-gnome-support
sudo apt-get update
sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support

```

hope it helps :P

ciop ciop

---

### Post by plm99 on 2005-09-24
Worked for me as well. I wonder if I had killed firefox.bin in the first place, the synaptic upgrade would have worked?

---

### Post by nubbe on 2005-09-27
[QUOTE=plm99]Worked for me as well. I wonder if I had killed firefox.bin in the first place, the synaptic upgrade would have worked?[/QUOTE]

no, so don't beat urself up  ;)

---

### Post by jdong on 2005-09-27
Alright, guys, here's the deal:

This problem happened because the Ubuntu Security Team took a turn no Backports developer imagined: shipped a newer version of a package (1.0.7 vs 1.0.2) after a stable release!


This problem has been solved in hoary-backports-staging, and is pending approval for hoary-backports.

---

### Post by Sionide on 2005-09-27
Ah, fixed it - thanks everyone.

---

### Post by beeldings on 2005-09-27
I followed the instructions and I was able to upgrade/restore Firefox on my system. However, because I had to remove firefox and firefox-gnome-support, firefox-dev was also removed. I need the firefox-dev package in order to properly install mplayerplug-in 3.11 (as mentioned in [christooss's thread](http://www.ubuntuforums.org/showthread.php?t=60505&highlight=mplayer+3.11)). So, when I attempt to install firefox-dev after removing both firefox and firefox-gnome-support, apt-get wants to also install firefox, but since I already have mozilla-firefox installed, the cycle repeats itself and I am once again presented with the upgrade error. Does anyone know of a solution to this problem or when I can download a .deb of firefox-dev which is not dependent on the firefox package? I am running Hoary on an x86 using both the mirrormax and official backports repositories, perhaps this is causing the problem?

---

### Post by jdong on 2005-09-27
hoary-backports should be fixed now...
perform a dist-upgrade again.

---

### Post by niels on 2005-09-27
I just tryed the thing at the quote, but when I run mozilla-firefow I get the following error

XML Parsing Error: xml processing instruction not at start of external entity Location: chrome://mozapps/content/profile/profileSelection.xul
Line Number 1, Column 1:

What is this?

I still have the firefox in /usr/bin/, and when I try to run this I get the same error...

[QUOTE=sk545]Yep, i had the same problem just now.  Its really stupid that they changed their package name from 'firefox' and 'firefox-gnome-support' to 'mozilla-firefox' and 'mozilla-firefox-gnome-support'.  I have no idea as to why they did this, but the update manager is telling you that you are trying to overwrite something in one package onto another which has the same files, and they just need to be updated.  The update manager isn't smart enough to tell that they are both the same packages.  Why they change the names?  Well, its Linux.  Its how things are sometimes.

Anyhow, to fix this mess, you have to remove the packages 'firefox' and 'firefox-gnome-support' first before installing the the update.  Don't expect that to go so easily if you already tried to update, since it messes up apt, and you will get errors.  Took me quite a while, and at the end i had to do this:

```
$ cd /var/cache/apt/archives
$ sudo dpkg -i --force-overwrite mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
$ sudo dpkg -i --force-overwrite mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb
$ sudo apt-get remove --purge firefox firefox-gnome-support 
```

Extremely dumb on the package maintainers part to change the names of the packages all of a sudden.[/QUOTE]

---

### Post by themindlessmatt on 2005-09-27
[QUOTE=niels]I just tryed the thing at the quote, but when I run mozilla-firefow I get the following error

XML Parsing Error: xml processing instruction not at start of external entity Location: chrome://mozapps/content/profile/profileSelection.xul
Line Number 1, Column 1:

What is this?

I still have the firefox in /usr/bin/, and when I try to run this I get the same error...[/QUOTE]

Got the same error. Fixed it with killing firefox-bin, then repeated the

$ sudo dpkg -i --force-overwrite mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
$ sudo dpkg -i --force-overwrite mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb

lines to reinstall firefox. Worked for me, may be a simpler solution....

---

### Post by niels on 2005-09-27
[QUOTE=themindlessmatt]Got the same error. Fixed it with killing firefox-bin, then repeated the

$ sudo dpkg -i --force-overwrite mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
$ sudo dpkg -i --force-overwrite mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb

lines to reinstall firefox. Worked for me, may be a simpler solution....[/QUOTE]
YES - it worked!

Thanks a LOT!

---

### Post by jdong on 2005-09-29
[QUOTE=themindlessmatt]Got the same error. Fixed it with killing firefox-bin, then repeated the
$ sudo dpkg -i --force-overwrite mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
$ sudo dpkg -i --force-overwrite mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb
lines to reinstall firefox. Worked for me, may be a simpler solution....[/QUOTE]

Just killing firefox-bin should've done it -- typically this happens when you upgrade with firefox open.

---

