---
title: "Jack won't start"
date: 2016-01-08
forum: Ubuntu Studio
---

### Post by bruce43 on 2016-01-08
Hi
Jack audio won't start, and i get this when i try to run it.

> [COLOR=#999999]12:39:21.021 Statistics reset.[/COLOR]
[COLOR=#cccc99]12:39:21.054 ALSA connection change.[/COLOR]
[COLOR=#999999]12:39:21.147 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
[COLOR=#66cc99]12:39:21.196 ALSA connection graph change.[/COLOR]
[COLOR=#ff0000]12:39:37.519 D-BUS: JACK server could not be started. Sorry[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
Fri Jan  8 12:39:37 2016: Starting jack server...
Fri Jan  8 12:39:37 2016: JACK server starting in realtime mode with priority 10
Fri Jan  8 12:39:37 2016: self-connect-mode is "Don't restrict self connect requests"
Fri Jan  8 12:39:37 2016: Acquired audio card Audio0
Fri Jan  8 12:39:37 2016: creating alsa driver ... hw:0|hw:0|256|3|44100|0|0|nomon|swmeter|-|32bit
Fri Jan  8 12:39:37 2016: Using ALSA driver HDA-Intel running on card 0 - HD-Audio Generic at 0xfeb44000 irq 29
Fri Jan  8 12:39:37 2016: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Fri Jan  8 12:39:37 2016: Released audio card Audio0
Fri Jan  8 12:39:37 2016: ERROR: Cannot initialize driver
Fri Jan  8 12:39:37 2016: ERROR: JackServer::Open failed with -1
Fri Jan  8 12:39:37 2016: ERROR: Failed to open server
Fri Jan  8 12:39:38 2016: Saving settings to "/home/bruce/.config/jack/conf.xml" ...
[COLOR=#ff0000]12:39:41.231 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock


Do anybody know what i should do?

---

### Post by bruce43 on 2016-01-13
Anybody...

---

### Post by marseille2 on 2016-01-15
(This will show your sound cards, so you can see which one/why the error message is talking about... which is card 0).
 
List the output of:

```
$ cat /proc/asound/cards
```

Also check out this [thread]("http://ubuntuforums.org/showthread.php?t=2269785&p=13248150#post13248150") on trouble-shooting Jackd, especially if you've got the pulseaudio jack [sinks]("http://packages.ubuntu.com/trusty/pulseaudio-module-jack") installed.

---

