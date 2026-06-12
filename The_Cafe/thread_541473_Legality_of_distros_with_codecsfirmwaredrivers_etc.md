---
title: "Legality of distros with codecs/firmware/drivers etc."
date: 2007-09-02
forum: The Cafe
---

### Post by Ozor Mox on 2007-09-02
Something I've been wondering while reading about other Linux distributions...

The ones that supply the codecs for playing DVDs, MP3s, WMVs etc. the firmware and drivers for wireless cards and graphics cards and so on...all the things that Ubuntu does not provide out of the box because of their commitment to free software...are they being legally distributed? Do these distributors pay a license fee for the use of them, and how do the ones providing their distribution for free do this? Xandros and Linspire for example could pay legally, but I doubt that PCLinuxOS or Linux Mint could (distros with proprietary stuff out of the box) Or do they just supply them on the assumption that although they are technically not legal, it's very unlikely that anyone is going to make a fuss.

Does the same legal status apply when someone downloads the restricted codes/firmware/drivers etc. for Ubuntu? I've set up my system to play DVDs and MP3s...what is the legality of that?

Just curious!

---

### Post by aysiu on 2007-09-03
> **Ozor Mox said:**
> Something I've been wondering while reading about other Linux distributions...

The ones that supply the codecs for playing DVDs, MP3s, WMVs etc. the firmware and drivers for wireless cards and graphics cards and so on...all the things that Ubuntu does not provide out of the box because of their commitment to free software...are they being legally distributed? Do these distributors pay a license fee for the use of them, and how do the ones providing their distribution for free do this? Xandros and Linspire for example could pay legally, but I doubt that PCLinuxOS or Linux Mint could (distros with proprietary stuff out of the box) Or do they just supply them on the assumption that although they are technically not legal, it's very unlikely that anyone is going to make a fuss. Linux Mint has a "light" edition for the US and a few other countries: [quote=Linux Mint About Page]**Why is there a Light Edition and a Full Edition?**
Linux Mint respects the GPL and it also respects the copyrights and licenses of the proprietary software it distributes. However it uses technologies that have been patented in some parts of the World. Most countries do not recognize the legitimacy of software patents so for most of our users this is not a problem. But if you're unlucky and you live in a country where software patents are legally enforcable, you need a version of Linux Mint which is free of patented technologies, and this is what the Light Edition is about.  [/quote] PCLinuxOS doesn't even try to explain about legality.

> Does the same legal status apply when someone downloads the restricted codes/firmware/drivers etc. for Ubuntu? I've set up my system to play DVDs and MP3s...what is the legality of that? It depends on what country you live in, how you interpret the law, and which codecs you're talking about. You're fine with MP3 playback. You're probably fine for *libdvdcss*. And you're probably not fine with *w32codecs*. Read more here:
[http://ubuntucat.wordpress.com/2007/05/28/the-legality-or-illegality-of-w32codecs-and-libdvdcss2/](http://ubuntucat.wordpress.com/2007/05/28/the-legality-or-illegality-of-w32codecs-and-libdvdcss2/)

---

### Post by Steveway on 2007-09-03
They should just add a mark:
Not legal in the United States of America.
And they should be fine.
Most other countrys don't have these stupid laws.

---

### Post by Ozor Mox on 2007-09-03
I see, thanks aysiu. I am of course sticking with Ubuntu because it's great, but I was just curious...I suppose here in the UK it's pretty much ok to download MP3 and DVD playing software.

:popcorn:

---

### Post by aysiu on 2007-09-03
Don't forget that Ubuntu also has [philosophical considerations](http://www.ubuntu.com/community/ubuntustory/philosophy) in addition to legal ones: [quote=Ubuntu Philosophy Page]For Ubuntu, the 'free' in 'free software' is used primarily in reference to freedom, and not to price - although we are committed to not charging for Ubuntu. The most important thing about Ubuntu is that it confers rights of software freedom on the people who install and use it. It is these freedoms that enable the Ubuntu community to grow, continue to share its collective experience and expertise to improve Ubuntu and make it suitable for use in new countries and new industries.[/quote]

---

### Post by bigbearomaha on 2007-09-03
[FONT=Verdana]Many of these distros solve the situation by making the questionable codecs, etc, easily accessible and available but not outright pre installed.  that confers the responsibility of installing and using said "illegal" items upon the end user.

Because there are so many countries who do not have laws that support IP patents, etc and a few that do, one cannot reasonably expect the devs and distributors to keep track of who or where the distro is being used.  So, to make it accessible is not an issue as it does not actually install and have the "offending" codecs, etc.

Big Bear
[/FONT]

---

### Post by aysiu on 2007-09-03
> **bigbearomaha said:**
> Many of these distros solve the situation by making the questionable codecs, etc, easily accessible and available but not outright pre installed.  that confers the responsibility of installing and using said "illegal" items upon the end user. As far as I know, the distros in question (Linux Mint and PCLinuxOS) don't just make the codecs accessible--they actually preinstall the codecs.

---

### Post by wolfen69 on 2007-09-03
watch out, the Codec Police are watching!

---

### Post by Ozor Mox on 2007-09-03
> **aysiu said:**
> As far as I know, the distros in question (Linux Mint and PCLinuxOS) don't just make the codecs accessible--they actually preinstall the codecs.

That was the key difference that I could see when I originally posted. In distros like Ubuntu and Debian, the codecs are available but up to the end-user to install if they like. In Linux Mint and PCLinuxOS and I'm sure several other distros, they are pre-installed, but not paid for as far as I know like they are in Linspire for example.

Personally, I prefer Ubuntu's way of doing things, but I accept that pre-installed codecs etc. make "the switch" easier...despite their apparently questionable legal status.

I suppose we'll only know for sure if and when one of these distros is called up on this.

---

### Post by BuffaloX on 2007-09-03
I don't get why there's such a fuss about this.

Ususally any maker of a codec, want as many as possible to have access to it.
Therefore the decoder is usually available for free, but the encoder cost money.
Sometimes even the encoder is free, and only cost money if you want the most advanced encoding with better compression to quality ratio.

Only exception to this AFAIK is DVD, because the movie industry wants to control separate markets. The industry have lost court cases about this in Europe, because a customer is entitled to be able to play back DVD's.

If I was a distro maker, I would enable all codecs for playback, but only open sourced codecs for encoding.

---

### Post by mips on 2007-09-03
> **aysiu said:**
> As far as I know, the distros in question (Linux Mint and PCLinuxOS) don't just make the codecs accessible--they actually preinstall the codecs.

Same for Sabayon which I use. Every thing from codecs, dvd to gfx drivers work out of the box.

---

### Post by hysteresis on 2007-09-03
PCLOS does not pre install win32 codecs or libdvdcss but they are available in their repositories

---

### Post by hysteresis on 2007-09-03
PCLinuxOS does not pre install win32 codecs or libdvdcss but they are available in their repositories

---

