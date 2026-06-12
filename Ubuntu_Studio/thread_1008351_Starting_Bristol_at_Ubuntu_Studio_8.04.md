---
title: "Starting Bristol at Ubuntu Studio 8.04?"
date: 2008-12-11
forum: Ubuntu Studio
---

### Post by kohina on 2008-12-11
Hello everyone, I have successfully used a few weeks Ardour and Rosegarden.
I installed Bristol normally from repos, thought no menu entry appeared.
Here is what I get when trying to launch from console:

```
:~$ bristol
	You may want to make bristolengine a suid-root executable
spawning midi thread
	flags are 8a000000
midi sequencer
Returning socket 3
Opened listening control socket: 5028
Client ID = 129
Queue ID = 1
Device name did not parse, defaults 128.0
Cannot subscribe port 0 from client 128: Operation not permitted
Error opening midi device /dev/midi, exiting midi thread
Could not get thread schedule
parent going into idle loop
connected to :0.0 (80f82f0)
display is 1024 by 768 pixels
Window is w 1024, h 768, d 24, 0 0 0
Using TrueColor display
masks are ff0000 ff0000 ff0000
INIT: 80f8008
Initialise the mini link to bristol: 80ff1e8
parent exiting
hostname is localhost, bristol
port is 5028
connect failed: Connection refused
connfailed
opening link to engine: -1
hostname is localhost, bristol
port is 5028
connect failed: Connection refused
connfailed
cleanupBristol(-4)

```

Any help appreciated.

---

### Post by seanbutnotheard on 2008-12-12
You'll want to start Bristol via the startBristol script.  Also, with the Bristol version packaged in Ubuntu, you'll have to tell bristol to use ALSA explicitly, otherwise it defaults to OSS:

startBristol -audio alsa -midi alsa -{the synth you want to start}

See the Bristol man page for more details (man bristol).  Also if you know how, I'd recommend compiling the latest version from the Bristol site... there have been a lot of features added, like JACK support, which you can invoke like this (after starting JACK):

startBristol -audio jack -rate {JACK's sample rate, e.g. 48000} -count {JACK's period size, e.g. 1024} -midi jack -{synth}

---

