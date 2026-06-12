---
title: "Optimal mp3 bitrate"
date: 2007-01-21
forum: The Cafe
---

### Post by dimovich on 2007-01-21
Hello,

I wonder, what is the most **optimal** MP3 bitrate that should play well on most audio systems (including very expensive ones)... Is it 192, 256 or 320; CBR or VBR ?

It's just that I want to convert my Audio-CD collection to mp3, and don't know what to choose best.

Thanks!

---

### Post by maagimies on 2007-01-21
For Mp3, 192kbps VBR is enough for me and my crappy soundsystem.
Although I use Ogg Vorbis nowadays :p

---

### Post by Mystere on 2007-01-21
OGG is a little more space costly is it not? or am I just using soundconverter wrong?

---

### Post by PatrickMay16 on 2007-01-21
Whoa man!!!!!!!!!

If I'm going to be listening to the music on my computer, I use average 192kbps. If It's to be put on my portable mp3 player, I may use average 80 or 90kbps. Sometimes 112 or 128.

---

### Post by Tuna-Fish on 2007-01-21
Space costly compared to what? I believe ogg vorbis is a truly VBR codec, that is you set the desired quality and the audio file is compressed to that quality, no matter how much sapce it takes. on comparative qualities vorbis usually takes a little less space than mp3.

---

### Post by Tuna-Fish on 2007-01-21
vorbis -q6 is usually considered transparent, ie an untrained ear cannot distinguish between original and compressed one.

---

### Post by raublekick on 2007-01-21
192kbps is optimal for me, the best mix of quality and compression.

for ogg, i don't use it much (can't listen to ogg on my current mp3 player), but i think q4 is pretty good.

---

### Post by banjobacon on 2007-01-21
> **Mystere said:**
> OGG is a little more space costly is it not? or am I just using soundconverter wrong?

You're probably using it wrong. Ogg Vorbis files are supposed to achieve higher quality audio at equal bitrates (equal bitrates = equal file sizes).

---

### Post by Knomefan_fan on 2007-01-21
> **dimovich said:**
> Hello,

I wonder, what is the most **optimal** MP3 bitrate that should play well on most audio systems (including very expensive ones)... Is it 192, 256 or 320; CBR or VBR ?

It's just that I want to convert my Audio-CD collection to mp3, and don't know what to choose best.

Thanks!

Depends totally on the music you are encoding. Provided that you are using the MP3 format, the best option is to use VBR encoding and let the encoder (i.e., LAME) decide the optimal bitrate (using a very advanced psychoacoustic model).

[http://wiki.hydrogenaudio.org/index.php?title=LAME](http://wiki.hydrogenaudio.org/index.php?title=LAME)

Personally, I'm using LAME 3.97, which is the recommended version, and the "-V 2" switch. I'm thinking about moving to FLAC though, just for the sake of it :)

---

### Post by maniacmusician on 2007-01-21
> **PatrickMay16 said:**
> Whoa man!!!!!!!!!

If I'm going to be listening to the music on my computer, I use average 192kbps. If It's to be put on my portable mp3 player, I may use average 80 or 90kbps. Sometimes 112 or 128.
90 Kbps? [faints] how do you listen to that? Man, my ears would bleed :)


@Knomefan_fan: If you switch to FLAC, you'll feel a kick in the pants as you watch your amount of free disk space falling, falling, gone!

---

