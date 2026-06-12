---
title: "mediamonkey v3.2.1.1297, wine 1.1.42, ubuntu 10.04 songs won't play"
date: 2010-07-24
forum: Wine
---

### Post by finny388 on 2010-07-24
I just installed wine 1.1.42 via Synaptic, then ran the mm install with wine.

MM installed and will open, sees library, can use skins, but:
[LIST]
[*]takes about 2 minutes to start the app
[*]won't play mp3s - just doesn't respond to the play button.
[/LIST]
I found this **[guide]("http://www.mediamonkey.com/wiki/index.php/Linux,_Wine_&_MediaMonkey")** but it refers to Ubuntu 8.04.

Does this guide still apply in Ubuntu 10.04?

Please don't suggest other players (unless you know MM intimately).

I am upgrading a friend's pc and the only app keeping him in  Windows is MM - pretty much.

So I'm trying to get it to work to show him the wonders of Ubuntu.

thanks

---

### Post by asdfoo on 2010-07-25
wine 1.1.42 is pretty old

update to wine 1.2 and retry

---

### Post by finny388 on 2010-07-25
I upgraded wine to 1.2 and reinstalled MM. No change.

---

### Post by finny388 on 2010-07-30
From what I've read, Media Monkey does not work very will on Linux. Synchronization, for example, doesn't work. And for me, it won't play songs.

So I've given up and he will stay with Windows going from XP to 7 premium. 

oh well.

---

### Post by asdfoo on 2010-07-30
if you could post the terminal output here it might help

[http://wiki.winehq.org/FAQ#get_log](http://wiki.winehq.org/FAQ#get_log)

---

### Post by finny388 on 2010-07-30
Thanks asdfoo but even if I got it working it would take a lot to convince him to switch.

Perhaps when MS screws up their next OS he may try.

Cheers

---

### Post by hilley on 2011-01-25
finny388, 

I just got MM working on ubuntu 10.10, wine 1.3.11, MediaMonkey 3.2.4.1304. From what i read on winehq was that it just worked after installation ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=15096](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15096)). But for me, the playback did not work with the wine audio drivers (song would "click" for like half a second and stop).

I downloaded the MAD .14.2b MP3 Input Plug-in from the MM site ([http://www.mediamonkey.com/addons/input-output/](http://www.mediamonkey.com/addons/input-output/)) and installed it and that did the trick! Make sure you follow the directions about renaming the existing MP3 decoder to disable it...

Hope this helps,
hilley

---

### Post by finny388 on 2011-01-25
Thanks hilley, that was a very considerate post :)

I may give that a try in the future

So fully featured and working like a charm? (not slow or anything)?

---

### Post by hilley on 2011-01-26
The speed is fine. No noticeable delays (and I'm on an ancient 3.4 GHz Pentium 4!). The only thing that doesn't work is View, Show Details. This was also mentioned on the wine site somewhere. A bit annoying, but using the "Album Art with Details" view is a compromise.

I'd be curious to know if you have any luck with it as well...

---

### Post by Robfuscate on 2011-09-04
> **finny388 said:**
> From what I've read, Media Monkey does not work very will on Linux. Synchronization, for example, doesn't work. And for me, it won't play songs.

So I've given up and he will stay with Windows going from XP to 7 premium. 

oh well.

Yes, there are a number of acceptable media players available for Linux users, but none of them work in the way that MediaMonkey does - without fuss, in a logical way that allows for library functions as well as playback and synch. 

Amarok in particular is bloated, slow and buggy - although I've only ever used it on Ubuntu/Mint machines - I simply dislike the KDE interface. 

Exaile is the closest to MM and that's what I'm using on my Mint 11 laptop for a small library of favourites - but when it comes to my JukeBox, I'm still running Windows XP and MM to manage 18,000+ titles.

---

