---
title: "an observation...."
date: 2008-03-05
forum: The Cafe
---

### Post by billybag on 2008-03-05
is it just me or does amarok, banshee, and rhythmbox all lack something great and have something awesome that the others do/dont. it makes it hard to choose

amarok has it all but is big laggy slow and installs kde

rhythmbox is small nice simple but doesnt have some features i like

banshee is really great but doesnt monitor folders and doesnt have a pidgin plugin/isnt compatable with currenttrack

---

### Post by pointone on 2008-03-05
Just FYI, Amarok was slow for me until I realized you really need to use a MySQL database. The default choice of SQLite is unbearably slow.

Otherwise, I agree with you. It's a bit of a mixed bag.

---

### Post by billybag on 2008-03-05
isnt mysql a bit tricky to set up?

---

### Post by murataht on 2008-03-05
It is not so hard to setup a mysql. (mysql + phpmyadmin is easier to manage).

But I don't know what is needed for amarok from mysql.

---

### Post by pointone on 2008-03-05
Fairly detailed instructions can be found [here]("http://amarok.kde.org/wiki/MySQL_HowTo"). It's trickier if you want to import your existing SQLite database. I recommend just starting from scratch.

The 10 minutes you potentially spend setting this up is WELL worth it, in my opinion.

---

### Post by logos34 on 2008-03-05
> **billybag said:**
> 
amarok has it all but is big laggy slow and installs kde

Not all--gapless playback using the xine engine is fatally flawed...it just doesn't work consistently like it should.:(  Granted, it's a backend problem and not an issue with Amarok per se, but it might as well be since most people use it with libxine (which otherwise is amazing because it plays just about every format).

---

### Post by SZF2001 on 2008-03-06
Let's just drop Totem all together and give default video client in fresh install of Ubuntu to VLC.

---

### Post by LaRoza on 2008-03-06
> **SZF2001 said:**
> Let's just drop Totem all together and give default video client in fresh install of Ubuntu to VLC.

That goes against the philosophy of Ubuntu.

---

### Post by SZF2001 on 2008-03-06
so then remove totem and have no video client let the user decide

---

### Post by LaRoza on 2008-03-06
> **SZF2001 said:**
> so then remove totem and have no video client let the user decide

Ubuntu isn't Arch ;)

---

### Post by jr.gotti on 2008-03-06
Damnit, theres gottah be SOMETHING we can do to get rid of totem as a default on ubuntu. It's *terrible.:)*

---

### Post by LaRoza on 2008-03-06
> **jr.gotti said:**
> Damnit, theres gottah be SOMETHING we can do to get rid of totem as a default on ubuntu. It's *terrible.:)*

I wouldn't know, I use VLC.

---

### Post by igknighted on 2008-03-06
> **jr.gotti said:**
> Damnit, theres gottah be SOMETHING we can do to get rid of totem as a default on ubuntu. It's *terrible.:)*

Why not mplayer?  Or Totem-Xine?

As for banshee and pidgin integration: [http://code.google.com/p/musictracker/](http://code.google.com/p/musictracker/)

---

### Post by quanumphaze on 2008-03-06
> **logos34 said:**
> Not all--gapless playback using the xine engine is fatally flawed...it just doesn't work consistently like it should.:(  Granted, it's a backend problem and not an issue with Amarok per se, but it might as well be since most people use it with libxine (which otherwise is amazing because it plays just about every format).

How do I change the backend? The pull down menu only gives Xine as an option.

---

### Post by John T. Monkey on 2008-03-06
I used to be annoyed by the lack of features and option in Rythmbox, but I've come to really like the simplicuty of it. I copy the music on to the computer (from my mp3 player or the Cd), and it just works from there. 

I used to liker amarok but have not used it for some time now, and I have never been a fan of Banshee. 

I still miss Foobar from when I was using windows though :( Ah well.

And Totem (xine) is great. Again, after a bit of tweaking with the DVD codecs, it does everything i want it to, perfectly.

---

### Post by curuxz on 2008-03-06
amorok is amazing and one of the main reasons i dont like using gnome. If you use kde then its great to have a fast integrated media centre!

---

### Post by logos34 on 2008-03-06
> **quanumphaze said:**
> How do I change the backend? The pull down menu only gives Xine as an option.

Uninstall amarok-xine and install **amarok-engines**

---

### Post by uberlube on 2008-03-06
Does Exaile have the same issues as Amarok? And I wouldnt bash totem too much. It was worked on pretty hard by the developers and it can only get better with people sending in bug reports and other suggestions. Who knows, one day it might be better than the alternatives.

---

### Post by justin whitaker on 2008-03-06
I'm actually liking the version of Rhythmbox in Hardy. It's clean, simple, and does pretty much everything Amarok does...or maybe a better comparison is Foobar. 

I used to prefer KDE apps in general, but I think that RBox+Brasero+VLC or MPlayer is about as good as anything on Windows or OSX in terms of media playback and burning.

---

### Post by kellemes on 2008-03-06
> **curuxz said:**
> amorok is amazing and one of the main reasons i dont like using gnome. If you use kde then its great to have a fast integrated media centre!

That's what it is.. a media center, pretty cool but a little too much for a lot of people.
I really think the Ubuntu defaults shouldn't lead to Vista'ish hardware requirements.
vlc for me..

---

### Post by billybag on 2008-03-06
i have to agree with most of you. amarok does seem like a bit too much. Rhythmbox, is what i ahve pretty much always used. i do love the simplicity of it, i kind of wish i twas set up like banshee as far as the neat windows with the album art and recommendations. i guess a combonation of banshee and rhythmbox would be nice.

i look forward to seeing the rhythmbox in hardy. i am waiting until the release in april before i upgrade. 

maybe when i am bored one day i will set up mysql for amarok, but i doubt i will use it much,  i just think it is... ugly. what would be sweet is a linux version of windows media player where as everything is just there, in one program. i think that is all i have to say for now. thanks for the input everybody and i am actiually glad people somewhat agreed with me

---

### Post by Linuxratty on 2008-03-06
> amarok has it all but is big laggy slow and installs kde

Not slow for me,nor laggy...Didn't install KDE cause cI already had KDE. I give five stars to KDE.:KS:KS:KS:KS:KS

---

### Post by logos34 on 2008-03-06
> **Linuxratty said:**
> Not slow for me,nor laggy...

linuxratty,

No problems fetching cddb album/track info for CDs, or slower than other media players?  What about gapless playback for ogg (assuming you use that format)? Any probs at all?  I'm beginning to wonder if I should uninstall and compile from source to fix mine.

---

