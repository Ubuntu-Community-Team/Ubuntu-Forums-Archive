---
title: "FA-101 Midi not working, audio fine!"
date: 2009-11-23
forum: Ubuntu Studio
---

### Post by caesura on 2009-11-23
Hi,

I have Hardy Heron, with UbuntuStudio installed separatedly, and my FA-101 firewire box is working fine for audio, but there is no MIDI input/output available in Jack - any idea where I start looking?

According to this :[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) it looks like Karmic needs a2jmidid, but does Hardy Heron?

Thanks for any pointers!

Caesura.

Edit : I'm not sure my FA-101 midi ports show up in alsa either - any tips on how to check that alsa is providing me with midi, or can I just have jack-midi with no alsa at all? ;)

---

### Post by bluesscream on 2009-11-23
I'm owner of a fa101 too and very happy with it on karmic. It's Midiports are not supported by current ffado versions afaik. To connect my midi harware I bought a resonably prized emu xmidi 2x2 on amazon, better then second hand devices in ebay.

---

### Post by caesura on 2009-11-24
Aha, yes I'm happy too with my FA-101 on Hardy, bluesscream.  

And I found the solution too - there is an ALSA tab on the connections window in the Jack control kit thingy - and from there you can make connections to other MIDI programs.  

Equally, there is a MIDI tab, whichis blank. Odd.

So it seems Jack uses Alsa to do its MIDI work for it!

So that was the solution if anyone was looking, its the ALSA tab to do MIDI connections, not the MIDI tab.

Now onto the latency tweeks, wish me luck, 92ms is a wee bit wide of the mark...

Caesura

---

### Post by dawiba on 2009-11-24
I'm using Karmic, so I'm not sure if this will apply to Hardy. Karmic comes with a2jmidi preinstalled. You may need to download and install it separately in Hardy.

To open it, press alt+f2. This will bring up a 'Run Application' window. In the window type 'a2jmidid'. This will start a2jmidi, although no new application window appears.

If you now go back to jack control and click the midi tab, you should now see a2j there ready for connections. You should also have a firewire_pcm option in this window. For me, I connect firewire_pcm to a2jmidi (there are different a2j options depending which program you're using) and record midi through that. I'll connect things up in the opposite direction to trigger external sounds.

This is jack now using firewire to connect midi. If you use the alsa tab, you will be using usb to connect midi (at least that's my understanding), which means a usb midi interface separate to your FA-101.

Hope this helps

---

### Post by caesura on 2009-11-24
Hi dawiba,

Thanks for that, useful stuff.

Well, it all seems to work without a2jmidid - in fact it seems like the ALSA tab in jack control is doing the same thing as a2jmidid.  

And that's using the FA-101's firewire connection only, no USB at all.

I'll try a2jmidid if the latency is an issue (er, I do have an external keyboard, an Ozone, connected to my FA-101 midi-in port, hopefully its not that, I need to try it in Windoze I guess).

Hope this is useful for Hardy users, I'd be interested what experiences they've had with all this!

Cheers,

Caesura.

---

