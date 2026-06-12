---
title: "Sound not working correctly"
date: 2008-09-09
forum: Ubuntu Studio
---

### Post by emu42 on 2008-09-09
I have recently installed Ubuntu, and the sound isn't working correctly. No matter what volume I set the sound to, it outputs full volume. In Rosegarden, the sound doesn't work at all.

I'm not sure whether this is a driver problem or I am not selecting the right device in the "Sound" management, or if my sound card is broken. Is this a common problem?

---

### Post by mazz0 on 2008-09-10
I'm not expert, but I had that myself (in Rthymbox I think, but I'm not sure,,,) when I had the wrong sound system selected.  I'm not sure why sound came out at all, come to think of it, but like I said - I'm not an expert (I've been using Ubuntu for months now and still haven't got my surround sound working!!:().

Check in System -> Preferances -> Sound and see what devices are selected, then look in the options for whatever programmes you're having problems with and make them the same as that one.  In my Sound settings it's set to Autodetect, which it may be in yours - I think the defualt is ALSA, but if not just try changing the sound device in your programme until you find one that works!

Did that help?

---

### Post by emu42 on 2008-09-11
No, it's still not working no matter which one I select in the sound settings. I tried other programs, and every program (except for Rosegarden) has the sound all the way up.

---

### Post by eye208 on 2008-09-12
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

---

### Post by emu42 on 2008-09-13
Thanks for the link. However, though I tried all it said exactly (set devices to ALSA, uncheck system sounds, uninstall pulseaudio, install esound, reboot), it didn't do anything but take away the system sounds.

---

### Post by mazz0 on 2008-09-14
Hmm, if the programmes aren't playing at the volume you've set your sound system to then they must be using a different system...  If you've definetly set them to ALSA then it stands to reason that it must be the volume changes that is being applied to the wrong sound system...

Right-click on the volume icon in your taskbar and select Open Volume Control and then click File -> Change Device.  Is it set to the correct one?  You could be playing through the right system but changing the volume on the wrong one, maybe?

---

### Post by emu42 on 2008-09-14
It's set to ALSA, which is what I'm playing the sound from. But you're right, the problem probably isn't the sound, but likely the volume control.

---

### Post by emu42 on 2008-09-17
Bump

Could I get this topic moved to the "Multimedia and Video" section? That forum is more active, and I might get some people who recognize my problem.

---

### Post by pqrs615 on 2008-09-17
**Nike Air Zoom Encore x Red Bull Shoes**

These are special Nike 6.0 sneakers developed for the Red Bull Music Academy. Fifty pairs of the Nike Air Zoom Encore shoes were laser engraved with the Red Bull logo and presented to lucky people during the RBMA event in Atlanta in May 2008. [Nike Shoes]("http://www.brandtrading.net/")

The toe box is light grey and has perforations. The mudguard at the toe cap is shiny blue while the mudguard between the toe cap and midsection is white leather. The Red Bull twin bulls logo is laser engraved on the white leather. The [Nike Shoes]("http://www.brandtrading.net/") lace is dark blue in color and it matches the shiny blue accent at the midsection of the shoe. The main midsection is in light grey. The Nike swoosh is in bright white and it stands out.

The back tab is a panel of shiny red leather that has &#8220;Nike&#8221; on it in yellow outlines. The base of the heel is also in shiny red leather. The midsole is white. The lower layer of the midsole is red for three quarters of the [Nike Shoes]("http://www.brandtrading.net/") while the base has an outline of yellow for its lower midsole. The inner sole is in dark blue. I like the use of blue accents as it provides a blue framework look for the shoe.

KeyWords: [Nike Shoes]("http://www.brandtrading.net/")

---

### Post by mazz0 on 2008-09-18
I don't know how to do that - if there's no edit option avaliable to you as thread creator I expect a forum admin would have to do it.  Might be easier creating a new thread with a link to this one in it (and a description too, as no-one's just going to click the link without knowing what it's about).

I think Ubuntu 8.10 is out at the end of next month - maybe it'll be fixed in that!

---

