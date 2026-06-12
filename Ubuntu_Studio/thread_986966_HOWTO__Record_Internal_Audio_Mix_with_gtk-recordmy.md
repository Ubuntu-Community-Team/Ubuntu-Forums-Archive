---
title: "HOWTO:  Record Internal Audio Mix with gtk-recordmydesktop using PulseAudio and JACK"
date: 2008-11-19
forum: Ubuntu Studio
---

### Post by mocha on 2008-11-19
I have struggled for over 1 year with my Intel HDA audio controller.  I could never figure out what I used to do with ease on Windows, to record the "stereo mix" audio, AKA the "audio that comes out of the speakers" from sources such as Flash webpages or internet audio streams.

These steps below have allowed me to finally accomplish this, it is very easy when you harness the power of the PulseAudio layer.  I spent much time discussing this issue with Alsa people and they could not figure out the problem.  The "power of Pulse" is not readily apparent.  It allows you to route audio.  So in other words you can "route" that audio coming out of your speakers into a program that records.  It's the software equivilent of connecting the line-out to the line-in.

Firstly, all of my thanks goes to this guide:

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=843012[/COLOR]]("http://ubuntuforums.org/showthread.php?t=843012")

The guide above is the only reason I could finally solve this problem.  It works on Intrepid and Hardy.  Make sure you follow everything in that guide, including installing the pulseaudio-module-jack and setup jackd properly as discussed.

Now onto my method for capturing audio/video along with gtk-recordmydesktop as well as audio only.  I am assuming you have followed the guide above to a tee.  I am also going to make an assumption that this method works with any audio controller, as PulseAudio is supposed to be a layer on top of ALSA, OSS, JACK, etc.  I can only say that it definitely works with Intel HDA controllers.

-----------------------------------------------

**First the gtk-recordmydesktop method**, this is useful if you are trying to grab a video from a site that dynamically changes the URL to the source Flash.  The big US television networks are an example of this on their websites.

Start JACK Control and start the Jack server.

Open the application that will play the audio/video (such as your web browser) and then open the PulseAudio Volume Control and move it's playback stream to the Jack sink.

Open one each of the PulseAudio playback and recording VU meters, move both of their streams to the PulseAudio JACK Sink.

In PulseAudio volume control output devices tab, set the Jack sink as default.  In input devices tab, set the Jack source as default.

In gtk-recordmydesktop, set the audio to be captured from JACK, select both system:capture_1 and system:capture_2.

Start the recordmydesktop recording, open the Jack connection dialog box and "connect" the PulseAudio JACK Sink to the recordMyDesktop input port.

-----------------------------------------------

**Now the method I use for audio only capture**, this is useful for many purposes, sometimes you might want to capture some audio from a webpage and you can't figure out the URL to the source, or streamripper doesn't work on it.  I've also seen webpages where the audio stream URL dynamically changes similar to the Flash videos, many US commercial FM stations do this.

Start the playback of the audio source.

Set the ALSA PCM as the default in the input and output devices in the PulseAudio volume control.

Open the PulseAudio playback and recording VU meters, move the stream of the recording meter to the Monitor Source of the ALSA PCM.  Both meters response should be following each other now.

The previous step is where you have "routed" the output of the audio that is playing back into the input which you can now record.

I use the command line "arecord" program, I think other programs would be similar.  Just make sure you don't specify a PCM device name.  So in arecord don't use the "-D" command line switch.

Here are some command lines I use.  The first one captures at 44.1 kHz, stereo, wav header "CD quality".  The other commands pipe the arecord output to Lame for real-time MP3 encoding.  Read the arecord and lame man pages, there are many other possibilties.

arecord -f cd -vv test.wav

arecord -f cd -t wav | lame -h -V2 - high_quality_output.mp3

arecord -f cd -t wav | lame -m s -a -b 64 - mono_low_44khz_output.mp3

arecord -f S16_LE -c1 -r22050 -t raw | lame -r -s 22.05 -m m -b 64 - mono_low_22khz_output.mp3

-----------------------------------------------

I hope these tips are useful to someone, I see posts occasionally asking these questions, but never any answers.  Hopefully these tips work for others.

---

