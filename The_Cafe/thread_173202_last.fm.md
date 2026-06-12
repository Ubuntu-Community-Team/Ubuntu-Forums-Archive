---
title: "last.fm"
date: 2006-05-10
forum: The Cafe
---

### Post by tikal26 on 2006-05-10
"I am tryiong to install the lastfm player on my kubuntu breezy, but nothing work I keep on getting a crash. I figures that I am probably not the only one that uses lastfm so I am just wondering if anyone has it working and how they did it?

---

### Post by briancurtin on 2006-05-10
do you specifically want to use the last.fm player, or do you just want to be able to report your usage to last.fm? several applications, like rhythmbox and listen, have last.fm capabilities.

if you are dead set on the last.fm player, then stick with it, but check out the support forums...

---

### Post by tikal26 on 2006-05-10
I menat it to listen to the recommended radio. I can't get it to work?

---

### Post by dolny on 2006-05-10
The player works for me in Dapper.

---

### Post by TeeAhr1 on 2006-05-10
I have the player on my machine and it works perfectly, but I use Gnome.  Where are you crashing out, on the install or run?  What message(s) do you get?

---

### Post by mostwanted on 2006-05-10
Here's a Gnome alternative (uses Gtk so it looks nicer as well). Does the same thing:

[http://www.o-hand.com/~iain/last-exit/last-exit-0.2.tar.bz2](http://www.o-hand.com/~iain/last-exit/last-exit-0.2.tar.bz2)

---

### Post by cbudden on 2006-05-10
Change the sound output to OSS rather than ALSA.  Fixed it for me.

---

### Post by barsanuphe on 2006-05-10
[QUOTE=cbudden]Change the sound output to OSS rather than ALSA.  Fixed it for me.[/QUOTE]
same here.

---

### Post by tikal26 on 2006-05-10
how do you change the sound to OSS
this is the erro message I get
Changing station!
 Using ALSA!
 Supports 16 bit
 
 RtApi: no devices found for given stream parameters:
 RtApiAlsa: error setting sample rate (44100) on device (hw:CK804,0): Invalid argument.
 RtApiAlsa: pcm device (hw:CK804,1) won't open: No such file or directory.
 RtApiAlsa: error setting sample rate (44100) on device (hw:CK804,2): Invalid argument.
 
 
 Segmentation fault


edit:figured it out and that works

---

### Post by cbudden on 2006-05-10
Click the settings icon (spanner) then click settings, then under the sound section, change it to OSS.

---

### Post by WildTangent on 2006-05-10
Can't install the Gnome version on dapper, ./configure stops here:
```
checking for LASTEXIT... configure: error: Package requirements (gconf-2.0  gdk-pixbuf-2.0                   gtk+-2.0 >= 2.6                 gstreamer-0.10 >= 0.10.0                gstreamer-base-0.10  gstreamer-plugins-base-0.10 >= 0.10.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the LASTEXIT_CFLAGS and LASTEXIT_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
```

I should have everything it mentions there...but it doesn't think I do.

-Wild

---

### Post by banjobacon on 2006-05-10
[QUOTE=WildTangent]Can't install the Gnome version on dapper, ./configure stops here:
[/QUOTE]
You can find a deb package for Dapper here: [http://ubuntuforums.org/showthread.php?t=149018&highlight=last-exit](http://ubuntuforums.org/showthread.php?t=149018&highlight=last-exit)

It works for me, except for the sound being very choppy. I'm not sure if it's a bug or just a problem with me.

---

