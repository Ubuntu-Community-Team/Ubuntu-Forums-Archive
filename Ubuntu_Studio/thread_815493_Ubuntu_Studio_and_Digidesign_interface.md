---
title: "Ubuntu Studio and Digidesign interface"
date: 2008-06-01
forum: Ubuntu Studio
---

### Post by kvk on 2008-06-01
I'm building a home recording studio, intending to run UbuntuStudio on a home-built Shuttle box and running a Digidesign 003 rack for instrument-DAW interface. As Digidesign gear is meant to run with Pro Tools, is there going to be a problem with compatibility here? Or is UbuntuStudio able to deal with the Digidesign gear with no problem?

I called a few large stores that handle the hardware, but they had no idea.

Thanks!!

---

### Post by prismatic7 on 2008-06-01
> **kvk said:**
> I'm building a home recording studio, intending to run UbuntuStudio on a home-built Shuttle box and running a Digidesign 003 rack for instrument-DAW interface. As Digidesign gear is meant to run with Pro Tools, is there going to be a problem with compatibility here? Or is UbuntuStudio able to deal with the Digidesign gear with no problem?

I called a few large stores that handle the hardware, but they had no idea.

Thanks!!

Hm. Firewire support in Linux generally (not just Ubuntu) is patchy at the moment (As I am discovering to my significant cost!), so you really need to be aware of what's supported and what's not. [FreeBoB](http://freebob.sourceforge.net/index.php/List_of_Supported_Devices), the current FireWire audio driver does not list the 003 Rack as supported. [FFADO](http://www.ffado.org/?q=devicesupport/list), the next-generation driver, lists the 003 rack as 'unknown', which [doesn't mean it's NOT supported](http://www.ffado.org/?q=node/138)

If you've already bought the Digidesign device, you'd be advised to test comprehensively before committing to ANY flavour of Linux. If not, maybe another device would fill your needs better.

---

### Post by Aurora on 2008-06-01
I have often read that Digidesign devices can't be used under Linux.  The USB  (or FireWire) interface is proprietary; AFAIK no one has cracked it.  I don't believe they work with DAWs other than Pro Tools on Windows or MacOS, either.  If you can find any way to use a Digi 003 with Linux, it will be news to a lot of people.

The M-Audio Delta series is used by many in the Linux Audio world with great success; also various EMU and RME Hammerfall devices are often mentioned.  The ALSA site has a page devoted to hardware compatibility:

[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

If you should happen upon an M-Audio Ozone interface/keyboard controller, run away.  Some people can get them to work with Linux, but I have been unable to get mine to work after over a year of trying.  The pre-amps and converters are cheap, anyway.

Sorry for the bad news.  I hope you either want to continue to use Pro Tools, or can return the Digi 003.

--Paul

---

### Post by kvk on 2008-06-01
Thanks for the input!

Fortunately, I have not made the giant purchases yet, so no useless 003 is sitting in my room. I wanted to make sure of exactly this sort of thing before spending $5000 on gear.

As for Pro Tools, I'm pretty much settled on using Ubuntu Studio. I've used Pro Tools in commercial studios, and love it, but I want to remain on a Linux platform using free/open source software for my home studio. 

Thanks again! I'll poke around and see what hardware works best, and maybe I'll post the final hardware/software setup.

:)

---

### Post by Aurora on 2008-06-01
> **kvk said:**
> 
Thanks again! I'll poke around and see what hardware works best, and maybe I'll post the final hardware/software setup.

:)

I'm so glad you didn't spend money on incompatible hardware, and I'm eager to see what you end up choosing, as someone who has worked professionally in the field.

--Paul

---

