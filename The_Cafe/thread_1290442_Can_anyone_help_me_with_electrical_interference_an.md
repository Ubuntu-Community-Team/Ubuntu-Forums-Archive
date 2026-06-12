---
title: "Can anyone help me with electrical interference and my sound card?"
date: 2009-10-13
forum: The Cafe
---

### Post by billdotson on 2009-10-13
I am having a lot of issues with EMI and my sound card (and onboard sound). I know this is the community discussion forum but I like this forum and there is likely to be someone that can help here.

I have an Intel Core 2 Duo E6600 overclocked to 3.15GHz (I don't think I over-volted it, and I think I was having these problems before I did that) an asus p5b deluxe wi-fi AP edition, a geforce 8800gt 512MB and a soundblaster audigy 4 (not pro). When I have my 5.1 speakers plugged into the sound card I get an EMI sound through the speakers and subwoofer if I turn the woofer up more than halfway. The emi is more noticeable in the subwoofer. If I plug a microphone into the pink mic slot it makes a terrible, almost deafening sound (if the microphone itself is turned on). If the microphone is plugged in but turned off it does not. However, if I plug a microphone or another device into line in there is no such issue. To complicate things more I was trying to use gnuitar for effects for my bass and when I turn that program on it amplifies it terribly and I have to close the program.

I tried using the onboard audio for the speakers and I don't get much EMI that way (I can turn the woofer and speakers all the way up and there is no noticeable sound for the most part) but there is still some. There is a very slight, almost imperceptible hum when running gnuitar and every now and then I hear a little bit of something if I am writing something using my wacom tablet. I can plug a normal microphone into the onboard along with the speakers and I do not get the terrible interference; however, if I use the stereo array mic that came with the motherboard it produces that sound. Also, for some reason when I tried playing one of my games (Batman: Arkham Asylum) the sound was really off. I could barely hear the voices in the game (and sometimes not at all) but all the other effects were as loud as they normally would be.

I tried using the audigy 4 as the recording device and the onboard for audio playback but even with nothing else plugged into the audigy the mic port gave off an awful EMI hum or buzz (I don't exactly know the difference).

So:
audigy 4 has noticeable EMI for speakers and unbearable with microphone in mic port. line in does not do this. Cannot use gnuitar or rakarrack without terrible EMI.

onboard audio has very little EMI with speakers (although I would like not to notice it at all) and none that I can tell with a normal mic but the array mic is unbearable. The sound is also messed up somehow in games (perhaps I had it set to 2 speakers instead of 5.1, but that wouldn't be the case unless the auto device recognition did that itself upon reboot). Can use GNUitar with onboard (haven't tried rakarrack as I have mainly been testing in Windows XP).

So basically I want to know how to get rid of this terrible EMI. I want to be able to use my audigy card as the recording device and the sound device without EMI on the speakers (normally or using a guitar effects program). It would also be nice to be able to use the microphones I own. If the onboard audio worked well in games and in Ubuntu, as well as working with the array mic, then I wouldn't worry much about it. However, I did pay about $70 for the sound card a few years ago, and assuming it has its own special devices on it to control audio, I would prefer to use that. Another reason I want the sound card to work is that I have heard that having a dedicated sound card can take some stress off of the CPU in gaming.

Note: my PC tower is an apevia aspire xpleasure and is partly aluminum and partly plastic (the front bay is plastic). It is sitting on carpet but stands a bit off the ground due to its legs.

Thank you.

---

### Post by squaregoldfish on 2009-10-13
My guess would be either a duff card, or a duff connection. Have you tried pulling out the card and reseating it? Perhaps try it in a different slot if you can.

Steve.

---

### Post by billdotson on 2009-10-15
Thanks, I will try taking it out and putting it back in. I sure hope the card isn't bad. I hope even more that the motherboard isn't bad! If a different PCI slot doesn't produce the EMI does that mean my board is going bad?

I would just use the onboard sound but for some reason sounds don't always work as they should. While playing Batman: Arkham Asylum it was near impossible to hear any of the in-game dialogue. Using the audigy 4 worked fine though. Also, I can also get the really bad EMI on the onboard sound if I plug the stereo array microphone in (that came with the motherboard). If the speakers are in onboard audio and a normal mic is plugged in it is fine, but once I put the array mic in it absolutely freaks out.

I really hope my parts aren't dying..

---

### Post by handy on 2009-10-15
It sounds like an earth leakage.

If you know someone who is into electronics, they should easily be able to pick up if it is being caused by a bad plug on the card, a dry joint on the board can be more time consuming as you are very lucky to be able to see one by eye, & if it is where involved in seating tiny components it becomes not worth the time & effort to attempt to repair.

It is also possible that the problem is being caused by an earth leakage in a speaker connection plug, have you tried using different ones (if possible)?

---

### Post by billdotson on 2009-10-16
It just seems strange to me that I don't get any noticeable interference using onboard audio.

I don't know any people who are particularly good with electricity-type stuff otherwise I would have them over here looking at it.

What exactly do you mean "earth leakage"?

---

### Post by OmegaAI on 2009-10-16
You can get some EMI shielding paper or whatever it is called, or you can do what I did (I DO NOT RECOMMEND THIS!) Do this at your own RISK!!!:

[http://www.overclock.net/sound-cards-computer-audio/571718-how-make-emi-shielding-your-sound.html](http://www.overclock.net/sound-cards-computer-audio/571718-how-make-emi-shielding-your-sound.html)

You have to make sure you insulate your card from the Al foil! And also, it does work BTW.

---

### Post by surfed on 2009-10-16
Is the EMI still there with WIFI disabled? Also my solution with some ground feedback (Earth leakage) was to break the ground off my power cord and it went away... :) Also try a different circuit like in a different room.

---

### Post by handy on 2009-10-16
Rather than breaking the earth/ground pin off your the power lead, you could plug your computer power lead into an extension lead, (or make a short lead for yourself).  You need the kind of plugs that are user serviceable, so you can pull the cover off the plug & disconnect the earth/ground lead from the pin.  Insulate & isolate the exposed wire right away from the exposed active & neutral parts inside the plug.

Do the above as a test, don't run your machine like it all the time, as if you get a power spike from without, or a condenser lets go in your PSU, your hardware would most likely suffer more damage.  Potentially a great deal more damage.

Only do this kind of thing if are familiar with this kind of stuff, as there is potential for serious human injury & also the potential for hardware damage if you get your wires mixed up or short them out somehow?

---

