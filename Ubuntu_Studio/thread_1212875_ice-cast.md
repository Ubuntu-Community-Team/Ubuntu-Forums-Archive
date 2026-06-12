---
title: "ice-cast"
date: 2009-07-14
forum: Ubuntu Studio
---

### Post by johnh10000 on 2009-07-14
Now I am new to this side of things please be gentle.

There's a chance I might be broadcasting for a internet station soon.  The software they recommend is all windows.  So I got icecast, djplay, Internet DJ console and jack.

Now for testing perposes, is it possible set this icecast thingy up so I can "broadcast" to my girlfriend in the living room.

We have a lan, mostly wired, and her lappy on the wifi (running windows 7)

The length and longth of it how do you configure Icecast?

---

### Post by bobince on 2009-07-17
You probably don't need to test with running your own icecast server if you are only wanting to DJ. There are public test casters available for you to play with, such as eg. [http://www.stream24.com/?page=icecast-server-demo](http://www.stream24.com/?page=icecast-server-demo)

(You're sure it's an ice server your station is using? Shoutcast is still more common at the moment, even though it's hideously old and nasty. idjc can easily connect to either type, of course, but you will probably want to compile the latest version yourself as the one in the ubuntu repos has no MP3 support and is totally out of date.)

---

### Post by johnh10000 on 2009-07-17
> **bobince said:**
> You probably don't need to test with running your own icecast server if you are only wanting to DJ. There are public test casters available for you to play with, such as eg. [http://www.stream24.com/?page=icecast-server-demo](http://www.stream24.com/?page=icecast-server-demo)

(You're sure it's an ice server your station is using? Shoutcast is still more common at the moment, even though it's hideously old and nasty. idjc can easily connect to either type, of course, but you will probably want to compile the latest version yourself as the one in the ubuntu repos has no MP3 support and is totally out of date.)

Don't know what ace radio is using but it strams to winamp, real, mediaplayer and something else.

As it happens I just download the latest icecast source.

oh ace's link is on my site. [http://tux.isa-geek.org](http://tux.isa-geek.org)

 I have got idjc and plan to use it.  I quite like djplay, but can't get a nosie out of it :(

BTW also got darkice, and darksnow, do I need them if I use idjc? 

Finnaly is there a nice gui for the playlist.txt side of things?

Well a gui for ices generally?

Didn't know and the testing grounds, will take a look at them later, thanks

---

### Post by bobince on 2009-07-19
> **johnh10000 said:**
> oh ace's link is on my site.

If that's the &#8216;Tux FM&#8217; link, yeah, that looks like an Icecast server judging by the link URL style. (Doesn't seem to actually be running to check for sure though.)

> BTW also got darkice, and darksnow, do I need them if I use idjc?Nope. idjc plays out directly to an icecast-or-shoutcast server; you don't need any further tools to broadcast (other than JACK itself and whatever audio format libraries you want).

Darkice (+darksnow frontend) is an a different caster you can use to broadcast any sounds you can funnel into it from other programs (typically via JACK); there's no player built in so you'd use whatever your favourite media player is, and connect/mute the mic manually if necessary.

> Well a gui for ices generally?Not that I'm aware of, but its operation is so simple it's probably not needed. A playlist file is just a list of newline-separated paths&#8201;&#8212;&#8201;which happens to be the same as m3u format, so if your media player can save .m3u playlists you're there already.

Again, if you are using IDJC (or darkice), you don't need IceS. It's just another possible caster.

---

### Post by johnh10000 on 2009-07-20
> **bobince said:**
> If that's the ‘Tux FM’ link, yeah, that looks like an Icecast server judging by the link URL style. (Doesn't seem to actually be running to check for sure though.)


No sorry mat that one IS icecast, I'm running it.. When you cheched yesterday I guess, it was moving house! for my main ubuntu box to the bedroom's one.  THats why it is/was down.

ace's link is on my links pgae, but [http://www.aceradio.co.uk](http://www.aceradio.co.uk)

> 
Nope. idjc plays out directly to an icecast-or-shoutcast server; you don't need any further tools to broadcast (other than JACK itself and whatever audio format libraries you want).

yeah that seems to be working fine.  just a bit of a struggle to get over to tux2.  tried to cheat, failed.  Had to recompile the thing anyway ;)

> 
Darkice (+darksnow frontend) is an a different caster you can use to broadcast any sounds you can funnel into it from other programs (typically via JACK); there's no player built in so you'd use whatever your favourite media player is, and connect/mute the mic manually if necessary.

that sounds more like what i need.  i have grovey player, from windoz, which works under wine.  so i need to grab sndcard output and stream it.

> 
Not that I'm aware of, but its operation is so simple it's probably not needed. A playlist file is just a list of newline-separated paths&#8201;—&#8201;which happens to be the same as m3u format, so if your media player can save .m3u playlists you're there already.

hmmm this bit i don't understand qonce i've got my playlist file what do ido with it?

