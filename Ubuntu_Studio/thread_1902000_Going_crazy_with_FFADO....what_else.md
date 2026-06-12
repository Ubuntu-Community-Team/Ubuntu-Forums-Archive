---
title: "Going crazy with FFADO....what else?"
date: 2011-12-29
forum: Ubuntu Studio
---

### Post by the.deathgate on 2011-12-29
Hi guys,

I am running Ubuntu 11.10.

I tried to get my brand new Focusrite Saffire Pro 40 to get working.
Starting ffado-mixer gave me a smile as all channels where present in the UI.
But Jack always crashed some seconds after initializing the interface (could hear a click in the headphones and LEDs where on, for the moment...).

Then I installed the Ubuntu Studio packages (some one mentioned that would be a nice idea in some forum).

OK, so now not even the FFADO-Mixer likes to start.
Something was wrong with the DBUS...so I checked ffado-dbus-server.
This tells me now:
[I]Library version mismatch. (required: libffado 2.999.0-, present: libffado 2.999.0-2018)
[/I]

This is really annoying. The versioning-info even looks strange...

---

### Post by sgx on 2011-12-30
hang in there, the ffado website, qjackctl wiki, and google
'focusrite firewire ffado' searches ending with
-2009 -2008 -2007 etc etc will remove some older search dross
Adding celebrity niks like trulan, falk, autostatic, pablo, and
stochastic, will be lucky, as they help solve many issues in recent years and days :popcorn:

The extraneous info you will pass through on the way to success
can be bookmarked for future quests.

youtubes of ardour, hydrogen, zynaddsubfx, ubuntu studio
and qjackctl, often include connections setup in qjackctl
which will be encouraging with visual familiarity.
Cheers

edit  I have read that the Texas Instruments firewire chipset on the motherboard
or firewire card is quite crucial to success.

---

### Post by sgx on 2011-12-30
[http://bobhamil.com/FFADO/index.html](http://bobhamil.com/FFADO/index.html)

[http://answerpot.com/showthread.php?2986612-help+with+focusrite+saffire+pro24](http://answerpot.com/showthread.php?2986612-help+with+focusrite+saffire+pro24)

Have you read this?
Cheers

---

### Post by jejeman on 2011-12-31
[QUOTE=sgx]edit  I have read that the Texas Instruments firewire chipset on the motherboard or firewire card is quite crucial to success.[/QUOTE]Not really, I use Nec with no problems.
```
FireWire (IEEE 1394): NEC Corporation uPD72873 IEEE1394 OHCI 1.1 2-port Host Controller (rev 01)
```

---

### Post by sgx on 2012-01-01
Hi, I found a SOS magazine article from 2006 that agrees with you. :)

[http://www.soundonsound.com/sos/dec06/articles/pcnotes_1206.htm](http://www.soundonsound.com/sos/dec06/articles/pcnotes_1206.htm)

(links in the article may be dead)

"Focusrite discuss their Firewire requirements for Liquid Mix in great detail and end up with a blanket recommendation for Texas Instruments and NEC chipsets."

[http://www.soundonsound.com/sos/dec06/articles/saffire.htm](http://www.soundonsound.com/sos/dec06/articles/saffire.htm) reviews
an older Focusrite.

This is a current pdf

[http://www.focusrite.com/answerbase/en/var/attachments/Focusrite_IEEE_1394_compatibility.pdf](http://www.focusrite.com/answerbase/en/var/attachments/Focusrite_IEEE_1394_compatibility.pdf)

It does not mention NEC, but warns against one nVidia motherboard chipset :(

But now we have a live witness that knows NEC works. :)
(case by case, as the linux hardware compatibility  saga marches on)

Cheers, and Happy 2012!

---

### Post by jejeman on 2012-01-01
Well if you were refer that for Focusrite exclusivly you need Texas, than ok. I appologize, I don't know about that.
I thought that you were talking about firewire cards in general. I use **Edirol** with NEC with no problems.

---

