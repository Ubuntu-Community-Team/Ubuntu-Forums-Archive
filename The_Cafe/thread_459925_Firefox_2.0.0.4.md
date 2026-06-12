---
title: "Firefox 2.0.0.4"
date: 2007-05-31
forum: The Cafe
---

### Post by _simon_ on 2007-05-31
Haven't seen it mentioned yet, so just to let you know it was released on 30th May.

[http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/)

Fixed in Firefox 2.0.0.4
MFSA 2007-17 XUL Popup Spoofing
MFSA 2007-16 XSS using addEventListener
MFSA 2007-14 Path Abuse in Cookies
MFSA 2007-13 Persistent Autocomplete Denial of Service
MFSA 2007-12 Crashes with evidence of memory corruption (rv:1.8.0.12/1.8.1.4)

---

### Post by Fr@nKy on 2007-06-01
How do I install it on Feisty?

---

### Post by bruce89 on 2007-06-01
> **Fr@nKy said:**
> How do I install it on Feisty?

You wait until the package is updated on the repos. Security updates aren't worth installing manually as they are boring.

---

### Post by mech7 on 2007-06-01
Why is it that in windows i just get a message restart firefox and you update is installed.. And with ubuntu they seem to have removed the button? it is greyed out? Why not let firefox update itself? now it takes so long to get it :(

---

### Post by BarfBag on 2007-06-01
Already using it in Arch.  It pays to use a bleeding edge distro.  2.0.0.4 seems a lot more stable, but I upgraded my Ram right before installing it.  It's probably just that.

---

### Post by bruce89 on 2007-06-01
> **mech7 said:**
> Why is it that in windows i just get a message restart firefox and you update is installed.. And with ubuntu they seem to have removed the button? it is greyed out? Why not let firefox update itself? now it takes so long to get it :(

Ubuntu relies on repositories for updates, Firefox's own update thingy would bugger stuff up big time. Ubuntu's version of Firefox is modified to make it crash more often too.

A few security fixes is nothing worth getting excited about, even the 1.5>2.0 upgrade was boring, unless you call more memory use a feature.

---

### Post by Fr@nKy on 2007-06-01
I'm tired of waiting for updates LoL That's what bores me on Linux :P I prefer Windows on (only) that ;)

---

### Post by mech7 on 2007-06-01
> **bruce89 said:**
> Ubuntu relies on repositories for updates, Firefox's own update thingy would bugger stuff up big time. Ubuntu's version of Firefox is modified to make it crash more often too.

Hmm so that is why firefox crashes allot under ubuntu. Why isn't there just a default version installed what is modifued it looks exactly the same :(

---

### Post by bruce89 on 2007-06-01
> **mech7 said:**
> Hmm so that is why firefox crashes allot under ubuntu. Why isn't there just a default version installed what is modifued it looks exactly the same :(

Here is the patch that Ubuntu applies - [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.3+1-0ubuntu2.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.3+1-0ubuntu2.diff.gz) 311.4 KiB gzipped.

---

### Post by Bachstelze on 2007-06-01
To those who wish to upgrade their Firefox using the built-in autoupdater :


Run Firefox as root :

```
gksudo firefox
```

The "Check for upgrades" menu item will not be greyed out anymore. When you click on it, the upgrade wil be downloaded. When it's done, you are prompted if you want to "restart Firefow now", say **No**. Then, close it manually and restart it with *gksudo* again. The update will then be installed. Re-close Firefox, and you can run it normally ever after.

Of course, this way of updating is by no means supported by Ubuntu, use at your own risk, blah blah blah.

---

### Post by bruce89 on 2007-06-01
> **HymnToLife said:**
> To those who wish to upgrade their Firefox using the built-in autoupdater :


Run Firefox as root :

```
gksudo firefox
```

The "Check for upgrades" menu item will not be greyed out anymore. When you click on it, the upgrade wil be downloaded. When it's done, you are prompted if you want to "restart Firefow now", say **No**. Then, close it manually and restart it with *gksudo* again. The update will then be installed. Re-close Firefox, and you can run it normally ever after.

Of course, this way of updating is by no means supported by Ubuntu, use at your own risk, blah blah blah.

None of this works, that's a good thing though.

---

### Post by Bachstelze on 2007-06-01
Very strange it doesn't work, it has always worked for me with previous releases... Out of curiosity, what does it do instead of working ?

---

### Post by starcraft.man on 2007-06-01
I don't see what the fuss is all about... Its just a security fix (plus better support for Vista... we don't need that on Linux). I looked over change log didn't see anything too substantial that would make me rush and get it.

