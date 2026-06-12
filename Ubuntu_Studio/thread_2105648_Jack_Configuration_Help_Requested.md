---
title: "Jack Configuration Help Requested"
date: 2013-01-16
forum: Ubuntu Studio
---

### Post by Alecossy on 2013-01-16
As the title says, I'm messing myself up with JACK to create a recording studio using a laptop (Acer 5742ZG).
As far as now I cannot start the JACK server. This is the messages console output:
> Wed Jan 16 20:09:13 2013: Starting jack server...
Wed Jan 16 20:09:13 2013: JACK server starting in non-realtime mode
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Wed Jan 16 20:09:13 2013: control device hw:0
Wed Jan 16 20:09:13 2013: control device hw:0
Wed Jan 16 20:09:13 2013: [1m[31mERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory[0m
Wed Jan 16 20:09:13 2013: [1m[31mERROR: Audio device hw:0,0 cannot be acquired...[0m
Wed Jan 16 20:09:13 2013: [1m[31mERROR: Cannot initialize driver[0m
Wed Jan 16 20:09:13 2013: [1m[31mERROR: JackServer::Open() failed with -1[0m
Wed Jan 16 20:09:13 2013: [1m[31mERROR: Failed to open server[0m
Wed Jan 16 20:09:15 2013: Saving settings to "/home/alecossy/.config/jack/conf.xml" ...
20:09:21.179 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

Everything is set to default in the Jack configurations panel, i'm using Alsa as driver, 128 frames, 44,1k sample rate and 2 buffers.

Can anyone help me sort the mess out?

---

### Post by CraigPid on 2013-01-16
Are you using the onboard audio?My guess would be that 128 frames is too low.Try bumping it up to 1024 & it will probably start & then see how low it will go until it starts clicking & popping.I've never really tried onboard audio with Jack but I think that although the chips (I accidentally typed cheaps) are pretty good nowadays for playback,they're not really made for recording.
Craig

---

### Post by Alecossy on 2013-01-17
Server started with 256, theoretical latency is 11 msec now.
What's the next step?

---

### Post by CraigPid on 2013-01-17
Are you asking how to use jack?

---

### Post by jejeman on 2013-01-17
> What's the next step? For what?

---

### Post by Alecossy on 2013-01-17
As I said i'm planning on using the laptop as a monitor /small recording platform so I guess I'm going to go for ardour... but how to get the best out of it?
Also, is there any way to pass web audio/other audio to jack? cuz whever I start jack it kills any other sound...

---

### Post by CraigPid on 2013-01-17
When you have jack running,click the volume icon on the top panel & click sound settings.In the Output devices section find Jack Sink & click the green icon that says Set As Fallback.That will route the sound to jack PulseAudioSink when alsa is not available which will happen everytime you start jack.
You should read this
[https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro)
& all the rest of the Ubuntu Studio Documentation.Also check out the Ardour manual.
Craig

---

### Post by CraigPid on 2013-01-17
Something you should do to get the best of it would be to disable as many unessary services as you can.If you're just using it for recording & not as a main operating system then that would be most of them.I'm not at my own computer right now but I think you would look at startup services in the settings panel.Also disable composting in the window Manager section & disable Power Saving.
Craig

---

