---
title: "Why does Ubuntu Package OO.o?"
date: 2010-05-26
forum: The Cafe
---

### Post by shane2peru on 2010-05-26
Ok, I recently had to remove the Ubuntu version of OO.o and install the vanilla OO.o because of a bug in the Ubuntu package.  It was probably a rare bug that only affected a very few number of users, and I'm not ripping on Ubuntu because I have used them for years without many problems.  However I got to thinking (dangerous I know) What does Ubuntu re-package OpenOffice?  Why does Ubuntu repackage a lot of stuff?  Why don't we use the vanilla packages?  Would it break Ubuntu?  Just out of curiosity.

Shane

---

### Post by forrestcupp on 2010-05-26
I'm pretty sure Ubuntu uses Go-oo, which is a fork of OOo.

---

### Post by mikewhatever on 2010-05-26
If you want modifications and bug fixes to be independent of the upstream, maintaining your own repositories is the way to do it.

---

### Post by Dragonbite on 2010-05-26
> **forrestcupp said:**
> I'm pretty sure Ubuntu uses Go-oo, which is a fork of OOo.

That's what I've heard, and Go-oo is a Novell project which incorporates some tweaks to make it more MS Office compatible (e.g. VBA support)

---

### Post by shane2peru on 2010-05-26
Ok, but overall, does it create system stability?  is it strictly for the MS tweaks that have been added?  This is the first I have heard of Go-OO  Here it is:  [http://go-oo.org/](http://go-oo.org/)  Interesting. :)  

Thanks for the feedback.  

Shane

---

### Post by zekopeko on 2010-05-26
> **shane2peru said:**
> Ok, but overall, does it create system stability?  is it strictly for the MS tweaks that have been added?  This is the first I have heard of Go-OO  Here it is:  [http://go-oo.org/](http://go-oo.org/)  Interesting. :)  

Thanks for the feedback.  

Shane

Virtually nobody packages vanilla OO.org. Everyone uses Go-OO.

---

### Post by shane2peru on 2010-05-26
Lol, well, I was going to download and install the Go-OO to see if the bug was there, however it is all rpms!  I know I could alien them to convert them, but ahh, too much work.  I will just have to miss out on the 'extra' goodies they put in the code.  I'm still curious about why most distributions, don't give you the generic OpenOffice, or other applications, instead they have to package everything, and you have to wait for updates from them instead of getting the packager's updates.

Shane

---

### Post by castrojo on 2010-05-26
> **shane2peru said:**
> I will just have to miss out on the 'extra' goodies they put in the code.

Ubuntu ships go ooo already, so you're probably not missing anything. Someone had an Openoffice PPA somewhere (which I can't find) with more updated versions.

>  I'm still curious about why most distributions, don't give you the generic OpenOffice, or other applications, instead they have to package everything, and you have to wait for updates from them instead of getting the packager's updates.

Most projects don't do their own packaging, or when they do they do it wrong or don't integrate with the system as well as they could, which is why you have things like go-ooo and distros shipping that instead of vanilla OOo. 

It mostly works really well, except of course when there's a bug affecting you. What bug is it?

---

### Post by ubunterooster on 2010-05-26
Likely you are using the Ubuntu repackaging of FF. Most are repackaged because of bugs or "lack of features" as defined by whoever rebuilds it. Of course there are things that go wrong in the altered version hat will not go wrong in the original, but it is usually more of a benefit than a hinderance to use a repackaging. 

--written via icecat

---

### Post by shane2peru on 2010-05-26
> **whiprush said:**
> 
It mostly works really well, except of course when there's a bug affecting you. What bug is it?

I filed a bug report, when I opened up a specific calc document, it would take about 12 min to load the file, it was just unreal.  I copied just part of the data out and pasted it into a new file, saved closed and re-opened it, another 12 minutes to open it up.  After removing and installing vanilla OO.o straight from their web site, opens in under 20 seconds.  It was bad for me, but apparently not affecting many.


> **ubunterooster said:**
> Likely you are using the Ubuntu repackaging of FF. Most are repackaged because of bugs or "lack of features" as defined by whoever rebuilds it. Of course there are things that go wrong in the altered version hat will not go wrong in the original, but it is usually more of a benefit than a hinderance to use a repackaging. 

--written via icecat

   That was another one, FF, although I have recently switched to Epiphany, I usually installed the vanilla Firefox too, so that I could have their updates.


Thanks all for the feed back.  I guess it isn't desktop stability, as much as just adding features.

Shane

---

### Post by Hagar Delest on 2010-05-26
I'm with you shane2peru!

Basically, repackaging is quite a loss of energy IMHO. I use the Vanilla version of FF, TB and of course OOo. Even Grisbi has to be installed from source because 0.5.9 is not compatible with the latest libraries shipped with Lucid. All these vanilla versions work fine, so why OOo debs would be defective for example???

Breaking OOo into plenty of packages can also be less intuitive (you can't change the icons set of OOo toolbars if you don't install the related packages first in Synaptic!).

Go-oo.org is more MS Office users oriented but has also more bugs (the PPA version has had severe troubles also, especially at the beginning of the 3.0 release).

---

### Post by Irihapeti on 2010-05-26
+1 Hagar de l'Est.

One of the first things I do after an install is to remove the provided OO.o and replace it with the vanilla version. I also install vanilla Thunderbird. FF, it depends, though I'm noticing that one of my add-ons isn't working properly with Ubuntu FF, so I might just do that shortly.

---

### Post by shane2peru on 2010-05-26
Well, that makes me feel better.  Perhaps we need an Ubuntu-Vanilla distro. lol.  I always like to stay close to the original product, so I generally avoid flavors of a distro, and stick to the main stream.  I guess I like to do the same thing with OO.o, and FF and a few others.  Those mainly though, they are mainstream apps.

Shane

---

### Post by ubunterooster on 2010-05-26
Minimal install do you mean?

---

### Post by Hagar Delest on 2010-05-26
I would not say that OOo would be part of a "minimal" install (there are even threads about removing it in the default install, like The Gimp).

No, we are talking about original packages, not tweaked by 3rd parties (Novell for the go-oo version of OOo for example). The OOo team gives deb package (which was not the case in the first version until something like 2.3) so just put them directly in Ubuntu without changing the packaging (icons sets, ...).

---

