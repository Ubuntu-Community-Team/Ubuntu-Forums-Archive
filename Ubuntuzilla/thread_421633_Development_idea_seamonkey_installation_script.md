---
title: "Development idea: seamonkey installation script?"
date: 2007-04-24
forum: Ubuntuzilla
---

### Post by nanotube on 2007-04-24
***EDIT*** Seamonkey installation is already available in ubuntuzilla. If you are interested, just go ahead and use it. :)

Just wanted to throw out the possibility of having a seamonkey install script, just like we have for ff and tb.
not sure how much use it will get, so vote in the poll. :)

also, anyone know whether seamonkey is in the repos for the various versions of ubuntu, and what the package name is, and what is the link that is put into /usr/bin for it? (this, in case i end up making the seamonkey install script. :) )

---

### Post by aysiu on 2007-04-25
There's no SeaMonkey in any Ubuntu repositories. 

I wrote up a little HowTo on the Wiki about SeaMonkey:
[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)

It's an installer, not a precompiled binary (unless there's one I don't know about).

---

### Post by nanotube on 2007-04-25
> **aysiu said:**
> There's no SeaMonkey in any Ubuntu repositories. 

I wrote up a little HowTo on the Wiki about SeaMonkey:
[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)

It's an installer, not a precompiled binary (unless there's one I don't know about).

well, it would probably be under "mozilla" or "mozilla-browser" or "mozilla-suite" package, if it's not under "seamonkey".

also, in addition to the installer, seamonkey has a tar.gz with the binary, without an installer (just like what they have for ff and tb). see here: [http://www.mozilla.org/projects/seamonkey/releases/](http://www.mozilla.org/projects/seamonkey/releases/) (under official builds>linux>tar.gz)

though i guess if they have an installer, and it works well, then we don't really need a script. it's just that i saw a thread about seamonkey where people said it didn't quite work right... don't recall the details though.

---

### Post by shane2peru on 2007-04-27
> **nanotube said:**
> Just wanted to throw out the possibility of having a seamonkey install script, just like we have for ff and tb.
not sure how much use it will get, so vote in the poll. :)

also, anyone know whether seamonkey is in the repos for the various versions of ubuntu, and what the package name is, and what is the link that is put into /usr/bin for it? (this, in case i end up making the seamonkey install script. :) )

I think it may be a little pre-mature for a poll.  :)  I like the idea, and happened to stumble across this hidden group.  I prefer FireFox, but SeaMonkey does have somethings that FireFox doesn't and occasionally I use it.  That is my 2cents worth.

Shane

---

### Post by sumashod on 2007-05-08
Here is a Script to install Seamonkey:

[Download](http://sumashod.su.funpic.de/scripts/seamonkey1_1_1-en.tar.bz2)

Andy

---

### Post by nanotube on 2007-05-08
hi
thanks for sharing your script, it's a good start. :)

---

### Post by shane2peru on 2007-05-08
I think that Songbird may be a higher priority than Seamonkey.  As far as installation scripts.  Is that in the works?  It would even be great if it offer to make it the default music player program.  Just a thought.  :)

Shane

---

### Post by nanotube on 2007-05-09
> **shane2peru said:**
> I think that Songbird may be a higher priority than Seamonkey.  As far as installation scripts.  Is that in the works?  It would even be great if it offer to make it the default music player program.  Just a thought.  :)

Shane

hi
erm, no, it's not even on the horizon - i had to search google to find out what songbird is. :) and upon visiting the website, i have to be honest that i was not impressed. it looks like they are trying a "kitchen sink" approach to a media player. maybe it's just me, but i'm a fan of having several apps that do one thing well, rather than one app that does many things poorly. (or even one app that does many, but unrelated, things well). why would i want to browse the web from my music player? no thanks. :) that's why i've got firefox, seamonkey, and elinks on my system.

not to mention that they don't even provide a download link from the main site. i had to rummage around until i found some downloads, and then, only  the nightly builds, so this appears to not even be a "stable" product. 

