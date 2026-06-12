---
title: "What Vorbis settings do you use? or The good and bad of Vorbis."
date: 2005-12-26
forum: The Cafe
---

### Post by MetalMusicAddict on 2005-12-26
Ive been playing around with switching to Vorbis lately. With .mp3s I use a VBR setting close to alt-preset standard. A little higher than a 192 average most of the time. With using the "quality" setting, for apps that use Vorbis, for me to get about a 192 avg looks like the setting is 6.6 or so. Im still looking into all of this.

For me I have 2 reasons I *might* not switch.
**-**Hardware. I have a Pioneer in-dash that plays mp3 CDs.
**-**Battery life in portables. I have a iRiver H340. I have seen many people say it takes more CPU power to decode Vorbis. Thus draining the battery faster.

These arent concrete reasons for me. Just considerations.

_So my questions are:_
**-**What do you use to encode music in linux?
**-**Is Vorbis always Stereo or does it use Joint Stereo?
**-**From what I've seen Vorbis really only does "better" (audibly) at lower bit-rates. Whats your experience?
**-**Becides hardware support whats the downside to Vorbis?
**-**What kind of "tag" does Vorbis use? Is it up to the container? ie: .ogg? If so, what types of "tags" does it support?
**-**If your *really* into music whats your philosophy/guidelines on using Vorbis?

And lastly:
**-**Ive seen post on audio fourms that people dont like Xiph. Is that true and why?

\m/

---

### Post by lcg on 2005-12-26
[QUOTE=MetalMusicAddict]Ive been playing around with switching to Vorbis lately. With .mp3s I use a VBR setting close to alt-preset standard. A little higher than a 192 average most of the time.[/QUOTE]
Have a look at the newer LAME -V settings, they allow for finer control over quality and bitrate.

[QUOTE=MetalMusicAddict]With using the "quality" setting, for apps that use Vorbis, for me to get about a 192 avg looks like the setting is 6.6 or so. Im still looking into all of this.[/QUOTE]
For me, q 6.0 usually has an average above 192kbs and is absolutely transparent to my ears (i.e. cannot be distinguished from the original).

[QUOTE=MetalMusicAddict]
For me I have 2 reasons I *might* not switch.
**-**Hardware. I have a Pioneer in-dash that plays mp3 CDs.[/QUOTE]
Something worth considering, I agree.

[QUOTE=MetalMusicAddict]
**-**Battery life in portables. I have a iRiver H340. I have seen many people say it takes more CPU power to decode Vorbis. Thus draining the battery faster.[/QUOTE]
Actually, that is true. Ogg Vorbis is more demanding and takes more power to decode.

[QUOTE=MetalMusicAddict]
_So my questions are:_
**-**What do you use to encode music in linux?[/QUOTE]
Vorbis -q 6.0, both in Linux and Windows.

[QUOTE=MetalMusicAddict]
**-**Is Vorbis always Stereo or does it use Joint Stereo?[/QUOTE]
Joint Stereo up to q 5.0 or q 6.0, stereo above that, AFAIK.

[QUOTE=MetalMusicAddict]
**-**From what I've seen Vorbis really only does "better" (audibly) at lower bit-rates. Whats your experience?[/QUOTE]
When comparing Vorbis and MP3 with approximately the same bitrate, I can usually tell the MP3 before the Vorbis as the bitrates go lower.

[QUOTE=MetalMusicAddict]
**-**Becides hardware support whats the downside to Vorbis?[/QUOTE]
I can't really think of any.

[QUOTE=MetalMusicAddict]
**-**What kind of "tag" does Vorbis use? Is it up to the container? ie: .ogg? If so, what types of "tags" does it support?[/QUOTE]
.ogg has its own tags. Basically, they are just arbitrary name/value pairs, so you can have whatever you want (there are some standard tags like artist, album and so on).

[QUOTE=MetalMusicAddict]
**-**If your *really* into music whats your philosophy/guidelines on using Vorbis?[/QUOTE]
I'm not sure what answer you want to hear to that question. Personally, I prefer Ogg Vorbis over MP3 for 2 reasons: 1.) Its superior quality at the same size (or the smaller size at comparable quality, if you want to put it that way). 2.) It is roalty free and constantly improved (OK, so is the LAME encoder).

[QUOTE=MetalMusicAddict]
And lastly:
**-**Ive seen post on audio fourms that people dont like Xiph. Is that true and why?[/QUOTE]
I don't really know if that is true. But then, I never really had anything to do with the Xiph guys.

Lars

---

### Post by MetalMusicAddict on 2005-12-26
Thanx for all the info lcg. ;)

[QUOTE=MetalMusicAddict]
**-**If your *really* into music whats your philosophy/guidelines on using Vorbis?[/QUOTE]
I asked this because some people dont really care and just use defaults of whatever app their using. I am rather anal about music.

---

### Post by lcg on 2005-12-26
> **MetalMusicAddict]Thanx for all the info lcg.  said:**
> 
You're welcome.

[QUOTE=MetalMusicAddict]I asked this because some people dont really care and just use defaults of whatever app their using. I am rather anal about music.
In that case and if you have the space, why not go lossless with flac?

If size is an issue, however, I suggest you get some 'typical' music for you, rip it to .wav, encode it with different quality settings and find out which one is best suited for your ears via a double blind test (A.K.A. ABX). Some tools to do that would be LinABX, ABC/HR, WinABX or ABC/HR-Java.

