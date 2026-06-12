---
title: "native instruments komplete audio 6 jack issues"
date: 2016-01-10
forum: Ubuntu Studio
---

### Post by thevmgas on 2016-01-10
[COLOR=#333333][FONT=Verdana][FONT=Lucida Grande]this has always been a plug and play device for me
all of a sudden jack does not recognize it from the usb port
it is recognized by alsa according to cadence so i closed cadence and when i check qjack it is not there and it is defaulting to the soundcard
i think i may have recently updated my low latency kernel and that could be the issue?
i tried booting with older versions of the 3.13 kernel but it doesnt seem to help
any ideas on solving this? it just seems strange that it will run if i choose alsa but not with jack

[/FONT]
[/FONT][/COLOR]
[vmgas]("https://linuxmusicians.com/memberlist.php?mode=viewprofile&u=12709") [COLOR=#000000]Posts:[/COLOR] 1[COLOR=#000000]Joined:[/COLOR] Sun Jan 10, 2016 10:08 pm
[LIST]
[*]
[/LIST]
[RIGHT][COLOR=#536482][FONT=Verdana][/FONT][/COLOR][/RIGHT]

---

### Post by thevmgas on 2016-01-10
when starting with cadence:
Sun Jan 10 22:30:21 2016: ------------------
Sun Jan 10 22:30:21 2016: Controller activated. Version 1.9.10 (unknown) built on Sat Oct 19 12:11:48 2013
Sun Jan 10 22:30:21 2016: Loading settings from "/home/cgi_hell/.config/jack/conf.xml" using expat_2.1.0 ...
Sun Jan 10 22:30:21 2016: setting parameter 'engine':'driver':'(null)' to value "alsa"
Sun Jan 10 22:30:21 2016: setting parameter 'drivers':'alsa':'capture' to value "hw:K6,0"
Sun Jan 10 22:30:21 2016: setting parameter 'drivers':'alsa':'playback' to value "hw:K6,0"
Sun Jan 10 22:30:21 2016: setting parameter 'drivers':'alsa':'hwmon' to value "false"
Sun Jan 10 22:30:21 2016: setting parameter 'drivers':'alsa':'inchannels' to value "2"
Sun Jan 10 22:30:21 2016: setting parameter 'drivers':'alsa':'outchannels' to value "2"
Sun Jan 10 22:30:21 2016: Listening for D-Bus messages
Sun Jan 10 22:30:23 2016: Starting jack server...
Sun Jan 10 22:30:23 2016: JACK server starting in realtime mode with priority 10
Sun Jan 10 22:30:23 2016: Acquired audio card Audio1
Sun Jan 10 22:30:23 2016: creating alsa driver ... hw:K6,0|hw:K6,0|1024|2|48000|2|2|nomon|swmeter|-|32bit
Sun Jan 10 22:30:23 2016: configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
Sun Jan 10 22:30:23 2016: ALSA: final selected sample format for capture: 32bit integer little-endian
Sun Jan 10 22:30:23 2016: ERROR: ALSA: cannot set channel count to 2 for capture
Sun Jan 10 22:30:23 2016: ERROR: ALSA: cannot configure capture channel
Sun Jan 10 22:30:23 2016: ERROR: Cannot initialize driver
Sun Jan 10 22:30:23 2016: ERROR: JackServer::Open failed with -1
Sun Jan 10 22:30:23 2016: ERROR: Failed to open server


i just tested with another audio interface and it was working fine so it has to just be the komplete audio 6 where the problem lies

---

