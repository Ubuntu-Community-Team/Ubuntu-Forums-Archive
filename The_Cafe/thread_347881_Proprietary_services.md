---
title: "Proprietary services?"
date: 2007-01-27
forum: The Cafe
---

### Post by pay on 2007-01-27
I just have a few questions about proprietary services. If it is illegal to use win32codecs without owning a copy of windows (atleast that is my understanding), then by the same arguement, wouldn't it be illegal to use the msn network with gaim? Also, if media like audio codecs and video codecs are proprietary (apart from theora, snow, dirac, vorbis, flac, etc) then are image formats like jpeg proprietary aswell? Is it legal to use all image formats? How about formats like pdf and .doc?

Thank you for helping to clear up my confusion:)

---

### Post by kevinlyfellow on 2007-01-27
w32codecs are copyrighted (they use the actual files from windows)... you can't copyright a network.  I don't know much about the legalities with 3rd party clients connecting to networks, but as far as I know its perfectly legal since you have signed up for the service of using the network.

There are some image formats that are proprietary... infact microsoft recently came out with some.  JPEG is patented by Forgent Networks and unless they decide to start charging for the use of the idea of jpeg compression, then open source compression programs are free to exist (in the US).  

This is my best understanding of the subject, not necessarily the truth, so if anyone know better then by all means, fix my misunderstandings

---

### Post by MkfIbK7a on 2007-01-27
MSN is free on all platfroms it is really just a protocol and network...

oh and jpegs if they were not free cameras would probably cost much more...

---

### Post by pay on 2007-01-27
Thank  you for your help. That makes sense about the msn network. I just have another question. If the msttcorefonts packages came directly from the windows cd, then wouldn't it be in the same department that the win32codecs package is in?

---

### Post by TheMono on 2007-01-27
JPEG's are free as in Beer, but they are still owned and the owner (I can't remember who) could press to have them licensed. They probably wouldn't win, but they could try.

---

### Post by kevinlyfellow on 2007-01-27
> Thank you for your help. That makes sense about the msn network. I just have another question. If the msttcorefonts packages came directly from the windows cd, then wouldn't it be in the same department that the win32codecs package is in? 

I think that that would be the case.  Microsoft undoubtedly would have that copyrighted.  But it also depends on how microsoft will let you use it.  As far as I know, its one of those legal areas that open-sourcerers need to tip-toe around

---

### Post by pay on 2007-01-27
Thank  you for all your help everyone. I was thinking, if enough people put in all the information they know about legalities with using linux and proprietary formats and services, then I might be able to compile a FAQ's thread.

---

### Post by Hex_Mandos on 2007-01-27
I think msttcorefonts is proprietary and copyrighted by MS, but can be freely used.

---

### Post by pay on 2007-01-28
> **Hex_Mandos said:**
> I think msttcorefonts is proprietary and copyrighted by MS, but can be freely used.Yeah. You're right. I found a EULA here [http://sources.gentoo.org/viewcvs.py/*checkout*/gentoo-x86/licenses/MSttfEULA](http://sources.gentoo.org/viewcvs.py/*checkout*/gentoo-x86/licenses/MSttfEULA) and it basically says that you are allowed to use it aslong as you don't alter them

---

### Post by pay on 2007-01-28
I found a good site to find out weither a image format is patented or not. [http://en.wikipedia.org/wiki/Comparison_of_graphics_file_formats](http://en.wikipedia.org/wiki/Comparison_of_graphics_file_formats)
I love wikipedia:)

---

### Post by az on 2007-01-28
> **pay said:**
> I just have a few questions about proprietary services. If it is illegal to use win32codecs without owning a copy of windows (atleast that is my understanding),

That's just an assumption made by some people.  AFAIK, each codec in that package has different terms of redistribution (if any at all).  AFAIK, it's not legal to ditribute or use them in any circumstance (whether you own a copy of windows or not).

> **pay said:**
> 
 then by the same arguement, wouldn't it be illegal to use the msn network with gaim?

AFAIK, the terms and conditions to using MSN - the client software and the network service - are clearly stated.  Although they have often changed the standard in the past to keep ahead of those who were reverse-engineering the client software, it is not expressedly forbidden to do either.

