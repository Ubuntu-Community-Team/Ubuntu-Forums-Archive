---
title: "audio interface options"
date: 2010-05-03
forum: Ubuntu Studio
---

### Post by suddentwigs on 2010-05-03
Hi there. I have been attempting to track down an audio interface that works with ubuntu 10.04 and is capable of recording 16 channels of analogue sound simultaneously. Does such a thing exist? If not, what are my best options? I have usb 3.0, firewire and PCIe connections.

---

### Post by sgx on 2010-05-03
Hi, try this sebsite

[http://www.linuxstudiopro.com/](http://www.linuxstudiopro.com/)

Details about what you will record will be helpful. A rock band, and
10 mics on the  drumkit?

PCI slots with a pair of maudio 1010 cards can be done, linux can problematic because you must choose hardware that you know will work,
and sometimes, selling/trading what you have, then buying what you need,
is the only way forward. Once the right hardware is yours, a great deal of freedom and creativity will emerge 
Cheers

---

### Post by AutoStatic on 2010-05-04
Hello suddentwigs, that should be possible with two Firewire devices like the Presones Firepod or Focusrite Saffire Pro 40 for example.

---

### Post by mango42 on 2010-05-04
> **AutoStatic said:**
> Hello suddentwigs, that should be possible with two Firewire devices like the Presonus Firepod or Focusrite Saffire Pro 40 for example.

Has anyone here tested the Saffire Pro 40 'flat out' with the ffado drivers yet, as I understood the devs were awaiting DICE v2.1? I'm just about ready to try it, once I install Lucid Studio on a 64bit machine.

On another subject entirely, do you have any recommendations as to where would be best to upload all-done-in-UbuntuStudio copyright-free music? I don't know much about Ubuntu One yet - seems enmeshed in 'distributors' and all that nonsense.

It would be a great antidote to all the deep-dark-tech-stuff we have to deal with on this sub-forum if we could blow our own trumpets occasionally! {:>

Hey, we could even start our own poll-based 'charts'... :rolleyes::lolflag:

---

### Post by AutoStatic on 2010-05-04
> **mango42 said:**
> Has anyone here tested the Saffire Pro 40 'flat out' with the ffado drivers yet, as I understood the devs were awaiting DICE v2.1? I'm just about ready to try it, once I install Lucid Studio on a 64bit machine.Nope, but you can keep an eye on it here: [http://ffado.org/?q=node/862](http://ffado.org/?q=node/862) (but you probably checked that yourself already ;) )

> **mango42 said:**
> On another subject entirely, do you have any recommendations as to where would be best to upload all-done-in-UbuntuStudio copyright-free music? I don't know much about Ubuntu One yet - seems enmeshed in 'distributors' and all that nonsense.Maybe Jamendo? Or Soundclick? Or aren't you referring to that kind of possibilities? You could also host it yourself.

> **mango42 said:**
> Hey, we could even start our own poll-based 'charts'... :rolleyes::lolflag:Yeah! Why not?

---

### Post by mango42 on 2010-05-04
> **AutoStatic said:**
> Nope, but you can keep an eye on it here: [http://ffado.org/?q=node/862](http://ffado.org/?q=node/862) (but you probably checked that yourself already ;) )

Daily ;-)

> Maybe Jamendo? Or Soundclick? Or aren't you referring to that kind of possibilities? You could also host it yourself.

Hosting's not an option but thanks for the tips - a cursory glance gives me the feeling 'poll charts' are already there ;-) 

Oops, no, not Jamendo - links to farcebook - yuck...

---

### Post by suddentwigs on 2010-05-04
Planning on recording rock trio/quartet live in the studio, with about 8 mics on the drums and the option of multiple mics on other instruments.

---

### Post by trulan on 2010-05-04
I do 16 tracks with two Presonus Firepods, they work great!  They are of course discontinued now, so you'll have trouble finding those new.  I got my first one new three years ago, bought my second one off ebay more recently.

But there are numerous firewire devices that can be daisychained to get sixteen tracks, or more.  You're definitely going to want to go with firewire to get that many tracks working properly though, IMO.

---

### Post by suddentwigs on 2010-05-05
Is Firewire definitely preferable to PCI for daisychaining, or just better than USB 2.0? Also is it significantly more difficult to set up a pair of units, or is it likely to work pretty easily/just the same as a single unit?

---

### Post by trulan on 2010-05-05
It probably depends on the unit, but I'd venture a guess that almost all firewire devices are designed to be daisychained.  I've found it no harder to run two than to run one, except it takes more computer power, so you need to allow slightly larger latencies.  But latency is a non-issue if you're just recording, and I can still get it down under 10 ms even with two firepods.

I have no experience with using multiple pci cards so I'm not qualified to comment on that.  I guess if the cards were designed to do it, it would work.  I was mostly recommending firewire over USB.

---

### Post by suddentwigs on 2010-05-05
The other thing I've been looking into is balanced cabling. It seems to cost a lot more to have balanced inputs, is it possible or even necessary to use balanced cables for a mostly live rock setup?

---

### Post by mango42 on 2010-05-06
> **suddentwigs said:**
> The other thing I've been looking into is balanced cabling. It seems to cost a lot more to have balanced inputs, is it possible or even necessary to use balanced cables for a mostly live rock setup?

It's refreshing to get a question here that I can actually answer with a degree of confidence!

Short answer, NO not necessary but, rule of thumb, your noise floor goes up as the cube of the cable length, so either keep your cables as short as possible or go balanced. Condenser microphones are by their very nature balanced, but rock groups are more likely to use acoustics like Shure SM58's, as they can double as hammers ;-)

I wouldn't worry about a balanced setup except for mastering - besides, a little line noise is irrelevant to Rock, surely?

Then there's the knotty problem of inserts. How many even professional mixers provide balanced inserts? Not a lot! If you have a regular analog mixer (eg my favourite tour jobs are Allen & Heath GL2's) and a patchbay, it's inevitable that your analog compressors & gates will be working unbalanced through the inserts, whilst your group and main outputs will be balanced (ideal for feeding into your brandy new firewire interface).

Another tip to keep the costs down is to make up your own cables for, 'yea verily, they will go forth and multiply' - this way you can achieve top quality at least cost. (Neutrik or Soundcraft fittings, OFC balanced cables, shorted cold for unbalanced use, and best LowMeltingPoint solder - good for years!)

Finally, if you want to get a truly professional view on all this, go read Rane's Sound System Interconnection page - it's the most lucid exposition on the whole subject and eminently readable, IMO:-

[http://www.rane.com/note110.html](http://www.rane.com/note110.html)

Bear in mind that I only use computers for the final mixing and arranging - all else is outboard, old style analog kit, as I'm not too keen on 'squeaky klean'

Nerdy joke time...
Q: Why do top flight audiophiles insist on using RCA phono plugs?
A: Because they are unbalanced!

---

### Post by suddentwigs on 2010-05-08
Irrelevant to some stuff yes but I don't want to be limited, there will be many times I shall need a completely clean signal. In real terms, how long does a cable need to be before the noise starts to register?

---

### Post by AutoStatic on 2010-05-08
Unbalanced? 3 meters I guess?

---

### Post by mango42 on 2010-05-09
> **AutoStatic said:**
> Unbalanced? 3 meters I guess?

Yep, but careful routing (especially of mains & firewire cables) helps enormously beyond that! But it's almost like asking how long is a piece of string... ;-)

---

### Post by suddentwigs on 2010-05-09
I thought as much. Noise level's obviously going to depend hugely on volume of instrument and how it is treated once it is in the system. I guess I'll save some pounds and go for the unbalanced box, and maybe augment it with a balanced box later. Thinking I'll go for the m-audio delta 1010lt. Does anybody know anything about using this device with a breakout box?

---

