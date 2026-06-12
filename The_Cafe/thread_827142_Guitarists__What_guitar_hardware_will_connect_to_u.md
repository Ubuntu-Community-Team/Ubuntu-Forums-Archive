---
title: "Guitarists:  What guitar hardware will connect to ubuntu pc?"
date: 2008-06-12
forum: The Cafe
---

### Post by gatorbrit on 2008-06-12
Hi, I have used line6 products, but I would like to do some basic recording using ubuntu.  Previously I have used the line6 guitarport.

What hardware / effects processors/ etc can you plug into a ubuntu pc and then record, say using audacity?

I am looking for a pretty simple solution..

Thanks

:guitar:

---

### Post by forrestcupp on 2008-06-12
All you have to do is buy a cheap 1/4" to 1/8" adapter to plug a guitar cord into your sound card for recording.

Edit:
And try using Ardour for recording.  You can do multi-track stuff with it better than Audacity.

---

### Post by gatorbrit on 2008-06-12
Duuhhh - why didn't I think of that!!!!!

Any recommendations for effects - reverb distortion etc?  Or could I do this:

Guitar->stomp box-> sound card?

Cheers!!

---

### Post by RiceMonster on 2008-06-12
> **gatorbrit said:**
> Duuhhh - why didn't I think of that!!!!!

Any recommendations for effects - reverb distortion etc?  Or could I do this:

Guitar->stomp box-> sound card?

Cheers!!

I usually line a stompbox into the soundcard on any OS. That should work just fine. I don't like using effects from software.

---

### Post by pluckypigeon on 2008-06-12
> **forrestcupp said:**
> All you have to do is buy a cheap 1/4" to 1/8" adapter to plug a guitar cord into your sound card for recording.


Is it really that simple? Don't you need a pre-amp to amplify the signal?

---

### Post by acelin on 2008-06-12
Yeah you can do these things, but it will sound horrible, and inflexible. You need something that outputs to midi, or a device that connect via USB rom microphone. As for Linux compatible, there are people who do this sort of thing... you might want to head on over to the sound and multimedia area of the forums for me help with this.

---

### Post by _DD_ on 2008-06-12
Generally when recording a guitar directly you want to do so from a high-impedance (Hi-Z) input to simulate the same "load" on the pickups to get the same sound that you would normally expect. Some audio interfaces offer Hi-Z pickups. I have an Edirol FA-101 and one of the Neutrik combination inputs on the front can be toggled to high impedance.

The best way to record guitar IMO is still just is still the good ol' fashioned way of mic'ing up a guitar cab. SM57s are the 'industry standard' for doing this. I've also had good results with various small-diaphragm condensers like C1000s, however these can sound a bit 'bright'.

In reality though, mic placement is almost more important (in terms of tone/sound) than the mic choice. For live SR I usually do an SM57 about halfway between the centre and the edge of the cone, pointing slightly inwards. A mic pointing directly at the centre of the cone is usually far too harsh-sounding.

Of course if you want to experiment with the mic idea you'll need an audio interface with mic preamps.

---

### Post by acelin on 2008-06-12
> **_DD_ said:**
> 

The best way to record guitar IMO is still just is still the good ol' fashioned way of mic'ing up a guitar amp. An SM57 will do this perfectly.

This man speaks the truth.

---

### Post by gatorbrit on 2008-06-12
Now would the mic just plug straight into the sound card?

---

### Post by _DD_ on 2008-06-12
No, you need a mic preamp.

You can get nice little USB or Firewire boxes nowadays called portable audio interfaces - they're like a step up from a sound-card, but not quite the 24 channel rackmount Motu's or whatever you'd find in a studio :p

They usually have a few inputs (including one or two mic preamps), a few outputs, etc, all packaged up.

As I said, I have one called the Edirol FA-101. You can get much simpler and cheaper ones which wouldn't be much different from your Guitarport. You'd need to check out which ones had linux drivers though. The FA-66 is a smaller version of the FA-101.