also for darkice, i found something called dark snow.
> 
Again, if you are using IDJC (or darkice), you don't need IceS. It's just another possible caster.
hmm and a confusing one at that.

Oh while we're at it say I have a stream of say playlist1, would I just set up idjc to just stream another stero pair?

Thank you for your help.

If all goes well today, I shoul be able to "broadcast" soon.

---

### Post by bobince on 2009-07-21
> **johnh10000 said:**
> [http://www.aceradio.co.uk](http://www.aceradio.co.uk)

Aha, yep: that's one's SHOUTcast. So you'll need to send it MP3, which means you'd have needed your own compile of idjc in any case. 

(DarkIce can also be configured to stream to SHOUTcast; or with IceS you have to use ices0 instead of the usual ices2 you'd use for Icecast.)

There are SHOUTcast test servers you can play with at eg. [http://www.stream24.com/?page=shoutcast-server-demo](http://www.stream24.com/?page=shoutcast-server-demo) , [http://www.shoutcastserver.org/](http://www.shoutcastserver.org/) .

> hmmm this bit i don't understand qonce i've got my playlist file what do ido with it?

ices can take input from a playlist file, if all you want is to send out a prepared list of tunes. Otherwise, not needed.

> Oh while we're at it say I have a stream of say playlist1, would I just set up idjc to just stream another stero pair?

Not quite sure what you mean by that, but with idjc you're using JACK, which makes it easy to route multiple audio streams between applications.

---

### Post by johnh10000 on 2009-07-21
> **bobince said:**
> Aha, yep: that's one's SHOUTcast. So you'll need to send it MP3, which means you'd have needed your own compile of idjc in any case. 
> 
This is not a problemo, I had to recomile it for jaunty anyway ;)

[quote]

(DarkIce can also be configured to stream to SHOUTcast; or with IceS you have to use ices0 instead of the usual ices2 you'd use for Icecast.)

There are SHOUTcast test servers you can play with at eg. [http://www.stream24.com/?page=shoutcast-server-demo](http://www.stream24.com/?page=shoutcast-server-demo) , [http://www.shoutcastserver.org/](http://www.shoutcastserver.org/) .


Hmm well I haven't got the job yet!

[quote]
ices can take input from a playlist file, if all you want is to send out a prepared list of tunes. Otherwise, not needed.

Not quite sure what you mean by that, but with idjc you're using JACK, which makes it easy to route multiple audio streams between applications.

Now this is where I'm at the mo. 

What Gfriend and I are doing/going to be doing is make several 1-2 hr shows.

Record to mp3.

now what do I need to do to be able to have a link on the website to say show 1 -> and it will produce a stream of that show?

Being able to stream it , wislst maing it is the easy bit.

Thanks for your help btw

Take a gander at the web site, and please sign the guestbook, a bit of code going to waste there ;)

[http://tux.isa-geek.org](http://tux.isa-geek.org)

---

### Post by johnh10000 on 2009-07-21
Oh I got the current icecast source and compiled that.  That's howcome we'r working at all!

I have just thought, I'd like to bbeable to stream say at 21:00 bst the same show, for that week.  Ok cron it.  Caould I use idjc as cron start up?

---

### Post by bobince on 2009-07-21
> Record to mp3.

Easy with IDJC, see the ‘Record’ stuff at the bottom of the ‘Servers’ config window.

> now what do I need to do to be able to have a link on the website to say show 1 -> and it will produce a stream of that show?

First, have a simple a-href link directly to the .mp3 file. Depending on browser configuration and plugins, clicking this might cause it to download the whole MP3, or it might try to play the MP3 in the browser. But this way guarantees everyone should be able to do *something* with the audio.

Other things you can do include:

* link to a playlist file containing the URL of the MP3. This will ensure that it is streamed by a media player instead of downloaded, but it is likely to require a manual step to load the playlist into a media player, and not all media players support the same playlist formats. Start with a .m3u file though.

* embed an inline Flash MP3 player pointed at the MP3 file. There are various free MP3 players to choose from.

* embed an inline media player of some sort, typically Windows Media Player, QuickTime or Real. This is much more likely to break and annoy than Flash though.

> Caould I use idjc as cron start up?

Technically yes, using a command-line switch like ‘-s 1’ to connect at start-up. I don't know of a way to make it play music automatically, although it'd surely be simple to add (as the main app is scripted in Python and the author lurks around these parts).

Then again, if all you're doing is restreaming a saved MP3, IDJC might be a bit over the top; it might be simpler to just start IceS0 for a single MP3. Either way, you would need to store that intermediate MP3 in as high a quality as possible&#8201;—&#8201;WAV would be even better&#8201;—&#8201;because whatever you use to stream (IDJC, IceS0 or DarkIce), they're all going to recode the audio input to MP3 again, which involves an additional loss of quality.

(It would be ideal if you could record to MP3 in the exact format/bitrate you'll end up sending to the SHOUTcast server, but unfortunately I don't currently know of any streamer tools that will send an existing MP3 without transcoding it.)

In any case a cronned start may or may not work well with the practices of the radio station itself... typically, SHOUTcast stations with multiple different DJ sources need some hand-holding at handover time to make sure that one DJ connects just after the previous one disconnects.

---

### Post by johnh10000 on 2009-07-21
> **bobince said:**
> Easy with IDJC, see the ‘Record’ stuff at the bottom of the ‘Servers’ config window.

i noticed that
> 
First, have a simple a-href link directly to the .mp3 file. Depending on browser configuration and plugins, clicking this might cause it to download the whole MP3, or it might try to play the MP3 in the browser. But this way guarantees everyone should be able to do *something* with the audio.

ok last choice.
> 
Other things you can do include:

* link to a playlist file containing the URL of the MP3. This will ensure that it is streamed by a media player instead of downloaded, but it is likely to require a manual step to load the playlist into a media player, and not all media players support the same playlist formats. Start with a .m3u file though.

ahh now this is the way i want to do it.
 Couldn't i just href to a .m3u file? well i know that don't work:(
what exactly should be in the playlist file?

I have at the mo in demo.m3u and aceradio.m3u (don't ask)
/home/johnh10000/tux.isa-geek.org/htdocs/demo/aceradio.mp3

is that right?

> 
* embed an inline Flash MP3 player pointed at the MP3 file. There are various free MP3 players to choose from.
* embed an inline media player of some sort, typically Windows Media Player, QuickTime or Real. This is much more likely to break and annoy than Flash though.

As I said I'd prefer to stream it, now I have the the thing working.
what would you recommend?

> 
Technically yes, using a command-line switch like ‘-s 1’ to connect at start-up. I don't know of a way to make it play music automatically, although it'd surely be simple to add (as the main app is scripted in Python and the author lurks around these parts).

does he? hmmm.  I know theres a tick box to play on start streaming in the gui so....
> 
Then again, if all you're doing is restreaming a saved MP3, IDJC might be a bit over the top; it might be simpler to just start IceS0 for a single MP3. Either way, you would need to store that intermediate MP3 in as high a quality as possible&#8201;—&#8201;WAV would be even better&#8201;—&#8201;because whatever you use to stream (IDJC, IceS0 or DarkIce), they're all going to recode the audio input to MP3 again, which involves an additional loss of quality.


that sounds interesting, i will lookinto that one

> 

(It would be ideal if you could record to MP3 in the exact format/bitrate you'll end up sending to the SHOUTcast server, but unfortunately I don't currently know of any streamer tools that will send an existing MP3 without transcoding it.)

In any case a cronned start may or may not work well with the practices of the radio station itself... typically, SHOUTcast stations with multiple different DJ sources need some hand-holding at handover time to make sure that one DJ connects just after the previous one disconnects.
[/quote]

are there your reading me at cross perposes.  The re-webcasting, is not for ace, it for me and "tux fm" or whatever the heck it gets called.

But I'd really like to know how this play list thingy, .m3u works.

---

### Post by StephenF on 2009-07-21
> **johnh10000 said:**
> 
I have just thought, I'd like to bbeable to stream say at 21:00 bst the same show, for that week.  Ok cron it.  Caould I use idjc as cron start up?
Yes you could but make sure to launch IDJC early and use the timed start and stop feature in the server window as well as checking the Upon connection button so the player starts automatically.

You could create several profiles and call them monday, tuesday, and so on. I think you know where I am going with this. That way you could preschedule a whole week of programming. Make sure to use cron to kill IDJC after each show.

For pre recording I suggest using the 24 bit FLAC format as that reduces the quality loss of re-encoding to a bare minimum. I'm assuming you have the disk capacity to spare.

In prefs->connection management I suggest increasing the number of connection retires since the standard configuration assumes a DJ will be present or use the unlimited option.

---

### Post by johnh10000 on 2009-07-21
> **StephenF said:**
> Yes you could but make sure to launch IDJC early and use the timed start and stop feature in the server window as well as checking the Upon connection button so the player starts automatically.

You could create several profiles and call them monday, tuesday, and so on. I think you know where I am going with this. That way you could preschedule a whole week of programming. Make sure to use cron to kill IDJC after each show.


well hmm thinks yeah kill that instance of dj

> 

For pre recording I suggest using the 24 bit FLAC format as that reduces the quality loss of re-encoding to a bare minimum. I'm assuming you have the disk capacity to spare.

In prefs->connection management I suggest increasing the number of connection retires since the standard configuration assumes a DJ will be present or use the unlimited option.

24 bit flack, hmm Had not even research ed that far. i run ther server for this perpose, but i still wan a 9pm show to go out at 9pm

thanks for your interest

we streaming dead air at the min the icecast server just moved into the bedroom, and i got the devs but for got the actuaal libs well some of 'em.
gfriend sleeping. back up 2morrow.

[http://tux.isa-geek.org](http://tux.isa-geek.org)

---

### Post by johnh10000 on 2009-07-21
Oh what do the gang think?

A website with achat room and mabe even a forum

email requests etc

it's jus a page on my website for now.

hmm must think about prs

---

