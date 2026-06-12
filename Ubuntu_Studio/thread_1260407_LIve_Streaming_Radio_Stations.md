---
title: "LIve Streaming Radio Stations"
date: 2009-09-07
forum: Ubuntu Studio
---

### Post by sheffrem on 2009-09-07
Hi everyone.

Im working on a project that consist of live streaming local radio station over the internet.
Im not referring to streaming an MP3 list or insert an online radio to the project(website) but rather what devices, software are required to broadcast local station which can only be listen with a normal radio to the internet. No matter the OS (Preferably UBUNTU) it works on i just need help to start something.

Thnks in ADVANCE.

---

### Post by Whiffle on 2009-09-07
I think you can use Icecast for this ( [http://www.icecast.org/](http://www.icecast.org/) ), and take input from a sound card input ( [http://www.6809.org.uk/media/ices2-howto.shtml#config-input-dev](http://www.6809.org.uk/media/ices2-howto.shtml#config-input-dev) ).  Shouldn't need much else.

---

### Post by sheffrem on 2009-09-07
Thanks for the quick reply. I made a mistake and forgot to say that i wanted to stream more than on local radio station, pls take a look at this link to see what i mean.
[http://www.ghanaweb.com/GhanaHomePage/NewsArchive/live-radio.php](http://www.ghanaweb.com/GhanaHomePage/NewsArchive/live-radio.php)

Again thanks in advance for anybody who reply and read this post

---

### Post by sheffrem on 2009-09-08
Anybody know about how this thing works ? pls help out.

---

### Post by bobince on 2009-09-08
Yes, you can run icecast with multiple mount points. Or SHOUTcast with multiple instances, or whatever.

How are you getting hold of the radio? Off the air? Analogue (AM/FM)? Just connecting a radio's line output to the sound card?

The cheapest way to get a single PC-controllable FM tuner connected would be to use an analogue TV capture card (from the likes of Hauppauge): many of those have built-in tuners, you could just ignore the TV signal and connect the audio into your sound card to transmit.

For serving multiple streams off the same machine, you could get a prosumer sound device with multiple recording channels, and connect those to sources from external tuner[s] or cards.

There are PCI cards with multiple tuners which would do the whole thing nicely and appear to have Linux drivers. See eg. [http://www.audioscience.com/internet/products/tuner_cards/asi8702.htm](http://www.audioscience.com/internet/products/tuner_cards/asi8702.htm) - but these are aimed at professional broadcasters and will cost you a big chunk of cash!

---

### Post by sheffrem on 2009-09-08
Thanks for the reply. checking your link.
I would prefer using a TV TUNER since they will allow me to get more than one station.
We have a script that when you click on an station logo it should play in a small player in the middle of the page.

I didnt know how that works until i check the code of america.fm and realised that only server with mms:// as URL could play directly in the page without openning a pop up. can icecast or shoutcast configure these station and stream as mms:// . 
I dont know much so pls excuse my ignorance.

Thanks in advance.

---

### Post by bobince on 2009-09-09
> **sheffrem said:**
> I would prefer using a TV TUNER since they will allow me to get more than one station.

Not simultaneously they won't (unless you're talking about a DAB tuner that can provide access to multiple streams on the same multiplex).

> I didnt know how that works until i check the code of america.fm and realised that only server with mms:// as URL could play directly in the page without openning a pop up.

No, in-page players do not rely on the type of stream. MMS is Windows Media Server only, but you can certainly have an embedded player that talks to SHOUTcast/IceCast via plain old HTTP. Indeed, you can use a Flash player to do it, which is much more convenient for everyone than messing around with Windows Media or Real plugins. (america.fm uses winmedia and doesn't work at all for me).

---

### Post by sheffrem on 2009-09-10
Again thanks guys for the great help.

So what type of software or equipment do i need to setup a mms server that stream many local radio station to the internet simultiniously.

---

### Post by bobince on 2009-09-11
If you want MMS streaming you must use Microsoft's Windows Media Services. I don't see why you'd want to though; MMS doesn't really give you anything the other streaming systems don't.

It has nothing to do with the ability to serve multiple streams: you can do that with any streaming system as long as you have the hardware to feed it with multiple tuner sources.

---

