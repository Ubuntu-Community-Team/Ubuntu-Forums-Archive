---
title: "[SOLVED] M-Audio Delta 1010LT + Audacity"
date: 2008-12-01
forum: Ubuntu Studio
---

### Post by euphonism on 2008-12-01
Simply trying to record from H/W ln 3 and 4 with an M-Audio Delta 1010LT and Audacity but no input is recorded. Have set both lines to capture and have maxed their volumes with alsamixer. In Audacity, Audio I/O recording device is set to ALSA: M Audio Delta 1010LT: ICE1712 and Channels: 2 (Stereo) is selected. When running arecord -l the following output is given:
```

**** List of CAPTURE Hardware Devices ****
card 0: M1010LT [M Audio Delta 1010LT], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M5461 [HDA ULI M5461], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Have been searching all morning for a solution to no avail. I'm using Ubuntu 8.10 AMD64. I'd appreciate any help!

---

### Post by thorgal on 2008-12-01
you should use envy24control for your h/w mixer app.
You will find some ADC and DAC faders for each channel. Make sure ADCs are up.

---

### Post by euphonism on 2008-12-01
Ok - I've installed envy24control from the alsa-tools package; have maxed out my ADC and DAC levels and have checked all other levels as well. Everything looks good from the control panel yet I'm still getting no input in Audacity when I try to record.

Little update: there actually is something being recorded, but even with all volume levels at max it's barely audible and the waveform appears static. However, the Every24 Control Utility seems to displaying the correct input levels.

---

### Post by thorgal on 2008-12-01
I never used that card with audacity and ALSA but it wouldn't surprise me that this is unfortunately a problem with audicity interfacing with the ALSA layer.

I used to own a D1010LT that I used with jackd and ardour.
It may be a bit too much for your needs, but once things are set up correctly with jackd (the pro audio server), things are quite easy and work as they should. 

You could try to install qjackctl, set up jackd through it (in particular, make sure the sample rate used by jack matches the one you chose in envy24control) and launch it, even in non realtime mode. 

Then fire up ardour, create a stereo track, set its inputs to system:capture_2 and 3 (if you do want to record in stereo since the Delta inputs are mono), arm it for recording, arm the main transport for recording as well and press the transport play button.

---

### Post by euphonism on 2008-12-01
Upon your suggestion I installed Jack and Ardour. After about a half an hour of head-scratching familiarization, I've recorded and exported a WAV successfully. The only problem that remains is my confusion with playback in Ardour. Under output options I see no place to select my system sound card for playback, and as such, cannot listen to recordings within Ardour. Nevertheless, I'm really just ecstatic to be able to record again. Thanks for all your help thorgal!

---

### Post by tgalati4 on 2008-12-01
I have a Delta66 card which is somewhat similar.  It's been a while since I've recorded with it, but as I recall, I had to change my patch panel to get playback.  So you have one set of patches to record and another set for playback.  This is painful, because you have to switch back and forth between recording and playing back.  It's not bad for a dedicated 2-hour recording session.  If you are mixing and editing during a recording session (say recording a vocal track), then it's a pain.

I was able to record beyond channels 1+2 with the card using ALSA and Audacity, but you have to get creative with the patch panel and I think you have to record 4 tracks in audacity (even though 1+2 would be null).

---

### Post by thorgal on 2008-12-01
euphonism

Glad you succeeded, sort of :)

About jackd :

jackd is the audio handler. It interfaces with the lower layer, which for you is ALSA (jackd uses the ALSA backend in this context).

Jackd creates inputs and output ports corresponding to what your hardware provides through its ALSA driver.

So inputs are system:capture_n
outputs are system: playback_n

n being an integer.

When you set up jack in qjackctl, make sure you set your device to full duplex operations. In ardour, most tracks will default their outputs to the master bus, whose own outputs must be connected to (most of the time) system: playback_1 and system: playback_2. Of course, it all depends where you have your speakers plugged. 1 and 2 are usually a very common setup.

Now, if you have never heard about realtime audio operations, low latency, kernel patch from Ingo Molnar, etc, I invite you to search the forum for this info as it may give your system a much better performance. If you don't know too much about these concepts, there are numerous places on the net where you can read about them. It is worth it as you expand your recording and editing sessions into more complex projects. And if you stick to ardour and jack, you will be amazed :)

---

### Post by euphonism on 2008-12-01
> **thorgal said:**
> 
When you set up jack in qjackctl, make sure you set your device to full duplex operations. In ardour, most tracks will default their outputs to the master bus, whose own outputs must be connected to (most of the time) system: playback_1 and system: playback_2. Of course, it all depends where you have your speakers plugged. 1 and 2 are usually a very common setup.


Yeh, unfortunately my speakers are plugged into an onboard sound card as the M-Audio does not provide a connection to these ancient speakers (Boston Acoustics). And as far as I can tell, jack does not provide capabilities for utilizing two sound cards at once, so I think I'm out of luck until I get some new speakers. My current procedure has been: run jack --> record with ardour --> export as uncompressed wav --> edit with audacity --> export as compressed FLAC. I'm sure over time my operations will change but getting this simply to work was the final step in my transition to linux. The listed topics you provided are ones I am not too familiar with and as such I will indeed be educating myself over the next few days. Thanks again for the help :)

---

### Post by thorgal on 2008-12-02
euphonism,

with your current h/w setup, there's a way you can redirect ardour's outputs to your speakers ;)

Indeed, what you need is a netjack tool called alsa_out

let's say your onboard chip is the ALSA hw:0 and your Delta is hw:1 (could be the opposite, depends on how you configured your alsa loader). Anyway, onboard on hw:0 is a fine choice.

Now, what you see in the qjackctl connection window is your Delta card's IO ports.

However, the command line tool called alsa_out can display your onboard audio outputs (the tool 'alsa_in' can include the onboard inputs in the jack graph but you don't need it here).

I invite you to read this quick howto :

[http://trac.jackaudio.org/wiki/WalkThrough/User/AlsaInOut](http://trac.jackaudio.org/wiki/WalkThrough/User/AlsaInOut)

In your case, you would have to launch this command from the terminal:

alsa_out -d hw:0 -f 30000 -m 128

if hw:0 is your onboard chip. You can even give a different name, the default being 'alsa_out' in the jack graph.

Once you see the new playback ports in the graph, all you have to do is redirect ardour's master bus outputs to alsa_out: playback_1 and 2.

Neat isn't it ? :)

Read the howto, it will explain this better than me.

EDIT: by the way, I just tried it in my studio. I enabled the onboard sound (intel HDA), set it to hw:0 and shifted my RME system to hw:1.

To do this, you can as a superuser edit a text file in /etc/modprobe.d that you can call 'sound'

mine looks like this :
```

alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-hdsp
options snd-hda-intel index=0
options snd-hdsp index=1

```

save and reboot. Of course, you should replace hdsp by ice1712 or whatever module for your delta

Now, I start jackd with hw:1 (RME system). My qjackctl setting leads to this command :

/usr/bin/jackd -R -P 80 -dalsa -dhw:1 -r96000 -p128 -n2

where options mean :

-R : use realtime mode (you need elevated user privileges to do so, if you cannot yet due to lack of system configuration, don't use it for now)
-P : jackd audio thread priority, not relevant without -R
-dalsa : use ALSA backend
-dhw:1 : handle device indexed 1 by ALSA (my RME system)
-r96000 : sample rate to use 96kHz (matching the rate I configured with hdspconf, you would use envy24control for that)
-p128 : use 128 frames per period (rather low latency as resulting buffers will be short)
-n2 : use 2 periods per buffer, which yields a buffer of 256 (2 x 128 )

The default setting in qjackctl is -p1024 -n2 which is rather safe so you avoid buffer under/overruns, which are generically called xruns.

OK, this said, I have a development version of jackd which I compile myself (latest source code, no packaged version here) so I benefit from the latest inclusion of netjack into the jack tools. Consequently, I have alsa_in and alsa_out available.

I started alsa_out like this :
```

alsa_out -j onboard -dhw:0 -f 30000 -m 64 >& /dev/null

```

which means :
-j onboard : the name I want to give this jack client so that it appears as onboard in the jack graph
-dhw:0 : use my onboard chip outputs
-f 30000 : "catch factor" to improve the resampling quality (the intel chip is using 48kHz for the sampling rate)
-m 64 : maximum difference in frames that I allow between both cards (I think that's what it means)

and the final >& /dev/null means that I redirect all screen outputs of alsa_out to the unix black hole :D because alsa_out is outputting quite some stuff, useful for monitoring performance but annoying in general

I then played a wav file with mplayer like this:

```

mplayer -ao jack:port=system file.wav  

```
It outputs to my normal speakers (RME outputs to studio speakers)
```

mplayer -ao jack:port=onboard file.wav

```
It outputs to my test el-crappo speakers plugged to the outputs of my onboard sound.

It works beautifully :)

Good luck!

---

### Post by euphonism on 2008-12-03
Ok, I followed you up to the alsa_out section. Even after building the latest release (0.115.6), which I thought included alsa_in and out I am getting "bash: alsa_out: command not found". Have scoured the web and forums a bit and really can't find any information on installing alsa_in and alsa_out (other than that they are tools included in the netjack package which looks a bit outdated). I'm at a bit of a loss :-k

---

### Post by thorgal on 2008-12-03
Hello, don't give up, it may be an installation issue or a $PATH problem.
where did you install your compiled jack suite ?

and in the jack source dir, what do you see in the tools subdir ?

---

### Post by euphonism on 2008-12-03
I extracted the files to my user directory (/home/xxx where xxx is my username) into a folder called "jack-audio-connection-kit-0.115.6". From there I did ./configure, make, and sudo make install. Installation seemed smooth and jackd gives the following output:

```
jackd 0.115.6
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


