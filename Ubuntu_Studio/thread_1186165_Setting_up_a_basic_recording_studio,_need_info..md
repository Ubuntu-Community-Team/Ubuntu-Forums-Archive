---
title: "Setting up a basic recording studio, need info."
date: 2009-06-13
forum: Ubuntu Studio
---

### Post by feardotcom on 2009-06-13
Hi,
After doing some research i think i have found what i am looking for, but im not 100% sure yet. From what i understand a midi controller keyboard is used to for a software synthesizer, correct?

And to connect my basic 10 channel mixer, with phantom power, i need an audio interface, correct? My mixer has RCA in's and out's.

I think i found what im looking for and if someone says these wont work then they will be what i purchase after i finish my new computer build. At that point i will be switching to Ubuntu Studio.

Heres what i picked out:

M-AUDIO Audiophile 2496 PCI interface
M-AUDIO Session Keystudio 49-Note USB MIDI controller
M-AUDIO Studiophile AV 30 2.0 Monitors(RCA input)

Will this work for a basic recording studio thats recording guitars, bass, electronic drums, vocals, and the keyboard connects via USB. 

Can anyone give a recommendation on a good entry Mic?

---

### Post by Unterseeboot_234 on 2009-06-13
I'm just getting started. For a real professional setup, look at the KarmaPod, a homebrew mobile recording studio for some ideas. Absolutely impressive.

[**karmapod**]("http://dto.github.com/notebook/karmapod.html")

I'm posting, without a real answer, to just track this issue.

---

### Post by CatKiller on 2009-06-14
> **feardotcom said:**
> Can anyone give a recommendation on a good entry Mic?

The main problem is that microphones that are good all-round performers tend to be expensive, so to have the same range of application with cheaper microphones you need more of them. Having lots of microphones available isn't necessarily a bad thing, though.

The canonical cheap & cheerful microphones are SM57 for close-miked guitar, SM58 for vocals (you'll see these on stage a lot) and something larger, like a D112, for the bass. You'll probably get away with DI on the bass - either from the bass amp or through a DI box, or straight into the desk if it has a good pre-amp.

For an all-round microphone I really like AKG's C414, but they aren't cheap. I'd generally recommend getting two, for stereo miking techniques.

---

### Post by moe19790 on 2009-06-16
i asked for some help regarding broadcasting software.. it seems you people are a little bit involved any ideas?

---

### Post by kayosiii on 2009-06-16
> **feardotcom said:**
> Hi,
After doing some research i think i have found what i am looking for, but im not 100% sure yet. From what i understand a midi controller keyboard is used to for a software synthesizer, correct?

Any Keyboard with MIDI out will do. With the Controllers you are just not paying for any onboard sounds. You can also control softsynths via notation, percussion sheets, or piano-rolls on the computer. A midi Keyboard becomes an advantage if you already know how to play keys and want to "perform" the music rather than "compose" it.

> **feardotcom said:**
> 
And to connect my basic 10 channel mixer, with phantom power, i need an audio interface, correct? My mixer has RCA in's and out's.

Worst case senario - you will be building a few custom cables ;)

> **feardotcom said:**
> 
I think i found what im looking for and if someone says these wont work then they will be what i purchase after i finish my new computer build. At that point i will be switching to Ubuntu Studio.

Heres what i picked out:

M-AUDIO Audiophile 2496 PCI interface
M-AUDIO Session Keystudio 49-Note USB MIDI controller
M-AUDIO Studiophile AV 30 2.0 Monitors(RCA input)


you sure seem to like M-AUDIO :) From memory the 2496 is supported though I would do a quick check through the linux-audio-user mailing list archives to see what the consensus on that particular piece of hardware.

From memory the keystudio is a very basic keyboard. Which will be fine as long as you don't need it to respond like a piano.

And my advice with monitors is to listen to them first (in a properly set up room). A good set will have a flat response across the frequency range, make it easy to hear what small changes in what you are doing, not hide problems in your mix and not be overly fatiguing for long recording sessions.

> **feardotcom said:**
> 
Will this work for a basic recording studio thats recording guitars, bass, electronic drums, vocals, and the keyboard connects via USB. 

Can anyone give a recommendation on a good entry Mic?

I personally find the SM58 not that useful a microphone for recording, they have an excellent reputation as a stage mic however. I have a couple of condenser Microphones - all of which give a much more transparent sound. I have played with reasonably priced Microphones made by MXL, sE and Behringer and all these do a pretty descent job for the money. My first mic would be a large diaphragm condensor (be warned however that this type of Mic is typically very sensitive to feedback). The 57 doesn't have the same presence peak as the 58 and might be somewhat more versatile.

Again I recommend searching through the linux-audio-user mailing list archives for further suggestions for cheap mics that work well.

---

### Post by Capoeira on 2009-06-17
condenser-mic is better for studio porpose

those monitors are very small, 3" woofers want give you any bass. start with real monitors, i think the cheapest are the behringer truth line

to connect things you don't even need tha audio-interface. the keyboard connects via usb, the mixer you put on input of onboard-soundcard; what makes it worth to buy a professional card like the one u mentioned is a) the lower latency and b) the better D/A converter

---

### Post by kayosiii on 2009-06-18
I have yet to hear a single good thing about the Behringer Truth Series... (incidently I know a few people wishing to sell them)

---

