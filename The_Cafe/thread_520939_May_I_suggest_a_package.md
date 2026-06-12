---
title: "May I suggest a package?"
date: 2007-08-08
forum: The Cafe
---

### Post by SZF2001 on 2007-08-08
Now, for a while I used SuSE - I know I shouldn't exclaim that on the Ubuntu forums - but that's beside the point.

There is a really awesome app in the packman repositories called [Open Movie Editor](http://openmovieeditor.sourceforge.net/) - basically like Windows Movie Maker, but ten times better, with more customization, more options for saving files (as in .avi and others), and just all around easier to work with.

And Ubuntu is made to be easy to work with, right? I've tried Kino - half the time it can't even import my normal files, let alone the standard files it's supposed to be based on (.dv or something).

LiVES isn't really that great to work with, either. But that's just my opinion.

I've tried compiling this by source and using alien to get the RPM to install and... I've had no luck. Of course, there are thousands more experienced Linux users who could easily make this work - it's only around one or two megabytes, anyway. I think if someone could get it working and it could be added to a repository... That'd be awesome. I really don't feel like switching back to SuSE... This could just be another solution for more people to stick with Ubuntu.

---

### Post by phrostbyte on 2007-08-08
I suggest you talk to a "Master of the Universe" (yeah I wish I had that title) to see if they can package it. They are the ones with the authority over stuff like that and most of them are very happy to help you.

:guitar:

---

### Post by Tomosaur on 2007-08-08
Thanks for telling us about this - I've been looking for a decent open-source movie editor for a while :P

---

### Post by 4KvRMU7Nnv on 2007-08-08
Tadaaa!!!! I made a deb file!!!!  tell me if it works.  thanks for pointing out this program.  I'm gonna test it out now.  The least I could do was package it for you!

[http://www.mediafire.com/?1m3bb4hlwwl](http://www.mediafire.com/?1m3bb4hlwwl)

^^^go to the link to get deb^^^^


LOL turns out I have no use for this as I don't have any quicktime files.  (which it seems to prefer)  I'll stick to pitivi.  But hey, at least you have your deb file!

---

### Post by 23meg on 2007-08-08
> **phrostbyte said:**
> I suggest you talk to a "Master of the Universe" (yeah I wish I had that title) to see if they can package it. They are the ones with the authority over stuff like that and most of them are very happy to help you.

:guitar:

I filed a bug to notify possible interested MOTU or MOTU hopefuls who may package it for Universe.

[https://bugs.launchpad.net/ubuntu/+bug/131219](https://bugs.launchpad.net/ubuntu/+bug/131219)

---

### Post by SZF2001 on 2007-08-09
Prefers quicktime files? Odd. That's not how I remembered it - you could slap any file type in there and mash 'em all together to make one giant (or small) .avi/.mov/.whatever file...

Regardless, thanks for making a stable .deb . I'm about to try it out myself - I'll also hang onto the .deb file in case that website takes it down or something happens or... whatever situation. Yea. Thanks again!

---

### Post by SZF2001 on 2007-08-09
UPDATE: Kind of a bump, sorry for double posting, blargh.

Anyway - here is my results with the program thus far:

I had to install a few things. If you are wondering why you can't find openmovieeditor in your GNOME menu, or XCFE "Applications" list, then just go to the terminal and type ' openmovieeditor '. From there, it will tell you what plugins you are missing.

For the few plugins I was missing (I'm on Feisty, btw), here is a quick code you can use to find some packages:

```
sudo aptitude install libquicktime0 libgavl0 libfltk1.1 libfltk1.1-dbg libjack0.100.0-0 libjack0.100.0-dev
```

It will load the program, even if it can't find "jack" - I think that's how it handles sound, or something.

Anyway - to my surprise, it is preferring quicktime movies, which wasn't the case on SuSE. I'm not sure where to start hunting for said codecs... Probably more RPM files on packman, I'm not sure. I'll try and look into this tomorrow - football is making me tired (condition/hell week will do that), so until then... Yea.

---

### Post by Bachstelze on 2007-08-09
For those interested, here's an Open Movie Editor DEB for Feisty I've made, which should have all the codecs enabled. I didn't include dependencies in it so if it complains about a missing lib, just install it - it's all in the repos.

[http://fkraiem.no-ip.org/stuff/openmovieeditor_0.0.20070607-1_i386.deb](http://fkraiem.no-ip.org/stuff/openmovieeditor_0.0.20070607-1_i386.deb)

---

### Post by 23meg on 2007-08-09
Oops, I noticed that it's already packaged in Gutsy.

---

### Post by SZF2001 on 2007-08-09
> **23meg said:**
> Oops, I noticed that it's already packaged in Gutsy.

It has? Awesome. Now I don't know if I should use the poster above you debian package or wait...

---