### Post by dimovich on 2007-01-21
> **Knomefan_fan said:**
> 
[http://wiki.hydrogenaudio.org/index.php?title=LAME](http://wiki.hydrogenaudio.org/index.php?title=LAME)


Thanks for the link. It was really helpful. In other words, the most optimal setting for mp3 would be using these LAME parameters: ```
-V 2 --vbr-new -m s
```

---

### Post by mips on 2007-01-21
I used VBR and I set the range between 192 & 320. So minimum was 192 and highest was 320 it would rip at.

---

### Post by tigerpants on 2007-01-21
> **dimovich said:**
> Hello,

I wonder, what is the most **optimal** MP3 bitrate that should play well on most audio systems (including very expensive ones)... Is it 192, 256 or 320; CBR or VBR ?

It's just that I want to convert my Audio-CD collection to mp3, and don't know what to choose best.

Thanks!

If you have a really good, transparent hifi system (a decent dual mono amp, decent speakers, ie B&W etc), then mp3's of any bitrate wont cut it. Whenever I've played compressed audio through my hifi, i hear pops and clicks and it general sounds like kack. On a general midi system thing, you wont hear anything, but on good hifi equipment you'll hear artifacts and crap you never knew existed. So, it depends on your gear. I encode mp3's for my Zen at 128 and its fine.

---

### Post by mips on 2007-01-22
> **tigerpants said:**
> If you have a really good, transparent hifi system (a decent dual mono amp, decent speakers, ie B&W etc), then mp3's of any bitrate wont cut it. Whenever I've played compressed audio through my hifi, i hear pops and clicks and it general sounds like kack. On a general midi system thing, you wont hear anything, but on good hifi equipment you'll hear artifacts and crap you never knew existed. So, it depends on your gear. I encode mp3's for my Zen at 128 and its fine.

In most cases you can hear a difference but it's really not that bad. Many people do not have hi-fi systems like you have.

Must add that i think you guys make good audio stuff.

Btw, seeing you took the word 'kack' from us you guys should at least spell it correctly ;)

---

### Post by dimovich on 2007-01-22
> **tigerpants said:**
>  [...] mp3's of any bitrate wont cut it.

tigerpants, in what format do you keep your audio collection?

---

### Post by Grey on 2007-01-22
> **dimovich said:**
> tigerpants, in what format do you keep your audio collection?

He says he doesn't use lossy audio.  So I would assume something like flac or shn.  (They are compressed, but not lossy.  So they sound just as good as the source wav).

Personally, I use q7 vorbis.  My sound gear isn't extremely high end, and my hard drive space is limited.  (I currently have about 80GB of mp3s, oggs, and others.  This would probably triple if I were to store lossless audio).

---

### Post by tigerpants on 2007-01-22
> **dimovich said:**
> tigerpants, in what format do you keep your audio collection?

On my computer, its all in mp3, with some ogg and flac. I only use the computer for listening to tracks downloaded from blogs and then sticking them on my Creative Zen. Any tracks I like, I go and buy on vinyl or failing that I slum it with a CD. 

My hifi is set up for vinyl first and foremost, and no digital source can match it - including my cd player with a DAC. Therefore playing audio from my computer is a no-go - so any audio I have on the computer I play through the £12.99 speakers I got for it :D  Sounds fine.

---

### Post by Corbelius on 2007-01-22
Ogg Vorbis 160kbps.

---

### Post by blueturtl on 2007-01-22
What ever bitrate you do choose just make sure it's not joint-stereo. I've heard some 128 bitrate MP3s that sound superior to 192+ bitrate MP3s with joint-stereo enabled.

128 kbps => good for mediocre (read most) computer speakers, small headphones
192 kbps - 256 kbps => better good computer speakers or headphones
320 kbps => best MP3s can generally offer, the only way to bear listening to them through a real audio system

---

### Post by dimovich on 2007-01-22
> **tigerpants said:**
> My hifi is set up for vinyl first and foremost.

tigerpants, can you please tell us what is you HiFi system made of (what gear)?

---

### Post by PatrickMay16 on 2007-01-22
> **maniacmusician said:**
> 90 Kbps? [faints] how do you listen to that? Man, my ears would bleed :)


@Knomefan_fan: If you switch to FLAC, you'll feel a kick in the pants as you watch your amount of free disk space falling, falling, gone!

In my experience, you don't notice the low quality of the sound when you're listening to the music on the drive to somewhere. The noise of everything drowns it out. So this is good for me, because I only have a 64MB mp3 player. 

So often I would encode mp3s for use in my mp3 player with "lame --preset 96".

---

### Post by tigerpants on 2007-01-22
> **dimovich said:**
> tigerpants, can you please tell us what is you HiFi system made of (what gear)?

Deck: Rega P3 with a customised RB300 tone arm, goldring MC cartridge
AMP: Musical Fidelity X-150
Speakers: B&W 704's (running these in, also have the 602's)
Cabling: All Kimber cables and interconnects, totalling about £700
CD Player: Cambridge Audio 640 (don't really listen to CD's, so no need for anything uber)
DAC: Musical Fidelity X-DAC

