---
title: "midi latency"
date: 2010-08-19
forum: Ubuntu Studio
---

### Post by foxruns on 2010-08-19
i use mainly ardour for audio with a fast track pro interface working perfectly but recently ive tried to figure out a way to get midi soft synths integrated with my ubuntu audio creation..i got vsts working through the host 'vestiged' in lmms, and with this and lmms's standard plugins i was set..i got it working with my midi controller, an axiom 49
theeen comes the problem, the midi controller has a latency that is by no means workable
i thought it might be because i was using vsts, which ran through wine and the host before i got my sound, but i found that even lmms's standard plugins, which i think are lv2s? i had a lag.
if anyone could help me with this latency itd be greatly appreciated

also lmms does not run through jack, with jack running i havent found a way to get a sound output
so im stumpted

---

### Post by realzippy on 2010-08-19
Do you run [ubuntustudio  10.04?]("http://en.wikipedia.org/wiki/Ubuntu_Studio")

Realtime/LowLatency kernel?

---

### Post by Pablo_F on 2010-08-19
I suggest, either use ardour with vst support or run the vsti's through a correctly jackified simple external host, like the command line vsthost from dssi-vst or, maybe more comfortable for you, festige, which is a graphical frontend for fst. In the second case, you will have to make the connections manually (via qjackctl, patchage or ardour itself) but having a simple host comes handy anyway. You will note the improvement in latency if you have a well configured jack, I am sure. All of this is available in falktx' ppa for ubuntu lucid or it can be built from the sources if you prefer.

I hope this helps, Pablo

---

### Post by foxruns on 2010-08-20
no, i run regular ubuntu 10.04 LTS
pablo, how would one run ardour with vst support?

---

### Post by foxruns on 2010-08-20
just installed festige..it runs vsts fine as well but i cant get audio because i have no clue how to make the connections
my jack is set up with my audio interface, if i am going to run either through festige or ardour with midi support am i going to need to reconfigure jack everytime i switch from audio to midi recording?
another thing..my fasttrack pro has midi as well and its midi ports show up so i can run my axiom keyboard through it, with no support for the knobs and such but idk if thatd work at the same time as audio either
im pretty confused and rambling haha

---

### Post by Pablo_F on 2010-08-21
> pablo, how would one run ardour with vst support? 

You can build it yourself or you can install ardourvst package via apt (synaptic for example) if you add falktx PPA to your software sources.

> just installed festige..it runs vsts fine as well but i cant get audio because i have no clue how to make the connections

If the vst is a software instrument it will have at least one midi input. You have to connect either your midikeyboard or some other thing that generates midi notes, e.g. a midi sequencer. 

You normally connect midi ports in the alsa tab of the connection windows of Jack Control. This is the alsa sequencer (alsa midi) and it has nothing to do with the alsa driver that jack uses for audio i/o. However, ardour3 (and already other synths and sequencers) will use jack midi (midi tab). To connect alsa midi and jack midi ports together you need to execute a2jmidid. "a2jmidid -e" so you see your axiom aswell in both connection tabs. 

Audio connections are made in the audio tab. "System" is your audio card.

A much more cool tool to make -jack audio, jack midi and alsa midi- connections is patchage if you upgrade to a recent version like the one in falktx' ppa.

To clarify: Ardour does not have midi tracks (ardour3 will have). So you can't yet sequence midi notes in ardour and feed them to a vst instrument. If you need an audio/midi sequencer I suggest Qtractor or Rosegarden. You can also sync a midi sequencer and ardour by using the jack transport.

> my jack is set up with my audio interface, if i am going to run either through festige or ardour with midi support am i going to need to reconfigure jack everytime i switch from audio to midi recording?

If I understand correctly you are not talking about midi recording, but audio recording through a soft synth. And no, you don't have to reconfigure jack. Just make the midi connections. In the setup of qjackctl you will see "midi driver". I always set it to "none" and if needed I launch "ajmidid -e". 

If you want to do pure midi recording you can't in ardour2. But you can in Rosegarden for example.

> 
another thing..my fasttrack pro has midi as well and its midi ports show up so i can run my axiom keyboard through it, with no support for the knobs and such but idk if thatd work at the same time as audio either

I think the knobs will send midi messages as well so you can control an app that has midi learn. But I am not familiar with this. For another topic maybe.

HTH, Pablo

---

### Post by foxruns on 2010-08-21
thanks a lot i accomplished what i was trying to get at, which was recording from soft synths.
the setup i used was festige, running a2jmidid -e, and patching everything through patchage, softsynth output to ardour
thanks for all your help
the only problem i have left is a little bit of crackling sometimes which could be from poor quality softsynths or poor configuration on my jack im guessing?

---

### Post by Pablo_F on 2010-08-21
God only knows. I suggest you try a native synth to compare so you can narrow down the problem (and you even could like it!). 

If you comment on what kind of sound you want to achieve, it could be that me or other US users suggest something that suits you to make some tests.

Cheers! Pablo

---

