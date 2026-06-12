---
title: "Drummer looking to set up a recording studio in the attic. Watcha got?"
date: 2010-01-25
forum: Ubuntu Studio
---

### Post by SomeGuyDude on 2010-01-25
All right, I've spent the last week or so looking this stuff up and still have no idea. So let me lay down the groundwork:

1) I'm a drummer, so I'm going to have between 4 and 8 mics.

2) I understand the mic situation and I've got Ardour to fiddle with, all I need help with is getting the sound from the mics into my machine.

3) I don't have a lot of money. I won't say a budget number because if need be I'll spend a little more, but I really, really would like the mixer/interface/whatever to be under $400.

So yeah, there's that. I have my drums set up in my attic and I'd like to start turning it into a mini recording studio. Any help you all could give me in the realm of doing so would be most appreciated.

My cursory research has left me drowning in a sea of jargon and not understanding just what hardware I should be looking at. Mixers? Unpowered mixers? Multi-track recorders? What?

---

### Post by JC Cheloven on 2010-01-25
If I understand you, what you need is either: 

An audio interface with lots of inputs, which works in linux, OR

An analog mixer, with lots of inputs (will merge in 2 channels to the pc)

For an audio interface, you should look for a firewire one. I'm looking for one myself, and mostly daydreaming with the focusrite saffire pro40, which seems to be supported soon by ffado. See [what is supported in ffado]("http://www.ffado.org/?q=devicesupport/list") and fits your budget. For example the pressonus firepod is widely reported to work. Note: an usb interface won't do as your main interface for recording.

For an analog mixer, there are plenty of options, and there is no worry about linux compatibility. Perhaps the best option for you. For example [Behringer]("http://www.behringer.com/EN/Products/") has good quality/price ratio.

Anyway, the microphones should be a concern. They're expensive and probably require most of your budget, whatever it is.

---

### Post by SomeGuyDude on 2010-01-25
Thanks for the response! I was starting to get disheartened LOL.

Well yeah, but mics are mics. That's a fairly simple thing to figure out, it's just a matter of finding a good set of them within my budget. I don't have to worry about compatibility or drivers or anything of that sort. Just give a guy $400 and say "give me the best set of drum mics I can get for this much."

What I literally do not understand is what hardware to buy. Can you give me an example of a solution within a price range of, say $300-400 that would work? Like an example of a mixer/interface/whatever that would allow me to do this:

