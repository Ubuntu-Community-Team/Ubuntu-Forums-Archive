---
title: "Recommendations for Firewire (ieee1394) ExpressCard for UbuntuStudio?"
date: 2008-06-01
forum: Ubuntu Studio
---

### Post by prismatic7 on 2008-06-01
Can anyone recommend a WORKING ieee1394 ExpressCard for use with a Firewire audio device (Focusrite Saffire LE)

I've been bitten by the not-at-all-infamous RICOH ieee1394 chipset bug (intermittent, inexplicable crashes during audio transmission ONLY!) and now I'm having significant trouble.

I bought an ST-Lab 1394b ExpressCard (Firewire 800) - a TI chipset - which is detected perfectly by Ubuntu, after 'sudo modprobe pciehp pciehp_force=1' Connecting the Saffire LE and starting jackd ('jackd -v -R -d freebob') means that jack starts, all the inputs and outputs are detected, MIDI drivers loaded... and then jackd aborts without throwing an error to stdout or syslog.

Could this be due to the ST-Lab card being FW800 rather than FW400, or is something more sinister at work?

If anyone, anyone at all has an answer that works, I will provide a prize.

---

### Post by Stochastic on 2008-06-01
One thing that may help is unplugging/replugging the firewire, or even a reboot.

---

### Post by prismatic7 on 2008-06-01
> **Stochastic said:**
> One thing that may help is unplugging/replugging the firewire, or even a reboot.

Unfortunately, I've tried that one :) Several times over!

There doesn't seem to be any issue with the Saffire LE itself - the fault on the inbuilt RICOH device is intermittent (but fatal) so I have heard sound from the Saffire LE. As far as I am able to tell, the problem with the Expresscard is either in pciehp or support for  the card itself.

---

### Post by Stochastic on 2008-06-02
Then you're most likely to find better assistance in the General Help section of the forums.  The only difference between Ubuntu and Studio in hardware terms, is the realtime kernel.

---

### Post by prismatic7 on 2008-06-02
> **Stochastic said:**
> Then you're most likely to find better assistance in the General Help section of the forums.  The only difference between Ubuntu and Studio in hardware terms, is the realtime kernel.

Agreed, but I was hoping for a recommendation for a working card from someone who is using it with firewire audio. It seems that my setup works fine for everything EXCEPT audio, so after nearly A$600  cash layout I absolutely NEED someone with pro-audio experience on Linux to recommend something. Which is what this forum is about.

---

### Post by Stochastic on 2008-06-02
For internal cards, TI (texas instruments) chipsets are known for their good audio handling, while RICOH are known for their lack thereof.  That's about all I know.

---

### Post by prismatic7 on 2008-06-02
> **Stochastic said:**
> For internal cards, TI (texas instruments) chipsets are known for their good audio handling, while RICOH are known for their lack thereof.  That's about all I know.

Which is why I got the TI chipset in Expresscard form... *sigh*

Maybe it *is* a FW800 vs FW400 issue, which leaves me with another outlay of at least A$70. Dammit. Wish I'd never gone down this road, now.

---

### Post by prismatic7 on 2008-06-02
OK.

Booting to 64Studio gave better verbose logging from jackd particularly here:

new client: qjackctl-7381, id = 2 type 2 @ 0xb6d44000 fd = 15
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
client qjackctl-7381: start_fd=5, execution_order=0.
client qjackctl-7381: wait_fd=14, execution_order=1 (last client).
-- jack_rechain_graph()
JACK tmpdir identified as [/dev/shm]
zombified - calling shutdown handler
11:45:20.906 MIDI connection graph change.
11:45:20.907 Shutdown notification.
11:45:20.908 Client deactivated.
11:45:20.909 JACK was stopped successfully.
11:45:20.909 Post-shutdown script...


I'm getting zombified and kicked... any ideas?

---

### Post by prismatic7 on 2008-06-03
Found it. *swears massively*