[http://www.ffado.org/](http://www.ffado.org/)
[http://freebob.sourceforge.net/](http://freebob.sourceforge.net/)

---

### Post by gatorbrit on 2008-06-12
> **_DD_ said:**
> No, you need a mic preamp.

You can get nice little USB or Firewire boxes nowadays called portable audio interfaces - they're like a step up from a sound-card, but not quite the 24 channel rackmount Motu's or whatever you'd find in a studio :p

They usually have a few inputs (including one or two mic preamps), a few outputs, etc, all packaged up.

As I said, I have one called the Edirol FA-101. You can get much simpler and cheaper ones which wouldn't be much different from your Guitarport. You'd need to check out which ones had linux drivers though.

[http://www.ffado.org/](http://www.ffado.org/)
[http://www.freebob.org/](http://www.freebob.org/)
OK.  Thanks!
I was hoping to be able to do some guitar stuff in ubuntu, but perhaps I should just stick to using the windows box also.

---

### Post by _DD_ on 2008-06-12
> **gatorbrit said:**
> OK.  Thanks!
I was hoping to be able to do some guitar stuff in ubuntu, but perhaps I should just stick to using the windows box also.

Well, no... don't be put off! :D

All the stuff I've been talking about is about the limitations of your current recording hardware and not Ubuntu itself. You'd need an audio interface like that whether you wanted to record a mic with Windows or Linux.

Your Guitarport is basically a Hi-Z input combined with a simple audio interface, so unless you wanted to try recording with a mic then you wouldn't see much benefit from an audio interface anyway.




Anywho, if you need any tips with recording/mixing then gimme a shout.

I'm only an amateur (I'm only a teenager!) but I've had quite a bit of practice. Basically I love doing live sound engineering (only at localish gigs), and then one day I thought it would be cool to try record one of the gigs. The A&H desk I usually use has direct outputs on each channel (all 32 of them :p ... I want to steal that desk soooo badly!) so I just multitrack record the channels I want onto a laptop and mix at home later. Had some successes and not such successes, but its good fun!

---

### Post by gatorbrit on 2008-06-12
> **_DD_ said:**
> Well, no... don't be put off! :D

All the stuff I've been talking about is about the limitations of your current recording hardware and not Ubuntu itself. You'd need an audio interface like that whether you wanted to record a mic with Windows or Linux.

Your Guitarport is basically a Hi-Z input combined with a simple audio interface, so unless you wanted to try recording with a mic then you wouldn't see much benefit from an audio interface anyway.
This is all pretty new to me - so forgive my ignorance.  I guess then, what I am looking to find out is what HiZ input hardware works with ubuntu? 

The guitarport plugs into the USB drive so it has to have drivers to run it.  So I doubt that it would work on ubuntu without a lot of effort.

---

### Post by _DD_ on 2008-06-12
I've had a quick google and it seems no-one has had much luck with the guitarport on linux.

So now your next simplest option would be to go back to the idea of recording using the line-in on your soundcard, but you'll need a DI box to convert the high-impedance input of the guitar to line level. These are fairly cheap and would do the job. You'd want to look for one with a jack output, as some only have balanced XLR out.

[http://www.dv247.com/invt/34411/](http://www.dv247.com/invt/34411/)


EDIT: just to clarify so you don't feel like you have to spend money. You CAN record the guitar with the line-in of your soundcard, however it wouldn't sound nearly so good. This is because the line-level input is low-impedance, so it doesn't put the 'load' on the pickups that a hgh-impedance input does. So certainly go ahead and try it with a 1/4" to 1/8" adapter first, but if you want to move on from there then there are more options.

---

### Post by gatorbrit on 2008-06-12
> **_DD_ said:**
> I've had a quick google and it seems no-one has had much luck with the guitarport on linux.

So now your next simplest option would be to go back to the idea of recording using the line-in on your soundcard, but you'll need a DI box to convert the high-impedance input of the guitar to line level. These are fairly cheap and would do the job. You'd want to look for one with a jack output, as some only have balanced XLR out.

[http://www.dv247.com/invt/34411/](http://www.dv247.com/invt/34411/)


EDIT: just to clarify so you don't feel like you have to spend money. You CAN record the guitar with the line-in of your soundcard, however it wouldn't sound nearly so good. This is because the line-level input is low-impedance, so it doesn't put the 'load' on the pickups that a hgh-impedance input does. So certainly go ahead and try it with a 1/4" to 1/8" adapter first, but if you want to move on from there then there are more options.
That behringer box looks interesting.  Maybe I'll swing by my local music store and see if they have something like it.  I note your point about the jack output.

Thanks for your help!

---

### Post by SteveNorman on 2008-06-13
If your a line 6 guy,,a lot of people us pod effects units as a di/pre-amp. its a pretty user friendly device with all the line-6 bells and whistles. The baggs para-acoustic is a very good di with multiple aps outside of just recording. If you plan to use any acoustic instruments live or recorded this is one of the better di's out there. it has xlr out AND 1/4 out.

---

### Post by gatorbrit on 2008-06-13
> **SteveNorman said:**
> AND 1/4 out.


AAHHHH - so i would be able to connect the 1/4 output to the input on my sound card.

I like PODs a lot - I have a line 6 amp that has POD features.  This would be a really nice solution....

---

### Post by SteveNorman on 2008-06-13
have you tried out the guitar port yet? you may be fine as is. Never know till you try it...

---

### Post by Zimmer on 2008-06-13
I use the Pod XT Live to output to Audacity . The Behringer DI box should convert the guitar signal to a mic strength signal . I use a DI box to plug guitars directly to mic inputs on the church mixer.
You may find this of interest,
[http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/)
Also
[https://sourceforge.net/forum/forum.php?thread_id=1772640&forum_id=713264](https://sourceforge.net/forum/forum.php?thread_id=1772640&forum_id=713264)

---

### Post by SteveNorman on 2008-06-14
check this link out:

[http://www.linuxstudiopro.com/](http://www.linuxstudiopro.com/)

---

