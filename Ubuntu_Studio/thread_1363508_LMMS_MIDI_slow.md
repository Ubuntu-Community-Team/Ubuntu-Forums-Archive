---
title: "LMMS MIDI slow"
date: 2009-12-24
forum: Ubuntu Studio
---

### Post by mikep_bluefish on 2009-12-24
Hi everyone. :)

I downloaded LMMS today and I connected my CME m-Key USB midi keyboard (which was detected and go fully functional as soon as I plugged it in :wink:).

Everything works more than perfect. The midi keyboard is detected, with a samplerate of 23.3m/s LMMS plays everything perfect, I can load also VST plugins through Vestige... :biggrin:

I 've got a problem though which is quite annoying... :-k

My usb midi keyboard responds a bit slow and this gives me trouble when I record midi. (basically it has a delay less than a quarter of a second, but even that small amount is enough to "cripple" me when I'm recording) :sad:

I'm using Ubuntu 9.04 32-bit ( NO realtime kernel installed )
My audio card is an Intel 8280L (on-board) 8-[

I know it's not that good trying to work with audio on a 32-bit Ubuntu with an on-board card.. :-\" but I'm planning to make a setup on another machine with the 64-bit version and buy me a decent audio card.

If anyone has any ideas on how to make the usb midi keyboard respond faster or give me tips on setting up a PC for audio on Ubuntu pls let me know. [-o<

Any information that could get me started is more than welcome.

---

### Post by AutoStatic on 2009-12-24
Hello mikep_bluefish, what is the current Audio Interface in LMMS? If it's PulseAudio you could try switching to ALSA. Or maybe even JACK, but then you have to configure JACK first to have it work well with your non-realtime setup.

---

### Post by mikep_bluefish on 2009-12-24
It must a latency issue then eh?

Both my MIDI and AUDIO are on ALSA.

I don't have JACK installed on this PC because I keep all of my job's data an applications and I don't want to experiment with it.

I'll definitely go for a 64bit Ubuntu distro (Studio maybe) and a Jack set-up on my other PC though.. 

If it is a latency issue, could a PCI or FireWire audio card aid to speeding things up?? :-k

I know on Windoze, that latency is a matter of ASIO "acceleration" tuning.

But in Linux there is no ASIO support. :-s

---

### Post by mikep_bluefish on 2009-12-24
I switched AUDIO to OSS and it looks like its OK.. 

I'm not 100% sure though.. 

I'll do a "heavyweight" test on it tomorrow probably and post back the results.

---

### Post by AutoStatic on 2009-12-25
> **mikep_bluefish said:**
> It must a latency issue then eh?Most probably yes.

> **mikep_bluefish said:**
> Both my MIDI and AUDIO are on ALSA.That's allright, if you have sound then it's best to stick with ALSA.

> **mikep_bluefish said:**
> If it is a latency issue, could a PCI or FireWire audio card aid to speeding things up?? :-kSuch soundcards work better with low latency settings but I read somewhere on this forum that it doesn't really matter, all modern soundcards can be set up to work with low latencies.

> **mikep_bluefish said:**
> But in Linux there is no ASIO support. :-sThere is: [http://sourceforge.net/projects/wineasio/](http://sourceforge.net/projects/wineasio/)
And JACK is more or less the Linux flavour of ASIO and ReWire mixed together.

---

### Post by mikep_bluefish on 2009-12-25
Hello again AutoStatic and Merry Christmass.

:-k mmm... but WineAsio addresses Windoz3 apps only yeah?
I mean what's the point of utilising WinAsio for Linux when you have an advanced audio server such as Jack... At the bottom of everything ASIO is just being able to tweak that latency setting of your soundcard. 

... so according to this: 
> And JACK is more or less the Linux flavour of ASIO and ReWire mixed together.

...logically Jack is able to utilise an audio card's hardware sync capabilities also yeah?

Do you know if there are any documentations, links or tutorials for QjackCtl that have explanations for all of the Jack settings *(because some of them I somehow understand what they actually mean but for others I don't have a clue 8-[ )* and how to use the Connections and Patchbay? I'de like to get to know Jack as good as I can.

P.S. I might regret this but.. :-\" I couldn't help it, so I installed Jack on my work machine along with a couple of apps (which worked straight out of the box right after istalling it from Synaptics \\:D/ ) and started fiddling around.. O:)

Hehe! That's Linux for me! I always have to go install and tweak everything until I manage to mess up everything.. :biggrin:

---

### Post by AutoStatic on 2009-12-25
> **mikep_bluefish said:**
> Hello again AutoStatic and Merry Christmass.Thanks, merry x-mas too!

> **mikep_bluefish said:**
> :-k mmm... but WineAsio addresses Windoz3 apps only yeah?
I mean what's the point of utilising WinAsio for Linux when you have an advanced audio server such as Jack... At the bottom of everything ASIO is just being able to tweak that latency setting of your soundcard.A lot of people use Windows applications with Wine and with wineasio you can route those apps through JACK, wineasio is more or less a bridge between Wine and JACK. Like this you can also profit from low latencies and realtime editing within applications running under Wine. 

> **mikep_bluefish said:**
> ...logically Jack is able to utilise an audio card's hardware sync capabilities also yeah?What do you mean with hardware sync capabilities?

> **mikep_bluefish said:**
> Do you know if there are any documentations, links or tutorials for QjackCtl that have explanations for all of the Jack settings *(because some of them I somehow understand what they actually mean but for others I don't have a clue 8-[ )* and how to use the Connections and Patchbay? I'de like to get to know Jack as good as I can.[http://downloads.sourceforge.net/qtractor/qtractor-0.3.0-user-manual.pdf](http://downloads.sourceforge.net/qtractor/qtractor-0.3.0-user-manual.pdf)

> **mikep_bluefish said:**
> P.S. I might regret this but.. :-\" I couldn't help it, so I installed Jack on my work machine along with a couple of apps (which worked straight out of the box right after istalling it from Synaptics \\:D/ ) and started fiddling around.. O:)

Hehe! That's Linux for me! I always have to go install and tweak everything until I manage to mess up everything.. :biggrin:If you keep track and have some idea of what you're doing you could already minimize messing up your install.

---

### Post by mikep_bluefish on 2009-12-25
> What do you mean with hardware sync capabilities?

All let's say "pro" sound cards like RME Hammerfall DSP or even Audigy have an internal hardware "clock" which can be for example used for synchronising multiple audio cards together *(which logically it would only be a requirement when there is a lot of workload in an audio project and more processing power is needed by the audio interface I guess, yeah?)*. I think this also applies for connecting peripherals such as MIDI keyboards or other devices that can be "clocked" and probably on these types audio cards, latency is probably directly affected by this feature.

Check out the Word Clock Module on the RME website here: [http://www.rme-audio.de/en_products_hdsp_expansion_boards.php](http://www.rme-audio.de/en_products_hdsp_expansion_boards.php)

By the way, I think RME has full support for Linux OS for the Hammerfall cards.

:biggrin: Thanks very much for the manual bro.

> If you keep track and have some idea of what you're doing you could already minimize messing up your install. 
Hahaha! Yeap! that's why I need go through all the info that I can get before I start setting up things... but I always end up trying to do everything before reading the manuals.. 8-[

---

