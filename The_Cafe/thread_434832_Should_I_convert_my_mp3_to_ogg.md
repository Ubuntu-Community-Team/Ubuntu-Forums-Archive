---
title: "Should I convert my mp3 to ogg?"
date: 2007-05-06
forum: The Cafe
---

### Post by nphx on 2007-05-06
I have an old used handy down iPod, that works sometimes so I was thinking of getting a iRiver mp3 player. Converting to Linux I thought the proper format to use is ogg over mp3. I've done some research on iRiver Clix it's a video player and mp3 player that supports ogg. 

Do you think converting all my mp3 collection to ogg would be a good idea? Or is it just a waste of time and resources?

 If I wanted to convert a massive mp3 folder what would be the best method to use?

---

### Post by jiminycricket on 2007-05-06
No, you'll lose quality by compressing a lossy format to another lossy format.  Get the originals, or convert from flac or shn (lossless) to ogg.

There's a nice GTK program in the repos that does conversions...

---

### Post by B0rsuk on 2007-05-06
It depends. Keep in mind that both .mp3 and ogg **vorbis*** are lossy formats and you lose some data forever with each encoding. 192 kbit is usually the best a human ear can hear, in case of .mp3 .  Ogg vorbis sounds comparable to 192kbit while having only 160kbit, except for some extremely rare cases like music with castanettes.

If I were in your shoes, I would encode all mp3's into ogg vorbis if they're better than 192kbit . Otherwise you're sure to lose some quality.
If you don't mind sacrificing some disk space to use completely lossless format, try .flac next time you rip a cd. It doesn't have as much compression as lossy codecs, but it sure beats .wavs and is somewhat resistant to data corruption.


* OGG is just container format and it doesn't mean music. What you have in mind is **vorbis** . Ogg can be used to store other media. For example Ogg Theora is a free video codec.

By the way, you can use *mp32ogg* package to conveniently convert mp3 to ogg vorbis.

---

### Post by Nrvnqsr on 2007-05-06
First, what kind of iPod you have? you can try to tinker with it and give new life with rockbox open source firmware.