From the [FFADO site](http://www.ffado.org/?q=node/251)

> USB/firewire and s400/s800 combo cards are not compatible. Symptoms are usually no audio recording/playback but device will install and sync, erratic audio performance and rarely will not allow the device to install or sync. We recommend a firewire card that ONLY has s400 firewire connections and preferably with a Texas Instruments or VIA chipset.

Firewire cards with NEC chipsets are not compatible. Symptoms are similar or the same as combo cards.

So my card *just won't work*.

These things will be documented.

---

### Post by Stochastic on 2008-06-03
Ouch, that's gotta hurt.

Next question on my mind would be, "What local repair shop can swap out the RICOH for a TI or VIA?"

Though that could be dangerous.

Other options: Swap your Saffire for a USB or PCMCIA card (I think the Echo corporation makes some nice PCMCIA cards)

---

### Post by prismatic7 on 2008-06-03
> **Stochastic said:**
> Ouch, that's gotta hurt.

Next question on my mind would be, "What local repair shop can swap out the RICOH for a TI or VIA?"

Though that could be dangerous.

Other options: Swap your Saffire for a USB or PCMCIA card (I think the Echo corporation makes some nice PCMCIA cards)

It really, really does. The laptop's still under Dell warranty, so I don't think I'll go down that road!

I'd really like to get the Saffire working - even if it means buying ANOTHER ExpressCard (ExpressCard's not backwards compatible with PCMCIA, so that rules out the Echo devices...) - because from the 30 seconds or so I've had it working it just sounds beautiful. So, more fiddling, more tweaking... At least when I finally get a chance to do some doco there'll be some real-life examples to talk about!

Anyway, cheers for all the help/support/suggestions, everyone.

---

### Post by scotty64 on 2008-07-25
> **prismatic7 said:**
> Can anyone recommend a WORKING ieee1394 ExpressCard for use with a Firewire audio device (Focusrite Saffire LE)

If anyone, anyone at all has an answer that works, I will provide a prize.

I had similar problems (Dell XPS M1330 with buggy Ricoh chip leading to interruptions, xruns and all kind of nasty stuff) and got myself a Lindy 2 port Firewire 1394a Express Card (TI chipset).
I am just coming out two days with several hours of recording (Presonus Firebox - Jackd - Ardour) and everything worked excellent. Not a single crash or xrun! The only problem with the card is that it is not recognized as hotplug device, so you have to plug it into your laptop before booting.

---

### Post by avijayendra on 2008-08-05
Did you get any driver for Firewire 800 (1394b)? If the driver supports only 1394a, then it won't be able to support the 1394b card.
1394b is backward compatible with 1394a, so a 1394b driver would be able to support 1394a cards as well.
If you have 1394b driver only, then can you pl. help me get the source code for the same?

---

### Post by prismatic7 on 2008-08-05
> **avijayendra said:**
> Did you get any driver for Firewire 800 (1394b)? If the driver supports only 1394a, then it won't be able to support the 1394b card.
1394b is backward compatible with 1394a, so a 1394b driver would be able to support 1394a cards as well.
If you have 1394b driver only, then can you pl. help me get the source code for the same?

No, I didn't get it working. Sorry.

After lots of experimentation, I discovered that my laptop just doesn't like working with ExpressCards! (in Linux and Windows!)

---

### Post by gregolak on 2008-09-04
> **scotty64 said:**
> I had similar problems (Dell XPS M1330 with buggy Ricoh chip leading to interruptions, xruns and all kind of nasty stuff) and got myself a Lindy 2 port Firewire 1394a Express Card (TI chipset).
I am just coming out two days with several hours of recording (Presonus Firebox - Jackd - Ardour) and everything worked excellent. Not a single crash or xrun! The only problem with the card is that it is not recognized as hotplug device, so you have to plug it into your laptop before booting.

Hi,

did you do something special to have the expresscard working ?  I just bought a TI firewire expresscard too, and can't manage to make it work...

See my post here : [http://ubuntuforums.org/showthread.php?p=5725347#post5725347](http://ubuntuforums.org/showthread.php?p=5725347#post5725347)

Thanks !

---

### Post by antdedyet on 2008-10-13
Bought a TI based expresscard recently, found here:


[http://tinyurl.com/3jg3vt](http://tinyurl.com/3jg3vt) (ebay)

Works in that closed OS as a OHCI controller, but isn't detected in Linux when loaded before boot or loaded after boot with hotplug.

Anyone else had success with this card? If so, what are the helpful details on getting it to work?

Thanks!



> **gregolak said:**
> Hi,

did you do something special to have the expresscard working ?  I just bought a TI firewire expresscard too, and can't manage to make it work...

See my post here : [http://ubuntuforums.org/showthread.php?p=5725347#post5725347](http://ubuntuforums.org/showthread.php?p=5725347#post5725347)

Thanks !

---