> **pay said:**
> 
 How about formats like pdf and .doc?


.doc is reverse-engineered.  .pdf is a standard that is free to use.  

The PDF standard was always openly known so that it would gain in popularity.  The same thing happened with the msttcorefonts - MS released them to be freely redistributed so that the standard would establish itself.  Many years ago, MS stopped doing that, however, the original fonts are still redistributable under the same licence.  So when you install them, you get them from a third-party.

---

### Post by pay on 2007-01-28
Thank you azz!!! You have cleared up alot for me. But if it is illegal to use win32codecs even if you own a windows cd, then under what circumstances can you use these codecs (specifically wmv)? Mplayer can now play back wmv, would that be legal to play the files with mplayer?

---

### Post by jdong on 2007-01-28
> **azz said:**
> That's just an assumption made by some people.  AFAIK, each codec in that package has different terms of redistribution (if any at all).  AFAIK, it's not legal to ditribute or use them in any circumstance (whether you own a copy of windows or not).


Azz is correct on this. A place I used to do some work at is in the process of migrating to Linux, and the topic of media codecs came up. Basically their legal team said it was an absolute no-no even if they had volume-licenses of XP for every PC. So I'd be very careful assuming that it's legal to be using them.

also, even if I own a copy of XP it's not legal for me to go out and torrent one -- the form of redistribution has to be kept in mind and clearly the way w32codecs is handled is quite illegal in my mind.


> 
if you own a windows cd, then under what circumstances can you use these codecs (specifically wmv)? Mplayer can now play back wmv, would that be legal to play the files with mplayer?

If you live in a country that does not uphold software copyrights and patents, then it's safe to use.

Mplayer (VLC, and a few others) play back WMV now because ffmpeg has implemented a WMV decoder. Like the situation with MPEG2, MP3, AAC, DIVX/XVID (MPEG-4 ASP), and H.264, no licensing fees has been paid to the respective parties and the GPL is incompatible with the idea of licensing/royalties also, so technically they are ALL illegal at least in the USA.

The only 100% legal media playback options in Linux are:
  (1) Ogg Vorbis and Ogg Theora -- 100% patent-free formats. Ogg Vorbis is an EXCELLENT quality audio codec that surpasses MP3 and rivals or exceeds AAC. Ogg Theora is a 100% patent-free video format but its quality still needs work. quality to bitrate wise, it surpasses MPEG2 but falls way short of xvid and h.264.
  (2) Uncompressed video with uncompressed Audio. What your digital camcorder spits back. Yeah, that thing that dumps 30GB for an hour of recording.

The above two can be implemented open-source, while the rest down here are various non-OSS ways that Linux can legally play back media:

  (1) MP3, RealAudio, RealVideo with Realplayer 10: Novell/SUSE uses Realplayer10 to do its mp3 decoding with all its media applications. The dapper-commercial/edgy-commercial repos contain Realplayer but in ubuntu it is not integrated with any playback software.
 (2) gstreamer-fluendo: Fluendo has released (closed source by necessity) codecs on top of GStreamer (i.e. Totem, rhythmbox) ... MP3 is free of cost while rest cost some licensing fees

---

### Post by pay on 2007-01-28
Thank you jdong. I think that I understand the situation with codecs now:)> **jdong said:**
> The only 100% legal media playback options in Linux are:
  (1) Ogg Vorbis and Ogg Theora -- 100% patent-free formats. Ogg Vorbis is an EXCELLENT quality audio codec that surpasses MP3 and rivals or exceeds AAC. Ogg Theora is a 100% patent-free video format but its quality still needs work. quality to bitrate wise, it surpasses MPEG2 but falls way short of xvid and h.264.
  (2) Uncompressed video with uncompressed Audio. What your digital camcorder spits back. Yeah, that thing that dumps 30GB for an hour of recording.Thats not quite true. There are also less popular codecs like snow, dirac and tarkin. Snow's bitstream might change so future version of the codec might be incompatiable with video that you encoded before (atleast untill they finalize the video). I don't think that anyone is developing tarkin. With dirac you have to completly uncompress the video, which makes it hard to use these codecs (yet anyway). I was testing out snow and it's quality was very good so it is promising. But I agree, Vorbis is great:)