[http://www.rockbox.org/](http://www.rockbox.org/)

---

### Post by slimdog360 on 2007-05-06
no for two reasons, the first is he loss of quality as already stated and two the extra battery which ogg vorbis will eat up in your player. I have all mine in ogg, but thats because my player has a rated battery life of 53 hours and I like the better sound quality.

---

### Post by forrestcupp on 2007-05-06
No, because it's a waste of time.  The only reason to convert is because of moral objections against non-free stuff.  I don't know about you, but Linux is my OS, not my religion.

---

### Post by Nonno Bassotto on 2007-05-06
Please, don't. There is absolutely no reason to do that, but there are some not to do that (time waste and quality loss). Moreover you will end up with a format that some portable players won't be able to read.

I suggest you rip in ogg your cds, rather than mp3, especially those you didn't already rip, abd keep a mixed collection.

---

### Post by DoctorMO on 2007-05-06
> but Linux is my OS, not my religion.

You know I really have to laugh when this is used as an excuse to support proprietory media formats, since such formats are technically problematic it isn't idealogical reasons that make them a problem is purely technical and legal. The fact that you have no problems with those formats at the moment doesn't mean that you could in the future or that other people won't have problems. it's a rather selfish and short sighted religion in the guise of an anti-religion.

As for the OP, I'd convert them, what the hell sounds like an interesting project.

---

### Post by tbroderick on 2007-05-06
> **nphx said:**
> 
Do you think converting all my mp3 collection to ogg would be a good idea? Or is it just a waste of time and resources?

 If I wanted to convert a massive mp3 folder what would be the best method to use?

I say go for it. Don't worry about converting lossy to lossy. Unless you plan on spending tens of thousands of dollars on stereo equipment, you will not hear a difference. There have been no double blind tests that prove otherwise. I've converted lots of 320 mp3 to quality 4 ogg vorbis and I can not tell the difference. The only difference noticeable is file size, the ogg vorbis is much smaller in size.

I use mp32ogg to convert.
```
mp32ogg --quality=4 --verbose folder/ 
```

---

### Post by PhatStreet on 2007-05-06
> **forrestcupp said:**
> No, because it's a waste of time.  The only reason to convert is because of moral objections against non-free stuff.  I don't know about you, but Linux is my OS, not my religion.
Except Vorbis sounds better at a lower bit rate, using less space. But like others have said, lossy->lossy is usually a no-no.
Personally I convert FLAC to q7/8 Vorbis.

---

### Post by qpieus on 2007-05-06
Unless you have some moral objection to using the proprietary format, don't bother with converting everything. That would be a waste of time....

---

### Post by darweth on 2007-05-06
No, I would never convert lossy to lossy regardless of whether or not I could tell the difference.  I am not an audiophile but I keep to a minimum set of standards.  If I wanted an all-ogg collection, I would seek out FLACs or the original source material.  And both are a waste of time when mp3 suits me perfectly fine.

---

### Post by juxtaposed on 2007-05-06
Transcoding is bad.

---

### Post by tbroderick on 2007-05-06
> **juxtaposed said:**
> Transcoding is bad.

No it's not.

---

### Post by qamelian on 2007-05-06
> **tbroderick said:**
> No it's not.

Yes, it is if you are going from one lossy format to another lossy format. While some people say you can't tell the difference, this is generally only true if both source and destination are using high quality settings and provided that the destination is basically only one step removed from the original source material.

To say that transcoding isn't bad is to demonstrate that you really don't understand how it works.

---

### Post by tbroderick on 2007-05-06
> **qamelian said:**
> Yes, it is if you are going from one lossy format to another lossy format. While some people say you can't tell the difference, this is generally only true if both source and destination are using high quality settings and provided that the destination is basically only one step removed from the original source material.

To say that transcoding isn't bad is to demonstrate that you really don't understand how it works.

Lossy to lossy is 'bad' only if you can hear the difference, and there have been no double blind tests to prove a 'normal' listener can tell the difference. If you got one, let me know (no anecdotal evidence please). If you are playing the music with cheap $100 speakers or $20 headphones, it won't really matter if you transcoded a file or not. The equipment you are using to play the file is far more important then if it's is a 320 mp3 or quality 4 ogg vorbis. I play my ogg vorbis files, some have been transcoded from 320 mp3, on a $1000 stereo and can not tell the difference.

---

### Post by qamelian on 2007-05-06
> **tbroderick said:**
> Lossy to lossy is 'bad' only if you can hear the difference, and there have been no double blind tests to prove a 'normal' listener can tell the difference. If you got one, let me know (no anecdotal evidence please). If you are playing the music with cheap $100 speakers or $20 headphones, it won't really matter if you transcoded a file or not. The equipment you are using to play the file is far more important then if it's is a 320 mp3 or quality 4 ogg vorbis. I play my ogg vorbis files, some have been transcoded from 320 mp3, on a $1000 stereo and can not tell the difference.

Well, I can hear the difference and my sound system is definitely not cheap or poor quality.And even if you personally, can't tell the difference, it isn't difficult to demonstrate the additional loss of quality using freely available audio tools to compare the waveform of both the original data and the transcoded data. Requesting additional test data when you can quite easily do the tests your self is rather silly.

---

### Post by tbroderick on 2007-05-06
> Well, I can hear the difference and my sound system is definitely not cheap or poor quality.

But you already know which file is which. That's why people do double blind test. On my sound system, I hear no difference.

> And even if you personally, can't tell the difference, it isn't difficult to demonstrate the additional loss of quality using freely available audio tools to compare the waveform of both the original data and the transcoded data. 

That's great, but I'm not talking about the technical difference , only the difference to the ear. Realistically, there will be data loss, but for all practical purposes, it only matters what you can hear.

> Requesting additional test data when you can quite easily do the tests your self is rather silly.

I don't see how it is silly. You can do the tests yourself, but you already know which file is which. Double blind tests insure that the participants do not know beforehand if the file was transcoded or what codec was used.

---

### Post by qamelian on 2007-05-06
> **tbroderick said:**
> I don't see how it is silly. You can do the tests yourself, but you already know which file is which. Double blind tests insure that the participants do not know beforehand if the file was transcoded or what codec was used.

Come on now. It isn't that difficult to set up a playlist that shuffles through the files and to score them for yourself (or have someone else do it!) and check after the fact which is which. 

The real test of the ear is when you rip the mp3 and ogg both from the original source. I find the doing this generally shows the ogg to be somewhat higher quality than an mp3 with equivalent qulity settings.

---

### Post by darweth on 2007-05-06
I personally like v2 mp3 and cannot tell the difference when it comes to anything above that.  Hell, 192 cbr is probably good enough.  Hard to tell there.  320 is super overkill and useless.  And I don't even want to talk about FLAC.  

Most of my music is in v0 mp3 because that is the acceptable standard in illicit communities which will go unnamed.  When it comes to mp3... I think 192/v2/v0 are all fine choices.  Anything above (in cbr form) is overkill.

I wish ogg was the standard, but it is not.

The punk band American Steel are back together!!!!!!!

---

### Post by kopinux on 2007-05-06
according to the vorbis site, to avoid loosing quality is uncompressing a ex: 128kbit mp3 into wav then converting wav to 128kbit ogg. but doing that will take a lot of time and the tag will be removed, not unless you get an auto software to do that. i think the sound konverter in ubuntu does that.

---

### Post by timpino on 2007-05-06
Don't do it.

Alot of people say you can't hear the difference between them on cheap headphones and the like, but what if 5 years from now you whent and bought some $500 headphones or the like?

If it aint broke, why fix it?

---

### Post by Sweet Spot on 2007-05-07
> **kopinux said:**
> according to the vorbis site, to avoid loosing quality is uncompressing a ex: 128kbit mp3 into wav then converting wav to 128kbit ogg. but doing that will take a lot of time and the tag will be removed, not unless you get an auto software to do that. i think the sound konverter in ubuntu does that.

That is totally misleading and WRONG information. First off, you can NOT put bits of information BACK into a file, no matter what. Converting to wav is useless and futile and a waste of time (much like the redundancy of that sentence). Secondly, going from 128p kbps, which is a pretty bad quality file in and of its self unless you're using crappy equipment which won't expose that, then to wav and then back to Ogg Vorbis is just plain stupid.   Thirdly, the entire idea is stupid to begin with no matter what, for the reason which timpino has stated below:

> **timpino said:**
> Don't do it.

Alot of people say you can't hear the difference between them on cheap headphones and the like, but what if 5 years from now you whent and bought some $500 headphones or the like?

If it aint broke, why fix it?

I was at work earlier and had typed a whole paragraph on this example, but didn't have time to post it, so it was squashed. To reiterate what timpino has said.... You'll feel awfully bad if one day down the road you choose to buy a nice set of IEM's or in ear canal phones which excel in terms of detail, and you come to find out that your files are now a swooshy, garbled mess, and that you could have avoided that from happening if only......... 

Seriously, HORRIBLE idea. And also consider this too please: There are people whom are saying that "most people" can't tell the difference between a 128 kbps, 320 kbps file, or a FLAC file or the original source file.... Some things to say about that:  A lot of things are left to chance. There IS the chance that if you took an average Joe from the street, and gave him an ABX test, he either could or could not tell the difference between above said files. 

There also is the CHANCE, that the same could be said about your standard audiophile. Nothing is for sure. With that said, what if you are one of those people whom IS able to tell the difference ?  I'd hate for you to have to find out the hard way man. Think about it, and do the right thing. Don't be lazy. Take the time to re rip and encode if you MUST use Ogg files. 

I'd also like to say, why do you feel the need to use Ogg anyway ? It's not like the Clix line does gapless playback with it, as opposed to with LAME encoded Mp3's ?  And one more thing, if you do purchase a Clix 2...  (hope the mods don't mind me doing this) come on over to [Misticriver]("http://www.misticriver.net") and join the community for discussions and or technical help w/iRiver brand DAP's (we do also talk about other dAP's, but started out w/iRiver stuff and do especially cater to iRiver products).  We ARE the premier iRiver site on the net. ;)

