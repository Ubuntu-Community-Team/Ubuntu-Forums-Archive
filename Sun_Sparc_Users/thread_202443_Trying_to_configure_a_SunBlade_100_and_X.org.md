---
title: "Trying to configure a SunBlade 100 and X.org"
date: 2006-06-23
forum: Sun Sparc Users
---

### Post by MintoTook on 2006-06-23
Right now I'm in the process of getting X.org running on a SunBlade 100 in my office and its not going very easily.

This used to be a computer lab machine so the following specs are a best guess:
[LIST]
[*]Sun PGX64 graphics card
[*]Sun 17" monitor
[*]Ubuntu Dapper
[/LIST]
X.org detects the graphics card and suggests the ati driver (the PGX64 is ATI RageXL-based for those who didn't know) and the monitor can do 1280x1024 @ 75 Hz so I selected 1280x1024 @ 60 Hz when configuring X.org since I didn't know the exact vertical and horizontal refresh rates.

So using the ati driver and telling X.org that the monitor can handle 1280x1024 @ 60 Hz, I'm getting monitor out of sync errors when starting Window Maker.  Are there any suggestions from anyone whose gotten Dapper to work on their SunBlade 100's or helpful comments?

/update:  I now have discovered that the monitor can actually only do 1024x768 (possibly 1152x900) with v-sync from 50-160 Hz and h-sync from 30-75 kHz.

/update 2:  Success!  After much googling, the following option is required under the "Device" section:
     Option      "ReferenceClock" "29.500MHz"

---

### Post by netztier on 2006-06-26
[QUOTE=MintoTook][LIST]
[*]Sun PGX64 graphics card
[*]Sun 17" monitor
[*]Ubuntu Dapper
[/LIST]
[/QUOTE]

Out of interest: which driver module are you using with that graphics card? Would you mind posting the Device section of your /etc/X11/xorg.conf file?

I wondered if it were possible to use ATI's flglrx with these cards and if it offered any benefits over X.org's module.

kind regards

Marc

---

### Post by hw-tph on 2006-06-26
[QUOTE=netztier]I wondered if it were possible to use ATI's flglrx with these cards and if it offered any benefits over X.org's module.[/QUOTE]

As far as I know, ATI offers no Linux drivers (fglrx) for the SPARC platform, only for x86 and x86_64. So getting a Sun/ATI card working on SPARC using fglrx should be impossible unless you have access to some secret SPARC ATI drivers. :)


Håkan

---

### Post by netztier on 2006-06-26
[QUOTE=hw-tph]So getting a Sun/ATI card working on SPARC using fglrx should be impossible unless you have access to some secret SPARC ATI drivers. :)
[/QUOTE]

Of course. Sometimes putting one's own mind in gear before letting the fingers touch the keyboard might help to avoid looking a bit stupid.  I had in fact thought about this before and eventually did come to the same conclusion.

"We apologize for the inconvenience"

kind regards

Marc

---

### Post by gaurab on 2006-07-09
Minto, I am also having the same problem on the machine I am trying to load Ubuntu.

The configuration is (much simillar to that of yours)

SunBlade 2000
Sun 17 inch monitor
UltraSparcIII+
PGX64

I was not being able to configure the X server.
I tried to do
```
sudo dpkg-reconfigure xfee-xorg
```

and selected the same optionsa as you did.

I also changed the "option" under the devices section. But apprantly am still unable to configure my X server. Please Advice.

Thanking you in advance
Gaurab

---

### Post by allnameswereout on 2006-07-12
> **hw-tph said:**
> As far as I know, ATI offers no Linux drivers (fglrx) for the SPARC platform, only for x86 and x86_64. So getting a Sun/ATI card working on SPARC using fglrx should be impossible unless you have access to some secret SPARC ATI drivers. :)


Håkan

True. However for 2D you don't need the proprietary drivers.

There is an opensource driver for some (older) cards of the Radeon series. This code has IIRC been imported in the appropriate project but i'm not sure which version of X.org has it.

[http://r300.sourceforge.net](http://r300.sourceforge.net)

An overview on ATI cards is here

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units)

But it doesn't contain info on wether theres an OSS driver available.

You also cannot assume these drivers are tested on SPARC hardware.

---

### Post by arkham on 2006-08-16
> **MintoTook said:**
> 

/update 2:  Success!  After much googling, the following option is required under the "Device" section:
     Option      "ReferenceClock" "29.500MHz"

Well, my googling led me here and this was the exact change needed - many thanks :D

---

