---
title: "Questions about the .OMG container and multichannel Vorbis."
date: 2005-12-20
forum: The Cafe
---

### Post by MetalMusicAddict on 2005-12-20
Ive been doing newier tests with the .AVIs I create. I do all of my media creation in windows. I find the tools there easier to use for now in my already time-constrained family life.

With that said I use [GordianKnot]("http://sourceforge.net/projects/gordianknot") to make .AVIs. Usually with DivX/AC3 codecs.

DivX6 is out and it got me thinking. I dont want to pay to upgrade nor do I want to pirate it. So Im looking again at XviD. I would use Theora but I cant use it in GordianKnot. (more on this later)

So with my recent XviD experiments Ive found Im getting as good visual results from Xvid as DivX with less encoding time. Nice. :)

So now Im switching to XviD. :D But heres where my delima begins.

I switched to one open format so why not move the rest?

-_Problem 1_
I can transcode and downsample (I know. I dont like it but it saves alot of filespace) .AC3 to multichannel Vorbis using Besweet.

My question with this is:
**-How does a soundcard send Multichannel Vorbis to a reciever?**

example: When I play a .AVI with .AC3 audio. the reciever sees it and flips it to 5.1 surround mode or I can manually do it. So when I play a Multichannel Vorbis will it be surround? Is it up to the app I use to play it?
Im just lacking info on how this works.


-_Problem 2_
The container. In GordianKnot I can use a choice of 3 containers. AVI, OGM and MKV. I was tryin to stay Xiph as much as possiable and use .OGM but I've read (Doom9, AfterDawn) its just about a dead format not supported by Xiph and a hack of .OGG. I'd go .OGG if I could. The O.C.D. in me wont let me go MKV.

**-So, is there a way to losslessly go from a .OGM to .OGG? Or should I just go with .OGM?**

I will one day switch to linux tools to do this when I find the right tools for me. I want to eventually move to Theora/Vorbis.OGG but having this info will help. Links to guides are cool. This is this weeks project and I have some reading to do. :)


Hi Poptones.

---

### Post by xequence on 2005-12-20
Isnt OMG sonys format? Its the extension to atrac3plus I think.

Oh, and Xvid = good :P

---

### Post by MetalMusicAddict on 2005-12-20
I got it mixed up. Its .OGM. Changed 1st post.

---

### Post by Malphas on 2005-12-20
You can't put a XviD stream in an Ogg container to my knowledge, I would go with Matroska - there's really no point in OGM any more.   Also, I find it shocking that some people are still using DivX, good call on ditching it in favour of XviD.

---

### Post by MetalMusicAddict on 2005-12-21
[QUOTE=Malphas]You can't put a XviD stream in an Ogg container to my knowledge[/QUOTE]Ill read up on that and like I said "The O.C.D. in me wont let me go MKV". :)
> Also, I find it shocking that some people are still using DivX, good call on ditching it in favour of XviD.
Why do you find it shocking? I think thats most peoples 1st big MPEG4 experience. That and Quicktime.

I had a DVD player that did DivX fine and was supposed to do XviD but never played them right for some reason. I have a new one now is supposed to do OGG. Hence the reevaluation of XviD. Though I dont think the DVD player will do Theora or MKV. I gotta look. I also have a HTPC but Im trying to keep my new DVD player compatiable. Now I have to go to work.

---

### Post by Malphas on 2005-12-21
[QUOTE=MetalMusicAddict]Ill read up on that and like I said "The O.C.D. in me wont let me go MKV". :)[/QUOTE]
Why not exactly?  It's the correct container for what you're wanting to do.  Ogg was intended to be a completely free format and thus only use Xiph.org endorsed codecs (for video this limits you to Theora and Tarkin).  Like you said OGM is basically a hack that allows you to use other codecs, this was basically a stopgap measure due to the Xiph.org codecs being somewhat immature.  MKV has basically eliminated the need for OGM entirely, in my opinion.