now, i haven't actually tried it, and maybe it's the best thing ever, but with my "quick glance" approach to evaluating software, i'm not sold. :) but you must have a reason for being so excited, so... please share with us. :)

---

### Post by shane2peru on 2007-05-09
> **nanotube said:**
> hi
erm, no, it's not even on the horizon - i had to search google to find out what songbird is. :) and upon visiting the website, i have to be honest that i was not impressed. it looks like they are trying a "kitchen sink" approach to a media player. maybe it's just me, but i'm a fan of having several apps that do one thing well, rather than one app that does many things poorly. (or even one app that does many, but unrelated, things well). why would i want to browse the web from my music player? no thanks. :) that's why i've got firefox, seamonkey, and elinks on my system.

not to mention that they don't even provide a download link from the main site. i had to rummage around until i found some downloads, and then, only  the nightly builds, so this appears to not even be a "stable" product. 

now, i haven't actually tried it, and maybe it's the best thing ever, but with my "quick glance" approach to evaluating software, i'm not sold. :) but you must have a reason for being so excited, so... please share with us. :)

I guess I have never really given it that critical of a review, or any review at all. :popcorn:  I found out about it on the Ubuntu forums, and had it installed before.  I liked it as a music player, you are right though the web browsing feature was not that great.  I could care less about the web browsing part, and forgot that it did that.  I guess it's popularity comes from that it plays mp3's out of the box?  I'm not sure really.  Maybe it is the cross platform that wins people, or maybe that is plays iTunes?  I only tried it for a while because it was on the forums and others were raving over it.  I run into Songbird on the forums more than I run into Seamonkey.  That is all I know about it.  Sorry I can't give you more info.  

Shane

---

### Post by nanotube on 2007-05-09
> **shane2peru said:**
> I guess I have never really given it that critical of a review, or any review at all. :popcorn:  I found out about it on the Ubuntu forums, and had it installed before.  I liked it as a music player, you are right though the web browsing feature was not that great.  I could care less about the web browsing part, and forgot that it did that.  I guess it's popularity comes from that it plays mp3's out of the box?  I'm not sure really.  Maybe it is the cross platform that wins people, or maybe that is plays iTunes?  I only tried it for a while because it was on the forums and others were raving over it.  I run into Songbird on the forums more than I run into Seamonkey.  That is all I know about it.  Sorry I can't give you more info.  

Shane

hehe no prob. it's always good to throw out a suggestion :)
so, you are saying that it actually plays itunes-drm mp3 files? i thought apple didn't allow others to use their "fairplay" drm? i don't have any drm'ed files, so it's not like i actually care :), but i'm very curious!

---

### Post by shane2peru on 2007-05-09
> **nanotube said:**
> hehe no prob. it's always good to throw out a suggestion :)
so, you are saying that it actually plays itunes-drm mp3 files? i thought apple didn't allow others to use their "fairplay" drm? i don't have any drm'ed files, so it's not like i actually care :), but i'm very curious!