---

### Post by pay on 2007-01-28
Proprietary Software FAQ's 

Q1) Is it legal to install win32 codecs on a Linux operating system?

A1) That depends on where you live. Some countries don't uphold software copyrights and patents. In those countries, you are fine to use the software. But in the United States, then it is illegal to use all patented codecs (MPEG 1/2/4, WMV, MP3 etc..)

Q2) Is it legal to use these codecs if I own a copy of Windows?

A2) No. It is still illegal.

Q3) It what circumstances can I use these formats?

A3) MP3, RealAudio, RealVideo can be legally played back with Realplayer 10. Also some commercial linux distros have the patents paid for.

Q4) If all these formats are patented, then what formats aren't?

A4) Vorbis and Theora are the most popular, but there are some other younger codecs like dirac, snow and tarkin that are under development and look promising. Also uncompressed audio and video are alright to use. For compressed , but lossless audio there is FLAC. Xiph also develops speex for human speech which is free to use.

Q5) If formats like audio and video can have patents, then why don't image formats have them?

A5) Well they do. They just aren't enforced as often. 

Q6) How about document formats?

A6) Each format has it's own license. Pdf is open. .doc is reverse-engineered. .odt is open. 

Q7) What are the legalities of using a network like MSN on Linux?

A7) You can't copyright a network. Connecting to it with a 3rd party client is okay since that you are agreeing to the network terms upon joining. Although they have often changed the standard in the past to keep ahead of those who were reverse-engineering the client software, it is not expressedly forbidden to do either.

Anyway, this is my faq's so far. If there is anything incorrect or you know of a question that should be added then please tell me. and then when it's ready, I'll put it somewhere where people can find it.

---

### Post by az on 2007-01-28
> **pay said:**
> Tunder what circumstances can you use these codecs (specifically wmv)? Mplayer can now play back wmv, would that be legal to play the files with mplayer?

Mplayer uses xine, which uses w32codecs, no?

You *can* buy a licence for a linux distribution that has paid the royalties to the respective patent/software owners.  I beleive Impi linux is Ubuntu with such add-ons.  As well, soon Linspire will offer a clicn'n'run repository for Ubuntu.  You pay to sign up, install the codecs and you are worry-free.

As well, regarding the royalties for mp3, I am pretty sure the codec is licenced in such a way that individuals can use it, but you cannot distribute it.  So, Ubuntu cannot ship it without paying a royalty, but you can download and install it in Ubuntu and use it without worry, so long as you use it for private, non-commercial purposes.

---

### Post by pay on 2007-01-28
> **azz said:**
> Mplayer uses xine, which uses w32codecs, no?Mplayer uses libavcodec which has it's own decoding of VC-1 and WMV.

---

### Post by jdong on 2007-01-28
> **azz said:**
> 
You *can* buy a licence for a linux distribution that has paid the royalties to the respective patent/software owners.  I beleive Impi linux is Ubuntu with such add-ons.  As well, soon Linspire will offer a clicn'n'run repository for Ubuntu.  You pay to sign up, install the codecs and you are worry-free.

Those solutions will likely be using non-free (either LGPL-gone-closed or a 3rd party thing like Fluendo) otherwise they would not be terribly legal either, since the GPL and paying royalties are mutually exclusive -- one invalidates the other.

But yes, there are distros like that. But more strangely, there's USA distros like MEPIS that just preinstall w32codecs :D

---

### Post by jdong on 2007-01-28
> **azz said:**
> Mplayer uses xine, which uses w32codecs, no?


And mplayer uses primarily ffmpeg (aka libavcodec, libavformat) along with some of its natively-implemented container decoders and some other codecs, and has the ability to employ w32codecs.

In the case of WMV/WMA decoding, nowadays ffmpeg is used to do it, unless w32codecs is installed, then most players will prefer w32codecs to do it unless explicitly overridden.

---

### Post by pay on 2007-01-28
So basically the only free way to watch a movie encoded as mpeg4 would be to convert it to theora first?

