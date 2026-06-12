---
title: "new codec-handling from Fedora"
date: 2007-11-09
forum: The Cafe
---

### Post by newbie2 on 2007-11-09
> The Fedora development community has traditionally declined to include codecs for proprietary encumbered multimedia formats in the distribution for legal and ideological reasons, encouraging users to adopt open formats like Ogg Vorbis and Theora instead. That hasn't changed in Fedora 8, but the new Codeina utility (don't call it Codec Buddy) will now make it possible for users to legally purchase support for proprietary formats directly from Fluendo. This is different from Ubuntu's codec installation tool, which will allow the user to install infringing open-source codecs for free that may not be legal to use in certain countries.
[http://origin.arstechnica.com/news.ars/post/20071108-an-old-hat-with-new-tricks-fedora-8-officially-released.html](http://origin.arstechnica.com/news.ars/post/20071108-an-old-hat-with-new-tricks-fedora-8-officially-released.html)
[http://fedoraproject.org/wiki/Interviews/CodecBuddy](http://fedoraproject.org/wiki/Interviews/CodecBuddy)

---

### Post by bruce89 on 2007-11-09
What if you live in Britain where such patents don't apply?

I never use proprietary formats for personal use, but I use the extra gstreamer codecs for other media where the distributor is an eejit.

---

### Post by Phil Airtime on 2007-11-09
There's a third-party repository called Livna, which I think is based in France, that you can add to Fedora to provide the same codecs, as well as other closed-source bits like video drivers.

---

### Post by BigSilly on 2007-11-09
> **bruce89 said:**
> What if you live in Britain where such patents don't apply?


Exactly. It's yet more mud-slinging from other distros.

---

### Post by bruce89 on 2007-11-09
> **BigSilly said:**
> Exactly. It's yet more mud-slinging from other distros.

Or indeed, anywhere apart from the USA. I hate the USA=world attitude Americans appear to have.

---

### Post by the_darkside_986 on 2007-11-09
I usually just get mplayer and the binary packages from their main site. Then I try to convert all restricted formats to free formats. I can only do this with music. The last time I tried to convert a quicktime movie file to theora, the theora video's image went way out of sync with the sound. 

patent laws are abused, but there should be much more encouragement to transcode and encode one's media into free formats instead of just making it easy to play them.

---

### Post by Erunno on 2007-11-09
> **BigSilly said:**
> Exactly. It's yet more mud-slinging from other distros.

It doesn't matter if the laws don't apply outside of the United States as RedHat is an US based company and liable under the US patent and copyright laws (contrary to Canonical which have their headquarters in the UK).

---

### Post by bruce89 on 2007-11-09
> **Erunno said:**
> It doesn't matter if the laws don't apply outside of the United States as RedHat is an US based company and liable under the US patent and copyright laws (contrary to Canonical which have their headquarters in the UK).

The Isle of Man is not really part of the UK, it's a "self-governing Crown dependency".

---

### Post by DoctorMO on 2007-11-09
> It doesn't matter if the laws don't apply outside of the United States as RedHat is an US based company and liable under the US patent and copyright laws (contrary to Canonical which have their headquarters in the UK).

Codecs are a very complex issue; We have Copyright violations (win32codecs), _possible_ software patent violations (liblame,ffmpeg) and then cryptographic problems (libdvdcss) involving the DMCA/EUCD.

I'd work on reverse engineering win32codecs which is happening slowly as ffmpeg I believe has wmv support these days. Anyone in the EU or certain other countries can use liblame and ffmpeg although since there has been no court case, and don't get me started on the last issue; lets just say it probably _isn't_ legal in the EU either.

---

### Post by professor fate on 2007-11-09
> **bruce89 said:**
> Or indeed, anywhere apart from the USA. I hate the USA=world attitude Americans appear to have.

I don't have that attitude and I'm an American.

---

### Post by jsmidt on 2007-11-09
> **bruce89 said:**
> Or indeed, anywhere apart from the USA. I hate the USA=world attitude Americans appear to have.

The issue here is stereotyping.  Many, if not most Americans favor us to have great relations with other countries where we aren't worried about who is superior.  

We aren't like people in Scotland who run around in kilts all day getting in massive beer brawls over redheads. :)

(Please know the comment was only a joke about stereotyping and not meant to insult.)

---

### Post by bruce89 on 2007-11-09
> **jsmidt said:**
> (Please know the comment was only a joke about stereotyping and not meant to insult.)

I'm Scottish, not English, so no offence taken.

Anyway, I'm sure most normal Americans are fine, it was a generalisation so I didn't have to type more.

Back on topic, I have no need for win32codecs, the normal extra gstreamer plugins are good enough.

---

### Post by tehet on 2007-11-09
> **BigSilly]It's yet more mud-slinging from other distros.[/quote]
The quote the OP posted is from Arstechnica. In fact Ubuntu is not mentioned in the Fedora intie.
[QUOTE=bruce89 said:**
> Or indeed, anywhere apart from the USA. I hate the USA=world attitude Americans appear to have.
The quote states "in certain countries" which is accurate enough cause this does not apply to the US only. I'm not from the US and I really don't see the problem in this particular case.

As far as paying for it in my view only acknowledges / condones somehing as broken as software patents. Civil disobedience ftw.

---

### Post by vexorian on 2007-11-09
I actually think that it would be denigrating for me, as a customer to have to pay for any codec in general,  whether I do it directly (like in windows/Linspire) or indirectly like on this case. I only want a little respect as a consumer but you see how the big media and software companies don't have any respect left for you.

Edit: This said, US ubuntu users that do care about this stuff should request canonical to try the same for Hardy, could even use the same store.

---

### Post by SunnyRabbiera on 2007-11-09
well if a store was offered I would use it happily.

---

### Post by MethodOne on 2007-11-09
Too bad Fluendo doesn't offer a CSS GStreamer plugin or a libdvdcss replacement library.  That would be great if it did because I don't have to put up with those proprietary players, like LinDVD, only bundled with or sold for commercial distributions.

---

### Post by BigSilly on 2007-11-10
Software patents are a load of cobblers. I think I already mentioned on here a big patent that Sega (the video games company) actually own - how the game camera moves around 3D graphics. [I think this is one example of their patents. ]("http://gauss.ffii.org/PatentView/EP841640")Surely if they were to call in things like this, they could destroy the games industry! Everyone must be guilty of infringing this.

I feel, as a consumer, that if I buy a DVD legitimately (and I do, lots of them!) then surely I have already "paid my dues" to the people who own the rights to the software. Why should I pay again to be able to play the thing on a PC? Ditto MP3's. I buy audiobooks legitimately, have I not paid my dues here too?

If there was such a store for Ubuntu, I wouldn't pay to use it. Maybe if I was having to buy a program like a DVD player of some sort  then yeah, but a* codec*...? I agree with vexorian above.

---

