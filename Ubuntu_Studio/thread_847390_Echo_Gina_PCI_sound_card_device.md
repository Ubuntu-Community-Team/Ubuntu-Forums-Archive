---
title: "Echo Gina PCI sound card device"
date: 2008-07-02
forum: Ubuntu Studio
---

### Post by jukingeo on 2008-07-02
Hello,

I have been thinking about upgrading my audio card since my current card isn't properly supported in Linux.

I have looked on the ALSA list and Echo Corporation products DO show up on the list as suppported, however I didn't see any Linux drivers on their website to download.  Where would I get the Linux drivers?

I am interested in the Echo Gina 3G.

As a note, M-Audio cards are supported as well and you CAN download the linux driver from their site.

Please advise.

Thank You,

Geo

---

### Post by Stochastic on 2008-07-02
You download alsa drivers from the ubuntu repository, but any ubuntu install should have alsa drivers already installed.

---

### Post by jukingeo on 2008-07-02
> **Stochastic said:**
> You download alsa drivers from the ubuntu repository, but any ubuntu install should have alsa drivers already installed.

Oh, Ok, so that means even if the company doesn't have a Linux driver, the driver is provided through ALSA?  So then what the ALSA device list says is gold?  Thus as long as the site claims it is supported, it should be supported then?

Now would that also go the same for devices supported under FreeBob?

Thanx,

Geo

---

### Post by Stochastic on 2008-07-02
yes the listings describe which cards those drivers will work with, so if alsa says it supports a card, then alsa is the driver you'd use for that card - same with freebob/ffado (if you're just now buying a firewire card, I'd look at the ffado listing as it's going to soon replace the freebob driver).

---

### Post by jukingeo on 2008-07-02
> **Stochastic said:**
> yes the listings describe which cards those drivers will work with, so if alsa says it supports a card, then alsa is the driver you'd use for that card - same with freebob/ffado (if you're just now buying a firewire card, I'd look at the ffado listing as it's going to soon replace the freebob driver).


Ok, good.  Now another question:

Is ffado already in effect, or no?  Now will Ubuntu have full ffado sound support in the future?  As I recall with the FreeBob system, firewire audio interfaces only worked through Jack.  So will that also be something that is going to change or even with ffado you will only be able to get audio through Jack?

Thanx,

Geo

---

### Post by Stochastic on 2008-07-02
ffado is still in beta testing, but I would expect by Intrepid's release that it will be included in UbuntuStudio (just my expectations, I'm not in charge of any of this).  As far as I know, yeah it only runs through jack, but there are ways of sending all the other system sounds (alsa and oss apps) to go into jack, so that you could use a freebob or ffado card as your main soundcard (ask thorgal for more info on doing this - it can be a touch complex to setup).

---

### Post by jukingeo on 2008-07-02
> **Stochastic said:**
> ffado is still in beta testing, but I would expect by Intrepid's release that it will be included in UbuntuStudio (just my expectations, I'm not in charge of any of this).  As far as I know, yeah it only runs through jack, but there are ways of sending all the other system sounds (alsa and oss apps) to go into jack, so that you could use a freebob or ffado card as your main soundcard (ask thorgal for more info on doing this - it can be a touch complex to setup).

Intrepid?  I guess that is the new name for the next Ubuntu release?  Is it just me or are the names intentionally following the alphabet? 

So then there IS a workaround if you need to get game and system sounds to work?  I would be curious in knowing how that could be done.

There are some really cool firewire audio devices that I COULD use and I wouldn't have to crack open my system.  Echo and Presonus has some nice firewire interfaces that are supposedly ffado supported.  Perhaps I will think of that for the future.  Right now I just need something simple to get some SOUND!

Thanx,

Geo

---