[mic'd drums] -> [something] -> [my computer with Ardour] 

Where the [something] is whatever hardware arrangement is necessary. If it sounds like I'm being lazy, I'm not. I've just spent all this time looking up mixers and interfaces and whatever else and gone "okay great, but I have no idea if this is what I need or if it'll even work."

Like, let's say I get the 1002: [http://www.behringer.com/EN/Products/1002.aspx](http://www.behringer.com/EN/Products/1002.aspx) . There's 10 inputs there. Can I just hook my mics up into that, then plug that into my computer, start up Ardour or Jokosher, and go from there? Or is there another piece?

---

### Post by sgx on 2010-01-25
> **SomeGuyDude said:**
> Thanks for the response! I was starting to get disheartened LOL.

Well yeah, but mics are mics. That's a fairly simple thing to figure out, it's just a matter of finding a good set of them within my budget. I don't have to worry about compatibility or drivers or anything of that sort. Just give a guy $400 and say "give me the best set of drum mics I can get for this much."

What I literally do not understand is what hardware to buy. Can you give me an example of a solution within a price range of, say $300-400 that would work? Like an example of a mixer/interface/whatever that would allow me to do this:

[mic'd drums] -> [something] -> [my computer with Ardour] 

Where the [something] is whatever hardware arrangement is necessary. If it sounds like I'm being lazy, I'm not. I've just spent all this time looking up mixers and interfaces and whatever else and gone "okay great, but I have no idea if this is what I need or if it'll even work."

Like, let's say I get the 1002: [http://www.behringer.com/EN/Products/1002.aspx](http://www.behringer.com/EN/Products/1002.aspx) . There's 10 inputs there. Can I just hook my mics up into that, then plug that into my computer, start up Ardour or Jokosher, and go from there? Or is there another piece?

You only need a soundcard and a mixer and mics, and a couple hours setting up software, to get started. A few definitions:

Alsa -this sound system gets your soundcard working
jackd -this gets you low latency i/o between all your hardware and software

qjackctl -gui for jackd, this is your virtual patchbay, your connections and important settings for audio and midi are done here. Play with it, it has buttons to push, widgets to click, labels to google for...

For example, to record your mixed drum output, start qjackctl, press its start button, then start ardour, which will get a place in the qjackctl
panels, make sure it is connected  to 'system' in the audio tab of qjackctl. Start a project in ardour, select a track, arm it for recording
etc  Put a radio or other constant soundsource by a mic, so you'll hear it
when the right connection happens.

Timemachine is an ultra-simple recording app when multi-track is not needed, it has a stop/start button, and a level meter, outputs w64 wav files that audacity sound editor can import and export in the common formats.

 Qjackctl has lots of google hits, so read up a bit, and in the interim, hydrogen linux drum machine is great to create and save your own beats, it has a pattern editor, pattern sequencer, excellent mixer, access to ladspa fx, 64th note resolution, and triplets, for on the fly percussion creativity, and creating custom kits from samples is also easy. 
Cheers

---

### Post by sgx on 2010-01-25
In the long run, linux and search engines free us from the bonds of
corporate computing. We have been given both the toolbox and the engine
of information technology. Good times! :D

---

### Post by SomeGuyDude on 2010-01-25
Okay so... I -can- just buy that Behringer mixer and then roll? There's no other hardware to buy? After all, my machine has a sound card in it, so does that mean I don't need anything else? You didn't really answer that part.

---

### Post by Mike'sHardLinux on 2010-01-25
> **SomeGuyDude said:**
> Like, let's say I get the 1002: [http://www.behringer.com/EN/Products/1002.aspx](http://www.behringer.com/EN/Products/1002.aspx) . There's 10 inputs there. Can I just hook my mics up into that, then plug that into my computer, start up Ardour or Jokosher, and go from there? Or is there another piece?

That mixer only has 2 microphone preamps. You'll need as many preamps as microphones.

---

### Post by SomeGuyDude on 2010-01-25
> **Mike'sHardLinux said:**
> That mixer only has 2 microphone preamps. You'll need as many preamps as microphones.

True, that wouldn't work per se, but the question remains if I can just snag a Behringer mixer and then plug it in without any other hardware.

This is why I'm getting headaches. It seems like no one can give me a straight answer. :confused:

---

### Post by Mike'sHardLinux on 2010-01-25
> **SomeGuyDude said:**
> True, that wouldn't work per se, but the question remains if I can just snag a Behringer mixer and then plug it in without any other hardware.

This is why I'm getting headaches. It seems like no one can give me a straight answer. :confused:

You CAN get a Behringer mixer as long as it has enough mike preamps and then connect to your current sound hardware line input. It will work. I guarantee it. BUT, if you use your current sound hardware, I don't know how good the quality will be. Definitely not great, though possibly usable.

Edit: I wanted to add, that if you do it this way, you will be mixing all your channels down to 2 channels (and 2 tracks) when recording; so you are losing flexibility compared to recording each individual microphone to its own track.

---

### Post by SomeGuyDude on 2010-01-25
Okay, then let's take that a step further.

1) Should I buy a USB or Firewire external sound card to hook up to the mixer? Would that help?

2) If that's bad, then what's good?!? It's like no one's telling me what I can do or what is usable hardware, just giving me generic advice.

---

### Post by Mike'sHardLinux on 2010-01-25
It's hard to give specific advice in this situation. We don't know exactly what you expect.....flexibility, quality, etc....

Also, finding Linux compatible hardware narrows the choices quite a bit. 

Can you be more specific on your budget. I understand you are willing to pay about $400 for the mixer and/or audio interface. What about microphones and cords? You will be surprised how much you'll have to spend on cables, even if it is just 4 microphones and 4 channels of simultaneous audio......and you stated 4 channels as your minimum.

---

### Post by SomeGuyDude on 2010-01-26
I'm sorry if I sounded short before. I'm just getting frustrated because it's turning out to be such an ordeal. Nothing personal.

Anyway, ignore the mic part. Mics are mics. It's not like if I get mixer/interface A I'll need a different type of microphone than if I get mixer/interface B. I'll put some decent money into that part of things. That's not difficult to understand. What IS difficult is understanding how to get the signal from the microphones into my Linux machine.

I don't know what specifics you want. I'd like to record into the computer for possible demo recordings. I don't know what "flexibility" I need, and obviously the best quality that will fit into my budget is what I'd like.

