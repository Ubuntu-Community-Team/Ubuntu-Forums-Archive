---
title: "Can't get sound in Spotify"
date: 2010-12-12
forum: Wine
---

### Post by yelserpdog on 2010-12-12
I've just managed to get Spotify in Wine but I can't get any sound no matter what combination of options I choose in the audio config in Wine.

I've also tried getting spotify preview for Linux via the terminal using the instructions on Spotify's website but I keep getting the error message:

E: Unable to locate package spotify-client-qt
E: Unable to locate package spotify-client-gnome-support

Any help greatly appreciated. I've been away from Ubuntu for a few years so still very much a noob.

thanks

---

### Post by matthewbpt on 2010-12-12
What version of Ubuntu are you running? On 10.10 and 10.04 I didn't need any extra configuration, the sound worked OOTB, but before that I needed to set the sound driver as OSS in winecfg and then run spotify like this:

```
padsp wine '~/.wine/drive_c/Program Files/Spotify/spotify.exe'
```

Also I selected Hardware Acceleration in the sound options in Spotify.

---

### Post by yelserpdog on 2010-12-12
I'm using 10.10. The sound on everything else is fine, just spotify won't work. I've tried the command you gave but I get this message:

wine: cannot find '~/.wine/drive_c/Program Files/Spotify/spotify.exe'

I haven't tinkered with any of the Spotify settings and have done what the Spotify website said to get it going. I'm a paid subscriber if that makes any difference.

cheers

---

### Post by Spyderkid on 2010-12-23
You need to go into

Wine > Wine configuration > Audio THEN...

> Tick the ALSA driver
> choose Emulation on Hardware Acceleration
> Make the default sample rate 44100 (IF IT ISN'T ALREADY)
> Make the default bits per sample 16 (IF IT ISN'T ALREADY)

And then try again.
if it doesn't work then you will have to un-install and install again

_________________

And hey presto your dreams come true!

---

### Post by Zzl1xndd on 2010-12-23
They do have a preview version for Linux.

[http://www.spotify.com/int/download/previews/](http://www.spotify.com/int/download/previews/)

---

### Post by Spyderkid on 2010-12-23
> **tweakedenigma said:**
> They do have a preview version for Linux.

[http://www.spotify.com/int/download/previews/](http://www.spotify.com/int/download/previews/)

However you need subscription for it.


[SIZE="1"]You need to go into

Wine > Wine configuration > Audio THEN...

> Tick the ALSA driver
> choose Emulation on Hardware Acceleration
> Make the default sample rate 44100 (IF IT ISN'T ALREADY)
> Make the default bits per sample 16 (IF IT ISN'T ALREADY)

And then try again.
if it doesn't work then you will have to un-install and install again[/SIZE]

_________________

And hey presto your dreams come true!

---

