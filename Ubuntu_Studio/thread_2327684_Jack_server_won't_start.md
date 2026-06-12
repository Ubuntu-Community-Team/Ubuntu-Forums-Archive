---
title: "Jack server won't start"
date: 2016-06-13
forum: Ubuntu Studio
---

### Post by parkerfeagins on 2016-06-13
I just installed ubuntu studio. I cannot get the jack server to start. Any help at all would be greatly appreciated. 
 
 ```
 [COLOR=#999999]09:30:52.742 Statistics reset.[/COLOR]
 [COLOR=#cccc99]09:30:52.802 ALSA connection change.[/COLOR]
 [COLOR=#999999]09:30:52.971 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 [COLOR=#66cc99]09:30:53.064 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]09:30:55.694 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 Mon Jun 13 09:30:55 2016: Starting jack server...
 Mon Jun 13 09:30:55 2016: JACK server starting in realtime mode with priority 10
 Mon Jun 13 09:30:55 2016: self-connect-mode is "Don't restrict self connect requests"
 Mon Jun 13 09:30:55 2016: Acquired audio card Audio0
 Mon Jun 13 09:30:55 2016: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Mon Jun 13 09:30:55 2016: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Mon Jun 13 09:30:55 2016: ERROR: Cannot initialize driver
 Mon Jun 13 09:30:55 2016: ERROR: JackServer::Open failed with -1
 Mon Jun 13 09:30:55 2016: ERROR: Failed to open server
 Mon Jun 13 09:30:57 2016: Saving settings to "/home/parker/.config/jack/conf.xml" ...
 [COLOR=#ff0000]09:31:01.417 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 [COLOR=#ff0000]09:31:17.707 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 Mon Jun 13 09:31:17 2016: Starting jack server...
 Mon Jun 13 09:31:17 2016: JACK server starting in realtime mode with priority 10
 Mon Jun 13 09:31:17 2016: self-connect-mode is "Don't restrict self connect requests"
 Mon Jun 13 09:31:17 2016: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
 Mon Jun 13 09:31:17 2016: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
 Mon Jun 13 09:31:17 2016: ERROR: Audio device hw:0 cannot be acquired...
 Mon Jun 13 09:31:17 2016: ERROR: Cannot initialize driver
 Mon Jun 13 09:31:17 2016: ERROR: JackServer::Open failed with -1
 Mon Jun 13 09:31:17 2016: ERROR: Failed to open server
 Mon Jun 13 09:31:19 2016: Saving settings to "/home/parker/.config/jack/conf.xml" ...
 [COLOR=#ff0000]09:31:36.058 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock


```

---

### Post by kazakore on 2016-06-13
See my post on this similar thread. I'm not sure if it will help either of you but fingers crossed it can get you in the right direction...

[http://ubuntuforums.org/showthread.php?t=2327630](http://ubuntuforums.org/showthread.php?t=2327630)

---

### Post by parkerfeagins on 2016-06-15
Looked in settings and changed audio interface, it wasn't connected to a soundcard. biggest facepalm ever.

---

### Post by RobertoRecordo on 2017-03-02
I found this thread because :redface: I was a victim of the same cockpit error: my external USB device was unplugged: I had unplugged the device while running to see which names would be removed from the QjackCtl connection settings.

The thing that confused me, is that I expected it to work without the external device: it had worked when I first installed Ubuntu Studio 16.04.1 two days ago: I recall starting it, setting up a synth and virtual keyboard and getting sound via the built in sound card.

So, it seems like the real difficulty is that the QjackCtl settings were changed to use the external device, and because of the irregular shutdown of the program that even after a reboot the program only knew to look for the last sound card used.

I tested this and indeed, when I unplug the sound card, I can not get QjackCtl to work until I go into settings and change "Interface: to default, Then I will be able to start jack without errors even though the sound card it still disconnected. Of  course, plugging the sound card in does the trick as well, but I think it is a bug that when it can't find the last device it used that it does not try the default setting.

I hope this helps the next person that finds their way here!

-Rob

---

