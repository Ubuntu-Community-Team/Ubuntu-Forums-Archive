---
title: "How do you know if codecs are legal in your country?"
date: 2009-02-25
forum: The Cafe
---

### Post by ArtF10 on 2009-02-25
How can one tell whether their country allows(legally) multimedia codecs(that are installed in steps 1-5 of this link:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683))[SIZE="7"]**?**[/SIZE])

For the particular system I am talking about(Ubuntu 8.04 or 8.10...can't remember), the install will be used by a person who is on a vacation in Canada and the U.S.

---

### Post by kelvin spratt on 2009-02-25
I think it mainly the US that has these draconian laws. certainly not the uk.

---

### Post by Skripka on 2009-02-25
> **kelvin spratt said:**
> I think it mainly the US that has these draconian laws. certainly not the uk.

About the only way to know is to hire an IP lawyer, and the fees alone will probably be equivalent to a 500-computer site-license for Vista Ultimate.

---

### Post by Dekkon on 2009-02-25
I'm sure it's illegal in the U.S. but that doesn't stop me from installing them, using proprietary codecs is a "necessity" for me.

---

### Post by swoll1980 on 2009-02-25
If you bought the computer with the codecs preinstalled then you already bought the rights to use them doesn't matter what country your in.

---

### Post by ArtF10 on 2009-02-25
What if one is doing a fresh install(of Ubuntu).....in that case if one choses to install the codecs themselves, can they first check to nmake suer that it is legal in their country?

---

### Post by Skripka on 2009-02-25
> **swoll1980 said:**
> If you bought the computer with the codecs preinstalled then you already bought the rights to use them doesn't matter what country your in.

A supermajority of Linux users download Linux and install it, and those proprietary codecs....having never "bought" rights to them with their box.  Most computers (of any OS) don't have said codecs preinstalled.

---

### Post by Kvark on 2009-02-25
I'm as sure as a non-lawyer can be (which is not very sure at all) that they're legal here in Sweden. It's not possible to patent math here so for example the LGPL'd LAME mp3 encoder is not proprietary here. It's illegal to crack copy protection so you could end up in court for using DeCSS to watch legal DVDs. Such a case has never been tried but the courts would most likely equal it to someone who was arrested for bike theft when cutting their own bike lock after losing the key.

---

### Post by mkendall on 2009-02-25
My view: if you load the codecs and the interweb police don't jump out of their tubes to arrest you, then it's legal.

---

### Post by BuffaloX on 2009-02-25
I don't know all codecs installed with those packages, put you are probably concerned with mp3, mpeg2+css and maybe Microsoft.

If you check mp3 on wikipedia it says:

> patent holders declined to enforce license fees on free and open source decoders, which allows many free MP3 decoders to develop

So it seems you are in the clear, at least unless Thomson change their mind.

If you need to play DVD you need mpeg2, but before mpeg2 can decode the video it must be descrambled, for that you need a descrambler with a key. This seems to be impossible to do legally in the US with open source, since the mere publishing of a useable key is illegal.

I'm not sure about the MS codecs, MS opened up some codecs, because they want Moonlight to be compatible with Silverlight, (so they can push flash out of the market), a firefox extension called moonshine utilize these codecs to enable general playback in Firefox with MS codecs.

I don't think there are other codecs that should be a problem.

None of the above codecs nor css should be a problem in the EU AFAIK.

Anyways to be sure you probably must buy the Fluendo codec pack.
I think the price in the Ubuntu shop is pretty competitive. :D

---

### Post by ArtF10 on 2009-02-25
Ok so that's roughly USD 40.00 every 3 years(assuming you install it on ONLY the LTS versions).  I guess that the good thing is that if you have to reformat the hard drive(if you decide to tweak Ubuntu and totally mess up something) you can re-download the software at no extra cost.

---

### Post by hansdown on 2009-02-25
Hi ArtF10.

The canadian parliament hasn't managed to pass any law to date.

---

### Post by I-75 on 2009-02-25
A good argument would be what if you decide to dual boot Linux on a Windows computer. Since through the Windows license you have rights to the codecs on that computer. So if you use Linux and listen to MP3's and watch DVDs on that same computer then you could be OK legally in the U.S.

---

### Post by Bart_D on 2009-02-25
@ArtF10, this is from the Mint Linux website:

Linux Mint Universal Edition
This edition aims to provide the same features as the Main Edition **without including proprietary softwar**e, patented technologies or support for restricted formats. **If you're** a magazine, a reseller or a distributor in Japan or **in the USA then choose this edition**.

Source:  [http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

The way I would interpret that is IF you are in the U.S., then you CANNOT use them.  While you are in Canada, you can use them.  Atleast that's what I would take from that statement.

---

### Post by ArtF10 on 2009-02-25
> **hansdown said:**
> Hi ArtF10.

The canadian parliament hasn't managed to pass any law to date.

Phew!!!  That was a close one......

---

### Post by BuffaloX on 2009-02-25
If you buy Fluendo it seems you get a deb file, that you'll probably be able to install on your next Ubuntu too.

[http://ubuntuforums.org/showthread.php?t=962543&highlight=fluendo]("http://ubuntuforums.org/showthread.php?t=962543&highlight=fluendo")

---

### Post by hansdown on 2009-02-25
> **ArtF10 said:**
> Phew!!!  That was a close one......

I know, right?

This might help.

[http://www.google.ca/search?q=bill+c-60&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=bill+c-60&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

I can't speak for the U.S.A.

---

### Post by TalioGladius on 2009-02-25
Personally, retarded laws like that shouldn't stop you from doing anything.

---

### Post by Ms_Angel_D on 2009-02-25
If you've ever bought a copy of windows, doesn't that give you license to use those codecs anyway?

---

### Post by perce on 2009-02-26
I'm not a lawyer, but as far as I've understood from various posts here and in Debian, nobody really knows at what extent restricted codecs are illegal, even in the United States. There are two different type of problems: DMCA-related ones for dvdcss and patents for MP3, MPEG and MS. Whatching a legally purchased DVD in your legally purchased computer using dvdcss is definitely illegal according to DMCA, but it is very unlikely that it will ever be enforced (remember the US are a common law country) and even if it is, there are conflicting laws about fair use that may protect the user. Patents must be defended in court, and there is a recent ruling that seemed to put in danger most software patents. Moreover, nobody will ever sue thousands of private users individually for breaking a patent simply because it's not economically profitable. Here the risk is more for the distributor of patented software, which is much more likely to be sued.

One last remark, that nobody seems to care about, but it's as important as all other legal objections from a moral point of view: patents and the GPL are incompatible if you have not the right to grant the use of the patents along with the program, so the restricted codecs, in the US, are infringing the GPL.

---

### Post by Chame_Wizard on 2009-02-26
Here in the Nethelands,it's freely legal to download(the law permits it).:lolflag:

---

### Post by jespdj on 2009-02-26
> **Chame_Wizard said:**
> Here in the Nethelands,it's freely legal to download(the law permits it).:lolflag:
It's legal to download copyrighted material; it is illegal to offer copyrighted material. So, this means that if you download illegally copied music or movies, it's the responsibility of the person that offers the stuff on the Internet, not of the one who downloads it.

However, you misunderstood what this topic is about. This topic is not about downloading copyrighted music etc.

It is about the **codecs**. In the USA, the algorithms and software of codecs is patented. That means that if you write software to decode MP3 files for example, you have to pay royalties to the people who invented the MP3 format. This is the reason why codecs for MP3, DVD etc. are not included in Ubuntu by default.

As far as I know, those patents mainly apply to the USA. Here in NL, you are not doing anything wrong if you install those codecs without paying anybody for them.

---

### Post by wildman4god on 2009-02-26
I am not sure in the USA which codecs are illegal other than DVD and windows/MAC but I think its one of those things that the law really doesn't care about, technically its illegal to download certain codecs for free no matter which OS you use, yet everyone does it and doesn't think twice about it. If it were that important to out gov. then I'm sure they would say something and not just let us guess, I actually tried to look up the laws and I couldn't find anything conclusive.

---

### Post by Dragonbite on 2009-02-26
It's murky.

I still don't quite see, though, how Mint and/or PCLinuxOS get away with distributing with codecs while Ubuntu and others do/cannot.

I know it is one part philosophy which keeps Ubuntu from distributing with codecs installed, and RedHat (Fedora, CentOS, etc.) is more adamant about not shipping non-OSS codecs, but the question is "can they" (without the parent company paying for them)?

For MP3 playback, Fluendo offers that codec for free. Other formats, though, will cost you but not too much.

With the proliferation of You-Tube style video playback via Flash (or Silverlight) I'm finding less frequently the need for these other codecs.

---

### Post by jespdj on 2009-02-26
> **Dragonbite said:**
> I still don't quite see, though, how Mint and/or PCLinuxOS get away with distributing with codecs while Ubuntu and others do/cannot.
Maybe with Mint and PCLinuxOS there is someone who pays royalties for the codecs, even though they give the OS with the codecs away for free? (I don't know, but that would be a possibility).

Or do they just give it away for free and hope that the patent holders are not coming after them?

---

### Post by Bart_D on 2009-02-26
> **Dragonbite said:**
> I still don't quite see, though, how Mint and/or PCLinuxOS get away with distributing with codecs while Ubuntu and others do/cannot.....

From the Mint website:

> **Linux Mint Universal Edition**
This edition aims to provide the same features as the Main Edition **without including proprietary software, patented technologies or support for restricted formats**.** If you're** a magazine, a reseller or a distributor in Japan or **in the USA then choose this edition**.

Source: [http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

I guess they are leaving it up to the end user to determine which version to download - Main(with codecs) or Universal(without).

---

### Post by sydbat on 2009-02-26
In the US, it would be illegal to include patented codecs with a distribution. To cover their a**, Canonical simply does not include codecs with Ubuntu (et al) just in case another country would frown upon the inclusion.

Additionally, outside the US it is legal to download and install these codecs because **US patent law does not extend beyond the US borders**.

Of course, even in the US, how are they going to know you have those codecs anyway? Linux does not call home and rat you out (like some other OS's) about what you have on your computer.

---