### Post by Ng Oon-Ee on 2008-11-20
Ah, another satisfied user of markbuntu's terrific guide :).

Just a note, perhaps you should add a disclaimer that such recordings are technically illegal in some countries (particularly as you specifically mention the US twice in your post). For myself, this is not an issue, my country doesn't enforce anywhere near the amount of licensing and copyright law the US does, however those people following your guide should at least know what they're 'risking'.

Thanks for the guide, as well. I've known how to do this for a while, but always good for someone to take the time to come out with a HOWTO.

---

### Post by Moezzie on 2008-11-30
Very good guidde mocha.
Unfortunately i can not get this to work. I think the main issue is that i dont know how to do step 2 and 3 in the audio caputer only section.

> Set the ALSA PCM as the default in the input and output devices in the PulseAudio volume control.

Open the PulseAudio playback and recording VU meters, move the stream of the recording meter to the Monitor Source of the ALSA PCM. Both meters response should be following each other now.
It would be nice of you to explain in some more detail how to accomplish these things instead of just saying do it.'
I was able to open the "PulseAudio playback and recording VU meters" with the command 
```
pavumeter
```
The rest i cant really figure out how to do.

---

### Post by mocha on 2008-12-02
I just made the assumption that the user has PulseAudio working and configured correctly.  In your "sessions" (if you use Gnome) or autostart or however you set applications to run at startup you should be loading the program called "padevchooser".  This will put a little headphone plug and wire icon in your system tray.  From there you can open the PulseAudio GUI apps such as the VU meters and do the routing for the input and output devices.

So basically you open the "volume control" from the new tray icon, then go to the "input devices" tab RIGHT click somewhere on the entry for the device and you can set it to be "default".  To move the streams, go to the "Recording" tab after you opened the VU meters and RIGHT click on their entry which gives you a menu to move their stream.

---

### Post by markbuntu on 2008-12-04
I was looking for something quick and easy that people could try once they got the pulse-jack connection working that would make use of both the sink and source and these two little projects are just the thing. I will be putting a link to this thread in the guide.

Thanks,
Mark

---

### Post by mocha on 2008-12-06
> **markbuntu said:**
> I was looking for something quick and easy that people could try once they got the pulse-jack connection working that would make use of both the sink and source and these two little projects are just the thing. I will be putting a link to this thread in the guide.

Thanks,
Mark

That's an honor!  Thank you!

---

### Post by andr3w on 2009-01-27
> **mocha said:**
> I have struggled for over 1 year 



You lost me at: Start JACK Control and start the Jack server.
Of course,
It's not like I'd want to install all the pulseaudio stuff when it never works. (Just a thought.)

That, or the jack server. (I guess starting the program doesn't start the program.)

I suppose I should have brought my pyramid..

---

### Post by mocha on 2009-01-27
If you followed that PulseAudio guide I linked to, then in your sound and video menu you would see a launcher for "jack control".  Execute that then press the start button to start the Jack server.

---

### Post by SergeantOreo on 2009-01-29
Thanks for this thread Mocha! I used it to 
configure my Alsa settings, but it still didn't work (because I wasn't using the method involving JACK). Instead, I figured out how to input the proper Alsa device name in RecordMyDesktop settings to utilize my microphone.

---

### Post by pokapeski on 2009-02-07
jezz, i've been struggling the whole day with this and all i can see is the sound performing on playback and recording VUmeters up and down. when i try to record anything i just get noise.
i am trying the "audio capture only" and everything went well. i mean, i don't think i can be failing at recording with arecord (i tried also with qarecord and same results, noise) :(

if the playback and recording VUmeters shows the proper signal (ups and downs,not just fixed signal), should i imply that the sound is being properly routed?

EDIT:
got it!
for the record. the thing is like this. you start pulseaudio. 
start volumemeter recording and playback
then you start volume control and go to the recording tab.
move all interfaces or whatever they are to the same device as the playback.
start the streaming application. in this point the playback vumeter should start dancing with the music
go to the voulumecontrol/recording and you'll see that another device has appeared. that's the one!
Move device to the same as the one in playback
start recording. it worked for me.
hopefully it helps. hopefully i am not misleading anyone as i don't really know what i am touching.

