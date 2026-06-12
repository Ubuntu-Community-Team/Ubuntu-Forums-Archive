---
title: "about the xVid codec.."
date: 2007-03-13
forum: The Cafe
---

### Post by billdotson on 2007-03-13
I have heard that the xVid codec is illegal.. which is odd because it is an open source project.  I also read that the DivX codec was originally considered illegal until it went commercial or something like that.  From what I have heard it is illegal to distribute the xVid codec unless you are distributing the source code.  You cannot distribute a pre-compiled binary and so you will have to compile the coded yourself to use it.  So the legal basis for the xVid codec's not being able to be distributed as a pre-compiled binary seems to stem from the "fact" that I heard that is illegal to distribute pre-compiled binaries of codecs without paying fees.

Is this true.. can you only get the source code and have to compile it yourself to use it?

BTW if it is true that you cannot distribute a pre-compiled binary of a codec w/o paying fees (I don't know who to) doesn't that seem like a stupid sort of restriction by a organization/company like the RIAA, Microsoft, MPAA would say??  I mean why can't you have a free video codec??  xVid isn't a hack of any of their codecs.. it doesn't use any of their code (as far as I know) so why do fees have to be paid? MPAA and RIAA need to find better ways to protect their IP w/o hurting consumer rights.. same goes for any other company/organization that does similar things.

Copyright and patent law has got to change to adapt to the internet.. it can't just stay the way it had always been.  Obviously the xVid codec is a great codec if it can compress a 2.5hr video down to 700MB.

---

### Post by mcduck on 2007-03-13
XviD, like DivX and many other codecs, uses MPEG 4 video format, which is patented proprietary technology and in countries where software patents are acknowledged you need to pay license fees to legally use it.

DivX is legal because the company behind it pays those license fees.

---

### Post by billdotson on 2007-03-13
oh... I guess I need to encode with DivX from now on.  But you can encode videos using the xVid codec and put them in an avi container though can't you?  That is what I have been doing.
OGM is an open source format like MPEG4 isn't it?? Can you use xVid to encode into OGM?

Also, if the xVid codec cannot be used in anyway unless a fee has been paid.. I have ffdshow installed on Windows.. how do I get the xvid codec out of it?  Also, Avidemux (in Ubuntu) seems to have the xvid codec automatically included (maybe it is just installed on my Ubuntu install).. how do I get rid of it (considering it might be on my Ubuntu install)?

using the xVid codec isn't worth paying for.. gar I hate proprietary video!

---

### Post by Mateo on 2007-03-13
i would just ignore it, millions of people encode to xvid, I wouldn't worry too much about it.  i don't.

---

### Post by mcduck on 2007-03-13
> **billdotson said:**
> oh... I guess I need to encode with DivX from now on.  But you can encode videos using the xVid codec and put them in an avi container though can't you?  That is what I have been doing.
OGM is an open source format like MPEG4 isn't it?? Can you use xVid to encode into OGM?

Also, if the xVid codec cannot be used in anyway unless a fee has been paid.. I have ffdshow installed on Windows.. how do I get the xvid codec out of it?  Also, Avidemux (in Ubuntu) seems to have the xvid codec automatically included (maybe it is just installed on my Ubuntu install).. how do I get rid of it (considering it might be on my Ubuntu install)?

using the xVid codec isn't worth paying for.. gar I hate proprietary video!

You have misunderstood the codec/video format thing. A codec is a program that codes and decodes video into some video format. So DivX, XviD and others are codecs, using the MPEG4 format. It doesn't matter which codec you use, the resulting video is always MPEG4. You don't need DivX codec to watch movies coded with DivX, any MPEG4 codec will work just the same way.

By default there is no MPEG4 codec installed in Ubuntu, if MPEG4 movies work for you you have installed the codec yourself.

(AVI and OGM are also not video formats, but they aren't codecs either. They are container formats, being able to contain video in any format, with audio (in any format), subtitles and other data combined into one file.)

---

### Post by maniacmusician on 2007-03-13
> **mcduck said:**
> You have misunderstood the codec/video format thing. A codec is a program that codes and decodes video into some video format. So DivX, XviD and others are codecs, using the MPEG4 format. It doesn't matter which codec you use, the resulting video is always MPEG4. You don't need DivX codec to watch movies coded with DivX, any MPEG4 codec will work just the same way.

By default there is no MPEG4 codec installed in Ubuntu, if MPEG4 movies work for you you have installed the codec yourself.

(AVI and OGM are also not video formats, but they aren't codecs either. They are container formats, being able to contain video in any format, with audio (in any format), subtitles and other data combined into one file.)
so you could take ogg and put it in an AVI container? which would allow players that don't support OGG to play it?

---

### Post by mcduck on 2007-03-13
> **maniacmusician said:**
> so you could take ogg and put it in an AVI container? which would allow players that don't support OGG to play it?

No. If you put MPEG4 video into AVI container, you need some MPEG4 codec to watch it. If you put OGG Theora into AVI, you need Ogg Theora codec to watch it. AVI is just a container, you still need a codec that understands the video and audio formats you put inside the container.

The only benefit of container files is that they put all files related to the movie into one file.

---

### Post by billdotson on 2007-03-13
I guess I should just use the DivX free version.. [tear] or I could pay the fees to use the mpeg4 format.. how much are those btw?

---

### Post by banjobacon on 2007-03-14
> **billdotson said:**
> MPAA and RIAA need to find better ways to protect their IP w/o hurting consumer rights.. same goes for any other company/organization that does similar things.

The RIAA and MPAA have nothing to do with this. It's easy to hate them, but they're not the source of *all* the world's evils.

> **billdotson said:**
> I guess I should just use the DivX free version.. [tear] or I could pay the fees to use the mpeg4 format.. how much are those btw?

You, as a consumer, aren't required to pay any fees. Fees are generally paid by distributors, those providing the technology (hardware and/or software) to play the encoded media.

I remember reading some of the licensing terms for MPEG-4 or MP3 (maybe it was posted by someone in this forum). Part of it stated, more or less, that no fees were required for personal use.

---

### Post by billdotson on 2007-03-14
so can I encode/transcode to mpeg4 w/ an xvid codec w/o legally having to pay fees.. as it is up to the codec distributors to do that?? Or should I just use DivX

---

### Post by ShadowVlican on 2007-03-14
if you're just passing stuff to your friends..... don't worry about it

for commercial purposes, better stick with more widely supported formats like DVD MPEG2 (so your customers don't have to fiddle to get things playing)

as for OGG in AVI? don't think it's possible.... that's why they made OGM container years ago..... and now the latest and greatest container is MKV.... it's extremely versatile

also there's no reason for you to be questioning distributing the XVID codec... there's already ton's of websites out there doing a fine job....

---

### Post by Tuna-Fish on 2007-03-14
Just to clarify:

For you, as an end user, there is absolutely nothing illegal in compiling xvid and using it. What would be illegal, is distributing a precompiled version. To do that, you'd have to pay fees to whoever who owns the mpeg4 patents.

Also, if you live in a country with sane patent laws, NONE of the above is illegal, it only applies if the country has software patents.

---

### Post by billdotson on 2007-03-14
I live in the U.S.  So I cannot use the xVid codec legally unless I download and compile it myself.. otherwise I have to pay fees for the usage of the mpeg4?  All this multimedia stuff is pretty confusing!  But I wonder.. Avidemux seems to include the xVid codec (xVid4) in it by default as one of the video codecs.. illegal?  So to use mpeg4 at all you are supposed to pay fees or is that only if you distribute video codecs that encode to the mpeg4 container (technically a transporter for the video and audio corrrect?? whereas avi or ogm is a container?)

So for use on Windows as my PC is not operational as of now (no PSU) what do I use to compile it if I have the source code??  Also I am trying to use Avidemux in Windows and on this PC there is no software to play DVDs.. so when I import a video into Avidemux or rip the video files off using a program like Roxio Easy Media Creator 7 (as opposed to opening the disc and copying the video files and pasting them to the desktop) I have no sound.. is this because there is no AC3 codec on this PC?  I do not remember installing an AC3 codec on Ubuntu I just copied and pasted the command to install all the normally needed codecs:

```

sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs

```

I also used automatix2 to install the 'multimedia codecs' but NOT the win32codecs or the libdvdcss2 ones (the ones in AUD-DVD non-free codecs section)

Also, so on the grounds of codec legality issues.. if I am using GNU/Linux I cannot use the libdvdcss2 w/o paying a fee to the MPAA.. what about the win32codecs.. when are they considered legal.. if I own a copy of Windows? If I don't redistribute them? If it is illegal to redistribute them then how can you get the win32 codecs legally?

Man this legal stuff w/ patents, etc. on multimedia codecs and other things is so cryptic and annoying!  Is there any clear way to know what is legal and what is not.. do the people that want these patents enforced make it cryptic on purpose?

---

### Post by G Morgan on 2007-03-14
Just install the codec. Copy the source code to /usr/local/src/ then if anyone asks any questions you compiled it and ran make clean afterwards.

---

### Post by maniacmusician on 2007-03-14
> **G Morgan said:**
> Just install the codec. Copy the source code to /usr/local/src/ then if anyone asks any questions you compiled it and ran make clean afterwards.
yeah 8)

---

### Post by Choad on 2007-03-14
i wish there were more people that used ogg

im sure an ogg torrent site would be pretty popular (read: profitable) 

someone make one.

---

### Post by billdotson on 2007-03-15
hmm so I can just download the source of the xVid, compile it install it and then use it to encode to mpeg4 o encode into an avi container for free i.e. not having to pay fees for the use of mpeg4 (I am talking legally.. I like to do things legally.. I am a stickler) Oh, btw what dows make clean do after you compile something?

All I want to do is record movies off of cable, cut the commercials out and encode them w/ xVid so I can put them on CDs.

Also, OGM is a video format.. or a container?  I know ogg vorbis is audio.. but I wonder.. why don't people encode all their stuff as OGM video w/ OGG audio so they can have patent-free videos?  The open source community should be able to make a better open source video format than mpeg4 (if OGM isn't already)  What would be cool is to have new DVD players that were advertised as OGM+OGG compliant \\:D/

---

### Post by fenian on 2007-03-15
[OGM]("http://en.wikipedia.org/wiki/Ogm") is a container which most often holds video encoded in XVID and audio encoded in Vorbis or AC3.Both XVID and Vorbis are open source and capable of producing high quality compression.

---

### Post by fenian on 2007-03-15
It's kind of interesting that you're worried about the legality of xVid (which I believe is legal to use but illegal to distribute in the U.S.A.) but don't seem too concerned about the legality of recording movies off cable,cutting the commercials and putting them on a CD (I'm pretty sure this is illegal in the U.S.A.).

---

### Post by billdotson on 2007-03-15
fenian: if I pay for cable and have a TV tuner or DVD recorder.. why can I not record movies or TV shows and cut out the commercials?  Isn't that what the entire idea that TV tuners are based on?  If it were illegal why would companies like Sony sell DVD recorders to record shows and such to DVDs?  I will not be distributing them at all so I shouldn't see a problem.

I am not being rude I am simply just inquiring as to why your belief is that it is illegal to record stuff off of cable and cut out the commercials, etc. as i have always assumed that if I have a DVD player that can record shows and I am paying for cable (not satellite or channels like HBO) and recording shows off of TBS, TNT, etc. that that is perfectly legal.  However I could be wrong and if I am that is a very messed up law/restriction.  All I am doing is recording them and then ripping the video files and editing out the commercials then encoding them as a smaller size for hard drive space.

Also, I have a question.. if you pay for satellite and all those channels.. would it be illegal for you to record those shows with your DVD player as long as the videos are not distributed?

So if I downloaded the source of xVid, compiled it myself and used to and vorbis to compress the audio and video into the OGM container would that be any good?  Or would I have to have a mpeg-4 codec to play the OGM file?  I still don't understand.. xVid can't be distributed unless license fees for mpeg-4 are paid (does that also mean to play mpeg-4 you have to pay a fee?)?  Are there sites out there that distribute it that pay those fees.. like for instance the developers of Avidemux (as xVid4 seems to be an included video codec by default)

I am just wondering about these things because I do not want to have any questionable codecs, etc. on Ubuntu.  If I do have to pay a fee to use mpeg-4 how do I get rid of the mpeg-4 codec I have installed.. as I know I can play mp4 files.  The only codecs I installed were the ones on ubuntuguide.org (with the exception of the win32codecs) and I used the commonly needed multimedia codecs script in automatix2 to install any ones I had missing.

---

### Post by billdotson on 2007-03-15
double posted-- sorry

---

### Post by Teg_Navanis on 2007-03-15
> **billdotson said:**
> fenian: if I pay for cable and have a TV tuner or DVD recorder.. why can I not record movies or TV shows and cut out the commercials?  Isn't that what the entire idea that TV tuners are based on?  If it were illegal why would companies like Sony sell DVD recorders to record shows and such to DVDs?  I will not be distributing them at all so I shouldn't see a problem.

I don't know whether what you describe is in fact legal or illegal in the USA, but I guess it is safe to say that laws are not the product of what you might call common sense, but are heavily influenced by lobbying by the industry - and, even worse, made by people who don't really understand new technologies and try to apply old concepts of thinking to them ("the internet is a series of tubes" anyone?). 

In fact, you could have made a similar argument for the copying of music: Why would Sony at the same time sell CD-writers and CD-Rs and try to stop people from copying music by advocating DRM and installing rootkits on their PCs? You'll just have to accept the fact that they do/did.

---

### Post by billdotson on 2007-03-16
can anyone respond and tell me please?

are there places that distribute the xVid codec that pay the fees? If not I just need to download the source, compile it and do 'make clean'?

Also, in order to watch, edit, do anything w/ mpeg4 files do I have to pay a fee to use mpeg4?  I can play mpeg4 but I do not recall installing mpeg4 myself.. unless the codecs I installed from ubuntuguide.org (with the exception of win32 codecs) and the commonly needed multimedia codecs script in automatix2.

---

