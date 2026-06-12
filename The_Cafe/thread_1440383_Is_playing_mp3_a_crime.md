---
title: "Is playing mp3 a crime?"
date: 2010-03-27
forum: The Cafe
---

### Post by superarthur on 2010-03-27
I bought 2 CDs recently, I imported the songs onto my computer as mp3 using iTunes while I booted into Windows. I wasn't bother to import them again when booting onto Ubuntu, so I saved the mp3 files onto my USB drive and transfer them to Ubuntu. (I should be able to just mount my windows partition, but I forgot I can do that :P)
Anyway, when I tried to play the songs on Rythmbox, I was told that extra plugins are needed, and those plugins are "ugly". I clicked install, and it gave me warning saying that it may be illegal in some countries. I proceeded anyway.
So what would be wrong with playing mp3, playing songs that I paid for?
It's not like wma, which I think is patented by Microsoft or something. (anyway, anything related to Microsoft is bad lol)
I thought mp3 is a commonly accepted file format, or else Apple (and any other company producing portable media player) would get sued.
Sorry if I am being ignorant here. :P

---

### Post by cgroza on 2010-03-27
Yes and No. Since it is relatively easy to create MP3 files from CD  selections and make them available on Web sites for downloading,  companies and sites that promote the MP3 format are sometimes accused of  encouraging copyright violations. (It is illegal to copy music from a  CD and redistribute it unless you have the copyright owner's  permission.) On the other hand, MP3 enthusiasts claim that what CD  publishers are afraid of is any kind of non-CD distribution. While there  are several proposals for how to discourage such piracy, there is  currently no secure distribution and copyright management standard that  publishers and other parties agree upon. Several Web sites are promoting  MP3 as both a high-quality audio format and as a way in which  self-publishers can gain ready access to an audience. Currently, some  music publishers are providing sample cuts in the MP3 format as a way to  entice users to buy a CD. However, not much mainstream copyrighted  material is available except as an illegal download.

[http://www.khouse.org/pages/mcat/mp3/what_is_mp3/](http://www.khouse.org/pages/mcat/mp3/what_is_mp3/)

---

### Post by dragos240 on 2010-03-27
Absolutely not. The mp3 format is NOT illegal.

---

### Post by NightwishFan on 2010-03-27
You can legally use the fluendo mp3 decoder I think. Not sure if libmad is legal or not in some areas. My best advice is to consult legal counsel.

Mp3 license has certain compliances that fluendo conforms to, I believe.

---

### Post by CharlesA on 2010-03-27
It is due to it being able to decode MP3s. The vanilla install of Ubuntu doesn't include any "non-free" packages. Since the package used for decoding MP3s is "non-free" it isn't installed by default.

I am not sure why it would be illegal in some countries tho.

---

### Post by superarthur on 2010-03-27
> **cgroza said:**
> Yes and No. Since it is relatively easy to create MP3 files from CD  selections and make them available on Web sites for downloading,  companies and sites that promote the MP3 format are sometimes accused of  encouraging copyright violations. (It is illegal to copy music from a  CD and redistribute it unless you have the copyright owner's  permission.) On the other hand, MP3 enthusiasts claim that what CD  publishers are afraid of is any kind of non-CD distribution. While there  are several proposals for how to discourage such piracy, there is  currently no secure distribution and copyright management standard that  publishers and other parties agree upon. Several Web sites are promoting  MP3 as both a high-quality audio format and as a way in which  self-publishers can gain ready access to an audience. Currently, some  music publishers are providing sample cuts in the MP3 format as a way to  entice users to buy a CD. However, not much mainstream copyrighted  material is available except as an illegal download.

[http://www.khouse.org/pages/mcat/mp3/what_is_mp3/](http://www.khouse.org/pages/mcat/mp3/what_is_mp3/)
What about the "preferred" format of Rythmbox?

---

### Post by tubezninja on 2010-03-27
It's just FUD language.  Yes, the MP3 codec is "non-free" but that doesn't make it illegal.  Fact is, the rights holders for the MP3 spec have made it clear that using MP3 encoders/decoders for personal use is perfectly fine.

[http://mp3licensing.com/help/index.html#5](http://mp3licensing.com/help/index.html#5)
> However, **no license is needed for private, non-commercial activities** (e.g., home-entertainment, receiving broadcasts and creating a personal music library)...

Where it gets dicey is when you crete software software that comes with the codec pre-installed.  The company that owns the patents has a royalty schedule for software distributed as binaries, but FOSS software has gotten around this by distributing LAME source code instead of a compiled binary.

I am not sure how ubuntu handles this, however.

---

### Post by dragos240 on 2010-03-27
> **superarthur said:**
> What about the "preferred" format of Rythmbox?

OGG or flac

---

### Post by superarthur on 2010-03-27
> **dragos240 said:**
> OGG or flac
how is it better than mp3?

---

### Post by NightwishFan on 2010-03-27
Both Ogg Vorbis, and FLAC are patent free.

Ogg Vorbis is similar to mp3 except it is of course free. It compresses audio to save space while retaining audio quality. The quality of vorbis was tested to be higher or equal to competitors such as wma and apple audio.
[http://en.wikipedia.org/wiki/Ogg_vorbis](http://en.wikipedia.org/wiki/Ogg_vorbis)

FLAC is a lossless free software format, which means it creates an exact replica of the audio you convert it from. (Mp3 and vorbis remove quality to save space). I personally use flac, which means I get full quality 44,100hz 16bit CD audio saving almost half the space.
[http://en.wikipedia.org/wiki/Flac](http://en.wikipedia.org/wiki/Flac)

Mp3 is supported by nearly all portable players. Ogg Vorbis is actually supported by many, I am going to buy a player at walmart that does. Flac is supported by a few awesome players, you will have to search yourself for one.

---

### Post by J_Stanton on 2010-03-27
expect the police to come for you in the middle of the night. you are a linux user and have no rights. you have broken the law and will be punished to the full extent. say your goodbye's now, for you will not see the light of day for many years. j/k

---

### Post by superarthur on 2010-03-27
> **J_Stanton said:**
> expect the police to come for you in the middle of the night. you are a linux user and have no rights. you have broken the law and will be punished to the full extent. say your goodbye's now, for you will not see the light of day for many years. j/k
LOL good one ;)

---

### Post by rainbow86 on 2010-03-29
It is complicated, i think you directly change a mp4 player or mp5 player.
Donot need change format.:p
 
Good luck.

---

### Post by gnomeuser on 2010-03-29
> **superarthur said:**
> how is it better than mp3?

Vorbis is designed to be variable bitrate from the beginning. It generally will give you superior quality at the same file size to any lossy format. It's algoritms are very highly tuned for audio quality and it has in fact won multiple listening tests on audiophile websites. Lately it has also gotten very advanced support for surround encoding.

As a secondary but important fact, it is not affected by any known patents (whereas MP3 is covered by patents at least till 2017 - making that the earliest date we can legally ship support). If we were to ship mp3 support that would put Canonical in the line of fire for something called Contributory Patent Infringement which is lawyer speak for "give us all your money and bend over". 

If you happen to live n a country where software patents are not legal, then you can safely install the package. If you do live in a country with software patents, you will be in violation of the law, while the patent holders might not hunt you down being a single person they will very likely go after the entity that gave you the codec, namely here Ubuntu and Canonical.  The only alternative you have if you a unwilling to break the law is to obtain licensed codec support, [Fluendo](http://www.fluendo.com) e.g. sells such codec packs which work with Ubuntu. Their zero cost MP3 decoder is available in the repos for you to use.

The MP3 patent holders have been especially aggressive when it comes to protecting their "property", raiding conferences and having products removed from display for lacking payments. It is just not a viable risk to run.

For the same reason you are not by default equiped to play other formats which are covered by patents.

---

### Post by cascade9 on 2010-03-29
> **NightwishFan said:**
> Mp3 is supported by nearly all portable players. Ogg Vorbis is actually supported by many, I am going to buy a player at walmart that does. Flac is supported by a few awesome players, you will have to search yourself for one.

And a few 'not so awesome'. I have an iRiver e100, supports ogg vorbis and flac, and while its a good little player, I dont count it as being awesome. ;) 

There is also rockbox, that brings support to some players for ogg, flac and lots of other codecs that 99% of people dont care about- MP1, MP2, MP3, AIFF, WAV, Ogg Vorbis (OGG), FLAC, MPC, AC3, WavPack (WV), ALAC, AAC, Shorten (SHN), SID, ADX, NSF, Speex, SPC, APE, WMA

[http://www.rockbox.org/](http://www.rockbox.org/)

---

### Post by BigSilly on 2010-03-29
I'd very much like to move over to Ogg Vorbis if I can. It makes sense in the long run. Does anyone know of any cheapish portable players that are compatible? Vorbis compatibility is not something that is generally advertised with most portable players. Thanks.

---

### Post by doas777 on 2010-03-29
> **dragos240 said:**
> Absolutely not. The mp3 format is NOT illegal.
but using it may be. gotta love that logic.

in the states it is legal to time/format shift media under a personal license, but it is illegal to posses or use any DRM circumvention technologies that would allow you to exercise your shifting rights.

---

