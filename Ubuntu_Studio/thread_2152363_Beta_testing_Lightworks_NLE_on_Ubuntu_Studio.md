---
title: "Beta testing Lightworks NLE on Ubuntu Studio"
date: 2013-06-07
forum: Ubuntu Studio
---

### Post by shaunthesheep on 2013-06-07
I am currently beta testing LIghtworks on Ubuntu Studio 12.04 LTS. Anyone else interested can get the public Beta from [here]("http://www.lwks.com/index.php?option=com_kunena&func=view&catid=19&id=44717&Itemid=81").

MTS files from my Sony SR10 camcorder were rather slower to be analysed than on  Windows but imported (via Create link) very quickly. The files are on an  external HDD formatted with NTFS. AC3 audio is not yet supported so I  had to demux the audio with Audacity and export as a PCM wav as  recommended in the Limitations and Known Issues list.

Initially, I was experiencing a 2 second delay starting and stopping  playback. I then tried playing the MTS file outside of Lightworks in the  Ubuntu Studio default player Movie Player. It reported that it needed  to install some software and I let it do so. After installation was  complete, it reported an error and would not play the file. However,  when I went back into Lightworks, the video and audio played instantly  and smoothly without the 2 second delay  [IMG]http://www.lwks.com/components/com_kunena/template/default/images/emoticons/smile.png[/IMG] 

Here is the log of the software that was installed:

Start-Date: 2013-06-08  17:54:56
Commandline: aptdaemon role='role-install-packages' sender=':1.58'
Install: libzbar0:amd64 (0.10+doc-7build2, automatic), libflite1:amd64  (1.4-release-4, automatic), gstreamer0.10-plugins-bad:amd64  (0.10.22.3-2ubuntu2.2), libgme0:amd64 (0.5.5-2, automatic),  libspandsp2:amd64 (0.0.6~pre18-2build1, automatic), freepats:amd64  (20060219-1, automatic), libwildmidi1:amd64 (0.2.3.4-2.1, automatic),  libcdaudio1:amd64 (0.99.12p2-10build1, automatic), libmimic0:amd64  (1.0.4-2.1build1, automatic), libwildmidi-config:amd64 (0.2.3.4-2.1,  automatic), libcelt0-0:amd64 (0.7.1-1, automatic),  libgstreamer-plugins-bad0.10-0:amd64 (0.10.22.3-2ubuntu2.2, automatic),  libofa0:amd64 (0.9.3-4, automatic)
End-Date: 2013-06-08  17:55:15


Not being remotely a technology geek but very much an advocate of free and open source software (software transparency), I have no idea whether this software installation was relevant to the solution. Any ideas about this gratefully received.

I am also getting my head around the superb Ardour (Audacity is an old friend). First time I imported a wav file into Ardour I got sound. Subsequent times not. I have this old, fancy sound card EchoAudio Mia (not Mia Midi) and that may be part of the problem. How do I set up the audio devices in Ardour so that I get sound. I also have an onboard sound chip Realtek. Would that work with low latency if JACK is running. Any  advice appreciated.

---

