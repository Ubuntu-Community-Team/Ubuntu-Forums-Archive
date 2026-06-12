---
title: "Only one connection to shoutcast-server with IDJC"
date: 2016-02-21
forum: Ubuntu Studio
---

### Post by alex9050 on 2016-02-21
Hi,
i'm using ubuntustudio 14.04 LTS. Packets are up to date.
For broadcasting I start the system with the lowlatency-kernel.

I do some radio-moderation for an internet radio via shoutcast. IDJC is working very fine, thanks to the author!
But: there is one issue, I'm not sure, where the mistake is:

At first start of IDJC after booting, everything is running very well, until: an error will happen on the stream server (seams, the stream server is a little bit instable, or somebody is fooling around there, anyway).
If the connection breaks, or even if the stream is occupied while trying to connect, IDJC will freeze, and nothing I tried, to start it again, without booting, would help. 

(sorry for my english :p )

I've made some loggings while starting IDJC via console:

1. normal start, no errors:

> xxx@ubuntustudio:~$ idjc
jack client ID: idjc_RxxxxDxxxxx
launching backend
backend launch attempt 1
started 1 encoders, 1 streamers, 2 recorders
player read buffer allocated for 1024 frames
awaiting reply
got idjc backend ready

threads initialised
jack sample rate is 48000
song title: 

activated ch 1
Toggle OFF recieved for signal: Listen
Restoring previous session
inter track fade was changed
Toggle ON recieved for signal: Listen
song title: 

stream-mon was toggled ON
20 JACK port connection(s) changed
jack connections saved

2. second start after normal disconnect:

> save_session called
encoder_start: initiating resampler(s)
encoder_start: successfully started the encoder
streamer_connect: established connection to the server
server [http://xxxx.xxxxx.de:12000](http://xxxx.xxxxx.de:12000) has 0 listeners
[Errno 32] Datenübergabe unterbrochen (broken pipe)
backend launch attempt 1
started 1 encoders, 1 streamers, 2 recorders
player read buffer allocated for 1024 frames
awaiting reply
got idjc backend ready

threads initialised
jack sample rate is 48000
streamer_disconnect: function called while not streaming
command failed for command: server_disconnect
encoder_stop: encoder is stopped
encoder_start: initiating resampler(s)
activated ch 1
encoder_start: successfully started the encoder
streamer_connect: established connection to the server
20 JACK port connection(s) changed
jack connections saved
streamer_main: connection failed, shout_get_error reports -4 No error
streamer_main: disconencting from server
encoder_unregister_client called
encoder_unregister_client finished
streamer_main: disconnection complete
streamer_disconnect: function called while not streaming
command failed for command: server_disconnect
encoder_plugin_terminate: waiting for encoder to finish

3. 3rd Restart after manual kill of all existing IDJC processes

> 
launching backend
backend launch attempt 1
started 1 encoders, 1 streamers, 2 recorders
player read buffer allocated for 1024 frames
awaiting reply
got idjc backend ready

threads initialised
jack sample rate is 48000
song title: 

activated ch 1
leaving fully processed mode, ch 1
Toggle OFF recieved for signal: Listen
Restoring previous session
inter track fade was changed
Toggle ON recieved for signal: Listen
song title: 

stream-mon was toggled ON
20 JACK port connection(s) changed
jack connections saved
encoder_start: initiating resampler(s)
encoder_start: successfully started the encoder
streamer_connect: established connection to the server
server [http://xxxx.xxxxx.de:12000](http://xxxx.xxxxx.de:12000) has 0 listeners
unexpected reply from idjcsourceclient 
[Errno 32] Datenübergabe unterbrochen (broken pipe)
backend launch attempt 1
started 1 encoders, 1 streamers, 2 recorders
player read buffer allocated for 1024 frames
awaiting reply
got idjc backend ready

threads initialised
jack sample rate is 48000
activated ch 1
streamer_disconnect: function called while not streaming
command failed for command: server_disconnect
encoder_stop: encoder is stopped
encoder_start: initiating resampler(s)
encoder_start: successfully started the encoder
streamer_connect: established connection to the server
20 JACK port connection(s) changed
jack connections saved
streamer_main: connection failed, shout_get_error reports -4 No error
streamer_main: disconencting from server
encoder_unregister_client called
encoder_unregister_client finished
streamer_main: disconnection complete
streamer_disconnect: function called while not streaming
command failed for command: server_disconnect
encoder_plugin_terminate: waiting for encoder to finish

Even killing jackd would'nt help.

Thanks for any hint!

---

### Post by nik.charles on 2016-04-26
hi alex

been using idjc for couple of years now and it has been very reliable at holding stream and reconnects ok on the few occasions stream drops

check idjc output settings troubleshooting tab - default setting for idjc is to try to reconnect after 10 second delay; again after another 10 seconds; then final attempt after 60 seconds. 10 seconds is a very long time when you are panicking at the other end!
I always change this setting to 5 seconds and enable the repeat option tick box, idjc then keeps trying to reconnect until told to stop.
if stream does drop, don't click anything and give idjc plenty of time to try to reconnect. 

Is more likely to be a problem with internet connection dropping out for a moment. 

Try an alternative streaming application - BUTT or Darkice (good to have as a backup option anyway). If stream still drops, if problem repeats, will not be down to idjc. Then you should check router logs and test internet connection for dropouts. Having super-fast internet isn't needed for radio streaming, but it has to keep a constant connection to keep pushing data

Also suggest try a different stream for testing - only free stream i know of now is caster.fm, but there should be other alternatives. If another stream works ok, problem is likely to be with the server

---

