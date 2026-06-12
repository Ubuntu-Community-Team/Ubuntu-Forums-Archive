---
title: "QJack - Jack Server Fails to Start"
date: 2012-07-27
forum: Ubuntu Studio
---

### Post by studiofreak on 2012-07-27
Right everything audio wise was working FINE with on board intel and m audio delta 1010 lt

then for some reason NOTHING I played around trying to fix this and found I ran the audio bug command that told me there was a problem with ALSA Base and to un install some 3rd party application as it couldn't continue

Sooooooooo I completely removed ALSA and all its parts then re installed and OSS,pulse audio and the envy24 Mudita24 etc and the audio is working but now jack wont start I get the following messages:


-------------------------------------------------------------------



Error - JACK Audio Connection Kit

D-BUS: SetParameterValue('driver:inchannels', '10'):

Parameter value type mismatch: was expecting 'i', got 'u'.
(org.jackaudio.Error.InvalidArgs)



---------------------------------------------------------------


Error - JACK Audio Connection Kit

D-BUS: SetParameterValue('driver:outchannels', '10'):

Parameter value type mismatch: was expecting 'i', got 'u'.
(org.jackaudio.Error.InvalidArgs)

--------------------------------------------------------------


Error - JACK Audio Connection Kit

D-BUS: JACK server could not be started.

Sorry


---------------------------------------------------------------

Error - JACK Audio Connection Kit

Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info


------------------------------------------------------------------

Also I made a script to try and fix this problem:

------------------------------------------------------------------

#load pulseaudio jack modules
#!/bin/bash

pactl load-module module-jack-sink 
pactl load-module module-jack-source

echo "set-default-sink jack_out" | pacmd
echo "set-default-source jack_in" | pacmd

------------------------------------------------------------------

named the file */ jack_startup /* and then set the permission to executable then I put that in home/scripts then ran that to start up with jack in jack settings etc and set the time out between 1k - 5k so I chose directly in the middle at 2.5k

------------------------------------------------------------------

I am completely baffled by this and I have no idea what is going on what so ever please could someone help?

Thanks :confused:

---

### Post by studiofreak on 2012-07-27
can anyone please help?

-------------------------------------------------------------------

04:53:51.168 Startup script terminated with exit status=32512.
04:53:51.176 D-BUS: SetParameterValue('driver:inchannels', '10'): Parameter value type mismatch: was expecting 'i', got 'u'. (org.jackaudio.Error.InvalidArgs)
Sat Jul 28 04:53:51 2012: [1m[31mERROR: Parameter value type mismatch: was expecting 'i', got 'u'[0m
Sat Jul 28 04:53:52 2012: Saving settings to "/home/*username*/.config/jack/conf.xml" ...
04:53:54.100 D-BUS: SetParameterValue('driver:outchannels', '10'): Parameter value type mismatch: was expecting 'i', got 'u'. (org.jackaudio.Error.InvalidArgs)
Sat Jul 28 04:53:54 2012: [1m[31mERROR: Parameter value type mismatch: was expecting 'i', got 'u'[0m
04:53:54.987 D-BUS: JACK server could not be started. Sorry
Sat Jul 28 04:53:54 2012: Starting jack server...
Sat Jul 28 04:53:54 2012: JACK server starting in realtime mode with priority 10
Sat Jul 28 04:53:54 2012: [1m[31mERROR: Cannot lock down 107302426 byte memory area (Cannot allocate memory)[0m
Sat Jul 28 04:53:54 2012: control device hw:1
Sat Jul 28 04:53:54 2012: control device hw:1
Sat Jul 28 04:53:54 2012: [1m[31mERROR: Failed to acquire device name : Audio1 error : Method "RequestRelease" with signature "i" on interface "org.freedesktop.ReserveDevice1" doesn't exist
[0m
Sat Jul 28 04:53:54 2012: [1m[31mERROR: Audio device hw:1,0 cannot be acquired...[0m
Sat Jul 28 04:53:54 2012: [1m[31mERROR: Cannot initialize driver[0m
Sat Jul 28 04:53:54 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Sat Jul 28 04:53:54 2012: [1m[31mERROR: Failed to open server[0m
04:53:56.196 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Sat Jul 28 04:53:55 2012: Saving settings to "/home/*user name*/.config/jack/conf.xml" ...

------------------------------------------------------------------


:confused:

---

