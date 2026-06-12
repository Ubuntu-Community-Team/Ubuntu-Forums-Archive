---
title: "vocal effects in linux / JACK"
date: 2011-02-03
forum: Ubuntu Studio
---

### Post by MarWestermann on 2011-02-03
Hi,

I try to make music with ubuntu / JACK like DUB FX does with his hardware.
(for those who dont already know him: [http://www.youtube.com/watch?v=bioYs6oAD8g](http://www.youtube.com/watch?v=bioYs6oAD8g))

What I already have:
a looper (sooperlooper)
a vocoder (autotalent / vocoder) as LADSPA-Plugins

what I didn't manage yet:
does anyone have an idea, how I can change my voice in that way that it sounds like a bass line or a guitar (all the cool stuff dub fx does) (the most synth only have a MIDI input but none for audio) I also tried AMS and I get manage an echo or a delay.. but not to sound like this bass-thing.

Any suggestions would help

Thanks
Marco

---

### Post by cchhrriiss121212 on 2011-02-03
To get that bass sound, he has applied a pitch shifter, distortion and probably compression as well, which you should be able to find in some of the plugin FX packages in the repos. Load as many as you like into jack rack or some other plugin host. The packages to get  loads of plugins are shown here:
[http://ubuntuforums.org/showpost.php?p=10293219&postcount=6](http://ubuntuforums.org/showpost.php?p=10293219&postcount=6)
Beware that some of them are not all that great, and some might not work at all under the wrong settings.

You can also try Rakarrack which is designed for guitars but you could easily use it for vocals. It has a couple of down-shifted presets as well as many neat effects, although it can chew up your cpu on some settings.

---

### Post by AutoStatic on 2011-02-04
[http://www.youtube.com/watch?v=tusCeI1aQ4c](http://www.youtube.com/watch?v=tusCeI1aQ4c)

Qtractor can be used as a mixer to host plug-ins too. Works great for that purpose.

Best,

Jeremy

---

### Post by MarWestermann on 2011-02-05
Hi 

thank you for your answers. Both look great.. Rakarrack is very interesting. Also Qtraktor looks great

Best,
Marco

---

