---
title: "IDJC being a pain in the ***..."
date: 2008-07-24
forum: Ubuntu Studio
---

### Post by lovhorror on 2008-07-24
I have all the dependencies installed, I have all the info on the radio server I'm trying to connect to, and yet when I hit "connect to server" the program freezes.

I ran it from the terminal and this is the output when I hit the connect button:
> 
encoder_start: resampler will not be used
live_ogg_encoder_main: first pass of the encoder
live_ogg_build_metadata: metadata for encoder 0
artist=(null)
title=(null)
live_ogg_encoder_main: wrote Ogg header packet
live_ogg_encoder_main: wrote Ogg header packet
live_ogg_encoder_main: wrote Ogg header packet
encoder_start: successfully started the encoder
streamer_connect: established connection to the server
streamer_main: waiting for the server to grant access
streamer_main: shout status -10 No error
encoder 0 running
streamer_main: waiting for the server to grant access
streamer_main: shout status -3 No error
streamer_main: connection failed, shout_get_error reports -3 No error
streamer_main: disconencting from server
encoder_unregister_client called
encoder_unregister_client finished
streamer_main: disconnection complete
streamer_disconnect: function called while not streaming
command failed for command: server_disconnect
encoder_unlink: waiting for encoder to finish
live_ogg_encoder_main: cycle restart
live_ogg_encoder_main: writing final packet
live_ogg_encoder_main: last pass of the encoder, freeing libvorbis structures
live_ogg_encoder_main: libvorbis structures freed
live_ogg_encoder_main: performing cleanup
live_ogg_encoder_main: finished cleanup

I really need some help here, I'm supposed to be DJ'ing for a radio station.

---

### Post by Oldsoldier2003 on 2008-07-24
Moved to multimedia production from CC. You're more likely to get the help you need here :)

---

### Post by Steveway on 2008-07-24
> streamer_main: connection failed, shout_get_error reports -3 No error
The adress seems to be wrong. Also note that IDJC from the repositories most propably doesn't support MP3. You'll need to compile it yourself.

---

### Post by lovhorror on 2008-07-24
I got all the dependencies on the main website.

---

### Post by Steveway on 2008-07-24
> **lovhorror said:**
> I got all the dependencies on the main website.

Well, don't forget that you need the -dev versions of the packages.
Also, i have to ask this because you didn't tell, did you compile it yourself from source or do you use a precompiled version.

---

### Post by lovhorror on 2008-07-24
I used the version in Synaptic.

---

### Post by steffe_riese on 2008-07-24
I have played around with some of the different programs for sending streams to icecast/shoutcast.

The only program that i have found working good is MuSE. You can download it from muse.dyne.org.

There is a small bug in the latest source, but it is kind easy to fix that bug. Unfortunatly there isn't an official ubuntu/debian package that works, but i have created one for my self, so send me an email so can i send you the package. I'm not sure if i compiled it with or without lame/mp3 support.

Best Regards
Stefan
[email]steffe_riese@yahoo.com[/email]

---

### Post by lovhorror on 2008-07-24
You could just upload it here, or use rapidshare and post a link. I don't really use my email addresses.

---

### Post by Steveway on 2008-07-25
> **lovhorror said:**
> I used the version in Synaptic.
There is your problem. Afaik the version in the repositories is compiled without support for closed formats like MP3.
If you want to stream something different than OGG then you need to compile it yourself.

---

### Post by steffe_riese on 2008-07-25
> **lovhorror said:**
> You could just upload it here, or use rapidshare and post a link. I don't really use my email addresses.

Ok. Here it comes.
Remark that it's compiled with support for lame/mp3-encoding, so its not 100% open-source by Ubuntus definition.

Best Regards
Stefan Riese

---

### Post by ndeezer on 2008-12-24
I get an error trying to install this package:
Dependency is not satisfiable: liblame0

When I try to install liblame0 with synaptic, it is not to be found.
(Ubuntu 8.10)

---

### Post by trucker33377 on 2009-01-10
> **lovhorror said:**
> I have all the dependencies installed, I have all the info on the radio server I'm trying to connect to, and yet when I hit "connect to server" the program freezes.

I ran it from the terminal and this is the output when I hit the connect button:


I really need some help here, I'm supposed to be DJ'ing for a radio station.

before you tried to connect to the server did you change the password?

---

