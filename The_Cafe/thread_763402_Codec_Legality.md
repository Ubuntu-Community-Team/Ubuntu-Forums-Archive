---
title: "Codec Legality"
date: 2008-04-23
forum: The Cafe
---

### Post by ubunnies on 2008-04-23
Just wanted to introduce myself. Been a long time Red Hat and Fedora user. I've been enjoying Ubuntu since the release of Gutsy.

One of the big things about Fedora is only including open source software. Of course users are free to add anything from anywhere, but Fedora itself would only release OSS. Obviously, this makes it very tough for new Linux users, and Ubuntu does a wonderful job with that. 

I came across this fedora thread where they started discussing the codec situation in Fedora vs Ubuntu: [https://www.redhat.com/archives/fedora-list/2008-April/msg02068.html](https://www.redhat.com/archives/fedora-list/2008-April/msg02068.html)

Since Fedora is sponsored by Red Hat, an American company, they have to watch out for patent issues in the US, so its difficult for them to distribute codecs for mp3s and dvds. Since Canonical is based out of Isle of Man and many countries don't allow software patents, its ok for the codecs to be in the Ubuntu repos. 

The reality is that many users live in countries, like the US, where patents are enforced, and are probably still using the mp3/dvd codecs without paying for them. Even though Ubuntu does not actively distribute it (in fact users have to choose to retrieve it since its not installed by default), can there be trouble for Ubuntu just for making it easily accessible?

I'm just wondering if this will cause issues down the line when Ubuntu has many more users. Microsoft just paid a billion dollars for patent violations, could something like this happen with Ubuntu?

thanks.

---

### Post by LaRoza on 2008-04-23
> **ubunnies said:**
> 
The reality is that many users live in countries, like the US, where patents are enforced, and are probably still using the mp3/dvd codecs without paying for them. Even though Ubuntu does not actively distribute it (in fact users have to choose to retrieve it since its not installed by default), can there be trouble for Ubuntu just for making it easily accessible?

I'm just wondering if this will cause issues down the line when Ubuntu has many more users. Microsoft just paid a billion dollars for patent violations, could something like this happen with Ubuntu?


No. VLC (even the Windows version) includes such codecs, and I know of no instances of any legal action. 

It is mostly a philosophical reason for not including them, as they aren't "free" in every sense of the word. The DMCA (that weird US law) has exceptions, and I feel that these codecs fall under them. 

MS doesn't have these patents. It won't happen. How would it be enforced? Who would be sued?

---

### Post by SoulinEther on 2008-04-23
As far as I know, the responsibility is borne by the user, not by the maker. to pay all royalties associated with using a codec if the decoder/encoder (er, codec) is "free" as in beer. If they wish to sell the codec/licenses to people, then the developer has to pay for the royalties themselves, I believe.

But.. when Apple provides you with iTunes for free, which can convert files to MP3, MP4, etc., either Apple is part of the patent protection thing, or they are covering the cost of users... otherwise, most people are in some serious issues. Unless, like LaRoza stated, the DMCA does not cover codecs....

But I don't believe in such nonsense. I have the right to save my files using whatever compression algorithm I desire.... who are you to say I can't? I don't believe one can, but, if anything, charge me for stealing the method, but you cannot charge me for using it!

---

### Post by jrusso2 on 2008-04-23
> **ubunnies said:**
> Just wanted to introduce myself. Been a long time Red Hat and Fedora user. I've been enjoying Ubuntu since the release of Gutsy.

One of the big things about Fedora is only including open source software. Of course users are free to add anything from anywhere, but Fedora itself would only release OSS. Obviously, this makes it very tough for new Linux users, and Ubuntu does a wonderful job with that. 

I came across this fedora thread where they started discussing the codec situation in Fedora vs Ubuntu: [https://www.redhat.com/archives/fedora-list/2008-April/msg02068.html](https://www.redhat.com/archives/fedora-list/2008-April/msg02068.html)

Since Fedora is sponsored by Red Hat, an American company, they have to watch out for patent issues in the US, so its difficult for them to distribute codecs for mp3s and dvds. Since Canonical is based out of Isle of Man and many countries don't allow software patents, its ok for the codecs to be in the Ubuntu repos. 

The reality is that many users live in countries, like the US, where patents are enforced, and are probably still using the mp3/dvd codecs without paying for them. Even though Ubuntu does not actively distribute it (in fact users have to choose to retrieve it since its not installed by default), can there be trouble for Ubuntu just for making it easily accessible?

I'm just wondering if this will cause issues down the line when Ubuntu has many more users. Microsoft just paid a billion dollars for patent violations, could something like this happen with Ubuntu?

thanks.

This is in fact more of a philosophical choice then a legal one.  Freespire is based in the USA and provides codecs in their Ubuntu based distro.  They just contacted the companies and made arrangements to provide them.  I am sure they had to pay a minimal fee for the use of some of them, but heck thats a very small price to pay.

---

### Post by macogw on 2008-04-23
There are also certain codecs where the patent holders have said "free license to FOSS.  commercial people must pay" I think MP3 is actually one of these.

---

### Post by Polygon on 2008-04-23
> **macogw said:**
> There are also certain codecs where the patent holders have said "free license to FOSS.  commercial people must pay" I think MP3 is actually one of these.

it cant be, then why isnt mp3 playback enabled by default then if its 'free for foss, but not for commercial?"

---

### Post by macogw on 2008-04-23
> **Polygon said:**
> it cant be, then why isnt mp3 playback enabled by default then if its 'free for foss, but not for commercial?"
from Wikipedia:
> Additionally, patent holders declined to enforce license fees on free and open source decoders, which allows many free MP3 decoders to develop.  Furthermore, while attempts have been made to discourage distribution of encoder binaries, Thomson has stated that individuals who use free MP3 encoders are not required to pay fees. Thus, while patent fees have been an issue for companies that attempt to use MP3, they have not meaningfully impacted users, which allows the format to grow in popularity.
Thomson only charges for commercial mp3 encoders/decoders, but there are other entities claiming they own some part of mp3 too.  The free-patent-fee deal also probably only applies when the people distributing are the ones making the software, and so it wouldn't extend to you copying the CD to give to your friend.

---

### Post by SoulinEther on 2008-04-23
Also from wikipedia ([http://en.wikipedia.org/wiki/MPEG-2#Patent_holders](http://en.wikipedia.org/wiki/MPEG-2#Patent_holders))

> According to the MPEG-LA Licensing Agreement MPEG-LA, any use of MPEG-2 technology is subject to royalties.

    * Encoders are subject to a royalty of $2.50 per unit.
    * Decoders are subject to a royalty of $2.50 per unit.[5]
    * Royalty-based sales of encoders and decoders are subject to different rules and $2.50 per unit.[5]
    * Also, any packaged medium (DVDs/Data Streams) is subject to licence fees according to length of recording/broadcast.

In the case of free software such as VLC media player (which uses the ffmpeg library) and in which the software is not sold, the end-user bears the royalty.

I am assuming that MPEG-2 video and MPEG audio are umbrellaed under the same category...

---

### Post by hyper_ch on 2008-04-23
> **Polygon said:**
> it cant be, then why isnt mp3 playback enabled by default then if its 'free for foss, but not for commercial?"

Free beer != Free speech

So it might be free of charge but not free in spirit ;)

---

### Post by bonzodog on 2008-04-23
The other big thing here is that Canonical, the company that runs Ubuntu, is based on the Isle of Man, between the Uk and Ireland. This tiny island is in a funny place legally, as, well, it doesn't have anything to do with the rest of the world law wise, has never been party to any international agreements, and is not part of the EU, though it is part of the EEC. It has a government called "The Tynewald", which predates written history. It is technically a Crown Dependency of the UK.
Therefore, Canonical do not have to listen to US law, or even UK law for that matter as concerns the Ubuntu distribution. The main reason Canonical chose to set up on the Island is because it also has no corporate taxation system of any kind.

---

### Post by jespdj on 2008-04-23
> **Polygon said:**
> it cant be, then why isnt mp3 playback enabled by default then if its 'free for foss, but not for commercial?"
As explained above, these codecs are not included because of the "free as in speech" philosophy. Even if the codecs cost nothing (free as in beer), they are still not open source / free as in speech, so they will not be included by default in Ubuntu.

---

### Post by stmiller on 2008-04-23
^This is true. If you ever read Shuttleworth's ideas he is against all proprietary things such as Adobe flash, mp3, .doc, quicktime, everything.

---

### Post by SunnyRabbiera on 2008-04-23
> **macogw said:**
> from Wikipedia:

Thomson only charges for commercial mp3 encoders/decoders, but there are other entities claiming they own some part of mp3 too.  The free-patent-fee deal also probably only applies when the people distributing are the ones making the software, and so it wouldn't extend to you copying the CD to give to your friend.

Yeh but by all standards MP3 right now is more open source then the other proprietary formats with them letting people use the codec on more then one OS

---

### Post by tikal26 on 2008-04-23
I think that some of this codecs are not included because they are not open source. As far as I know fluendo provides mp3 suport for free and it is included in the repos. I think that the only thing that might be 'illegal' is the microsoft codecs, but it is definetly  a grey area. If you want to feel better about it and safe you can buy them from fluendo. they sell them for linux

---

### Post by drascus on 2008-04-23
Interesting question. First of all every country's patent system is separate from every other one. So a US company could not sue a company in country X if they didn't have a patent in country X. Also if country X didn't have a patent system there would be no way to enforce patents in that country. Now individuals can be sued for Patent infringement that is true. However this is usually a strategical move in order to get some company to pay a bunch of money to the patent holder. In this case that wouldn't happen because Canonical doesn't have a bunch of money and doesn't fall under US jurisdiction. 
This of course doesn't mean patents aren't an issue. The ultimate goal is to get rid of software Patents all together. Then their would be no guess work or danger. Everyone could just use or develop anything they want without need for tons of lawyers expenses and legalities.

---

### Post by jespdj on 2008-04-23
> **SunnyRabbiera said:**
> Yeh but by all standards MP3 right now is more open source then the other proprietary formats with them letting people use the codec on more then one OS
It doesn't matter if it is used as if it is patent/license free *in practice* - it's really *officially* not free as in speech, and it isn't included in Ubuntu because it's not officially free as in speech. This is about principles, not about how it is in practice.

---

### Post by ssam on 2008-04-23
you can always pay for licensed codecs from fluendo. if things got nasty (and noone could defeat the patents) then effect people would have to pay 28 euros if they wanted to use those codecs.

---