---

### Post by jdong on 2007-01-28
Well, or decompress it... provided that your decoder and converter are both licensed (decoding a mpeg4 with ffmpeg in order to recode it to theora is no better than just playing the mpeg4)


Again, it all depends on how strictly you personally interpret these regulations... most people have no problem with using ffmpeg.

---

### Post by pay on 2007-01-28
I don't have a huge problem with using ffmpeg. Infact, I think that Australia has those laws but they aren't enforced by anyone (like RIAA). It's more of a fact that I wanted to understand the laws. Personally if I'm going to encode a DVD to my harddrive, I'll use vorbis and theora because of philosophical beliefs, but still use ffmpeg for everything else. Thanks for everyones help.

P.S. Don't use wmv/wma, it would just lead to Microsoft controlling our lives:D

---

### Post by az on 2007-01-29
> **jdong said:**
> Those solutions will likely be using non-free (either LGPL-gone-closed or a 3rd party thing like Fluendo) otherwise they would not be terribly legal either, since the GPL and paying royalties are mutually exclusive -- one invalidates the other.


Yes, Linspire 5.0 shipped with the w32codecs package.  I would be curious to know if the version of the w32codecs package they ship actually has a copyright file.  The version of that package that you get for Ubuntu has an empty copyright file.

According to Kevin Carmony, Linspire CEO, they pay for the licences to distribute those codecs.

---

