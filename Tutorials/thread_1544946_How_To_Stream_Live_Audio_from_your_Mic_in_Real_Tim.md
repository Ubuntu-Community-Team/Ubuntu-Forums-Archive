---
title: "How To Stream Live Audio from your Mic in Real Time"
date: 2010-08-03
forum: Tutorials
---

### Post by prupert on 2010-08-03
This How To is an edited version of my blog article, found here: [http://www.prupert.co.uk/2010/08/02/stream-live-audio-from-a-microphone-in-near-real-time-in-ubuntu/](http://www.prupert.co.uk/2010/08/02/stream-live-audio-from-a-microphone-in-near-real-time-in-ubuntu/)

I found no useful information online for doing this in Ubuntu, so I decided to write down all my experiences. I include various options for different situations. 

You first need to setup your audio inputs. If you are running with Gnome or KDE, this is easily done via the sound widget. If you are running headless, then you need to use the ncurses-based ALSA mixer. So, run ```
alsamixer
``` to set mixer levels via the command line. Select your Mic input as the recording input (use F5 to get to inputs and press Space to select the mic. Push up the volume of the Mic input. You may also need to push up the volume on a generic channel called Capture, if you have one. Don't forget to run ```
alsactl store
``` afterwards to save your settings. As a result of doing all this, ```
/dev/dsp
``` should now point to your microphone input. I found I have lots of strange issues with audio echo and feedback. I managed to eliminate this by ensuring all my audio streams where always only mono, not stereo. 

**_FFmpeg and FFserver_**

**Why Use?** Only really useful if it uniquely supports a combination of video / audio feed that you need to produce. 

One streaming option is FFmpeg and FFserver. You'll need to build the latest versions of FFmpeg (which comes with FFserver) , you can use the excellent guide [here ]("http://ubuntuforums.org/showthread.php?t=786095&highlight=ffmpeg+x264+latest")or use my automated script that I wrote, based on that How To, [here]("http://code.google.com/p/x264-ffmpeg-up-to-date/"). To use FFserver, you must first edit its config file. It seems when you build FFserver, it expects to find the config file at /etc/ffserver.conf, but it doesn't create one. There is a default one available on the FFmpeg website [here ]("http://ffmpeg.org/sample.html") or you can use the one that I have created, found [here]("http://www.prupert.co.uk/media/ffserver.conf"). You then run FFserver, using ```
ffserver 
```. Once FFserver is up and running, you then need to run FFmpeg, to pipe audio and or video to it. This is the FFmpeg command I found that allowed me to pipe the mic input to FFserver:```
ffmpeg -f oss -i /dev/dsp http://localhost:8090/feed1.ffm
```.

The most important part is "http://localhost:8090/feed1.ffm" as this sends the output of FFmpeg to FFserver. Try messing around with the various ffserver.conf options. You only need one input from FFmpeg, but you can have output streams in FFserver. However, be careful, your input has to match the output. So if the ouput expects video and audio, but you only send it video, then FFmpeg with fail (it seems FFmpeg reads the stream options from FFserver and checks that what it is sending it will work, so any problems will usually occur with FFmpeg and not FFserver).

The main problem for me with FFserver was the delay. It was typically around 30 seconds or so and got worse over time. This is a known problem with FFserver and thus I can't recommend it for real-time use. In fact, I couldn't really see any reason to use FFserver at all sadly. It is limited in the types of streams it can produce and how it can offer those streams. It's seems to get less attention that FFmpeg, as it only gets a few commits each month via SVN.

**_Icecast2 and Darkice_**

**Why Use?** Useful if you want to stream music or live DJ mixes. Supports MP3 and OGG (depending on the tool you use to pipe music to icecast.

Icecast is a streaming music solution, primarily designed to allow you stream music over a network, based on WinAmp's Shoutcast technology, essentially making your own radio station. Just like FFserver, you need a server program and a source program (that takes the audio and sends it to the server). I used ```
icecast2
``` as the server program and ```
darkice 
``` as the source program. Darkice is perfect as it is designed to stream live audio from the audio input. Both programs are configured via xml files. Here is my [icecast.xml]("http://www.prupert.co.uk/media/icecast.xml") and my [darkice.xml]("http://www.prupert.co.uk/media/darkice.xml"). You'll have to edit both these files so they work on your system, such as the log file location is correct for example. You set up various streams in the icecast2.xml file, these are confusingly called mount points. You then set up various sources in the darkice.xml file, that direct the audio to these mount points. Due to the bizzare way that alsa sometimes works, /dev/dsp doesn't always work. So in the case of darkice, I used hw:0,0 instead. This refers to the same thing, but in a different way it seems (the reasons for it go beyond me, I think it refers to the first card and the first input (the first being 0, the second being 1 etc)). You then run the icecast2 server using: ```
icecast2 -b -c ~/icecast.xml
``` and then darkice using: ```
darkice -c ~/darkice.cfg.
```. You might find you need to run darkice using sudo, as there might be some permission problems with accessing the audio input. 

This worked much better than FFserver, the delay is around about five seconds. However, I got constant buffering issues, meaning the audio constantly cut off for ages. Also, over time, the delay would gradually get worse over time. It seems icecast is perfect for streaming music, but it doesn't work well in realtime. 

**_SSH and CAT_**

**Why Use?** If you want a quick and dirty solution, for short term use and minimal setup. 

A fellow Linux user suggested this. After ensuring that SSH is setup on both PCs (using ```
ssh
```) you simply need to run this command from the PC that you want to listen to the audio on ```
ssh SERVER 'cat /dev/dsp > /dev/dsp'
``` where SERVER is the IP address of the PC that you want to stream the sound from. This literally copies the input from the microphone on the SERVER to the output of your local PC using SSH. The delay is about the same as with icecast, of around five seconds, but you will suffer from bad buffering issues, as it is transferring raw uncompressed audio over your network.


**_VLC_**

**Why Use?** If you want a huge amount of streaming options, both in format and streaming protocols.

VLC offers a huge range of options for both the protocol used to stream as well as the format of the stream. It also acts as both source and server, taking the audio input and streaming it (although it actually does this using the Live555 streaming media module). You can use http, rtp, rtsp among others and transcode the stream into pretty much any format you can think of. It can be quite complicated to setup. VLC can be run via a GUI or via the commandline using cvlc. The [VLC wiki]("http://wiki.videolan.org/Documentation:Streaming_HowTo") has lots of information about the various streaming options, but the documentation is sadly outdated. After lots of trial and error, I finally came to the following command that worked for me: 
```
cvlc -vvv alsa://hw:0,0 --sout '#transcode{acodec=mp2,ab=32}:rtp{dst=192.168.1.5,port=1234,sdp=rtsp://192.168.1.5:8085/stream.sdp}'
```

This basically takes the microphone input, transcodes it into an MP2 file and then streams it via rtp to the address rtsp://192.168.1.5:8085/stream.sdp. If you then open "rtsp://192.168.1.5:8085/stream.sdp" in VLC on the client PC you get live audio, in near real time! The delay is about 1.5 seconds and requires*very little bandwidth. Sadly, there are three problems with this. First; only one client could connect at a time, secondly; the stream seems to fail after a while, sometimes after five minutes, sometime after two hours, but it would always fail and third it very CPU intensive (I am thinking this is why the stream failed on my box). 


**_FFmpeg_**

**Why Use?** If you want a near-realtime reliable stream.

The best solution I found for realtime audio streaming is FFmpeg as it can stream via rtp nativley, with no need to use FFserver. I used the following command: ```
ffmpeg -f oss -i /dev/dsp -acodec libmp3lame -ab 32k -ac 1 -re -f rtp rtp://234.5.5.5:1234
```. This is similiar to the VLC command, except that this time I am converting into MP3 and streaming to the address: rtp://234.5.5.5:1234. Once again, all you need to do is enter rtp://234.5.5.5:1234 as the streaming source in VLC. There are a few huge advantages with this method, first, the CPU usage is only about 25% on my naff little 750Mhz Transmeta Crusoe. Second, multiple clients can connect at once and third, it seems rock solid. I have had this command running for three days straight with no problems. Memory usage seems to creep up over time, but that's about all. I get a delay of roughly 1.5 seconds, but this does not change over time.

**_Other Options_**

There are other options that I tried but failed to work. I am including them here for completeness. 

Pulse Audio: you can share your audio inputs and outputs over a network using Pulse Audio. I managed to see the shares, but whenever I accessed them, it seemed to crash my network, I guess due to the high bandwidth involved (I was using wireless).  

Live555MediaServer / LiveCaster: this is the module that powers VLC. Sadly it only has minimal documentation and I couldn't figure it out.  

MPEG4IP: primarily designed to stream video, it actually worked reasonably well, but requires a GUI and I was working headless.

---

### Post by JackandJohn on 2011-01-31
I'm curious as to if there is a way to have mic input encoded into an mp3 live (say, with a 10MB buffer), and then have a server list it as a regular song: This would allow all sorts of awesome tricks, such as what I want to do:

Run a subsonic server, and allow people to choose catalog mp3s, OR choose to listen live (from the mixer output of a couple turntables).

In your specific setup, it would also mean being able to connect to the baby monitor from any computer, or stream it live to a mobile device. (I can see the benefit of having one earbud in while doing cleaning elsewhere in the house)

---

### Post by mindracer on 2013-03-01
thanks so much, you did all the dirty work for me.  thanks for sharing :)

---