Oh and to mech7, I have no idea why you crash often. My firefox is fine...

---

### Post by aidanr on 2007-06-01
> **HymnToLife said:**
> Very strange it doesn't work, it has always worked for me with previous releases... Out of curiosity, what does it do instead of working ?

check about:buildconfig, firefox in the repos is built with updates disabled

---

### Post by Rashid584 on 2007-06-01
> **Fr@nKy said:**
> I'm tired of waiting for updates LoL That's what bores me on Linux :P I prefer Windows on (only) that ;)

Its not Linux in general that does that, just Ubuntu

I'm running Sidux at the moment, and its bleeding edge, you can upgrade everything whenever you want (or not, if you don't want)

One drawback, is that it could be less stable, but I haven't had any major show stopper problems with it.

Having a stable distro like [k]ubuntu is nice when you want stability, but sometimes living on the bleeding edge is more fun :p

-Rashid

---

### Post by gregmark on 2007-06-04
I use Fiesty as my host OS on my work PC.  Last week, my firefox browser was crashing hourly.  Since I ran the synaptic update this morning, I haven't crashed once.

It disturbs me that the myriad complaints about firefox crashing in this forum have, for the most part, gone unanswered by Ubuntu forum overlords.

---

### Post by Rashid584 on 2007-06-05
The Ubuntu devs don't really come on this forum (for whatever reason...I think thats a mistake personally but I guess they don't have the time. I understand there's "forum ambassadors" and such so thats a good idea imho)

Firefox is still very memory intensive, and slow/unresponsive and "unstable" in the sense of relatively frequent crashes (although it is useable)

I guess I'm gonna need an upgrade...although I do recall that firefox 1.0 (and probably 1.5 for that matter) were a lot more stable than this.

-Rashid

---

### Post by casals on 2007-06-08
I have Xubuntu/Feisty on an IBM TP 600x (500mhz, 192MB). I let it go update Firefox a couple of hours ago. The update was agonizing, took over an hour, machine completely unresponsive. It finally finished, with the window manager frakked -- ctl-alt-backspace to restart. Seemed ok then, so I started Opera (my browser of choice). Once again, heavy heavy disk use, machine so tied up I can't even move the cursor. It's been doing this for about an hour.   

What to think?

---

### Post by AlanR8 on 2007-06-08
Must be missing something here....

I upgraded from the repositories about 10 days ago........

---

### Post by casals on 2007-06-08
This is a very new installation (put it on the machine last Sunday). I've been running the Update Manager I guess every day to see what wanted updating; today was the first day it said it wanted to update anything -- Firefox.

---

### Post by AlanR8 on 2007-06-08
Hmm

I can assure you I didn't do it the hard way........or was it in Automatix? I can't remember.

---

### Post by starcraft.man on 2007-06-08
> **casals said:**
> This is a very new installation (put it on the machine last Sunday). I've been running the Update Manager I guess every day to see what wanted updating; today was the first day it said it wanted to update anything -- Firefox.

Uh, firstly its a good idea that you make a new thread over [here.]("http://ubuntuforums.org/forumdisplay.php?f=73") Just copy and paste your two posts. The cafe is not a good place for support, its mostly random banter/fun, and that section of the forum is dedicated to support.

Personally, I have no idea why the update took that long. If everything else updates quickly, theres no reason for that to take so long (only took a minute on my old p4)... maybe someone with more experience with Xubuntu can help you in beginner forum.

---

### Post by casals on 2007-06-08
Thanks!

---

### Post by Isaac_x on 2007-06-08
Hm

---

