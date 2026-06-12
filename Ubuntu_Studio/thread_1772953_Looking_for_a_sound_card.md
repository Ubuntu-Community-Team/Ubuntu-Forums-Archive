---
title: "Looking for a sound card"
date: 2011-06-01
forum: Ubuntu Studio
---

### Post by And6ate9 on 2011-06-01
I am looking for a sound card to complete my studio machine, so I can finally record all that sweet love I have been making to my guitar.

What's a good sound card to get. I was looking for something with a front input.

[http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=3988132&sku=C44-3392&SRCCODE=WEM2694MH&cm_mmc=email-_-Main-_-WEM2694-_-tigeremail2694]("http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=3988132&sku=C44-3392&SRCCODE=WEM2694MH&cm_mmc=email-_-Main-_-WEM2694-_-tigeremail2694")

---

### Post by Sylos on 2011-06-03
Hello there.

If you are looking for a sound card that will be good for recording instruments I wouldnt suggest you get anything like the SB XFI - these types of card are more geared towards gaming and sound output rather than getting a good sound recording (the lack of standard Jack/XLR inputs is a give away). That being said the SB XFI does seem to have 24/96 capability so you would be able to get a good quality sound - you may just be paying for more frills that arent necesarry (assuming you dont want the other features for other purposes).

The following is based on opinion and others may differ - this is just the way I look at it:

1. Allways go for 24/96 capable - if you want a good recording that is what you want.

2. I would never go for an outboard card running via usb or firewire. Anything running on USB1 will be limited in the amount of info it can carry so is not good if you want multiple inputs. Firewire is better from this point of view but can have other difficulties in getting it to work well - you would need to make sure the HW is compatible with the ffado standards. For these reasons I would always go with a PCI/PCIe interface.

3. If your looking for a one-stop solution then look carefully at the pre-amps built in to the box. No matter how good the rest of the card if you have a poor pre-amp you are always going to be limited in the quality of the recording you get.

4. Always check on the ALSA compatibility list for the HW you are looking at before buying. 

As for recomendations - I have a nice M-Aduio DELTA with an omni breakout box featuring 2 pre-amps. The qaulity is pretty good and works pretty much out of the box so is quite easy going. They are expensive new I think but you can get them pretty reasonbly priced if they crop up on ebay (like mine!).

Whats your budget?

---

### Post by And6ate9 on 2011-06-03
could you post some examples from ebay or amazon?

So you say that the sound blaster could do the recording but it has extra stuff right? Or it it just totally garbage for recording?

---

### Post by Sylos on 2011-06-04
Well I wouldnt say that its garbage but it definitely isnt designed specifically for recording music. The specs show that it can do the quality but it is somewhat limited in the input department. It has a mini-jack input for a mic but professional standard mics tend to come with XLR leads or at the very least a full sized jack. You could use a reducer to fit into it but that is a bit of a work around to fit a device that perhaps is not best suited to the task. 
Also, Im not sure it it does full duplex - meaning it may not be capable of playback and recording at the same time. This would be unsuitable if you want to multi-track.

As for examples - the M audio delta 66 that I have is quite common on line but they rarely come up with the Omni breakout box as well (this is different to the standard break out box as it has the preamps in for mic inputs).

Heres the basic pack:

[http://cgi.ebay.co.uk/M-Audio-Delta-66-Audio-Interface-NEW-/130434632884?pt=UK_Consumer_Professional_RL&hash=item1e5e828cb4#ht_1087wt_1184](http://cgi.ebay.co.uk/M-Audio-Delta-66-Audio-Interface-NEW-/130434632884?pt=UK_Consumer_Professional_RL&hash=item1e5e828cb4#ht_1087wt_1184)

Or if you need less than 6 inputs you could try the Delta 44

[http://cgi.ebay.co.uk/M-Audio-Delta-44-Pro-4-In-4-Out-PCI-Audio-Sound-Card-/370515531751?pt=LH_DefaultDomain_0&hash=item56447257e7](http://cgi.ebay.co.uk/M-Audio-Delta-44-Pro-4-In-4-Out-PCI-Audio-Sound-Card-/370515531751?pt=LH_DefaultDomain_0&hash=item56447257e7)

They are basically the same but one has 4 inputs the other 6.

The only catch with these two is that you would need a separate preamp for recording a mic. It depends on how you want to record. You could just DI your guitar into the card and use software to model amps/cabs/effects etc. If you want to record it live from your amp cab then you would need to get a preamp module to sit between mic and pci card. Not sure which are good stand alones to get - Im no expert on preamps. A little googling may help.

Hope that helps.

---