---

### Post by forrestcupp on 2007-05-07
> **DoctorMO said:**
> You know I really have to laugh when this is used as an excuse to support proprietory media formats, since such formats are technically problematic it isn't idealogical reasons that make them a problem is purely technical and legal. The fact that you have no problems with those formats at the moment doesn't mean that you could in the future or that other people won't have problems. it's a rather selfish and short sighted religion in the guise of an anti-religion.

I'm not anti-religion; I'm anti-making-Linux-a-religion.  At least in my own life.  If I ever have trouble with a certain proprietary format, that is when I'll switch.  If I'm not having trouble, why waste my time?

 While creating original ogg's may sound better than mp3's, I seriously doubt that creating an ogg from an mp3 will make it sound better than the original mp3.  It may or may not sound worse, but you can't make something sound better than the original by just converting the format.  The only good argument I've heard to convert is that  the filesize is smaller.  Is it worth the time that it will take just to save a couple of megs?  If so, go for it.

---

### Post by omns on 2007-05-07
> **forrestcupp said:**
> If I ever have trouble with a certain proprietary format, that is when I'll switch.  If I'm not having trouble, why waste my time?

ditto

---

### Post by Arathorn on 2007-05-07
If you wait long enough, the mp3 patents will expire in a few years' time. ;)
But still, transcoding lossy to lossy is very bad, avoid it.

