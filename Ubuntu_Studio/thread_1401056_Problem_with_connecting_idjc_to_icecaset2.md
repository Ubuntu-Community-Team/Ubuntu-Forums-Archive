---
title: "Problem with connecting idjc to icecaset2"
date: 2010-02-07
forum: Ubuntu Studio
---

### Post by Red_Unix on 2010-02-07
Hey i have icecast2 server running all smoothly and whatnot but idjc will not connect to the server. This is what i get

```
encoder_start: resampler will not be used
live_ogg_encoder_main: first pass of the encoder
live_ogg_build_metadata: metadata for encoder 0
artist=(null)
title=(null)
encoder_start: successfully started the encoder
streamer_connect: established connection to the server
streamer_main: busy, waiting for the server to grant access
streamer_main: connection failed, shout_get_error reports -3 No error
streamer_main: disconencting from server
encoder_unregister_client called
encoder_unregister_client finished
streamer_main: disconnection complete
encoder 0 running
failed to get server stats for tab 1
streamer_disconnect: function called while not streaming
command failed for command: server_disconnect
encoder_unlink: waiting for encoder to finish
live_ogg_encoder_main: cycle restart
live_ogg_encoder_main: writing final packet
live_ogg_encoder_main: last pass of the encoder, freeing libvorbis structures
live_ogg_encoder_main: libvorbis structures freed
live_ogg_encoder_main: performing cleanup
live_ogg_encoder_main: finished cleanup
encoder_stop: encoder is stopped

```
If you need more information to help diagnose the problem i will be sure to help.

---

### Post by StephenF on 2010-02-08
What version are you using?

---

### Post by Red_Unix on 2010-02-08
its ok now. i just uninstalled and reinstalled everything but right now only certain programs can play it like vlc and Mplayer. iTunes on my other computer wont play it and I'm planning to make an iphone site to access the stream from. I would like to stream it in mp3 but it says i need to install libmp3lame which i already have. All my software is up to date as well.

---

### Post by Red_Unix on 2010-02-08
Heres my stream btw
[http://192.168.1.105:8000/](http://192.168.1.105:8000/)

---

### Post by StephenF on 2010-02-09
It sounds to me like you are using an old version of IDJC. 0.8.1 is the latest version.

---

### Post by Red_Unix on 2010-02-09
WOW thank you! Everything now works!

---

