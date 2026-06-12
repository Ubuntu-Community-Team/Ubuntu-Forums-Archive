---
title: "RealPlayer: way better than I thought?"
date: 2008-08-24
forum: The Cafe
---

### Post by MaxIBoy on 2008-08-24
Okay, my business is to archive records onto CDs with a USB turntable. Some of you may remember my thread asking for help adding metadata to the tracks, but I never got it working. I've just taken to warning customers that they'll have to manually rename the track titles if they ever rip the CDs for an MP3 player.


This evening, one of the customers said that I didn't know what I was talking about, all the track titles, as well as the artist and the cover art, were right there in front of her in RealPlayer. I couldn't believe her, so I burned another copy of the CD (I hadn't deleted the sound files yet,) put the CD into my parents' XP box, and was astounded to see that she was right. 


The only way I can think of for this feature to work is if it compared the actual waveforms with a database somewhere and identified the album. This floors me. As a test, I tried a few other media players in XP and Ubuntu and none of them had this feature. 


Are there any FOSS media players that can also do this?

---

### Post by cardinals_fan on 2008-08-24
RealPlayer 11 is actually a very good media player for Linux.  It's almost as good as AlsaPlayer.

---

### Post by MaxIBoy on 2008-08-24
I don't use RealPlayer because it has more features than I need, runs pretty slowly, and takes up too much screen room. Audacious for the win! But that feature in particular wasn't something I even knew existed yet, except in a couple experimental websites. I'd heard something about a website that would help you track down the name of a song you had stuck in your head, if you hummed/sang/whistled it into a microphone.

---

### Post by cookies on 2008-08-24
I think the metadata is there, it's just that sometimes some programs don't "see" it. I've had this happen, and then looked at the file in another player, it was there.

---

### Post by cardinals_fan on 2008-08-24
> **MaxIBoy said:**
> I don't use RealPlayer because it has more features than I need, runs pretty slowly, and takes up too much screen room. Audacity for the win! But that feature in particular wasn't something I even knew existed yet, except in a couple experimental websites. I'd heard something about a website that would help you track down the name of a song you had stuck in your head, if you hummed/sang/whistled it into a microphone.
Eh?  RealPlayer is actually quite compact (and not THAT feature-overloaded), while Audacity is a powerful audio editor with TONS of features for tweaking audio.

---

### Post by tel93 on 2008-08-24
> **cardinals_fan said:**
> It's almost as good as AlsaPlayer.

No other graphical media player touches AlsaPlayer. :)

---

### Post by SunnyRabbiera on 2008-08-24
Realplayer under linux is also better too, the regular real on windows is too slow.
Sure it has a lot of crap in it, but linux has its own tools.

---

### Post by cardinals_fan on 2008-08-24
> **tel93 said:**
> No other graphical media player touches AlsaPlayer. :)
Obviously :)

---

### Post by MaxIBoy on 2008-08-24
> **cardinals_fan said:**
> Eh?  RealPlayer is actually quite compact (and not THAT feature-overloaded), while Audacity is a powerful audio editor with TONS of features for tweaking audio.Dammit, I meant Audacious.


Anyway, RealPlayer runs pretty badly on my parents' PC, so I never tried it anywhere else. I wasn't even aware there was a Linux version.




> **cookies said:**
> I think the metadata is there, it's just that sometimes some programs don't "see" it. I've had this happen, and then looked at the file in another player, it was there.Not possible, this was captured from a 33 1/3 RPM LP. Vintage vinyl records are analog, and do not carry digitally embedded metadata (that I know of.)

---

### Post by Redache on 2008-08-25
Interesting. The only thing Real Player can do better than anything else :p

---

### Post by Icehuck on 2008-08-25
> **Redache said:**
> Interesting. The only thing Real Player can do better than anything else :p

Well no, it can display "buffering" better than any other player.  In all honesty, I'm surprised anyone still uses it. I haven't used in years and probably won't ever use it again.

---

### Post by yabbadabbadont on 2008-08-25
It's also pretty good about phoning home with everything you do with it...  I guess that could be considered a feature.  :)

---

### Post by Sinkingships7 on 2008-08-25
> **Icehuck said:**
> Well no, it can display "buffering" better than any other player.  In all honesty, I'm surprised anyone still uses it. I haven't used in years and probably won't ever use it again.

I remember those days. Though I still don't use it, it's changed *very* dramatically.

---

### Post by Lord DarkPat on 2008-08-25
Actually, metadata is grabbed from the "Gracenote CDDB", and it is identified by the waveforms. Currently, iTunes, Mediamonkey, RealPlayer and even AmaroK(I think) download metadata from it, on the fly
Sound ripper uses it, too

---

### Post by Kernel Sanders on 2008-08-25
Realplayer is a virus. KILL IT WITH FIRE.

---

### Post by MaxIBoy on 2008-08-25
> **Lord DarkPat said:**
> Actually, metadata is grabbed from the "Gracenote CDDB", and it is identified by the waveforms. Currently, iTunes, Mediamonkey, RealPlayer and even AmaroK(I think) download metadata from it, on the fly

AmaroK can do that? I didn't know. I've never used it with songs which are missing metadata before. And at least the MediaMonkey free version doesn't have the feature.

Any chance of using this to actually put the metadata in the actual sound files before burning them?

---

### Post by billgoldberg on 2008-08-25
> **MaxIBoy said:**
> Okay, my business is to archive records onto CDs with a USB turntable. Some of you may remember my thread asking for help adding metadata to the tracks, but I never got it working. I've just taken to warning customers that they'll have to manually rename the track titles if they ever rip the CDs for an MP3 player.


This evening, one of the customers said that I didn't know what I was talking about, all the track titles, as well as the artist and the cover art, were right there in front of her in RealPlayer. I couldn't believe her, so I burned another copy of the CD (I hadn't deleted the sound files yet,) put the CD into my parents' XP box, and was astounded to see that she was right. 


The only way I can think of for this feature to work is if it compared the actual waveforms with a database somewhere and identified the album. This floors me. As a test, I tried a few other media players in XP and Ubuntu and none of them had this feature. 


Are there any FOSS media players that can also do this?

You can't add metadata to the tracks?

I presume you mean ID3 tags.

Tagtool will do that for you, been using it forever and works on everything.

---

### Post by MaxIBoy on 2008-08-25
Well whenever I add them, they don't survive the CD burning process. Nor are they visible after the tagging program closes, not to any program, even to the same program that created the tags.

(NOTE: I had not even attempted to add metadata in the case of this particular CD.)

---

### Post by Lem on 2008-08-26
Have you tried using the Picard tagger from musicbrainz on your tracks? It's in the repos and will tag your files using the waveform.

---

### Post by RiceMonster on 2008-08-26
I tried installing realplayer. It changed all my mp3 icons (which annoyed the hell out of me) and had absolutely nothing that attracted my attention (in a good way). I'll stick with audacious as well.

---

### Post by yabbadabbadont on 2008-08-26
> **MaxIBoy said:**
> Well whenever I add them, they don't survive the CD burning process. Nor are they visible after the tagging program closes, not to any program, even to the same program that created the tags.

(NOTE: I had not even attempted to add metadata in the case of this particular CD.)

So let me get this straight.  You want to add tags to a standard audio CD...

---