Now, I'm REALLY close to simply scrapping Linux and getting a Tascam 1641 since that seems like it'd work just fine with Windows.

---

### Post by sgx on 2010-01-26
> **SomeGuyDude said:**
> Okay so... I -can- just buy that Behringer mixer and then roll? There's no other hardware to buy? After all, my machine has a sound card in it, so does that mean I don't need anything else? You didn't really answer that part.
Most of the motherboard sound chips work fine. I have an Intel motherboard soundchip, and it does a good job if needed. If yours doesn't work, I'll eat steak.


 Once you get your mics placed in your drumkit, and apply some acoustics in your attic area, then get an audio interface. The final output quality depends on the sum of the parts, so a high-end soundcard in a studio
area that has not yet had sound preparations won't yield immediate results, so be patient and save some money while you focus on your mic/drum/mixer/acoustics setup. 

Cheers

---

### Post by SomeGuyDude on 2010-01-26
Yeah, but the guy up above was telling me that the Behringer isn't so good because it condenses the output into two channels. For most practical purposes, is that really a big deal?

---

### Post by Mike'sHardLinux on 2010-01-26
> **SomeGuyDude said:**
> Now, I'm REALLY close to simply scrapping Linux and getting a Tascam 1641 since that seems like it'd work just fine with Windows.

Funny you mentioned that...... I cannot speak for the build quality or sound quality of that interface, but it seems ideal for your situation and well within your price range. I came across it in my search, too. But, I didn't mention because I am sure it does not work in Linux.

---

### Post by Mike'sHardLinux on 2010-01-26
> **SomeGuyDude said:**
> Yeah, but the guy up above was telling me that the Behringer isn't so good because it condenses the output into two channels. For most practical purposes, is that really a big deal?

I started out doing this very thing. Actually, at first I didn't even have a mixer. I recorded into 2 channels. Eventually, I got a mixer and another cassette deck, and used to bounce tracks from one deck to the other while adding more audio channels from the mixer. This is a very "lo-fi" approach, but I guess, it also helped me learn a good understanding of how everything works, and how to squeeze every little bit of quality out of my equipment.

---

### Post by SomeGuyDude on 2010-01-26
Yeah. I'm about THIIIIS close to dual-booting with WinXP just for the purposes of using the Tascam. Seems to have GREAT reviews.

---

### Post by sgx on 2010-01-26
> **Mike'sHardLinux said:**
> Funny you mentioned that...... I cannot speak for the build quality or sound quality of that interface, but it seems ideal for your situation and well within your price range. I came across it in my search, too. But, I didn't mention because I am sure it does not work in Linux.
Technically, anything with line-out jacks is just a linux rompler, used to feed cool sounds to rakarrack, creox, jackrack, or tracked with icing on the cake from zynaddsubfx, hydrogen, or linuxsampler
:D

---

### Post by Mike'sHardLinux on 2010-01-26
> **sgx said:**
> Technically, anything with line-out jacks is just a linux rompler, used to feed cool sounds to rakarrack, creox, jackrack, or tracked with icing on the cake from zynaddsubfx, hydrogen, or linuxsampler
:D

Ummmm......the whole point of that device is converting those 8 analog inputs into the digital domain for your PC. If you only use the line outputs, it defeats the purpose. The OP is a "real" drummer. Doesn't sound to me like they want to record sounds for a sampler.

---

### Post by SomeGuyDude on 2010-01-26
LOL, wow that was complicated sounding.

And yeah, I'm talking about using an acoustic drum kit with mics attached. No sampling or anything.

---

### Post by Stochastic on 2010-01-26
Hey SomeGuyDude, I'll just jump in and recommend that you get a Firewire soundcard that has 8 inputs (even if you only start with using 4, it's nice to have the expansion room later).  Don't go the mixer route, mixing down to 2 digital inputs because you will loose the ability to compress the bass drum, gate the snare, re-amp the toms, etc... once everything is mixed down to a single stereo "drum track".

I recommend firewire because it can give the dedicated bandwidth that serious multi-track audio demands.  USB can get bogged down by other devices on that same bus (mouse, harddrive, etc...) and loose bandwidth at critical times (this is true regardless of operating system).

My personal soundcard is a Presonus Firepod (now marketed as an FP10 or something).  I love the thing and it has nice clean preamps for percussion.

Is that clear?  Do I need to clarify/expand on anything?

