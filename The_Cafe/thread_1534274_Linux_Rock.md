---
title: "Linux Rock?"
date: 2010-07-19
forum: The Cafe
---

### Post by Jaecyn42 on 2010-07-19
So, my friend and I are considering starting a "Linux Rock Band".  

The idea is fairly straightforward:  Two dudes, making music, with their computers (with conventional instruments functioning as peripherals).

The underlying premise (and the means of doing so) is slightly more complex:  We want to provide an example of the ever increasing potential for self-expression through technology and spread awareness of Linux and the Open Source community.  The general spirit of this project is embodied in our planned band name, "SUDO CHMOD 777", or "Everything is permitted (possible)".

That being said, we have a lot of work to do in order to make our vision possible.  The plan is to build our own specialized, minimalist system (something akin to Xubuntu or Slackware with XFCE) on top of the Real Time Kernel in order to ensure the greatest amount of system resources are available for the various sound applications we will be using (Samples, Sequencer, Effects plugins, etc).  In all likelihood, a significant portion of the Ubuntu Studio package will wind up in our toolbox; but nothing has been decided yet.

Now, this entire undertaking is slightly over both of our heads.  It will definitely be a learning experience, to say the least.

And so I ask, what general (or specific) advice do you have to offer, CC?  Has such a thing been done before, and how?

EDIT:

In terms of ACTUAL music, we're drawing a lot of inspiration from Radiohead, Bassnectar, Rage Against the Machine and Nine Inch Nails, just to give you an idea of the sound we are going for.  :)

---

### Post by LowSky on 2010-07-19
Awesome, go for it!

Personally it doesn't matter what DE you use, I would just go with vanilla Ubuntu with the RT kernel. JACK will be your friend for using real instruments, and you can use Audacity to mix your tracks.

---

### Post by Jaecyn42 on 2010-07-19
Right, JACK is a must, with which I am actively acquainting myself.  As far as DAWs go, I was considering Ardour over Audacious, as I have some experience with it already.

The mixing and recording of tracks does not worry me; I have done a bit of this already.  What I am uncertain of is the feasibility of doing live performances with computers as the ACTUAL instruments.

Basically, his computer and mine will form the instrumental core of our live performances.  All the sound; guitars, bass, drums, vocals, samples and synths; will come directly from his computer or mine, which will then be patched directly into the PA.

For the live performance aspect, I'm not entirely sure how to proceed.  Would JACK and the relevant audio software (sequencer, sampler and effects plugins) be sufficient to accomplish this?  Or would I need some sort of stripped down DAW software as well?

---

### Post by Penguin Guy on 2010-07-19
*facepalm*

---

### Post by Simian Man on 2010-07-19
Why don't you just concentrate on making good music?  Nobody cares what tools you use.

---

### Post by RiceMonster on 2010-07-19
> **Simian Man said:**
> Why don't you just concentrate on making good music?  Nobody cares what tools you use.

Well, some musicians or sound engineers might, but that would require you to make good music first.

---

### Post by cchhrriiss121212 on 2010-07-19
> For the live performance aspect, I'm not entirely sure how to proceed. Would JACK and the relevant audio software (sequencer, sampler and effects plugins) be sufficient to accomplish this? Or would I need some sort of stripped down DAW software as well?
You can just pipe all of your various audio sources to your outputs using jack and patchage, so there is no need for a DAW unless you want to record what you are doing.

To be honest though what you are talking about seems like a bad idea, all of the bands you mentioned rely on live instruments to get their sound, and it would be difficult to replace that with computer samples. There are acts that perform essentially the same way using just a computer, but these are electronic artists, eg: Prodigy, Animal Collective and most hop-hop djs.

---

### Post by keithweddell on 2010-07-19
Don't worry about the naysayers.  Follow your star.  Have fun.

Keith

---

### Post by Jaecyn42 on 2010-07-21
> **keithweddell said:**
> Don't worry about the naysayers.  Follow your star.  Have fun.

Keith

Thanks for the encouragement, Keith.

As for the rest of you who have voiced some criticism of the idea of "computers as instruments", I think perhaps I have failed to describe accurately what I have in mind.

We will, of course, be using "live instruments" in our performances: keyboard, guitars, digital turntable, etc.  However, these instruments will function mostly as peripherals, for lack of a better word.  They will feed directly into our computers, via USB soundcards (mine is a Lexicon Lambda), where we will mix, modify and otherwise manipulate the sound and then output it directly to the PA/Amps.  The goal behind this approach is theatrically to create an impressive variety and breadth of sound, for being just two guys fooling around with instruments and computers.

Perhaps it would be more accurate to say that our computers will function as glorified Pre-Amps/Effects racks to our proper instruments; but, I digress.

As for making good music, rest assured; I'm working on that.  :)  As we begin recording, we will gladly make our work available to the community.

On a side note, this may seem a very silly question; but is it possible to license musical works under the GNU GPL?  We are, after all, trying to make "Open Source Music".