Its very transparent :) You really notice badly produced and recorded stuff, but on the upside, well produced stuff sounds magnificient. Its not the most expensive or uber system in the world, but it does sound great. :D

---

### Post by joker on 2007-01-22
I encoded several tracks at various bitrates and then listened to them on my midfi equiptment.  I choose to encode my CDs at the bitrate where I could not hear a difference between the origional source and the MP3, which for me was 192 VBR (--preset extreme).  I figure even if I get better (more revealing) speakers in the future, my hearing will degrade with age, so in the end they will still sound good to me.

---

### Post by dimovich on 2007-01-22
> **tigerpants said:**
> Deck: Rega P3 with a customised RB300 tone arm, goldring MC cartridge
AMP: Musical Fidelity X-150
Speakers: B&W 704's (running these in, also have the 602's)
Cabling: All Kimber cables and interconnects, totalling about £700
CD Player: Cambridge Audio 640 (don't really listen to CD's, so no need for anything uber)
DAC: Musical Fidelity X-DAC

Man! I've googled for these components, and they just seem incredible! How much have you paid for this whole set?

---

### Post by tigerpants on 2007-01-22
> **dimovich said:**
> Man! I've googled for these components, and they just seem incredible! How much have you paid for this whole set?

I can't remember off-hand, probably in the region of around £4k all in. I had an engineering friend make some mods to my decks tonearm, and that pushed up the price. Usually a P3 with cartridge is about £400.

Trouble with hifi is that spending lots of money doesn't necessarily get you a better sound. Its all subjective really, My friend's system is about £20k, and I can't stand the way it  sounds :)  So you have to demo everything and make sure its the right sound for you.

---

### Post by dimovich on 2007-01-22
tigerpants, what music styles do you usually listen to on your HiFi system? Is there any difference in quality between listening to some jazz and listening to some hardcore metal?

---

### Post by tigerpants on 2007-01-22
> **dimovich said:**
> tigerpants, what music styles do you usually listen to on your HiFi system? Is there any difference in quality between listening to some jazz and listening to some hardcore metal?

I listen to everything, from pre-war blues and jazz through to Osaka noisepunk and everything in between. Style of music isn't really relevant in terms of hifi, its more about how the piece of music you are listening to is produced and mixed - this is especially true if you have a transparent system. If you put crap into my hifi, you get very well reproduced crap out the speakers... put good stuff in, you get good stuff out.

I have CD's and LP's I've binned because the production on them is so awful I can't bear to listen to it - my current hifi reveals every detail, details my old hifi couldnt. I hear microphone studio noise, coughs, even on some recordings the singer taking an in breath before singing - never noticed them before. So its a real ear opener getting come decent kit.

---

### Post by Knomefan_fan on 2007-01-22
> **blueturtl said:**
> What ever bitrate you do choose just make sure it's not joint-stereo. I've heard some 128 bitrate MP3s that sound superior to 192+ bitrate MP3s with joint-stereo enabled.


That is an old myth.

[http://harmsy.freeuk.com/mostync/](http://harmsy.freeuk.com/mostync/)

Lame 3.97, which is the (by audiophiles) recommended MP3 encoder, uses joint stereo for the high-quality presets.

---

### Post by mips on 2007-01-22
> **tigerpants said:**
> 
I have CD's and LP's I've binned because the production on them is so awful I can't bear to listen to it - my current hifi reveals every detail, details my old hifi couldnt. 

I have a Soft Cell CD like that gives me the absolute irrates, worse cd I heard in my live.

---

### Post by Daveski on 2007-01-22
> **dimovich said:**
> I wonder, what is the most **optimal** MP3 bitrate that should play well on most audio systems (including very expensive ones)... Is it 192, 256 or 320; CBR or VBR ?

It's just that I want to convert my Audio-CD collection to mp3, and don't know what to choose best.

Obviously with any form of lossy compression you should go for the highest bit-rate you can to get the best approximation of the original (although it will never be perfect). You have to balance file size against quality.

In my experience, a well encoded 128 bit MP3 will be noticably better quality than an average encoded 256. The faster an encoder works, the more likely the audio quality will be reduced.

---