### Post by jdong on 2007-01-29
Interesting, Azz.... Does Linspire ship with any kind of Xine/ffmpeg? If so, do they claim that they've paid for those, and/or they are still GPL'ed? (I know some limited configs of ffmpeg can be LGPL'ed)

---

### Post by az on 2007-01-29
> **jdong said:**
> (I know some limited configs of ffmpeg can be LGPL'ed)

What do you mean?  

Take LAME.  LAME is GPLed.  The fact that, for example, the mp3 codec/format is patented and the patent holders charge a royalty for any implementation of it does not affect the licencing between the author of the software and the end-user.  The fees that the user or a third-party distributer must pay to the patent holder have nothing to do with the licencing of the software.  

The author of the code does not reserve the right to limit redistribution but the patent holder does.

The software (the code) is licenced in one way and the implementation of the mp3 codec (whether it is FLOSS or proprietary) is another.

A distributer of a media player, for example, must pay the royalty in the same way, AFAIK.

My understanding of the way that this influences FLOSS is that the distro cannot ship the codec withtout paying the royalty (X number of dollars per hundred thousand licences)  And since Ubuntu is freely-redistributable, that is not possible.  So the implementatino of mp3 is not shipped out-of-the-box.  However, that does not mean that the actual code is not distributed under a GPL or lGPL licence.

I thought ffmpeg and all the other codecs (that are reverse-engineered or authored by people other than the patent holder) were licenced in the same way?

> **jdong said:**
>  otherwise they would not be terribly legal either, since the GPL and paying royalties are mutually exclusive -- one invalidates the other.



Only if the author of the code is the holder of the patent and uses that to charge the royalty.

---

### Post by Mateo on 2007-01-29
xvid is legal....

---

### Post by Hendrixski on 2007-01-29
Wow, this thread is very informative.  It's very important that users know which software formats have their needs in mind, and which of them have the big corporations in mind.  And it's important to know the legality of using them unlicensed if you use your Linux in a business setting.

So I take it, all of the enterprise versions of Linux have all the legality sorted out and have purchased the licenses to play all of this stuff out-of-the-box?  So if I were to watch DVD's in RHEL or Suse Enterprise, I'm not breaking the law by breaking the encryption, I'm actually using licensed DVD playback?   

I just installed OpenSuse, and it comes with a bit more media functionality than purely non-proprietary distro's like Ubuntu, but getting the less legal w32codecs is more of a hassle with YaST.

Keep up the good thread.

---

### Post by Mateo on 2007-01-29
I don't see why people even worry about this sort of thing.  Playing your DVD, that you purchased, on your computer might be "breaking the law", but it's a victimless "crime" that you have virtually no chance of being caught doing.  Same for playing a WMV file.  People don't think twice about driving 10 miles over the speed limit, and that's a "crime", so I don't see why anyone should care about this, especially since there is no way for anyone to know what you're doing on your computer.

---

### Post by az on 2007-01-29
> **Mateo said:**
>  People don't think twice about driving 10 miles over the speed limit, and that's a "crime", so I don't see why anyone should care about this, especially since there is no way for anyone to know what you're doing on your computer.

For now.  Ever heard of DRM?

What happens when you are not able to:
1. do without your media
and
2. play it on a free-libre operating system?


You will have to give up your freedom to run software of your choice just to be able to read/view/listen to the media that you want.  You (may) even have to agree to be spied upon.

Think of how awful it would be if DRM was mandated by law?

A much more elegant solution is to use free and open formats.  But that would prevent the use of DRM and prevent the multimedia industry from continuing to make money at the rate they are doing so now.  The model by which multimedia is distributed would really have to change for that to happen.  The bulk of the industry would have to be eliminated (the middle man).

So, is sidestepping the law today going to help promote change?  Will it increase the chance of DRM one day becoming law?

---

### Post by macogw on 2007-01-29
gif was patented, but last year they opened up the format or something...i just know FSF doesnt hate them anymore

---

### Post by jdong on 2007-01-29
> **azz said:**
> What do you mean?  

Take LAME.  LAME is GPLed.  The fact that, for example, the mp3 codec/format is patented and the patent holders charge a royalty for any implementation of it does not affect the licencing between the author of the software and the end-user.

From my reading of Part 7 of the GPL it does:

> 
"7.  If, as a consequence of a court judgment or
allegation of patent infringement or for any other
reason (not limited to patent issues), conditions are
imposed on you (whether by court order, agreement or
otherwise) that contradict the conditions of this
License, they do not excuse you from the conditions of
this License. If you cannot distribute so as to
satisfy simultaneously your obligations under this
License and any other pertinent obligations, then as a
consequence you may not distribute the Program at all.
[b]For example, if a patent license would not permit
royalty-free redistribution of the Program by all
those who receive copies directly or indirectly
through you, then the only way you could satisfy both
it and this License would be to refrain entirely from
distribution of the Program.[/b]"

So going back to the LAME example, if the MP3 group does not grant LAME permission to allow everyone who recieves LAME to distribute it royalty-free, then the LAME people may not distribute the program.

From that interpretation, the GPL would not be a valid license to use with non-royalty-free stuff.


And xvid is not "legal" in the perspective that it is a GPL'd implementation of the patent and royalty encumbered MPEG-4 Part 2 codec.

---

### Post by jdong on 2007-01-29
> **Mateo said:**
> I don't see why people even worry about this sort of thing.  Playing your DVD, that you purchased, on your computer might be "breaking the law", but it's a victimless "crime" that you have virtually no chance of being caught doing.

Most home users go by this logic to install media codecs and libdvdcss on their Linux machines, or even to install 3 copies of a proprietary program of which they were licensed only one seat of.

However, consider a business or more formal deployment of Linux where there would be a need to deal with receiving media in a, say, MPEG4 or WMV format. Then it's not so brilliant an idea to start installing w32codecs and ffmpeg.

>  People don't think twice about driving 10 miles over the speed limit, and that's a "crime", so I don't see why anyone should care about this, especially since there is no way for anyone to know what you're doing on your computer.
That is quite overgeneralizing.... 10mph over the limit here is enough (especially for new drivers) to get suspended licenses or those wonderful driving classes where you're bored out of your mind and pass away the time by answering the test questions with wise cracks, thus landing myself in even more classes.... nevermind.


But the point is, committing illegal acts because you think there is a low chance of being caught  doesn't excuse one from being fully informed about the legal situation with these patented formats and the implications of using them.

---

### Post by Ramses de Norre on 2007-01-29
There is a little error in your faq, you state that flac isn't compressed but in fact it is. More info can be found [here](http://en.wikipedia.org/wiki/Flac).

---

### Post by az on 2007-01-29
> **jdong said:**
> 

So going back to the LAME example, if the MP3 group does not grant LAME permission to allow everyone who recieves LAME to distribute it royalty-free, then the LAME people may not distribute the program.

From that interpretation, the GPL would not be a valid license to use with non-royalty-free stuff.

But LAME and ffmpeg are distributed under the GPL (lGPL, actually, but that's irrelevant).  I always thought that that portion of the GPL/lGPL was meant to spell out the fact that you can't have it both ways.  That you can't claim rights under a patent that you give away with the GPL licence  ("*they do not excuse you from the conditions ofthis License*" - like Novell GPLing software, but enacting a patent covenant with Microsoft regarding these technologies).  

It does not expressedly state that the licence is rendered invalid, it just says that the software should not be distributed - which is accurate.  You don't satisfy patent rights by playing around with licencing.

[I]For example, if a patent license would not permit
royalty-free redistribution of the Program by all
those who receive copies directly or indirectly
through you, then the only way you could satisfy both
it and this License would be to refrain entirely from
distribution of the Program[/I] 

Obviously, in the case of LAME, neither are being satisfied.  Not everybody is allowed to redistribute it because of the patent, but you won't fall victim to legal action if you download and run it for personal use.  Likewise, The FSF will not go after the author of the code because not everyone is entitled to downloading it and redistributing it, it has nothing to do with the authors.  To remove the code would do a disservice.

So, is lame lGPLed or do it's authors only claim that it is?

If a patent would invalidate the GPL, under what licence would such software then be?  What happens to software that is released under the GPL and then subsequently patented by a third party at a later time?  

I believe that the GPL does its best to try to uphold software freedom.  In the event that software patents get in the way, you have to defer to what the patent rights are in your country.  

If someone would ask me if running LAME or a free-libre implementation of mp3 on my home computer is legal or not, (in the sense of the patent or the GPL), I would say that it is.  I am reasonably sure that it's the same for some of the other codecs like windows media and Real media.

But that's just my interpretation...

---

### Post by pay on 2007-01-29
> **Ramses de Norre said:**
> There is a little error in your faq, you state that flac isn't compressed but in fact it is. More info can be found [here](http://en.wikipedia.org/wiki/Flac).Thank you. I fixed that now. Also 10mph over the speed limit is not a victimless crime when you run over poor little Sally infront of here school. I don't really know what a mile is because we don't use it in Australia but I'm guessing it would take you about 10-20m extra to stop incase on an emergency.

---

### Post by FyreBrand on 2007-01-29
So where does xine and xine-extracodecs fit in?  Are they illegal?  Or is it just the xine-extra-codecs that are illegal?  I have permission to do a test installation of a few systems at work, but they need to be legal.  So far on my test box in the shop I have Kubuntu installed with xine-extracodecs.

We do have volume licensing for XP but I realize that doesn't permit me to install w32codecs.  I didn't realize that it doesn't permit me to use xine.  What am I supposed to use for the Amarok back end?

[quote=azz]A much more elegant solution is to use free and open formats. But that would prevent the use of DRM and prevent the multimedia industry from continuing to make money at the rate they are doing so now. The model by which multimedia is distributed would really have to change for that to happen. The bulk of the industry would have to be eliminated (the middle man).
 
 So, is sidestepping the law today going to help promote change? Will it increase the chance of DRM one day becoming law?[/quote]I think this is a really good point.  I don't like DRM but I see why it's in place because people steal and rationalize it.  I'm guilty of having w32codecs and xine-extracodecs installed at home so I can watch media and I rationalize it with the fact I own an XP license.  I do think sidestepping now isn't doing the right thing whether it will result in legalized DRM.  Your well worded insight has poked me to removing the extra codecs I've installed.  A clear conscience is worth more than a few video files anyways.

---

### Post by pay on 2007-01-29
I believe it would be legal to use the real player backend for amarok. But I may be wrong.

---

### Post by zugu on 2007-01-30
> **macogw said:**
> gif was patented, but last year they opened up the format or something...i just know FSF doesnt hate them anymore

AFAIK, the GIF patent expired last year and now it's public domain. That's why the FSF is not hating them anymore.

And while the patent owners were counting their royalties money, the W3C invented the PNG format, a much better replacement for GIF.

---