[QUOTE=MetalMusicAddict]Why do you find it shocking? I think thats most peoples 1st big MPEG4 experience. That and Quicktime.[/QUOTE]
Not really, XviD overtook DivX in terms of videos being released on the 'net years ago.  Not to mention that DivX is inferior quality, proprietary (yes, I know XviD isn't 100% free either) and costs money (most of the time).  And I really don't think many people other than Mac users use Quicktime, most people see it as a nuisance, like RM files.  Edit: Actually, perhaps this is changing with the iPod.  I've never liked Quicktime anyway.

[QUOTE=MetalMusicAddict]I had a DVD player that did DivX fine and was supposed to do XviD but never played them right for some reason. I have a new one now is supposed to do OGG. Hence the reevaluation of XviD. Though I dont think the DVD player will do Theora or MKV. I gotta look. I also have a HTPC but Im trying to keep my new DVD player compatiable. Now I have to go to work.[/QUOTE]
I see.  In this case - and I know a lot of people here may disagree with me completely - the best solution is probably XviD with the FOURCC set to DivX (or ideally H.264, if your player supports it), AAC audio and an MP4 container.

---

### Post by majikstreet on 2005-12-21
dot oh my god?
dot oh my gosh?

LOL..

---

### Post by MetalMusicAddict on 2005-12-21
[QUOTE=Malphas]due to the Xiph.org codecs being somewhat immature.[/QUOTE]
So is Theora mature now?

As far as the audio goes Ill either stay AC3 or go Vorbis. I want to go all Xiph because my player seems to support it from what I can read. Wont really know till this weekend when I have read more and have more free time.

Do you know how a home theater handles multi-channel Vorbis?

---

### Post by poptones on 2005-12-21
How does your player connect to the amp? If it uses AC3 transport you're going to have to stay with AC3. If you have analog outputs switched through a receiver then you can probably use pcm, but that's going to be up to your player as well.

I'm not aware of any digital transport of sound between player and peripherals other than AC3 and DTS, and both those are proprietary. Once you get a HTPC setup you might be able to install software to encode AC3 on the fly (as some games now do) but no matter how you do it you're going to use AC3 (edit, I meant AC3 or DTS ie something "not free") if you want digital sound transport between appliances.

---

### Post by MetalMusicAddict on 2005-12-21
Both my DVD player and my HTPC connect through SPDIF. I would like to use the multichannel Vorbis on at least the HTPC. If all I have to do is install a app/mixer/codec that would be great. I dont think my receiver will handle/decode it though. Still more research. I have a feeling Im not in luck and Ill have to stay AC3 if I want surround. Ill make some vids this weekend.

Quick pick of Ubuntu, plasma and Olivia. :) Im still working on getting Ubuntu setup right for the plasma.

---

### Post by poptones on 2005-12-21
The thing is, about "converting" ac3 and such is it's not going to help much anyway. Making ac3 (or DTS) into something else is just going to add more compression artifacts (something ac3 has too much of already).

BTW I dunno what kind of sound card you have but I assume it's not an "I'll just resample everything to 48khz" SoundBastard type card. That won't even give you proper ac3 output.

If you don't think your receiver will decode ac3 then how are you getting surround right now? If you are using rca patch cords from the dvd player/htp to the amp then you should be able to use anything you want (although, as I said, recompressing the audio is just going to make it worse).

---

### Post by MetalMusicAddict on 2005-12-21
I guess I wasnt so clear. Right now I do have a HTPC that I play my DivX/AC3.AVIs. The audio goes out through the SPDIF output of my soundcard. This is all in windows so far. Im workin on Ubuntu. I guess if the soundcard doesnt see a AC3 or DTS signal Iit will act funny but I was hoping that installing something would help.

Yea, I know. Like I said in my 1st post going from one already lossy format to another isnt the best but it saves me filesize and I can live with it for now. If it were for music there would be no way in hell I would do this. I usually yell at people who do.

---