disclaimer: if having problems, it wasn't me, blame someone else. :P

---

### Post by mocha on 2009-02-10
> **pokapeski said:**
> got it!
for the record. the thing is like this. you start pulseaudio. 
start volumemeter recording and playback
then you start volume control and go to the recording tab.
move all interfaces or whatever they are to the same device as the playback.
start the streaming application. in this point the playback vumeter should start dancing with the music
go to the voulumecontrol/recording and you'll see that another device has appeared. that's the one!
Move device to the same as the one in playback
start recording. it worked for me.
hopefully it helps. hopefully i am not misleading anyone as i don't really know what i am touching.

disclaimer: if having problems, it wasn't me, blame someone else. :P

Maybe your sound hardware is different somehow, because this is not necessary for me.  All I do is open the record and playback VU meters, then in the Volume Control - Recording tab, move the recording VU meter to the Monitor Source of the ALSA PCM.  

In other words, the only items that ever appear in my Recording tab are the VU meters.

---

### Post by mocha on 2009-02-10
> **SergeantOreo said:**
> Thanks for this thread Mocha! I used it to 
configure my Alsa settings, but it still didn't work (because I wasn't using the method involving JACK). Instead, I figured out how to input the proper Alsa device name in RecordMyDesktop settings to utilize my microphone.

But what about the internal audio?  I think you will still need to use JACK for that, unless you use the CLI recordmydesktop and start it with the padsp wrapper.  I never attempted this becuase gtkrecordmydesktop is just so much easier.

---

### Post by pokapeski on 2009-02-11
> **mocha said:**
> Maybe your sound hardware is different somehow, because this is not necessary for me.  All I do is open the record and playback VU meters, then in the Volume Control - Recording tab, move the recording VU meter to the Monitor Source of the ALSA PCM.  

In other words, the only items that ever appear in my Recording tab are the VU meters.

dunno, actually when i was writing my post i had 1 pcm playback, 1 pcm recording, 1 monitor playback, 1 monitor recording and 1 pcm-wine-thingie(the app running the streaming).
but don't really worry much about it. your config should work for the universe. it's just that i am the uber tester, i never get anything working at first attempt and if something does it must be an state of the art config :p

---

### Post by DagMan on 2009-02-22
Thanks, you rock!
I've been trying various ways to get this going with the audio but it kept coming down to a lack of hardware support over and over... but Finally!!!

Not to break the law, of course, but I'm off to test it with something playing in a free commercial music player in a Virtualbox Windows install ;)

---

### Post by mocha on 2009-02-22
> **DagMan said:**
> Thanks, you rock!
I've been trying various ways to get this going with the audio but it kept coming down to a lack of hardware support over and over... but Finally!!!

Not to break the law, of course, but I'm off to test it with something playing in a free commercial music player in a Virtualbox Windows install ;)


It should work, I record stuff coming from Virtual machines all the time.  Just make sure VirtualBox is setup to use PulseAudio as the "host audio driver" in each machine's settings.

---

### Post by mj_ja55 on 2009-03-25
Is JACK also required for recording the internal audio alone, or is that only needed if you are using gtkrecordmydesktop?

---

### Post by mocha on 2009-03-27
> **mj_ja55 said:**
> Is JACK also required for recording the internal audio alone, or is that only needed if you are using gtkrecordmydesktop?

Only for recordmydesktop.  Actually, you could probably run recordmydesktop without it if you use the command line version and use the padsp wrapper.  Using the gtk version is a lot easier though, and makes use of JACK.

---

### Post by crazybuntu on 2009-05-30
could you please post with screenshots or a screencast ???

whats the settings in JACK ?? you didnt explain,
i have hw0, hw0:0, hw0:1; hw0:2, default, dev/audio as options ..
I ran jackd as server

And i dont see JACK as an option in Pulseaudio SINK / SOURCE .. when i typed JACK in it, i cannot play mp3 from rhythmbox

im confused... i tried almost all combination of input / source is JACK but none works , and when i use DEFAULT , i cannot play mp3 in Rhythmbox ????

when i played mp3 before i start jack, it says hw0 already in use ?? whats the problem ???

please again if you have screnshots it would be lot of help

---

