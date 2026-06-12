---
title: "No gstreamer profile settings?"
date: 2012-03-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by screaminj3sus on 2012-03-04
Am I missing something, or is there no way to edit the gstreamer profile settings?

In rhythmbox and soundjuicer, I can select between the mp3/ogg/flac ect.. profiles, but the option to edit them isn't there. Is there anyway to do this in precise?

---

### Post by mc4man on 2012-03-04
Last I checked, (a couple of months ago), rhythmbox couldn't but sound-juicer could. 
Noticed today that it still wasn't fixed in rhythmbox so got around to filing a bug on. 
Didn't bother to check sound-juicer, probably should edit the report unless  there is an earlier one

[https://bugs.launchpad.net/bugs/945987](https://bugs.launchpad.net/bugs/945987)

---

### Post by screaminj3sus on 2012-03-04
The edit profiles button seems to be gone from soundjuicer:
[http://i.imgur.com/X57mX.png](http://i.imgur.com/X57mX.png)

---

### Post by mc4man on 2012-03-04
> **screaminj3sus said:**
> The edit profiles button seems to be gone from soundjuicer:
[http://i.imgur.com/X57mX.png](http://i.imgur.com/X57mX.png)

It certainly is gone, the changelog indicates a new upstream ..

So it was either removed because someone just decided to or they removed it because it wasn't doing anything..? (did work in 11.10) or there is some other less than obvious way to adjust the encoding parameters  

As far as rhythmbox it hasn't worked in 11.10 or 12.04

Maybe the target users really don't need such options?

Edit: the previous version of SJ did have the profile edit which works fine in 12.04
[https://launchpad.net/ubuntu/+source/sound-juicer/2.32.1+git20111010.2d5deeb-1](https://launchpad.net/ubuntu/+source/sound-juicer/2.32.1+git20111010.2d5deeb-1)

(and if you edit profiles with the older version, while those settings will stick, neither the new SJ or rhythmbox will use them

---

### Post by KozaG on 2012-04-25
> **mc4man said:**
> 
(and if you edit profiles with the older version, while those settings will stick, neither the new SJ or rhythmbox will use them

I'm also trying to figure out why there is no *edit profiles *option in new Sound Juicer. Does this all mean that they have removed it and the older versions, which had the option, doesn't work? Which other program I should use then to be able to rip .wav to .ogg and be able to configure kbps?

I'm using Ubuntu 12.04.

Thanks!

---

### Post by mc4man on 2012-04-25
> **KozaG said:**
> I'm also trying to figure out why there is no *edit profiles *option in new Sound Juicer. Does this all mean that they have removed it and the older versions, which had the option, doesn't work? Which other program I should use then to be able to rip .wav to .ogg and be able to configure kbps?

I'm using Ubuntu 12.04.

Thanks!
Pretty much anything But RB or sound-juicer
I use rubyrippere or abcde, additionally there is ripper-x, soundkonveter, banshee, asunder,  ect. ect.

RB will now only accept a preset,   it's fairly easy to create the .psr(s), some Examples here - mp3 VBR & CBR, vorbis
[http://ubuntuforums.org/showthread.php?t=1965432](http://ubuntuforums.org/showthread.php?t=1965432)

The gconf profile pipelines are still there if you run into something that will use it.

---

### Post by cryptotheslow on 2012-04-25
This is probably the wrong forum for this, but why, just why?

The Edit Profiles button in Sound Juicer was hardly obtrusive and the defaults were probably fine for most people, so no need for it to be any more obtrusive - it was just there should one want it.

Is it just a Gnome2 to Gnome3 transition thing?

I can still open a Terminal and run:
```
gnome-audio-profiles-properties
```

to edit the profiles and add new ones as before.

Is there actually something obstructing SJ from referencing them or was it a deliberate choice to just provide a limited bunch of set choices on format to rip to in the drop-down to aid the easily confused?

Removing choice is never a good thing in my book.

Hmm... just looked and it seems SJ is not a Canonical supported project so this post is probably not relevant here. Anyone know where to go to express this to the right people?

---

### Post by mc4man on 2012-04-25
AS far as sound-juicer it uses the same preset deal as Rhythmbox, actually has a rhythmbox.gep in /usr/share/sound-juicer/

So you'd do as I showed in link in previous post, except 1st edit in a
preset= 
in 
```
sudo gedit /usr/share/sound-juicer/rhythmbox.gep
```

If doing for both RB & S-J you must use the same preset name
(actually if already done in rhythmbox just replace the .gep in /usr/share/sound-juicer/ with the one from /usr/share/rhythmbox/

---

### Post by mc4man on 2012-04-25
Anyway - trying to get S-J included in the SRU-0 along with RB & hopefully new default presets for both  mp3 (VBR 2) & vorbis q @ 5 or maybe 6

Once the new .geps are in place then users can alter the parameters in ~/.gstreamer-0.10/presets/*  as desired using available gstreamer options/values

Obviously may not be as convenient as before, but that's the new gnome/gstreamer world
I'm sure someone can create a gui to edit these presets, maybe one of those tweak apps, not too difficult really

---

