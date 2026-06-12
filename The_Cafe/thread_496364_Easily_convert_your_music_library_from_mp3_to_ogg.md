---
title: "Easily convert your music library from mp3 to ogg"
date: 2007-07-09
forum: The Cafe
---

### Post by maddog39 on 2007-07-09
Hello all,

Well I've been wanting to convert all my music from mp3 to ogg and quickly found that there was no real easy way to do it. So I made a small command line utility to do exactly that. Because I really hate mp3 and proprietary formats because they are such a pain in the butt and in the US (as far as I know) they are illegal or so I thought. Well anyway, I was just reading reading the topic about how many songs you have in your library and I think everyone who replied to that topic had their entire library in mp3 and Im sure that alot of people would like to support the open format, if it were only easier.

So I called my utility am2o (auto mp3 to ogg) and its written in PHP (no it does NOT require a webserver what so ever, its a command line utility). I purposely wrote it in PHP to show people that PHP is just like any other scripting language and to debunk the misconception that its only for websites. It also wraps around ffmpeg to do the transcoding.

My personal need for it was to take all the music that I download from gnutella (frostwire/limewire/gtk-gnutella/etc) and convert it to ogg and put it in my music directory and when you download alot of mp3's you keep them in the same folder and when you rerun the command you dont want to re-transcode all of the music thats already transcoded, so it supports filename caching for each unique directory. You may optionally disable caching as well.

To run it you need the ffmpeg and php5-cli packages from the repository. You can get them from Synaptic, or by command line.
```

sudo apt-get install ffmpeg php5-cli

```The package itself is attached to this post. To install it just unpack the tarball then run:
```

cd am2o
sudo ./install.sh

```Examples on how to use the program are included in the readme but heres one for a quickstart, its really easy.
```

am2o -i ./Shared -o ./Music

```We use -c to enable filename caching (this flag is require, to disable use -c=no), and ./Shared is our input folder (where we will pull mp3's from) and ./Music is the output folder (where we put the transcoded ogg's).
**NOTE:** **As of version 0.2, the -c flag is no longer required and will automatically default to yes if left out.**

If you have a big music library that you are transcoding, and you have a multi or dual core CPU system, I dont recommend running multiple instances as this will probably cause it to clash if you are running it on the same directories. Maybe in the future, if people like this tool, I will add support for multiple ffmpeg instances to encode multiple files at a time.

I hope this tool inspires you to convert to and use ogg to support it as an open format.

**[Edit]**
I have released am2o v0.2 with support for lossless flac and flexible flags and arguments. You may use all flags/arguments in any order but you must use the -i and -o flags to specify input and output directories respectively. The default transcode format is ogg, if you would like to transcode to flac, you must use the '-f flac' flag. Refer the '-h' or the readme for more information.

Enjoy!
-maddog39

---

### Post by user1397 on 2007-07-09
Wow!  Thanks so much!

Again, open-source at its best! :)

---

### Post by Arathorn on 2007-07-09
> **maddog39 said:**
> I hope this tool inspires you to convert to and use ogg to support it as an open format.
I'm sorry to say this after all your hard work, but I hope it doesn't. Transcoding from a lossy format to another lossy format results in huge quality loss, and the mp3's you can download with p2p networks are often bad quality already. If you're an open-source zealot I don't think you'll care, but if you love music you will.

---

### Post by Erik Trybom on 2007-07-09
As Arathorn said, DON'T convert between the two formats if you care about the music quality.

Mp3, as well as ogg, is a lossy format. This means some of the information in the raw music files are thrown away to save disk space. That is generally a good thing, because otherwise the files would have been some 5-10 times larger. However, it also lowers the quality of the music. The more compression, the worse it gets. At 192 kbit/s it's almost always impossible to hear any difference, at 128 kbit/s you can hear it if you've got some good equipment and at lower bitrates it's generally quite easy to hear the difference from a CD.

The mp3-making application chooses which part of the music to discard based on an algorithm. It's designed to keep the audible sound and discard the sound that you cannot hear anyway (there's a lot of that in a regular pop song). Ogg Vorbis has a similar algorithm but it's a bit different, which means if you convert from mp3 to ogg you will get *the losses of both compression algorithms*. The result is a file that may sound considerably worse than the original mp3.

