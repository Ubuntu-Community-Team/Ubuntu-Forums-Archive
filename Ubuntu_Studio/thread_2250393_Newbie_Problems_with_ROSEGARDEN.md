---
title: "Newbie Problems with ROSEGARDEN"
date: 2014-10-28
forum: Ubuntu Studio
---

### Post by cambium0 on 2014-10-28
Lenovo ThinkPad T400 
High Definition (HD) Audio, Conexant CX20561 codec

Ubuntu Studio 64-bit

Rosegarden

I put a "click track" of midi wood block tones in 4/4 for 107 measures.  I chose "audio" for the second track, then selected the record button for the track, then clicked the record button in the player menu.  I get a popup that says the audio subsystem is not available.  The lenovo site says that the sound card in the T400 is full duplex.  And I had been having the usual trouble getting even the click track to produce sound, I messed with alsamixer and unmuted one of the columns and later I got sound.  But at one point I did successfully record audio but I didn't have my headphones on...it may be that the wood block track was not sounding out, meaning that the card was working as though it was semi-duplex.  So I am considering getting a usb sound card but i understand that that screws up some kind of indexing which requires its own fix.  But really, I think this should work.  Any ideas?  Thanks

cambium0

---

### Post by jejeman on 2014-10-28
Is the JACK running?

---

### Post by cambium0 on 2014-10-28
Suppose Jackd was not running--then I wouldn't get any sound at all on playback right?  I don't know.  How do I tell if jackd is running from the command line?  Something from etc/init.d ?  But the point is when I did get sound on playback, I was disallowed from recording at the same time.  I'm assuming that Jackd was running when I got sound on playback.

---

### Post by jejeman on 2014-10-28
Well, only you know what is going on in your PC.
Try
```
ps -e | grep jack
```

---

### Post by cambium0 on 2014-10-28
8721 ?        00:00:27 jackd
 8921 ?        00:00:02 qjackctl
 8923 ?        00:00:00 jackdbus


I opened qjackctl on advice in another thread.  I just tried the same routine outlined above again, and to start there's no sound with the midi wood block notes, but I was able to record audio and play it back (heard it).  My recollection is that when I CAN hear the wood block, I get a popup when I attempt to record audio saying the audio subsystem is not available.  Right now, I cannot get the wood block track to sound--I've deleted the audio track 2 so there's just one track, it still won't sound.  Yet when I record audio, it plays back immediately. 

...

I just tried playing a midi file with timidity from the command line--no sound.  So I think I'll look into this a bit.

---

### Post by cambium0 on 2014-10-28
alright maybe I should put it this way--I cannot get a midi sequence to sound in rosegarden.  I did have it producing sound at one point today, so I have whatever that would require installed.  then if I cannot record again, I'll deal with that at that point.

---

### Post by jejeman on 2014-10-29
Sorry, I don't use Rosegarden, so I can't help you with that. But, regarding MIDI, you need a sound module to produce sound which is driven by MIDI data. Don't know if you already know that.

---

### Post by cambium0 on 2014-10-29
OK I gave up on midi for the time being. I used a software synth as the audio device instead, and then wood block was one of the selections in the sound font for this synth, which somebody told me was in /usr/share/sounds or I never would have found it.  And this worked.  So I imagine, if "General Midi Device" was the audio device in my earlier efforts, I needed something analogous to the sound font I used for the software synth.  But if you select "General Midi Device" you don't get the same button that I used to configure the sound font for the synth, instead you get a selector for which "Bank" you want to use, and the default is General Midi which sounds like it should be the right one.  Therefore I really don't know how to get midi to work.  Somebody else advised in another thread that one should open timidity from the command line with some arguments that send its output to JACK, then open QJackCtl and open connections, and connect timidity to rosegarden.  It looked like I had done that, but I still didn't get any sound.

Fortunately, the software synth does everything I wanted midi to do so I don't need midi right now.  If I wanted to build off of some midi tracks in the future, I might want it though.  Anyway thanks for your help.

---

### Post by jejeman on 2014-10-30
It is a little contradictory in your statements.
Soft synths are all about MIDI. They are made to be MIDI data driven sound modules, (well maybe there are OSC data driven too.)
So, I don't know how you don't "need" MIDI, but use soft synth?
GM device is more related to the MIDI program bank managment - standard bank of programs (sounds). You can use it if the device supports GM Bank.

I think that you need to read/learn more about MIDI to understand what is going on.

---

### Post by cambium0 on 2014-10-30
My comments were about the Rosegarden interface.  But it's true I don't know anything about midi.  The instruments available under the softsynth approach I described appeared at cursory glance to be the exact same instruments available under the General Midi selection, so maybe you're right they are related.  More specifically, the instrument list came from the sound font, not the synth device.  But the issue is that the interface allows either General Midi OR a few software synths as the device, and I couldn't get anything going under general midi--never hooked up with a sound font, it would seem.  Perhaps the first place the midi looks is my sound card for built-in midi capability, and if it's not there, I would have to load a sound font just as I did with the software synth.  But I didn't see a way to do that.  I'll be working with rosegarden for a while since I got it to do what I wanted it to do, so in time I might figure this out.  I suspect my sound card does have built-in midi though.

---

