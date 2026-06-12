---
title: "Audio Compression"
date: 2010-10-01
forum: Ubuntu Studio
---

### Post by oldmankit on 2010-10-01
I was watching a film last night (using VLC) and was jumping up and down to turn the volume up (for quiet dialogue) and down (for explosions etc.).  It was late at night and I didn't want to bother the neighbours in my apartment.

VLC doesn't have anything that will enable me to compress audio on-the-fly.  I'm not talking about re-encoding the audio track with compression.  

I've done a little research and JACK was mentioned.  Before I get into that whole territory, could someone confirm (and perhaps give a few pointers) about whether it's feasible to get that set-up on a laptop with no special sound cards or anything?  And will I be able to get my compression for movies?

Thanks all.

---

### Post by mas_sergio on 2010-10-02
you know... that's a problem I've had with certain videos as well. One part everyone is quite and talking low then next out of no where *BOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOM*.... and i just woke everyone up. Most of the time I tend to use headphones when watching stuff at night time. It would be nice to see a feature like that in VLC. Maybe if somehow you can get VLC to run through JACK and then reroute it's audio channels into CALF JACK HOST and apply a Audio Compressor in there and reroute it (with effects) back to SYSTEM for live play (no encoding needed). IF big IF you can do that it should solve your problem but I don't think VLC can be used in Jack or did they change that already? lol

hmm... this in theory i don't think it will work but AUDACITY can be used in JACK. Perhaps if Audacity routed the audio to jack(since it can record system wide) but jack would have stopped VLC's audio capabilities at start up right? then this would be a no no... unless you find some way around i duno just offering advice but what your asking for may not be possible and then again this is linux half of what ubuntu does today was impossible in the past so yeah...i'll end it like that lol.

---

### Post by Pablo_F on 2010-10-02
You can try jack with your onboard card. I think it will work, once you get the realtime and memlock privileges. To "jackify" some popular multimedia players, including VLC, see:

[http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507](http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507)

Then you can use jack-rack as a host for ladspa (audio effects) plugins. Install jack-rack and ubuntustudio-audio-plugins for starters. One of those plugins could fit your needs. SC3 maybe.