### Post by mocha on 2009-06-01
There's been a little change with Jaunty.  Take a look at this thread for a procedure to build the Jaunty version of Pulseaudio with the JACK module [http://ubuntuforums.org/showthread.php?t=1163390]("http://ubuntuforums.org/showthread.php?t=1163390").  All this procedure does is compile Pulseaudio with the JACK module which the Ubuntu devs didn't do originally for some reason.  Then you just copy the module to your pulse library directory, it doesn't replace or mess up anything.  

This is a critical step.  When you start JACK you have to load that module, this is what I use the script /usr/bin/jackd for.  It's explained in the guide I linked to in my first post.  You really have to follow the guide I linked to in my first post to setup your Alsa/Pulse environment correctly, otherwise this stuff doesn't work properly.  Ubuntu still has a way to go in getting a lot of this kind of stuff setup properly.

Here is a quick screencast, if you view it fullscreen it's readable enough to get the important parts.  [http://www.youtube.com/watch?v=9ykJmmRy6kI]("http://www.youtube.com/watch?v=9ykJmmRy6kI")

---

### Post by crazybuntu on 2009-06-01
great job doing the screencast, problem is i cannot get pulseaudio compile from source.. i got error when make .lib module jack .la  ;; its in the other post  [http://ubuntuforums.org/showthread.php?t=1163390](http://ubuntuforums.org/showthread.php?t=1163390).

---

### Post by durand on 2009-06-01
Awesome, nice tutorial! Thanks pokapeski for clarifying that..

---

### Post by durand on 2009-06-22
By the way, if anyone wants to record to an ogg file, the command is ```
oggenc -b 192 -o radio.ogg -
```

instead of the lame command.

---

### Post by kilgore9 on 2009-07-06
HELP!  I followed the guide and have everything installed.  But when I try to start JACK it gives me an error.  I suppose this has to do with the script that is mentioned to load the module, though I can't find instructions on how to make that script anywhere in the link in the first post.  Can someone please post those instructions here?   I've never made a script, don't know how to do it....

---

### Post by mocha on 2009-07-06
Just make a text file with the following, and make it executable in the file properties.

```
#!/bin/bash

pactl load-module module-jack-sink channels=2
pactl load-module module-jack-source channels=2
```

The point of the script is to load the jack sink and source for use with pulseaudio when Jack starts.  You can execute the 2 commands above in a terminal and it accomplishes the same thing.  The point of doing it in a script is so you only load the modules when you start Jack.  I know a lot of this seems convoluted at first, but you'll get the hang of it eventually.

---

### Post by durand on 2009-07-06
If anyone cares, I've almost finished writing a script which allows you to record any pulseaudio stream. I've currently got a problem with it not returning the stream back to the correct output device but it does work fully. You just need to manually move it back with pavucontrol or pactl. If anyone wants it, I'll post it here.

---

### Post by mocha on 2009-07-06
> **durand said:**
> If anyone cares, I've almost finished writing a script which allows you to record any pulseaudio stream. I've currently got a problem with it not returning the stream back to the correct output device but it does work fully. You just need to manually move it back with pavucontrol or pactl. If anyone wants it, I'll post it here.

Sounds good.  Let's have a look!

---

### Post by durand on 2009-07-06
```

#!/usr/bin/python

## This script helps you to record pulseaudio streams

# Filename of the recording
filename = "recording.ogg"
# Bitrate of the recording in kbps
bitrate = 192

import os

# Get a list of pulseaudio objects
objects = os.popen('pactl list').read().split('\n\n')
# Form dictionaries containing the details of the 
# inputs
streams = {}
for object in objects:
    if "Sink Input" in object:
        object = object.replace('\t','').split('\n')
        # Get the stream id
        id = object[0].split('#')[-1]
        # Get the stream's name and app to identify it
        for info in object:
            if "media.name" in info:
                media_name = info.replace('"','').split(' = ')[-1]
            if "application.name" in info:
                app_name = info.replace('"','').split(' = ')[-1]
        # Add the details to the dictionary
        streams[id] = (app_name,media_name)

# Display the streams and ask the user to choose one to record
id = 0
stream_list = streams.keys()
for stream in stream_list:
    id += 1
    print str(id) + ") " + streams[stream][0] + ": " + streams[stream][1]
print
try:
    stream_id = int(raw_input("ID of stream to record: "))
except:
    stream_id = -1
while stream_id not in range(1,id+1):
    print stream_id,range(1,id+1)
    try:
        stream_id = int(raw_input("ID of stream to record: "))
    except:
        stream_id = -1
# Get the PA id of the stream to record
stream_id = stream_list[stream_id-1]
# Load a null sink
print "Loading a null sink..."
null_id = os.popen('pactl load-module module-null-sink').read()

# Start recorder and get its pid to kill it later. We need to use threads here to background it.
print "Starting recorder..."
import threading
class Recorder(threading.Thread):
    def run(self):
        try:
            os.popen('arecord -f cd -t raw | oggenc -b %s -o %s --raw -'%(bitrate,filename))
        except KeyboardInterrupt:
            print "I'm not quitting!"
Recorder().start()

# Wait for arecord to load
import time
time.sleep(2)
objects = os.popen('pactl list').read().split('\n\n')

for object in objects:
    # Get name of the null sink
    if "Sink #" in object and "Owner Module: " + null_id in object:
        object = object.replace('\t','').split('\n')
        for info in object:
            if "Name: null" in info:
                null_name = info.replace('Name: ','')
    # Get recorder id (Assume that it is the last Source Output)
    if "ALSA Capture" in object:
        object = object.replace('\t','').split('\n')
        recorder_id = object[0].split('#')[-1]

# Move stream to null sink
print "Moving %s to %s..."%(streams[stream_id][1],null_name)
os.popen('pactl move-sink-input %s %s'%(stream_id,null_name))

# Move recorder to null monitor
print "Moving recorder to %s..."%null_name
os.popen('pactl move-source-output %s %s'%(recorder_id,null_name+".monitor"))

print "Stream recording to %s!"%filename

```

I'm having a bit of trouble with getting it to close nicely. It's the threading thats causing the problem but I'm completely out of depth there.

Run it with python file.py

---

### Post by durand on 2009-07-06
Oh yea, forgot to mention that you need oggenc installed for that. Its in the [vorbis-tools]("apt:vorbis-tools") package. If you want to use lame instead, just replace the encoding line in the script.

---

### Post by mocha on 2009-07-07
That's nice!  I'll try it later and let you know what happens.

---

### Post by durand on 2009-07-07
Okay. I'll post on the python mailing list about that error. Hopefully, it will be fixed soon.

---

### Post by mocha on 2009-07-08
It doesn't work for me, just records silence, this is what I get:

```
1) Audacious: xxxxx
2) VBox: temp liveCD (pcm_out)
3) ALSA plug-in [firefox]: ALSA Playback

ID of stream to record: 3
Loading a null sink...
Starting recorder...
Encoding standard input to 
         "recording.ogg" 
at approximate bitrate 96 kbps (VBR encoding enabled)
Recording raw data 'stdin' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
	Encoding [ 0m01s so far] | Moving ALSA Playback to null.2...
You have to specify a sink input index and a sink
Moving recorder to null.2...
You have to specify a source output index and a source
Stream recording to recording.ogg!
	Encoding [ 0m15s so far] | ^CAborted by signal Interrupt...
Exception KeyboardInterrupt in <module 'threading' from '/usr/lib/python2.6/threading.pyc'> ignored

```

---

### Post by durand on 2009-07-08
Hmm, for some reason I can't replicate that problem. Could you post the output of **pactl stat** at the point that you run the script?
Do you have jack or something else running that may interfere with the script? I really want to get it working for all main environments but I don't really have them set up here so if you could help me debug this, that would be great!

You could try changing:
```
# Move stream to null sink
print "Moving %s to %s..."%(streams[stream_id][1],null_name)
os.popen('pactl move-sink-input %s %s'%(stream_id,null_name))

# Move recorder to null monitor
print "Moving recorder to %s..."%null_name
os.popen('pactl move-source-output %s %s'%(recorder_id,null_name+".monitor"))
```

to:
```
# Move stream to null sink
print "Moving %s to %s..."%(streams[stream_id][1],null_name)
os.popen('pactl move-sink-input "%s" "%s"'%(stream_id,null_name))

# Move recorder to null monitor
print "Moving recorder to %s..."%null_name
os.popen('pactl move-source-output "%s" "%s"'%(recorder_id,null_name+".monitor"))
```

That may help. I really should have done that from the start.

---

### Post by gabx84 on 2009-09-23
So I'm sure this is the same as what you're doing or an easier way to do it.  (first in volume control, go to preferences and make sure capture mux, speaker, and capture are on, (also go to the recording tab and drag both bars up))  

Go into the terminal and type:

sudo apt-get install pavucontrol

then when that's finished type:

pavucontrol

then start your audio and in another terminal type:

arecord -c 2 -f cd test

(so that you are both playing audio and recording it)
then, the last step, in pavucontrol go to the recording tab and click the down arrow to the right of "ALSA Capture" >> click "Move Stream" >> click "Monitor source of ALSA PCM...."

I don't know if this an actual easier way or what you're describing but you guys are just doing it in more depth but that's what worked for me and it's pretty easy. (Aka, feedback's good so I can know if I just repeated everything like an idiot or not)

---

### Post by durand on 2009-09-23
Yeah, thats pretty much what the other methods are about but I think PA's changed a bit since this thread started.

---

### Post by Anubis on 2010-01-17
1.Install gtk-recordmydesktop.
2.Press the red button on the taskbar.
3.Press the same button when done recording.
4.Watch video with audio.

You don't need Jack, or anything else, except a working system.#-o

---

### Post by VertexPusher on 2010-01-18
> **Anubis said:**
> You don't need Jack, or anything else, except a working system
... with a 16bit sound card from 1997.

Welcome to 2010. Audio loopback in hardware is a thing of the past.

---

### Post by Shwan.c on 2010-08-23
I'm maybe off topic but pulse do have the transfer function for recording called "Monitor  device ..."

take a look at [http://blog.stebalien.com/2009/03/howto-ones-linux-computer-with.html](http://blog.stebalien.com/2009/03/howto-ones-linux-computer-with.html)
or
[https://wiki.ubuntu.com/PulseAudio#Recording](https://wiki.ubuntu.com/PulseAudio#Recording) example using PulseAudio and Audacity the latest one ie last part

---

### Post by wachin on 2013-04-13
the only way to work Recordmydesktop from Jack

O.S. used UbuntuStudio 12.04.2 (32bits), Laptop Dell Inspiron 1750


Steps I did:

I uninstalled (via Synaptic):

recordmydesktop (this dont working)
gtk-recordmydesktop

Note: This uninstalled Kdenlive, but then returned to install.

I Download:

recordmydesktop_0.3.8.1 svn602-2 + + jackfix_i386.deb

from:

[http://www.remastersys.com/forums/index.php?topic=1608.0](http://www.remastersys.com/forums/index.php?topic=1608.0)

and install it from the terminal: sudo dpkg-i *. deb:

Then I installed (via Synaptic):

gtk-recordmydesktop

Ready now

I opened Jack Control (QjackCtl) and run Jack Server (Play button)

With Gtk-recordmydesktop opened, in Tab "Sound" Select the audio to be captured from Jack (crushing Ctrl):

system: capture_1
system: capture_2

I closed the window, and click Record buttom

STEREO MIX
You must configure your PC  in pulseaudio  Tab "Input devices" in "Port" record from the microphone of the laptop (if you have it) adjust the volume, I have to put such halfway to not sound ugly, or "Line In" if you use a external Mic. And Jack Control (qjackctl) you must click on the "Connections" tab "Audio" manually connect the music player that is playing to "recordmydesktop", you can use:

Audacious (must choose "File / Preferences / Output Options" JACK)
VLC (but must install from Synaptic vlc-plugin-jack


[IMG]https://dl.dropboxusercontent.com/u/83295394/Jack%20Connections/RecordMyDesktop%20%2B%20Jack%20Support.gif[/IMG]


and ready, that's all, ESTERO MIX WITH JACK FROM RECORDMYDESKCOP

Saturday 13 April 2013 10:12

---

### Post by wildmanne39 on 2013-04-13
Thanks for sharingThread closed. Please do not post in old threads.

---