---

### Post by Random_Dude on 2010-07-21
> **Jaecyn42 said:**
> On a side note, this may seem a very silly question; but is it possible to license musical works under the GNU GPL?  We are, after all, trying to make "Open Source Music".

If you provide free download of the music and the samples that you used, maybe it's the closest you can get to GPL. :D

---

### Post by Jaecyn42 on 2010-07-21
> **Random_Dude said:**
> If you provide free download of the music and the samples that you used, maybe it's the closest you can get to GPL. :D

We definitely plan on making our music available for free, or on a "pay-what-you-wish" basis like Radiohead did with *In Rainbows*.  That's not the problem.

The problem is we want to make absolutely certain that our works are never used for any commercial purpose.  I know Copylefting music is hardly a new concept; but I am curious as to what license is most commonly used to Copyleft music.

---

### Post by potat on 2010-07-21
> **Jaecyn42 said:**
> 
On a side note, this may seem a very silly question; but is it possible to license musical works under the GNU GPL?  We are, after all, trying to make "Open Source Music".

A Creative Commons license might be what you're looking for.
[http://creativecommons.org/choose/](http://creativecommons.org/choose/)
EDIT: CC-BY-SA is the most like the GPL as it is "copyleft".

If you really want to make the music "open-source", you should release sheet music or guitar tabs (some MIDI programs can auto-generate sheet music as you play) and the unmixed tracks separately, so that others can reproduce and/or remix your music. I think this can all be done under Creative Commons.

---

### Post by whiskeylover on 2010-07-21
While being in a band may attract a lot of chicks to you and make you popular, the huge amount of nerdage will just cancel it out. Its like mixing alcohol and gatorade.

---

### Post by Simian Man on 2010-07-21
> **whiskeylover said:**
> While being in a band may attract a lot of chicks to you and make you popular, the huge amount of nerdage will just cancel it out. Its like mixing alcohol and gatorade.

That is awesome :).

---

### Post by Jaecyn42 on 2010-07-21
> **potat said:**
> A Creative Commons license might be what you're looking for.
[http://creativecommons.org/choose/](http://creativecommons.org/choose/)

If you really want to make the music "open-source", you should release sheet music or guitar tabs (some MIDI programs can auto-generate sheet music as you play) and the unmixed tracks separately, so that others can reproduce and/or remix your music. I think this can all be done under Creative Commons.

Perfect!  Exactly what I was looking for, many thanks! :)

> While being in a band may attract a lot of chicks to you and make you popular, the huge amount of nerdage will just cancel it out. Its like mixing alcohol and gatorade. 


I think I have my first signature. :D

---

### Post by RiceMonster on 2010-07-21
If you're more focused on the legal and moral aspects of your music before you even have any, I wouldn't worry about anyone using your music for commerical purposes.

---

### Post by Jaecyn42 on 2010-07-21
> **RiceMonster said:**
> If you're more focused on the legal and moral aspects of your music before you even have any, I wouldn't worry about anyone using your music for commerical purposes.