There is no way someone can tell you what level of compression sounds good to you. Most of the time, Ogg Vorbis is transparent to me at q 4.0 or 5.0. When I started ripping my CD collection, I decided to go with q 6.0, though, just to be on the safe side. (I'm still waiting for a bitrate peeling tool to reduce my files to a quality that is more suitable for portable devices.) Who knows, as harddisk space is growing far faster than my CD collection is, I might one day decide to re-rip using flac. Yes, I might really do that if I ever find the time ... ;)

HTH,
Lars

---

### Post by MetalMusicAddict on 2005-12-26
[QUOTE=lcg]In that case and if you have the space, why not go lossless with flac?[/QUOTE]
Space is a little issue only in that I dont want to have TBs of space in order to hold it all. :) Though, I do have about 800gigs now. :rolleyes: I have about 1200 CDs that all sit nicely on a 80gig drive at the moment. I started my mp3 collection years ago and all of it is at the same settings minus a couple of things I downloaded. So I stay for continuity.

As for listening tests I have been trained as a audio engineer (live sound mostly) and have got to do tests in nice studio booths. :) I could tell the difference between a CD and what I use there but outside of a controlled environment the difference was hard to tell so I stuck with it. I plan on doing some nice headphone tests since I dont have access to a booth now.

Mostly my reason for switching is to support open formats. Most people dont like to because mp3 is all they download. Its nice to own my CDs. ;)

---

### Post by lcg on 2005-12-26
> **MetalMusicAddict]As for listening tests I have been trained as a audio engineer (live sound mostly) and have got to do tests in nice studio booths. :) I could tell the difference between a CD and what I use there but outside of a controlled environment the difference was hard to tell so I stuck with it. I plan on doing some nice headphone tests since I dont have access to a booth now.[/QUOTE]
OK, I obviously can't compete with that kind of equipment and training.  said:**
> Mostly my reason for switching is to support open formats. Most people dont like to because mp3 is all they download. Its nice to own my CDs. ;)
Yes, though I do download music from time to time, it is more of an extended test. I still prefer CDs with a printed booklet and all the 'eye candy'. I'm a collector when it comes to music and movies. I really like to have a shelf full of CDs or DVDs in the living room. I just don't like having to walk over and get the CD I want to listen to while working on the computer, so I keep an Ogg Vorbis copy on the house server.
However, I am really ticked off by the outrageous prices that the entertainment industry charges. I mean, come on, some months later they sell stuff for half the price. And you can be certain they are not giving anything away for free, not even for the lower price. Right now, I mostly wait until prices reach a point which I am willing to pay.

The only thing I really avoid are copy protected CDs. Why would I buy a CD with a defective error correction? (I have one and it is horrible to listen to; there's clicking noises all the time, even in really good CD players. I can only hope that this was intentional to create some feeling of nostalgia, though it ruined the album either way.)
And the latest, most annoying trend on DVDs in Germany (and probably elsewhere) are those little video clips condemning piracy. I mean, come on, I just bought the darn thing. Do they really think that the people downloading the movie will get to see that? The only ones who have to suffer from it are the ones who bought it in the first place. Thanks very much.

OK, that's enough ranting for one night. Is anybody still reading this? ;)

Lars

---

### Post by MetalMusicAddict on 2005-12-26
> **lcg]Yes, though I do download music from time to time, it is more of an extended test. I still prefer CDs with a printed booklet and all the 'eye candy'. I'm a collector when it comes to music and movies. I really like to have a shelf full of CDs or DVDs in the living room.[/QUOTE]
Same here. I have them on either side of my 43" plasma.  said:**
> I just don't like having to walk over and get the CD I want to listen to while working on the computer, so I keep an Ogg Vorbis copy on the house server.
However, I am really ticked off by the outrageous prices that the entertainment industry charges. I mean, come on, some months later they sell stuff for half the price. And you can be certain they are not giving anything away for free, not even for the lower price. Right now, I mostly wait until prices reach a point which I am willing to pay.
I still buy ALOT of CDs even though it pays big record companies also. But I try to buy at an artists show where they actually see more money from it.

Or lately Ive been advocating buying CDs used. Noone past the merchant sees money on used CDs. 
> The only thing I really avoid are copy protected CDs. Why would I buy a CD with a defective error correction? (I have one and it is horrible to listen to; there's clicking noises all the time, even in really good CD players. I can only hope that this was intentional to create some feeling of nostalgia, though it ruined the album either way.)
I have a couple and havnt run into problems yet. With pops from the actual CD or ripping it in my PC. :)
> And the latest, most annoying trend on DVDs in Germany (and probably elsewhere) are those little video clips condemning piracy. I mean, come on, I just bought the darn thing. Do they really think that the people downloading the movie will get to see that? The only ones who have to suffer from it are the ones who bought it in the first place. Thanks very much.

OK, that's enough ranting for one night. Is anybody still reading this? ;)

Lars
I find it funny. I have friends thave boot-leg DVDs with the warning still in it. :)

---

### Post by xequence on 2005-12-26
If your goal is good quality lossy music you cant beat Musepack.

Though I personally find MP3 to be great quality at --alt-preset standard.

---

### Post by bugmenot on 2006-03-20
Just throwing in some arguments for closure...

- The Vorbis format allows gapless playback without hassle (contra MP3)
- The Vorbis tagging (called vorbis comments) is very clean (contra ID3 character encoding mess) and the only tag format one has to deal with (contra MP3)
- The vorbis stream is better at seeking and can be rewritten (for example to cut it in pieces; contra Musepack)

---