Wooo, don't qoute me on that. ;)  I just read something about that on the web site.  Something about it replaces iTunes, here it is from the horses mouth:
>  Anything, Anywhere
  Use an iPod, USB device
  Play tracks from iTunes
  Store, Yahoo! Unlimited from: [http://www.songbirdnest.com/](http://www.songbirdnest.com/)  I only play mp3's so I really don't know about all that stuff.  You may search the forums and see if it is worth while or not to the Ubuntu community.  I can't really say as I don't get into all that stuff so much.  I just play mp3's from my computer. :)

Shane

---

### Post by nanotube on 2007-05-09
> **shane2peru said:**
> Wooo, don't qoute me on that. ;)  I just read something about that on the web site.  Something about it replaces iTunes, here it is from the horses mouth:
 from: [http://www.songbirdnest.com/](http://www.songbirdnest.com/)  I only play mp3's so I really don't know about all that stuff.  You may search the forums and see if it is worth while or not to the Ubuntu community.  I can't really say as I don't get into all that stuff so much.  I just play mp3's from my computer. :)

Shane

ah hehe i c. :)

---

### Post by sumashod on 2007-05-09
[quote="shane2peru"]I think that Songbird may be a higher priority than Seamonkey. As far as installation scripts. Is that in the works? It would even be great if it offer to make it the default music player program. Just a thought.

Shane[/quote]

No problem! Here is the script to install the Songbird:

[Songbird 0.2.5 Developer Preview](http://sumashod.su.funpic.de/scripts/songbird0_2_5_en.tar.bz2)

Andy

---

### Post by aysiu on 2007-05-09
Apparently, [Seamonkey now has a .deb](http://ubuntuforums.org/showpost.php?p=2624532&postcount=14)?

---

### Post by nanotube on 2007-05-09
> **aysiu said:**
> Apparently, [Seamonkey now has a .deb](http://ubuntuforums.org/showpost.php?p=2624532&postcount=14)?

hmm, looks like it... though it is coming from a third-party source, and they re-brand it "iceape" :)

---

### Post by aysiu on 2007-05-09
Yes, the Debian folk thought Mozilla's branding licenses were too restrictive, so they created Iceweasel (Firefox) and Iceape (Seamonkey).

---

### Post by nanotube on 2007-05-09
> **aysiu said:**
> Yes, the Debian folk thought Mozilla's branding licenses were too restrictive, so they created Iceweasel (Firefox) and Iceape (Seamonkey).

yea, i've heard of the iceweasel thing, but not iceape :)

but afaik, the branding problems only arise when the redistributor makes changes to the codebase, and thus potentially compromises product quality. if the .deb were a simple packaging into a .deb, without any changes to the code, a rebranding would not be required. so this then raises the question of what kind of changes they have made to seamonkey before packaging it into a .deb...

---

### Post by dolphinsonar on 2007-05-12
> **shane2peru said:**
> Wooo, don't qoute me on that. ;)  I just read something about that on the web site.  Something about it replaces iTunes, here it is from the horses mouth:
 from: [http://www.songbirdnest.com/](http://www.songbirdnest.com/)  I only play mp3's so I really don't know about all that stuff.  You may search the forums and see if it is worth while or not to the Ubuntu community.  I can't really say as I don't get into all that stuff so much.  I just play mp3's from my computer. :)

Shane


Erm, I was running sonbird as an open source alternative to Itunes for the Macintosh at my work, and I tried to use the previous Itunes library and the Mp3s would not play.  I didn't investigate the problem very deeply, but I just figured it was DRM.  Yuck!

---

### Post by southsanity on 2007-05-14
like a lot of other people, i would prefer to use seamonkey that FF, FF runs really slow.....atleast thats how i find it, better to install seamonkey, but i think it would be irrelevant to create a script, considering you can download it here: [http://download.mozilla.org/?product=seamonkey-1.1.1&os=linux&lang=en-US](http://download.mozilla.org/?product=seamonkey-1.1.1&os=linux&lang=en-US)
just download into your home directory, then launch nautilus as root, or use the nautilus root script from automatix, extract the archive,  locate the seamonkey-installer file, and run it, ensuring you are still running nautilus as root, it will install into /usr/local/seamonkey.

to run it use this command: /usr/local/seamonkey/seamonkey
it's all prettty simple really
nearly as simple as using synaptic or a script, considering you would need to find a repo that contains it, then add it to sources.list
i guess the only reason we would need to script it would be for a bit of polish to the OS

---

### Post by nanotube on 2007-05-14
heh well, since the seamonkey install script already exists at this point, the question is moot...
but thanks for your comment, anyway. ;)

---

### Post by compiledkernel on 2007-05-14
> **nanotube said:**
> Just wanted to throw out the possibility of having a seamonkey install script, just like we have for ff and tb.
not sure how much use it will get, so vote in the poll. :)

also, anyone know whether seamonkey is in the repos for the various versions of ubuntu, and what the package name is, and what is the link that is put into /usr/bin for it? (this, in case i end up making the seamonkey install script. :) )

[https://launchpad.net/iceape/](https://launchpad.net/iceape/) 

the unbranded version of Seamonkey, I believe that getdeb.net has a deb file as well.

---