---

### Post by gashcr on 2007-05-07
I'd say... Try it with one file only, if you get to notice the difference, it's up to you to continue with the rest. In the end, the only important thing is making what makes you feel comfortable. My advice is, don't do drastic changes that could lead to ruin your whole collection. In these cases is better to work with "lab rats", jaja.

---

### Post by Sweet Spot on 2007-05-07
> **gashcr said:**
> I'd say... Try it with one file only, if you get to notice the difference, it's up to you to continue with the rest. In the end, the only important thing is making what makes you feel comfortable. My advice is, don't do drastic changes that could lead to ruin your whole collection. In these cases is better to work with "lab rats", jaja.

Again, this is kind of pointless. IF on the off chance that he can't detect a degradation in sound quality when doing this with one file, that doesn't necessarily mean that he won't detect it using alternative hardware, which he may not even own yet. Also, some files or songs don't always exhibit the kind of compression artifacts which others do, so playing around with one, two or even a bunch of files may not prodauce an answer here.

Seriously dude, play it safe. Think about it: If you purchased all of your mp3 files from an music service, would you be so bold as to experiment with them, only to find out that you had wasted your money ? I'd hope not. 

Why don't you do this:  Rip a few CD's. Encode to 128 kbps. Then convert those files to Vorbis files. Then:

1) attempt to get a hold of a really good pair of cans or IEM's and test BOTH files (keep original of course) and use them with your DAP of choice. 

2) Perhaps also try using the DAP's line out going to a really nice home audio set up which has good speakers too ? 

Might sound like overkill, but could save you a big headache in the future.

---

### Post by TravisNewman on 2007-05-07
I have done this before, and then performed double blind studies of my own-- I was changing the tracks while a friend listened, and then my friend changed the tracks while I listened. I made sure to get a wide variety of encoding schemes on my mp3s. My friend and I could tell a difference on all but a few. In general, if the mp3 is encoded at 320 it's pretty safe to transcode without much loss, but in the others I could definitely tell. Some sounded like they'd been recorded in the bathroom.

---