Why so hostile? :(

We've got half a dozen crude tracks, so far; nothing worth sharing at the moment, but we're polishing what we have and working on more.

That said, the legal, moral and technical aspects of our music is our very impetus to make music.  The current musical paradigm is corrupt and unsustainable.  Our goal is to change it.  

Are we likely to elicit any real change?  Probably not.

Is such an undertaking still worthwhile?  Absolutely.

---

### Post by RiceMonster on 2010-07-21
> **Jaecyn42 said:**
> We've got half a dozen crude tracks, so far; nothing worth sharing at the moment, but we're polishing what we have and working on more.

Good. My advice is to focus on that. Trust me, forming a band with other dedicated musicians you can really play well with and creating music you can really be satisfied with is far too difficult to be worrying about how people can access your music before hand. I've played in a few bands, done a bunch of shows, and made numerous recordings, both entirely on my own and with other muscians. Perhaps it's because I'm such a perfectionist with music, but I really feel it takes a lot of practise and hard work to make good music.

Get your songs ready, and focus all your energy on making music you really love. The legal, moral and technical aspects come much later in the game. Afterall, shouldn't it really be about the music itself? Obviosuly you're free to do what you like, but that's my view.

---

### Post by wojox on 2010-07-21
This is all I can picture

[IMG]http://musicianstools.files.wordpress.com/2009/03/devo.jpg[/IMG]

---

### Post by Jaecyn42 on 2010-07-21
> **RiceMonster said:**
> Good. My advice is to focus on that. Trust me, forming a band with other dedicated musicians you can really play well with and creating music you can really be satisfied with is far too difficult to be worrying about how people can access your music before hand. I've played in a few bands, done a bunch of shows, and made numerous recordings, both intirely on my own and with other muscians. Perhaps it's because I'm such a perfectionist with music, but I really feel it takes a lot of practise and hard work to make good music.

Get your songs ready, and focus all your energy on making music you really love. The legal, moral and technical aspects come much later in the game. Afterall, shouldn't it really be about the music itself? Obviosuly you're free to do what you like, but that's my view.

Fair enough.  I too know the difficulties and frustrations that come with finding other dedicated, like-minded musicians who are willing to do the work to make good music.  

I was in one such band, once.  The lead guitarist/vocalist wanted to be in a Jam band, the rhythm guitarist/back-up vocalist wanted to be Billy Corgan, the drummer fancied himself to be Lars Ulrich and I, the bassist, just wanted to play.  Apart from myself, nobody was too interested in practicing or writing originals; just enough work to do covers.

Needless to say, that band lasted for one disastrous show.

At any rate, this project, a duo, won't face the same fate.  My partner in crime and I share an equal amount of dedication to perfecting our craft.  We also share an overwhelming amount of passion for Linux and the Open Source community.  In our minds, technology, Open Source Software, creative self-expression and the Rights of the Individual are irrevocably linked.

It is, indeed, all about the music; which, for us, in turn, is all about the freedom to create, express and innovate.  Without the legal and moral message behind our music, we may as well just be an upgraded Kraftwerk cover-band. :P

With all that being said, we have the pure music aspect covered.  It is the legal, moral and technical aspects where we need help and advice; hence why I posted here and not in a music forum.

---

### Post by Random_Dude on 2010-07-21
May I suggest this for live shows?

[IMG]http://www.mooncostumes.com/image/15273[/IMG]

---

### Post by RiceMonster on 2010-07-21
> **Jaecyn42 said:**
> I was in one such band, once.  The lead guitarist/vocalist wanted to be in a Jam band, the rhythm guitarist/back-up vocalist wanted to be Billy Corgan, the drummer fancied himself to be Lars Ulrich and I, the bassist, just wanted to play.  Apart from myself, nobody was too interested in practicing or writing originals; just enough work to do covers.

Oh dear, I hope I never have to play with that drummer (I have a strong dislike for Lars Ulrich's drumming)! My current band is kind of just casually jamming and writting songs at the moment, because we all have busy and conflicting schedules. Me and the drummer (who I've been playing with since I was 14) have gone through a few bassists and other guitarists. Either they weren't interested, or in some cases, I almost ripped their head off (for things like telling me to write down a totally improvised guitar solo, how I should adjust my amp settings, or claiming a song that we had just started writting had "no structure").

> **Jaecyn42 said:**
> Without the legal and moral message behind our music, we may as well just be an upgraded Kraftwerk cover-band. :P

Well that would be something to be working on then, wouldn't it? :)

---

### Post by Jaecyn42 on 2010-07-21
> **Random_Dude said:**
> May I suggest this for live shows?


Anything is possible, lol.

Before we go buying Penguin outfits, though; we have a significant amount of hardware to invest in.  At least one more sound-card, a digital turntable (my friend only owns an analog turntable), at least two touch-screen monitors (hopefully four, eventually) and potentially some upgrades to our rigs (I could use more RAM, my friend may need a new computer entirely).

---

### Post by Eisenwinter on 2010-07-21
> **Jaecyn42 said:**
> The problem is we want to make absolutely certain that our works are never used for any commercial purpose.
If you were truly interested in making your music completely free, you wouldn't mind it being used by someone commercially.

It's like saying "Only people who think like me can use my stuff". That's not the true essence of free culture/software/music/anything.

I know RMS sometimes sounds like "Keep it free, but only for the likes of me", but he's a bit extreme, to say the least.

If you want your music to truly be free, you will allow anyone to do anything with it.

---

### Post by Swagman on 2010-07-21
Drop the sudo from the name.. too much of a mouthful

Chmod 777 works, or maybe TuxXed ?

---

### Post by Jaecyn42 on 2010-07-21
> **Eisenwinter said:**
> If you were truly interested in making your music completely free, you wouldn't mind it being used by someone commercially.

It's like saying "Only people who think like me can use my stuff". That's not the true essence of free culture/software/music/anything.

I know RMS sometimes sounds like "Keep it free, but only for the likes of me", but he's a bit extreme, to say the least.

If you want your music to truly be free, you will allow anyone to do anything with it.

Not sure if serious...

I don't see commercial use as free use, I see it as restricted use.  At any rate, I'm not talking exclusively in terms of Free as in Freedom; but Free as in beer, as well.

Simply put, I am willing to allow anyone to do anything they like with my work except make a profit off of it.

Is it complete Freedom?  Perhaps not, but it is completely Free.

---

### Post by Random_Dude on 2010-07-21
> **Swagman said:**
> Drop the sudo from the name.. too much of a mouthful

Chmod 777 works, or maybe TuxXed ?

Why not ReadWriteExecute?
It's less geek. :p

---

### Post by Jaecyn42 on 2010-07-21
My friend thinks "sudo chmod 777" is too much too, it's still a point of debate between us.

Would go with just "SUDO", but sadly, it's taken already.

---