If you want to use ogg, then use it when you rip your CDs. Then you'll only get the compression losses from the ogg algorithm and not from the mp3 algorithm as well.

---

### Post by Arathorn on 2007-07-09
Or just use FLAC. ;) You can even find quite a lot of that on P2P, but it will take longer to get, because there are less sources and the files are bigger.

---

### Post by mrgnash on 2007-07-09
Nice work :)

---

### Post by diesel1 on 2007-07-09
> **Arathorn said:**
> I'm sorry to say this after all your hard work, but I hope it doesn't. Transcoding from a lossy format to another lossy format results in huge quality loss, and the mp3's you can download with p2p networks are often bad quality already. If you're an open-source zealot I don't think you'll care, but if you love music you will.

This is exactly why I am re-ripping my entire collection again!

Diesel1.

---

### Post by FoolsGold_MKII on 2007-07-09
Now all I need to do is buy a media player that supports OGG and I'll be set.

I'll just throw away this perfectly good MP3 player and spend money for one that supports OGG. Thank goodness for open source!

:(

---

### Post by maddog39 on 2007-07-09
Heh, well I do realize that both mp3 and ogg are lossy formats and that you may lose some quality, but all the songs that I transcoded sound awsome, and I play them on studio headphones fairly loud. There are only a few songs where i can notice it. Perhaps adding a function to transcode to flac would make a difference?

---

### Post by tbroderick on 2007-07-09
> **maddog39 said:**
> Well I've been wanting to convert all my music from mp3 to ogg and quickly found that there was no real easy way to do it. So I made a small command line utility to do exactly that. 

There's also mp32ogg and dir2ogg in the the repos. mp32ogg can convert songs or entire folders and it preserves the tags.

---

### Post by maddog39 on 2007-07-09
But what backend do they use to transcode, and how old are they? I trust ffmpeg to do a good job, as it always has so far for me. Im adding flac and a few other things, maybe to increase people's willingness to use open formats.

[Edit]
Those utilities tbroderick mentioned dont look like they support caching, so they re-transcode all the files each time.

---

### Post by Polygon on 2007-07-09
just to throw this out there, its much better to convert FLAC or the original CD to ogg, rather then going from mp3 to ogg

its because they are both lossy formats and they both remove certain parts of what you hear so you get a less quality sound then if you went from CD/Flac to ogg

but, if you have no choice, this guide is good :D

---

### Post by maddog39 on 2007-07-09
I almost have 0.2 debugged and ready which has support to transcode to flac, which people should like better.

---

### Post by kamaboko on 2007-07-09
> **FoolsGold_MKII said:**
> Now all I need to do is buy a media player that supports OGG and I'll be set.

I'll just throw away this perfectly good MP3 player and spend money for one that supports OGG. Thank goodness for open source!

:(

LOL.  Exactly.

---

### Post by stmiller on 2007-07-09
> **Arathorn said:**
> I'm sorry to say this after all your hard work, but I hope it doesn't. Transcoding from a lossy format to another lossy format results in huge quality loss

I agree. Do not do this. The audio file quality you end up with will be horrible. The way mp3 encoding works is that it removes parts of the audio file humans can't hear, as well as drastically cutting at 13k for most encoders. When running that already cut-up file again through the math that ogg encoding does, you end up with crap.

---

### Post by maddog39 on 2007-07-09
All the mp3 files that I've transcoded sound perfectly fine, despite what many may think. But for that very reason i've added flac to am2o 0.2 and it works and I'll package it up and append it to the post with updated usage instructions. So to all those who say mp3 to ogg would make the quality terrible, I heavily disagree. Just take my word for it and try it (using ffmpeg or my tool). :)

---

### Post by stmiller on 2007-07-09
> **maddog39 said:**
> All the mp3 files that I've transcoded sound perfectly fine, despite what many may think. But for that very reason i've added flac to am2o 0.2 and it works and I'll package it up and append it to the post with updated usage instructions. So to all those who say mp3 to ogg would make the quality terrible, I heavily disagree. Just take my word for it and try it (using ffmpeg or my tool). :)

Disclaimer: I'm an audio engineer.

You can visually see the information loss with a program like this one:

[http://www.baudline.com/](http://www.baudline.com/)

...to test for yourself. Open the original mp3, then open the mp3s you turned into ogg and compare.

It's like running the audio file through two different types of shredders.

---

### Post by maddog39 on 2007-07-09
I understand that you **do** lose quality. But in my personal experience it hasnt been enough for me to notice any difference. I have posted am2o 0.2 which flac support and a few other things, updated information is on the original post.

---

### Post by tbroderick on 2007-07-09
> **maddog39 said:**
> 
Those utilities tbroderick mentioned dont look like they support caching, so they re-transcode all the files each time.

They use mpg123 (libmad) to decode and oggenc from vorbis-tools to encode. I'm not sure what you mean by caching. mp32ogg has a --delete switch. If you did;

```
mp32ogg --delete --quality=5 /path/to/folder
```

It will delete the mp3s after trancoding.

---

### Post by maddog39 on 2007-07-09
What i mean by caching is, it caches all the mp3's that is already transcoded so that if you download more from p2p for example and you rerun the command, it doesnt retranscode every file. So it skips the ones it's already done.

---

### Post by tbroderick on 2007-07-09
> **stmiller said:**
> Disclaimer: I'm an audio engineer.

You can visually see the information loss with a program like this one:


It really only matters what a person can hear.

---

### Post by maddog39 on 2007-07-09
Well anyway. My thought was that I really needed a tool that suited me and I made one, and I figured that a lot of other people might find it quite useful as well. I got some feedback and added things accordingly, thats all. :)

---

### Post by kamaboko on 2007-07-09
i'd like to hear this incredible difference.  i rip my cd's to mp3 at 192kbits.  can someone post a copy of a mp3 and an ogg file of the same song?  preferalbly at the same bit rate.

---

### Post by maddog39 on 2007-07-09
I would but being in the US and piracy stuff... I only have copyrighted material.

---

### Post by Blue Sky on 2007-09-27
I really don't understand why you would do this. But nevertheless thanks.

---

### Post by Spike-X on 2007-09-29
Why would you want to transcode MP3 to flac? You'd just have the same lossy/compressed sound quality, but your file size would be (up to) five times bigger.

---

### Post by n3tfury on 2007-09-29
> **maddog39 said:**
> All the mp3 files that I've transcoded sound perfectly fine, despite what many may think. But for that very reason i've added flac to am2o 0.2 and it works and I'll package it up and append it to the post with updated usage instructions. So to all those who say mp3 to ogg would make the quality terrible, I heavily disagree. Just take my word for it and try it (using ffmpeg or my tool). :)

if you can barely or sometimes only hear a difference, then it's probably the placebo effect.  especially since this is your project.  sorry, but as others have pointed out, transcoding from one lossy format to another is *never* a good idea.

---

### Post by n3tfury on 2007-09-29
> **maddog39 said:**
> I would but being in the US and piracy stuff... I only have copyrighted material.

funny how you can hear a difference (incredible?) between the same bitrate of an mp3 compared to ogg, but you can't hear the difference between the transcoded final product and the original lossy?   what?

---

### Post by blueturtl on 2007-09-29
There is a difference between compressed audio and CDs. Most people can't hear the difference even at a bitrate of 128 kbps.

Obviously re-compressing the audio (which is what happens when you convert from one form of compression to another) will lessen the quality even further, that's not the issue. The issue is will people notice? Like with CDs I doubt it. Not unless you've got really good audio hardware (rare for a typical PC*).

* I suspect the average PC now uses some form of integrated audio and some tinny speakers that came with in the box.

This little utility will make lot's of users happy. You should include the ability to do the conversion vice versa (for people with portable players that only support mp3).

---

### Post by Erik Trybom on 2007-09-29
The thread is full of posts that explain why conversion is bad so I won't go there again. What I want to know now is, WHY do people want to convert their files from mp3 to ogg? I mean, it's not like the quality gets better or anything, and I''ve yet to see a player that supports ogg but not mp3. Is it because you refuse to install patented codecs on your Ubuntu system?

I understand that the losses in sound quality will be small, but why go through the hassle? I just can't see a reason for it.

---

### Post by richcoosa19 on 2007-10-01
> **FoolsGold_MKII said:**
> Now all I need to do is buy a media player that supports OGG and I'll be set.

I'll just throw away this perfectly good MP3 player and spend money for one that supports OGG. Thank goodness for open source!

:(

If you have a main steam Media player, you might be able to use Rockbox, it will play pretty much whatever format you can throw at it.  I have a Sansa e260 and I  personally like the Rockbox firmware better then the factory firmware.  Rockbox supports may other players other than mine.
:guitar:

---

### Post by Guitar John on 2007-10-24
Just for yuks, a while back I converted a random mp3 to ogg using [Audacity]("http://audacity.sourceforge.net/").  Interestingly, the mp3 file is 13.4 MB.  The resulting ogg file is 21.9 MB.  In other words, it grew.  Go figure.

---

### Post by forrestcupp on 2007-10-24
Lol.  It's funny that people feel like they need to convert their unethical and illegal music downloads into a more ethical and legal file format.

---

### Post by HermanAB on 2007-10-24
One line:
find . -name \*.mp3 -print -exec sox {} {}.ogg \;

Beat that!

Herman

---

### Post by n3tfury on 2007-10-24
> **forrestcupp said:**
> Lol.  It's funny that people feel like they need to convert their unethical and illegal music downloads into a more ethical and legal file format.

LOL , so so true.

---

### Post by HermanAB on 2007-10-24
It is somewhat like buying an artifact that was stolen from a grave 4000 years ago in an art gallery.  Is it more legal or less stolen after it has been restolen and resold numerous times?

---

### Post by n3tfury on 2007-10-24
what does age have to do with anything?  also, did the "buyer" knowingly purchase the artifact even though he knew that it was stolen?  why, yes he did.  does that make it okay?  *think*.

point?

---

### Post by forrestcupp on 2007-10-24
I think Herman is making a point that is agreeing with us.

---

### Post by n3tfury on 2007-10-24
i totally didn't get that and still don't, but ok.

---

### Post by vasiliymeshko on 2007-10-24
> **Guitar John said:**
> Just for yuks, a while back I converted a random mp3 to ogg using [Audacity]("http://audacity.sourceforge.net/").  Interestingly, the mp3 file is 13.4 MB.  The resulting ogg file is 21.9 MB.  In other words, it grew.  Go figure.

I noticed that this happens every time I try to convert MP3 to ogg or vise versa, and the converted files would end up increasing up to twice in size.Why?

---

### Post by Guitar John on 2007-10-24
> Lol. It's funny that people feel like they need to convert their unethical and illegal music downloads into a more ethical and legal file format.


I don't have any mp3's on my computer that were not freely offered from an artist's website.  Actually, most of my files are from my church's [website]("http://www3.calvarychapel.com/ccy/teachings.html").

If you are refering to the fact that some people rip cd's in mp3 format and then share with others, thus robbing the artist of a potential cd sale, that could theoretically be done in ogg format as well.

---

### Post by n3tfury on 2007-10-24
compared to .mp3's, the .oggs floating around on torrents are most likely very few.

---

### Post by Anessen on 2007-10-24
I would also like to point out that all ethics are subjective.

Funny, seeing how MP3 is patented and all. What about the ethics and legality of not paying royalties for decoding it on your Ubuntu system?

---

### Post by Guitar John on 2007-10-24
Additional thought, sort of on subject.  


Also just for yuks, I installed a utility call OggConvert from Synaptic.  What it does is convert any file that GStreamer can read (wmv, avi) into ogg format.  

As before, the file size nearly doubled.  I maximized the Audio and Video quality in the controls.  The video quality was not too bad.  The audio quality was a bit crackily.  

But the issue is, you still need the GStreamer codecs (the ones that it is illegal to have on a free system) to make the conversion.  If the idea is to have a completely free system, this kind of misses the boat, unless I'm missing something. 

The files themselves, I have legally.  But in order to access them I need the codecs.  BTW, I would pay for them if I knew who to pay.  

Any thoughts?

---

### Post by n3tfury on 2007-10-24
> **Anessen said:**
> I would also like to point out that all ethics are subjective.

Funny, seeing how MP3 is patented and all. What about the ethics and legality of not paying royalties for decoding it on your Ubuntu system?

good point.  good think i do cd>.flac then

---