Oh and my personal preference (if I was in your buying position) would be to steer clear of Tascam soundcards.  I've been burned by that company's products in the past.

---

### Post by SomeGuyDude on 2010-01-26
Quite clear! Thank you, sir. Looks like I'll just snag that then. So I just plug my mics into that, FireWire the FP10 to my machine, and start up Ardour/Jokosher and I'm on my way then?

---

### Post by sgx on 2010-01-26
> **SomeGuyDude said:**
> Quite clear! Thank you, sir. Looks like I'll just snag that then. So I just plug my mics into that, FireWire the FP10 to my machine, and start up Ardour/Jokosher and I'm on my way then?
Once again, everything revolves around and connects through the qjackcontrol gui for jackd. Your firewire or other audio items, software, or hardware, all need to be connected there. It is quite easy, but like I said, allow a couple hours to get familiar with the labels and buttons and what they do. Google has much info, videos etc on linux as a whole,
and its audio apps in particular.
Cheers

[http://forums.presonus.com/showthread.php?t=5886](http://forums.presonus.com/showthread.php?t=5886)  link to FP10 drums/mics topic

---

### Post by AutoStatic on 2010-01-26
I'm with Stochastic. I don't own a Presonus device though, I have a Focusrite Saffire Pro which works very well. So that broadens the range of possibilities a bit ;)
And regarding hooking everything up, that's where this forum is for and there are quite a few very helpful howto's, manuals and help pages so I wouldn't worry about that.

---

### Post by SomeGuyDude on 2010-01-26
Sweet guys. I'm kind of excited now. Presonus FP10, a Shure Beta 52a for the kick, PG56 for the snare, a pair of PG81's for the overheads and we're ready to roll.

Then it's just a matter of learning how to work with JACK and Ardour...

---

### Post by fedexnman on 2010-01-26
google    ubuntu studio prep     and follow the stuff for setting up firewire, rt kernel, starting qjack etc .  just be patient and follow these how to s and most of all have some fun !

---

### Post by Stochastic on 2010-01-26
Yeah, one thing that hasn't been explicitly stated is that firewire soundcards are still a bit tricky to setup in Ubuntu.  Still, people are successful with them it just takes a bit more setup work.  When you're ready for that process ask in these forums.  If you get hopelessly stuck or start running in circles poke me with a private message.

---

### Post by usndmac on 2010-01-26
I'll just add my $.02 here.

I own both the FP10 and the Audiofire 12. (The AF12 is all line level in so it requires mic preamps for use with mics)

I am satisfied with both.

As noted getting firewire/audio working with Ubuntu can require some learning and, frankly, some frustration.

To be honest I've not tried the latest Ubuntu Studio, but I understand it has matured to some degree.

It might be a good place to start, since it does a lot of the configuring for you.

---

### Post by robeast on 2010-01-26
You've got great advice, SomeGuyDude. I also use a Presonus Firepod; it's a great value and works well in Linux. However, if you are getting frustrated just figuring out what interface to get you may give up when you actual start setting up what you got and hit the learning curve. If you are patient I guarantee it will pay off but it can be a bumpy ride :)

---

### Post by fedexnman on 2010-01-26
is that rob east   or  ro beast ( voltron cartoon ) lol ??  i hope someguydude will come back to this thread if he has problems setting it up, he seems pretty ancious to get it goin. i know ive had my whathefreak moments getting firewire all goin right .

---

### Post by JC Cheloven on 2010-01-26
Hi, sorry for my absence. I'm glad you got excellent advice over there. Just my (another) 2p:

- Of course a 10 input-XLR-with-phantom firewire audiocard is better. Only I understood that your intent is to setup a somehow cheap home studio, rather than a semi-professional one. If you want to stay on the cheap side, you may still think IMO in a mixer as the one you saw, to use with some dynamic mics and only 2 condenser mics (those are much beter, true, but more expensive too).

- However, If you can afford it, I'd go for the firewire path, as it will give you better quality.

- If you need some ideas, there are a lot of "tutorials" (plenty of advertisement but anyway) from the manufacturers. For example [this one from shure]("http://www.google.es/url?sa=t&source=web&ct=res&cd=1&ved=0CAwQFjAA&url=http%3A%2F%2Fwww.shure.com%2Fstellent%2Fgroups%2Fpublic%2F%40gms_gmi_web_ug%2Fdocuments%2Fweb_resource%2Fus_pro_mic_techniques_drums_ea.pdf&rct=j&q=mics+for+drums&ei=3bNfS9XHD5iCnQOBiYTLDA&usg=AFQjCNH6rVR88rxw2bIQfAQb57XpRSkG0A"). Hope this will not lead to your ruin! ;-)