Use the connection window of qjackctl (or patchage) to make virtual connections between VLC, jack rack and the system: playbacks (your card's outs).

Cheers! Pablo

---

### Post by JC Cheloven on 2010-10-02
Also, I'd suggest to try the calf compressor. Once your jack setup is ready, install the package calf-plugins, and use the "Calf Plugin Pack for JACK" (will appear in your sound menu) within jack. There is a nice compressor, among a few more decent-quality effects. 

JC

---

### Post by oldmankit on 2010-10-04
Thanks for the advice.  I really look forward to being able to try out these compressors.  But alas, I can't get JACK going.  

I've spent about an hour reading through various guides and trying a few different settings.  JACK seems to open OK, starts OK, I connect up what I suppose should be connected, but, alas, nothing comes out through my headphones.  When I stop JACK, sound comes back.

I've attached a screenshot to shed some light on my set-up.  I really do appreciate any help.

---

### Post by Pablo_F on 2010-10-04
Hi, 

VLC ports are not present in your screenshot. You have to jackify VLC. 

As a proof of concept, try aqualung, a simple audio player which works out of the box with jack.

sudo apt-get install aqualung

But then go and follow the guide in the link of my previous post to jackify VLC.

I personally prefer mplayer. I think it behaves better with jack. 

You don't need monitor ports. You need to connect:

player --> plugin host with a compression plugin loaded --> system: playbacks

[IMG]http://img266.imageshack.us/img266/3171/pantallazopatchage1.png[/IMG]

Increase the frames/period value so you don't have xruns.

Cheers! Pablo

---

### Post by cchhrriiss121212 on 2010-10-04
VLC has a normalisation effect that you may want to try out before fiddling with jack.

---

### Post by oldmankit on 2010-10-04
@cchhrriiss121212
I didn't know about VLC's normalisation, but it's still not the compression I wanted...

> **Pablo_F said:**
> VLC ports are not present in your screenshot. You have to jackify VLC. 

Ah, I didn't read your first post properly.  It's working now.  Thank you!  I'm a happy man.

I've attached a screenshot for no particular reason.  I'm just happy that I'm able to do this.  I've wanted to do this kind of thing for quite a while now!

---

### Post by oldmankit on 2010-10-28
Not sure whether to start a new thread or continue this one.

What you guys have helped me set-up so far is good and has helped with our movie watching.

Now of course I want more.  Does anyone know of a way to get a **multiband** compressor in ubuntu?

---

### Post by Pablo_F on 2010-10-29
Hi, the calf plugins suite has a multiband compressor. See image attached. I am not sure if the packaged version has it though. In this case, you could compile the source from the git repo.  Check

[http://calf.sourceforge.net/](http://calf.sourceforge.net/)

Feel free to ask if you get stuck.

You can also try jamin which it is in the repos. It is conceived as a mastering tool, but it could be an option.

Cheers! Pablo

---

### Post by oldmankit on 2010-11-01
> **Pablo_F said:**
> Hi, the calf plugins suite has a multiband compressor. See image attached. I am not sure if the packaged version has it though. In this case, you could compile the source from the git repo.  Check

[http://calf.sourceforge.net/](http://calf.sourceforge.net/)

Feel free to ask if you get stuck.

You can also try jamin which it is in the repos. It is conceived as a mastering tool, but it could be an option.

Cheers! Pablo

Pablo,

that looks awesome.  I couldn't see that plugin at [http://calf.sourceforge.net/?id=3](http://calf.sourceforge.net/?id=3).  Is it an experimental plugin?  

I've downloaded the source. It doesn't seem to want to let me work with JACK.  When I do ./configure, it gives me:
```
    Calf configured

    Debug mode:             no
    Experimental plugins:   no
    LADSPA enabled:         yes
    DSSI enabled:           yes
    DSSI GUI enabled:       no
    LV2 enabled:            no
    LV2 GUI enabled:        no
    JACK host enabled:      no
    LASH enabled:           no
    Old-style JACK MIDI:    no

    Installation prefix:    /usr/local

```despite showing
```
checking jack/jack.h usability... yes
checking jack/jack.h presence... yes
checking for jack/jack.h... yes
checking for GLIB_DEPS... yes
checking for JACK_DEPS... yes
checking for jack_port_register in -ljack... yes
checking for JACK_MIDI_DEPS... yes

```I've done all I could to check I have the right dependencies.  What am I doing wrong?

---

### Post by Pablo_F on 2010-11-01
Hi, 

You need the source from the git repo (under development, not officially released). The stable sources don't feature the multiband compressor, even if you configure with experimental enabled. So you need to:

sudo apt-get install git-core
git clone [http://repo.or.cz/r/calf.git](http://repo.or.cz/r/calf.git)
cd calf

Now, to build the plugins, you need to sudo apt-get install these adittional packages (I think this will do it for you at this stage):

lv2core libglade2-dev liblash-dev libfluidsynth-dev libgconf2-dev

Now, do a:

./autogen.sh

If all goes OK:

make
sudo make install

I think this is all, but again , feel free to ask if you encounter problems.

If something is wrong after a "make", don't forget to do a "make clean".

For bug reports, comments... contact the devs. This is bleeding edge.

Cheers! Pablo

---

### Post by oldmankit on 2010-11-01
> **Pablo_F said:**
> Hi, 

You need the source from the git repo (under development, not officially released). The stable sources don't feature the multiband compressor, even if you configure with experimental enabled. So you need to:

sudo apt-get install git-core
git clone [http://repo.or.cz/r/calf.git](http://repo.or.cz/r/calf.git)
cd calf

Now, to build the plugins, you need to sudo apt-get install these adittional packages (I think this will do it for you at this stage):

lv2core libglade2-dev liblash-dev libfluidsynth-dev libgconf2-dev

Now, do a:

./autogen.sh

If all goes OK:

make
sudo make install

I think this is all, but again , feel free to ask if you encounter problems.

If something is wrong after a "make", don't forget to do a "make clean".

For bug reports, comments... contact the devs. This is bleeding edge.

Cheers! Pablo

It's good that I asked - I never would have found may way through that.  I didn't know what 'git' was.

All good up until ./autogen.sh.  I get
```
./autogen.sh: 2: aclocal: not found
./autogen.sh: 3: libtoolize: not found
./autogen.sh: 4: autoheader: not found
./autogen.sh: 5: autoconf: not found
./autogen.sh: 6: automake: not found
./autogen.sh: 9: ./configure: not found
```Thanks again for your help.

---

### Post by Pablo_F on 2010-11-02
Hi, You need at least:

build-essential autotools-dev automake libtool

Cheers! Pablo

---

### Post by oldmankit on 2010-11-02
Wonderful.  Thank you very much.

I thought I might not ever get this to work, and now it's going nicely.  This is great.  I've tested it with a movie, and it really helps bring down the deafening parts whilst keeping dialogue  at a good level.  Also, with some classical recordings this multiband compressor really improves the overall sound.  Lovely!

:guitar:

---

### Post by daniel_san on 2011-05-14
Thank you guys! Though this thread is somewhat old, it just helped me a lot at getting jack + calf multiband compressor + mplayer running!

---

### Post by oldmankit on 2011-11-02
Should I start a new threat because this is so old?

I've just installed 11.10 and would love to have my old multiband compressor back.  I tried the repo calf-plugins but the multiband compressor is still not in it.  Back to the git version.

Things have changed.  liblash-dev is no longer in the repos, I had to install liblash-compat-dev.  

The git repository you linked to ([http://repo.or.cz/r/calf.git](http://repo.or.cz/r/calf.git)) doesn't seem to respond any more.  I found a new one here: (git://calf.git.sourceforge.net/gitroot/calf/calf)

The autogen script and make both worked, but when I did sudo checkinstall, I got these errors:
```
========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/kit/downloads/linux/calf/calf/src'
Making install in calf
make[2]: Entering directory `/home/kit/downloads/linux/calf/calf/src/calf'
make[3]: Entering directory `/home/kit/downloads/linux/calf/calf/src/calf'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/kit/downloads/linux/calf/calf/src/calf'
make[2]: Leaving directory `/home/kit/downloads/linux/calf/calf/src/calf'
make[2]: Entering directory `/home/kit/downloads/linux/calf/calf/src'
make[3]: Entering directory `/home/kit/downloads/linux/calf/calf/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c calfjackhost '/usr/local/bin'
libtool: install: warning: `calf.la' has not been installed in `/usr/local/lib/ladspa/'
libtool: install: /usr/bin/install -c .libs/calfjackhost /usr/local/bin/calfjackhost
test -z "/usr/local/lib/calf" || /bin/mkdir -p "/usr/local/lib/calf"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   calf.la '/usr/local/lib/calf'
libtool: install: /usr/bin/install -c .libs/calf.so /usr/local/lib/calf/calf.so
libtool: install: /usr/bin/install -c .libs/calf.lai /usr/local/lib/calf/calf.la
libtool: install: /usr/bin/install -c .libs/calf.a /usr/local/lib/calf/calf.a
libtool: install: chmod 644 /usr/local/lib/calf/calf.a
libtool: install: ranlib /usr/local/lib/calf/calf.a
ranlib: could not create temporary file whilst writing archive: No more archived files
make[3]: *** [install-pkglibLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/kit/downloads/linux/calf/calf/src'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/kit/downloads/linux/calf/calf/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/kit/downloads/linux/calf/calf/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```I have no idea how to proceed.  Please help!

---