usage: jackd [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
             [ --name OR -n server-name ]
             [ --no-mlock OR -m ]
             [ --unlock OR -u ]
             [ --timeout OR -t client-timeout-in-msecs ]
             [ --port-max OR -p maximum-number-of-ports]
             [ --debug-timer OR -D ]
             [ --verbose OR -v ]
             [ --clocksource OR -c [ c(ycle) | h(pet) | s(ystem) ]
             [ --replace-registry OR -r ]
             [ --silent OR -s ]
             [ --version OR -V ]
             [ --nozombies OR -Z ]
         -d backend [ ... backend args ... ]
             The backend can be `alsa', `coreaudio', `dummy',
                                `freebob', `oss', `sun', or `portaudio'.

       jackd -d backend --help
             to display options for each backend
```

So I assume I'm using the correct version. Files found in the tools directory (/jack-audio-connection-kit-0.115.6/tools) include the following:

```
/jack-audio-connection-kit-0.115.6/tools$ ls
alias.c           connect.c    ipunload.c   monitor_client.c  transport.c
alsa_in.c         evmon.c      lsp.c        netsource.c       tw.c
alsa_out.c        freewheel.c  Makefile.am  time_smoother.c
capture_client.c  ipload.c     Makefile.in  time_smoother.h
```

---

### Post by thorgal on 2008-12-03
I see. You're using the official release ... I use the SVN source code. But never mind, it may well be because the ./configure step has an option that should be enabled explicitely to include the netjack tools.

If not, I believe it's because some Makefile seed (Makefile.am) does not contain the tools directory. One way or another, the simple configure && make && sudo make install is not enough. Your tools directory listing shows me that nothing has been compiled.

This is rather strange. So I propose two things :

1- if you are eager to continue, you will have to pick the SVN code which is about to be released (v0.116). But then, you will have to uninstall what have installed, and moreover, uninstall the jackd package from synaptic or apt-get that sits in /usr instead of /usr/local. This will avoid headaches due to some runtime lib directory issue (LD_LIBRARY_PATH). When you configure the svn code, you will have to use ./configure --prefix=/usr
The jack API and ABI have not changed since 0.109.2 I think, so all your existing jack clients will work OOB :) 

2- wait for tomorrow or Friday as Paul Davis just said on the jack mailing list that 0.116 would be released by then.


About the main Makefile.am (in the top source dir), inspect the file and see if it contains this line :

DIST_SUBDIRS = config jack libjack jackd drivers example-clients tools doc

which includes the tools subdir.

---

### Post by euphonism on 2008-12-03
Although I am eager, I think I'll play it safe and just wait for the official release. The Makefile.am contains the following code:

```
MAINTAINERCLEANFILES    = Makefile.in

if HAVE_SNDFILE
JACKREC = jackrec
dist-check-sndfile:
else
JACKREC =
dist-check-sndfile:
	@echo
	@echo ' ******' You need sndfile installed to make dist.' ******'
	@echo
	@false
endif

if HAVE_READLINE
JACK_TRANSPORT = jack_transport
dist-check-readline:
else
JACK_TRANSPORT =
dist-check-readline:
	@echo
	@echo ' ******' You need readline installed to make dist.' ******'
	@echo
	@false
endif

if HAVE_SAMPLERATE
NETJACK_TOOLS = jack_netsource
if HAVE_ALSA
NETJACK_TOOLS += alsa_in alsa_out
endif
dist-check-readline:
else
NETJACK_TOOLS =
dist-check-readline:
	@echo
	@echo ' ******' You need libsamplerate installed to make dist.' ******'
	@echo
	@false
endif

bin_PROGRAMS = jack_load \
	       jack_unload \
	       jack_monitor_client \
	       jack_connect \
	       jack_disconnect \
	       jack_lsp \
	       jack_freewheel \
	       jack_evmon \
	       jack_alias \
	       $(JACKREC) \
	       $(JACK_TRANSPORT) \
	       $(NETJACK_TOOLS)

noinst_PROGRAMS = jack_thread_wait

if HAVE_SNDFILE
# note! jackrec_CFLAGS syntax not supported by automake-1.4
sndfile_cflags = @SNDFILE_CFLAGS@
endif

AM_CFLAGS = -I.. $(JACK_CFLAGS) $(sndfile_cflags)
AM_CXXFLAGS = -I.. $(JACK_CFLAGS) $(sndfile_cflags)

jack_connect_SOURCES = connect.c
jack_connect_LDFLAGS = @OS_LDFLAGS@
jack_connect_LDADD = $(top_builddir)/libjack/libjack.la

jack_disconnect_SOURCES = connect.c
jack_disconnect_LDFLAGS = @OS_LDFLAGS@
jack_disconnect_LDADD = $(top_builddir)/libjack/libjack.la

jack_monitor_client_SOURCES = monitor_client.c
jack_monitor_client_LDFLAGS = @OS_LDFLAGS@
jack_monitor_client_LDADD = $(top_builddir)/libjack/libjack.la

jack_thread_wait_SOURCES = tw.c
jack_thread_wait_LDFLAGS = @OS_LDFLAGS@
jack_thread_wait_LDADD = $(top_builddir)/libjack/libjack.la

jack_evmon_SOURCES = evmon.c
jack_evmon_LDFLAGS = @OS_LDFLAGS@
jack_evmon_LDADD = $(top_builddir)/libjack/libjack.la

jack_alias_SOURCES = alias.c
jack_alias_LDFLAGS = @OS_LDFLAGS@
jack_alias_LDADD = $(top_builddir)/libjack/libjack.la

jack_lsp_SOURCES = lsp.c
jack_lsp_LDFLAGS = @OS_LDFLAGS@
jack_lsp_LDADD = $(top_builddir)/libjack/libjack.la

jack_freewheel_SOURCES = freewheel.c
jack_freewheel_LDFLAGS = @OS_LDFLAGS@
jack_freewheel_LDADD = $(top_builddir)/libjack/libjack.la

if HAVE_SNDFILE
jackrec_SOURCES = capture_client.c
jackrec_LDFLAGS = @SNDFILE_LIBS@ @OS_LDFLAGS@
jackrec_LDADD = $(top_builddir)/libjack/libjack.la
endif

if HAVE_READLINE
jack_transport_SOURCES = transport.c
jack_transport_LDFLAGS = -lreadline @READLINE_DEPS@ @OS_LDFLAGS@
jack_transport_LDADD = $(top_builddir)/libjack/libjack.la
endif

#
# General purpose in-process loader/unloader
#

jack_load_SOURCES = ipload.c
jack_load_LDFLAGS = @OS_LDFLAGS@
jack_load_LDADD = $(top_builddir)/libjack/libjack.la

jack_unload_SOURCES = ipunload.c
jack_unload_LDFLAGS = @OS_LDFLAGS@
jack_unload_LDADD = $(top_builddir)/libjack/libjack.la

#
# Netjack slave tools
#
if HAVE_SAMPLERATE
jack_netsource_SOURCES = netsource.c $(top_builddir)/drivers/netjack/netjack_packet.c
jack_netsource_CFLAGS = -I$(top_srcdir)/drivers/netjack
if HAVE_CELT
jack_netsource_CFLAGS += -DHAVE_CELT
endif
jack_netsource_LDFLAGS = -lsamplerate @OS_LDFLAGS@
jack_netsource_LDADD = $(top_builddir)/libjack/libjack.la

if HAVE_ALSA
alsa_in_SOURCES = alsa_in.c time_smoother.c
alsa_in_LDFLAGS = -lasound -lsamplerate @OS_LDFLAGS@
alsa_in_LDADD = $(top_builddir)/libjack/libjack.la

alsa_out_SOURCES = alsa_out.c time_smoother.c
alsa_out_LDFLAGS = -lasound -lsamplerate @OS_LDFLAGS@
alsa_out_LDADD = $(top_builddir)/libjack/libjack.la
endif #HAVE_ALSA
endif #HAVE_SAMPLERATE

EXTRA_DIST = time_smoother.h

dist-hook: dist-check-sndfile
```

Doesn't look like it contains the line of code you were looking for. I suppose I'll have to go outside and enjoy this beautiful day - thanks again for all the help.

---

### Post by thorgal on 2008-12-03
that's what I suspected ... different stuff. Yeah, just wait, here in DK, it's utterly dark and cold and rainy / snowy ALL day long. Enjoy the sun! :)

---

### Post by kamlapati on 2008-12-31
I'm no expert, in fact I'm struggling myself to get my recording set up all working, but in my setup jack gives me the option of selecting different inputs and outputs from the default HW interface.

Using the **setup **option on Qjackctl it is on the right side, lower half, pull-down selector.

BTW, back to the original problem, I have found that my Audacity does not play that well with ALSA, and that all works OK if you directly select the input and output interfaces from the preferences control inside Audacity, but it doesn't work if you just use the ALSA mixer.

---

