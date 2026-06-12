---
title: "Can't get QJackCtl to start, even after killing pulseaudio in 14.10"
date: 2015-01-05
forum: Ubuntu Studio
---

### Post by plafonky on 2015-01-05
After killing Pulseaudio I try to start QJackCtl and it throws two errors and fails completely. Also I tried to look up the path " /org/freedesktop/ReserveDevice1/Audio0" and there is not even a /org/ directory.

Here's the error.


```

Mon Jan  5 12:38:56 2015: Starting jack server...
Mon Jan  5 12:38:56 2015: JACK server starting in non-realtime mode
Mon Jan  5 12:38:56 2015: self-connect-mode is "Don't restrict self connect requests"
Mon Jan  5 12:38:56 2015: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Mon Jan  5 12:38:56 2015: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Mon Jan  5 12:38:56 2015: ERROR: Audio device hw:0 cannot be acquired...
Mon Jan  5 12:38:56 2015: ERROR: Cannot initialize driver
Mon Jan  5 12:38:56 2015: ERROR: JackServer::Open failed with -1
Mon Jan  5 12:38:56 2015: ERROR: Failed to open server
Mon Jan  5 12:38:58 2015: Saving settings to "/home/pablo/.config/jack/conf.xml" ...
[COLOR=#ff0000]12:39:00.994 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started


```

All help is appreciated. Thank you very much.

---

### Post by unimatrixdoc2 on 2015-01-11
I've used qjackctl for a while now, maybe I can help.

1st: SETUP --> Settings --> check "Verbose messages"

2nd: SETUP --> Display --> set "Messages limit" to 5000
You could use SETUP --> OPTIONS --> Logging --> "Messages log file"

3rd: Under MISC --> check the following:
"Single Application Instance"
"Enable D-Bus interface"
"Stop JACK audio server on application exit"

4th: verify your user is in the groups: audio, pulse, pulse-access, rtkit.
Not sure exactly the specific groups needed, but these should do the trick.
Log out, and then log back in.

5th: Now launch qjackctl again and click start.
Paste the output of Messages to the following site:
[http://paste.ubuntu.com](http://paste.ubuntu.com)

Give me the link and I'll take a closer look. :)

---

