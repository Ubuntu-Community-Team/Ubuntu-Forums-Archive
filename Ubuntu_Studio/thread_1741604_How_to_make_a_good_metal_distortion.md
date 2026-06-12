---
title: "How to make a good metal distortion?"
date: 2011-04-28
forum: Ubuntu Studio
---

### Post by Ippo343 on 2011-04-28
Hi,

I've been trying to get a good metal distortion sound using jack rack with the caps plugins, but I can't seem to find any way to get a decent sound.
They are good with clean sound, but I need a really really heavy and fat distortion (listen to this for reference, it's the sound I'd like to emulate: [http://www.youtube.com/watch?v=TIGZqHy3Eu0](http://www.youtube.com/watch?v=TIGZqHy3Eu0) ). The same applies to rackarrack, good for clean but horrible distortion.
I even tried chaining multiple distortions together, but the outcome is absolute garbage.

Any metal-head got this figured out already?

---

### Post by snowpine on 2011-04-28
Mic a tube amp? I'm in a metal band, that's how our guitarist does it (he uses a Marshall).

---

### Post by Joe of loath on 2011-04-28
Yup, you'll never get a good distortion sound with plugins. Grab an SM57 or equivalent and record your amp that way.

---

### Post by Ippo343 on 2011-04-28
Those were the 2 solutions I wanted to avoid :)

My amp doesn't have a line-out, except for use with external speakers, and I found out the hard way that you really don't want to connect into a pc (yeah, I know... now.) because it fries the line-in.

As for the mic options, I don't think it's a feasible solution. I get noise (a lot of it) basically in every stage of my setup, because I'm using terrible hardware in a terribly noise room (I mean electronic noise), so using a microphone draws in so much noise that it's unusable.

I'll give a shot to amplitube metal though, seems nice.

---

### Post by Pablo_F on 2011-04-28
I suggest you try gx_head, a virtual amp based on guitarix. For the time being you will have to download the source code and compile. Feel free to ask if you get stuck. 

Cheers! Pablo

---

### Post by snowpine on 2011-04-28
> **Ippo343 said:**
> As for the mic options, I don't think it's a feasible solution. I get noise (a lot of it) basically in every stage of my setup, because I'm using terrible hardware in a terribly noise room (I mean electronic noise), so using a microphone draws in so much noise that it's unusable.

A lot of times, that noise you're hearing is inaudible once the other instruments are added. Also I assume you know how to use a noise gate to eliminate hum during quiet sections?

If your room is really that terrible then I recommend a technique called "reamping." Record your guitar parts clean and direct until you are 100% satisfied with your performance, then bring them in to a pro studio with a good guitar amp setup. They will play your finished tracks through their amp and record the results. This will only take a couple of hours so will be much cheaper than paying for studio time for the complete process.

I listened to the Testament track in your link and I really don't think that sound was achieved using digital computer plugins. It sounds like the cabinet was mic'd by someone who really knew what he was doing, the is mic is correctly placed to capture the overtones coming from the speaker.

---

### Post by Ippo343 on 2011-04-28
Well, my guess at the testament sound is something like:

_good musicians (don't have)
_good instruments (don't have)
_good amp (don't have)
_good mic (don't have)
_good tech guy (don't have)
_good studio (don't have)

I know I'm not going to get a serious recording at home unless I'm willing to pay a lot of money on professional equipment.
But the point is, there must be a way to get a serious distortion on a computer. Amplitube does it, so I guess that a way exists...

I'll give another shot at recording the amp, see if I can do something better.
Cool stuff the thing of reamping, never heard of it, thanks ;)

(I'm compiling gx_head, will let you know)

---

### Post by sgx on 2011-04-28
[http://www.youtube.com/watch?v=begpC9T4yRE](http://www.youtube.com/watch?v=begpC9T4yRE)

This is the Amplitubes new Soldano amp model being tested.
Its $20 using the new custom shop. Open account, download
free Amplitube 3.5, open custom shop, slap da plastic, and its yours.

Cheers :)

---

### Post by Ippo343 on 2011-04-28
I'm trying to mic my amp. I'm trying to add some plugins in ardour, and I have to say, that it's quite a decent solution.

I guess I have no choice but play with the plugins and get a better mic...

---

### Post by sgx on 2011-04-28
> **Ippo343 said:**
> I'm trying to mic my amp. I'm trying to add some plugins in ardour, and I have to say, that it's quite a decent solution.

I guess I have no choice but play with the plugins and get a better mic...
gx-head .deb file is here:

[http://www.bandshed.net/debian/](http://www.bandshed.net/debian/)

a dependency or two may be called for
found in ubuntu repositories or

[http://www.bandshed.net/checkinstall/](http://www.bandshed.net/checkinstall/) or

[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)

If you can shake out $80-$99 for a Fender Mustang 1
guitar amp, it will revolutionize your guitar life.
A linux sound editor has been written for it, called
Plug v.7 that replicates the crucial parts of the 
Fender Fuse software used in windows and mac. Combining
its metallics with rakarrack, is the beez kneez! :)

Florescent lights destroy your audio circuits with noise, use candles,
anything but Obamas pet f bombs. Use a heavy gauge extension cord,
and find the quietest circuit in your home.
Cheers :)

---

### Post by FuzzShifter on 2011-04-28
If you're using VSTs, there's a plugin  called FreeAmp available for free ([link]("http://www.vst4free.com/free_vst.php?id=580")).

It has a movable virtual mic, selectable cabinet, two channels (several models in each channel) and built in pre-compression and noise gate, effects 'pedals', virtual synth...

Sounds good, so that's the point.:)

---

### Post by chkneater on 2011-04-28
I know that overdriving the outputs of the software can produce a distortion?

---

### Post by xwindowsfan on 2011-05-01
just throwing it out there. as far as distortion goes.
there are a couple of stomp box effect VST plugins.
one is Red Skull Distortion (which may not be for everyone)  [http://www.kvraudio.com/get/3555.html](http://www.kvraudio.com/get/3555.html)
the other is the excellent Metal Clone which emulates the Metal Zone 2 pedal;
[http://www.kvraudio.com/db/metal_clone_by_mokafix_audio](http://www.kvraudio.com/db/metal_clone_by_mokafix_audio)

---

### Post by sgx on 2011-05-02
> **xwindowsfan said:**
> just throwing it out there. as far as distortion goes.
there is a couple of very good stomp box effect VST plugins.
one is Red Skull Distortion [http://www.kvraudio.com/get/3555.html](http://www.kvraudio.com/get/3555.html)
the other is Metal Clone which emulates the Metal Zone 2 pedal;
[http://www.kvraudio.com/db/metal_clone_by_mokafix_audio](http://www.kvraudio.com/db/metal_clone_by_mokafix_audio)
California Sun, a nice basic ampsim, is in the collection, very pleasing tone to give to rakarrack, and also in the collection is a very well featured pitch-shifter. Thanks for the links :)

---

### Post by xwindowsfan on 2011-05-04
yw. KVR is a great site for snagging free plugins. :guitar:

---