Cheers.

---

### Post by SomeGuyDude on 2010-01-27
Thanks for the help, y'all. Truth be told everything's all on paper currently. And... I actually threw Win7 on my machine just to see if I could stomach it should I find myself in a bind, LOL.

---

### Post by longjohn119 on 2010-01-30
I'd go with a Nady PRA-8 8 channel microphone preamp ($130 Musician's Friend) and a M-Audio Delta 1010 ($200 Musician's Friend) and the other 70 bucks can go to interface cables and such.

Mixing and everything else can be done in software and you'll have a professional quality 8 input channel recording studio for under 400 bucks .... The Delta cards are high dynamic range (99 REAL dB's measured and not just a marketing hype number) and low noise (-99dB measured and not just marketing hype numbers) and has hardware monitoring (Important for doing overdubs while monitoring existing tracks) plus have good drivers for both Linux and Windows (Unlike the Creative/E-MU junk)

I've personally been using a modified Delta 44 for several years and 4 inputs are all I need for what I'm doing but if I were going to upgrade a Delta 1010 would be my choice (I already have a bunch of solid state and tube mic preamps I made myself) ... The Nady preamps is average but about the same quality and circuitry you'd find in a cheap mixer's mic pre like a Behringer

---

### Post by robeast on 2010-01-31
> **longjohn119 said:**
> I'd go with a Nady PRA-8 8 channel microphone preamp ($130 Musician's Friend) and a M-Audio Delta 1010 ($200 Musician's Friend) and the other 70 bucks can go to interface cables and such.

Beware! The Delta series went through an architecture change in 2007 that make them incompatible with ALSA!

---

### Post by sheehanje on 2010-02-01
I don't know if you are still reading this thread, but I will second the PreSonus Fp10 I've been using it for 3 years (was just called the FirePod then), and it works great with Ubuntu Studio.  The other interface I've had great success with is the ART TubeFire 8.  I set that up for a drummer I know, and he loves it.  Both can be found for about $399 new, and I do suggest buying new as a lot of times with used or refurbed units, sometimes the pots are a bit dirty.

I used to use Cubase with the FP10, but I switched to Jack and Ardour.  Mainly because Patchage makes this stuff a breeze to route.  While it took a bit of tweaking to get everything the way I wanted, the end result was well worth it.  I now have a rock solid DAW solution.  One of the other great things is using Compiz for the desktop cube, so I can easily rotate and see all my mixers and other controls.  I always thought the cube was great eye-candy, but with this type of application it proves more useful because I can quickly get to all my programs and watch them as they are running while rotating through the screens.

Good luck with your endeavors.

---

### Post by longjohn119 on 2010-02-01
> **robeast said:**
> Beware! The Delta series went through an architecture change in 2007 that make them incompatible with ALSA!

Oh Horse Hockey.

Just because Ubuntu/Pulse Audio programmers can't write decent drivers isn't the fault of M-Audio.

---

### Post by AutoStatic on 2010-02-01
> **longjohn119 said:**
> Just because Ubuntu/Pulse Audio programmers can't write decent drivers isn't the fault of M-Audio.

Hello longjohn119, the 1010 should work, M-Audio is pretty Linux friendly. And PulseAudio is not a driver stack, it's a sound daemon like JACK and Esound. And your assumption is wrong in my opinion, any vendor that does not provide any specifications for their devices so proper Linux drivers can be written for them is to blame.

[quote=robeast]Beware! The Delta series went through an architecture change in 2007 that make them incompatible with ALSA![/quote]

Which 1010 doesn't work? Which serie, from when on, any links?

---

### Post by sgx on 2010-02-03
> **AutoStatic said:**
> Hello longjohn119, the 1010 should work, M-Audio is pretty Linux friendly. And PulseAudio is not a driver stack, it's a sound daemon like JACK and Esound. And your assumption is wrong in my opinion, any vendor that does not provide any specifications for their devices so proper Linux drivers can be written for them is to blame.



Which 1010 doesn't work? Which serie, from when on, any links?

Since RoHS applied in 2007, there may be a few products that needed changes to comply, and manufacturers used that time to also find
more efficient, or less expensive components, and also tried to reduce the
parts count per circuit board, so good products with many years of production, like some maudio cards, some tascam cards, once worked, but
need a second look at compatibility, after some new designs went in to production, and don't quite work anymore. It was hard enough getting data from manufacturers the first time!

---

### Post by AutoStatic on 2010-02-03
Hello sgx, thanks for the answer but it doesn't answer my question.
And if the post 2007 1010's still use an Envy24 chipset it shouldn't make any difference unless that chip itself changed.

---

### Post by atomizer on 2010-02-03
If you got firewire400, I would go for the [Presonus FP10]("http://www.presonus.com/products/Detail.aspx?ProductId=3")


It has 8 mic/jack inputs and [should work fine in ubuntu]("http://ubuntuforums.org/showthread.php?t=522738")

I have only played with it on a Mac and Windows PC, and it gives good audio.

Price here is about 300 euro

---

### Post by robeast on 2010-02-03
> **AutoStatic said:**
> Hello sgx, thanks for the answer but it doesn't answer my question.
And if the post 2007 1010's still use an Envy24 chipset it shouldn't make any difference unless that chip itself changed.

I have no personal experience with recent Delta cards, but I got a comment dropped on my site that states what sgx said above and I have seen that mirrored in a few places. My advice, don't buy a new Delta. There are plenty of other interfaces that are just as good that you can be fairly certain will work perfectly or at least with most of the interface's functionality. If you must get a Delta, either get a used one from before 2007, or get a brand new one and expect difficulties. I would love to be proven wrong, because the Delta series has been a long time favorite of Linux audio users and it is a shame to see regression there.

---

### Post by sgx on 2010-02-04
> **AutoStatic said:**
> Hello sgx, thanks for the answer but it doesn't answer my question.
And if the post 2007 1010's still use an Envy24 chipset it shouldn't make any difference unless that chip itself changed.

It is circuit changes and different support chips that are problematic.
Otherwise, you might see Envy24 replaced by 'Envy26'.
Tascam usb devices also employed some cost-cutting circuit changes, and have new issues when used in linux. E-mu hardware products have changed over the years while keeping names intact, and theres  nothing wrong with cost-cutting in a crowded competitive market, assuming performance is maintained or improved. Sadly, it puts unpaid linux devs behind a yet another new 8-ball, and makes buying products known to work a little more challenging.  
Cheers

---

### Post by AutoStatic on 2010-02-04
> **sgx said:**
> It is circuit changes and different support chips that are problematic.
Otherwise, you might see Envy24 replaced by 'Envy26'.Envy26? Googled that one, nada, nothing :(

> **sgx said:**
> Tascam usb devices also employed some cost-cutting circuit changes, and have new issues when used in linux.Yes, that's right, but the problems exist mainly with the USB2 devices. No wonder, there are simply no class-compliant USB2 devices.

> **sgx said:**
> E-mu hardware products have changed over the years while keeping names intact, and theres  nothing wrong with cost-cutting in a crowded competitive market, assuming performance is maintained or improved.E-mu, that's Creative right? [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)
They seem to be cooperative but taking in account the number of Creative and E-mu related topics on these forums I would never buy a device of one of these vendors myself.

And did some digging myself in the ALSA bugtracker on the Delta 1010, pre 2006 is 'rev d' (VT1712) and post 2006 is 'rev e' (VT1712G chip) probably. So something did change. But it has been fixed: 2008-01-16 13:14 perex File Added: delta1010e.patch
So I reckon any Delta 1010 should work with ALSA.

---

### Post by niffcreature on 2010-02-06
he doesnt appear to be reading this thread anymore.

wonder if he will have enough pre amps?


wonder if he has a firewire port?

i swear, you guys, sometimes you go so out of your way to talk about linux rather than the whole big picture situation...

---

### Post by robeast on 2010-02-06
> **niffcreature said:**
> he doesnt appear to be reading this thread anymore.

wonder if he will have enough pre amps?


wonder if he has a firewire port?

i swear, you guys, sometimes you go so out of your way to talk about linux rather than the whole big picture situation...

The topic of this conversation has changed naturally--look, it's changing again!--and if you had been lurking throughout it's entirety you know that we gave ample information for him to make an informed decision based on his available hardware and recording needs. 

Personally I am STILL confused about the new Deltas. I'm going to start a new thread about this because it has been popping up a lot here and there...

---

