---
title: "Cannot connect my USB mic to Ardour3"
date: 2016-02-07
forum: Ubuntu Studio
---

### Post by Nosphky on 2016-02-07
I'm using UbuntuStudio 14.04.3 LTS and just trying to get to grips with understanding the DAW, Ardour3.  I have a USB mic (Samson condenser mic) originally used with Skype on Windows) plugged into a usb hub.  My desktop doesn't have any dedicated sound card but relies on the built in facilities on the motherboard.  I am aware that I might have to get an audio interface.

I just can't get any sound into Ardour and neither Qjackctl nor Patchage seem to 'see' the mic.
 
I've examined many similar threads on this forum and clearly anything connected to usb (audio interface or mic) seems to bring a heap of problems.  I thought I might have found the answer in this article : 

[https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices)

but my various tries at editing /etc/modprobe.d/alsa-base.conf  did not achieve the hoped for result.  The mic records ok into audacity and shows lots of activity in the PA sound settings/input devices tab - so the mic is serviceable.  

$ lsusb    shows the mic as follows :  

"Bus 002 Device 007: ID 17a0:0002 Samson Technologies Corp. Q1U dynamic microphone"

$ cat /proc/asounds/cards shows the mic as at hw:2  --

"2 [Microphone     ]: USB-Audio - USB Microphone
                      USB Microphone USB Microphone at usb-0000:00:1d.0-1.4.5, full speed"

(confirmed by unplugging and rechecking)

On the system side, Qjackctl and Patchage show 'capture1' and 'capture2'.    I don't really understand how these entry points relate to the mic or whatever.

It is entirely possible that I have misunderstood lots of things, but I am hoping someone can suggest how I can arrange to connect the mic to Ardour.

---

### Post by jejeman on 2016-02-07
Looks like it is supported by ALSA.
"System:capture_1" type ports are inputs on your audio hardware. Use them. It will never write "USB mic" or something like that.
Make sure you started JACK with USB device, not onboard sound card.

---

### Post by Nosphky on 2016-02-07
I just spent a week getting jack to start on startup of the pc so I could use video in Firefox and sound on audacious and audacity and try ardour without the DAW killing all the sound.   Now I can stop jackd and restart it but I don't understand what you mean by "Make sure you started JACK with USB device, not onboard sound card."

The USB device is only a mic and it's always 'on' so it could be seen by jack when it starts or restarts.

qjackctl shows capture_1 and capture_2 linked to PulseAudio Jack source front-left and front-right but I don't get any sound output from the mic.
I could kill PA but that would undo all the work we did last week to get to be able to switch between the DAW and other sound utilities without having  the DAW kill them all.

If I start the DAW, it looks like capture_1 and 2 are well linked into everything but I get no signal entry from the mic.

---

### Post by jejeman on 2016-02-07
As you know, in JACK settings you need to choose audio driver and audio device for capture and playback. So JACK works **only with one audio device that is selected**. Optionally you can use two devices, one for capture, other for playback. It is all set in JACK settings.
Now, if you want to add pulseaudio in the "mix", then I can't tell you what to do. I don't mix pulseaudio and JACK. But, my guess then is, if this "system:capture" ports are pulseaudio, then choose in pulseaudio controls your hardware for input.
Usually pulseaudio is shown in JACK as "pulseaudio-sink" ports, not "system".

On the side note, Ardour4 works with ALSA. If you don't use multiple audio applications you don't need JACK.

---

### Post by Nosphky on 2016-02-07
Just after my last post, I was stopping and starting jackd to see if I could get the mic picked up by jack and I don't know exactly what I did but suddenly in Ardour3 I could see that I had mic input signal and I managed to record a test message.

Unfortunately, I couldn't get it to play back nor could I get the other tracks containing wav files to play either.  And I found out that the other applications like Firefox, audacious and audacity which over the past week I'd managed to get going on the jack-sink modules in PA had now stopped working but they could play if I changed them back to other outputs.

When I looked at Patchage to see how ardour was connected to get that miracle recording with the mic, I found that ardour had vanished from patchage.

I rebooted but now cannot get ardour to provide any sound output at all nor do the other applications work through their jack-sink module.  I don't know what I did, but I'm probably going to have to spend a little time trying to repeat it.  Maybe its time to try Ardour4 ?

---

### Post by marseille2 on 2016-02-08
[SIZE=3]Hi Nophsky :) ... Take a look at this >> [link]("https://linuxmusicians.com/viewtopic.php?f=4&t=10798"). It elaborates on what Jejeman was saying, and explains the usb vs on-board audio headache. Another thing that's probably up your alley, if you resort to configuring Jackd at the command-line:[/SIZE]> [SIZE=3][FONT=arial][COLOR=#373737]When using -P or -C to specify different devices, do not use the -d argument (which specifies a single device) and do not use the -D argument (which tells JACK to configure a device for playback & capture).[/COLOR][/FONT][/SIZE][SIZE=3]more about that [here]("http://jackaudio.org/faq/multiple_devices.html")...[/SIZE][HR][/HR][SIZE=3]That aside, here's a tip about **recording with Ardour**...  When you open Ardour, _create a new session with automatic connections_ ... then you can further configure inputs and outputs in _Ardour's mixer_, if needed.The following is about **connecting a mic** from a thread at Ardour. It worked for me on version 3.x:
[/SIZE]
> [COLOR=#333333][SIZE=3]QUICK-N-DIRTY INSTRUCTIONS

1) Make sure you've created a track.

2) In the 'Window' Menu, Choose 'Mixer'. This will bring up the mixer window.

3) In the mixer window, there is a 'mixer strip' for each track you create, plus a Master strip. Click on the button labelled 'INPUT' in the strip for the track you want to record to.

4) Choose the input your mic is on.

5) Record-enable the track by clicking on the button that says 'RECORD' on the mixer strip for your track.
[FONT=arial][SIZE=3]
[/SIZE]6) Hit the record button in Ardour's main window, then press play. 

When you are done recording, press stop.[/FONT][FONT=Open Sans][FONT=arial]i am making a few basic assumptions, i know. there are obviously a few *very* basic things you'll have needed to figure out on your own to follow the above instructions. all of those things are addressed very well in the ardour manual. for serious work, much more effort will be needed; but, the above instructions should help you record simple audio with a mic connected to your soundcard.[/FONT][/FONT][/SIZE][/COLOR]
[COLOR=#333333][SIZE=3]
see more at this [thread]("https://community.ardour.org/node/583")...[/SIZE][/COLOR][HR][/HR][COLOR=#333333][SIZE=3]In any case... multiple **terms** **for mic and playback** gets confusing. In rudimentary *lay-speak*, I'd put it like this:
[U]

Pulseaudio[/U] calls [/SIZE]
[LIST]
[*][SIZE=3]playback: SINK[/SIZE]
[*][SIZE=3]mic: SOURCE [/SIZE]
[/LIST]



[SIZE=3]&#8203;[/SIZE][SIZE=3]_Jackd_ calls [/SIZE]
[LIST]
[*][SIZE=3]playback: SYSTEM PLAYBACK ... and playback1, playback2 for stereo left and right speakers.[/SIZE]
[*][SIZE=3]mic: SYSTEM CAPTURE ... and CAPTURE1, CAPTURE2 for stereo left and right of the mic.[/SIZE]
[/LIST]
[/COLOR]

---

### Post by Nosphky on 2016-02-09
Hi marseille2 - welcome to my new problem.  

After my last post, I could not get Ardour to reconnect so I dumped the session and restarted. I took my system back to where I had it before I learned about module-jack-sink etc and then put it back together again.  I reached the point where I just can't get jack (or maybe its Ardour ) to identify system capture_1 (or 2) with the USB mic despite having configured qjackctl in its setup tab to take input from hw:2 by selecting from its drop down input device choice : 

"hw:microphone      USB Microphone (hw:2)"

and record enabling the appropriate input track in Ardour.  I can speak to mic, scrape it , tap it, but never do I see the slightest indication of audio input on the mixer channel - except the once which I noted in my previous post and then having recorded a little mic input , I couldn't get any playback of any audio track - and I found that somehow all system_outputs had disappeared from jack and patchage.

That dropped me into total despair with linux audio and for a short time I considered giving Windows a go. Then  life came along with other stuff to keep me occupied a couple of days.  

Thanks for  the new input - I'll follow these thro gently so it may take me a little time to get back to this thread.

---

### Post by jejeman on 2016-02-09
If you selected USB mic as a soundcard then it is logical not to have system playback. It is a microphone after all - only input.
In your case you need to choose two soundcards, one for capture, other for playback.
You can connect directly capture to playback ports to see if mic, JACK setup is working. Then, go to Ardour...

---

### Post by Nosphky on 2016-02-09
After a lot of trials and using the advice supplied by jejeman and marseille2, I now have a repeatable method to record audio into Ardour3 using my USB mic, playback into external system speakers, use Audacious and also FireFox video tutorials interleaved with trying out Ardour3.

The initial state of my desktop system is with PulseAudio started but without the 2 jack-sink/source modules loaded.  I initially added them into /etc/pulse/default.pa at around line 50 but found it better to comment them out.  There is no jackd nor jackdbus process running.

1. First step is to open QjackCtl :  in its setup, I have :

input device set to "hw:Microphone   ....   USB Microphone (hw:2)"   and
output device set to "hw: PCH  ...  HDA Intel PCH (hw:1)"

These correspond to what I see in the output of $ cat /proc/asound/cards .

2.  Start the Jack server - start button in QjackCtl.  This starts a jackdbus process but not a jackd process (to my surprise).

 3.  Start Ardour3 and open my test session with a mono track to record into with the USB mic.  In the track channel, input is set to system capture_1 and output to the master bus.  Master bus output is set to system playback 1.  I can immediately see available audio activity from the mic and can record a clip into the track.  The recording can be played back correctly.

In this procedure, the order is critical.  If Ardour3 is started first, it results in a jackd process being started and then I cannot connect the USB microphone nor play back.  

If at any time during the work period, a jackd process gets started, this plays havoc with everything.  Even if the jackd process is killed, I can't get the USB mic recording again and various problems exist with playback from Ardour and Firefox.  Audacious seems to cope a little better because I can also select Alsa output for Audacious.   The only workaround I have found, if a jackd process has messed things up, is to reboot.

I don't know why this is so and I do find it all a bit fragile and surprising in UbuntuStudio giving the specificity of its feature list.  But I also have noted that sound on linux is the subject of many problems for lots of users.

Thanks to all who have helped.

---

### Post by marseille2 on 2016-02-11
I have to give to you Nophsky... you did well. I gave up on USB mics with Linux audio long ago. And when it comes to Jackd and Ardour, I find that it's best to stick to a compatible audio interface, and XLR mics. And apparently, it's also the [recommended set-up](https://community.ardour.org/node/4875). So no matter what Linux audio distro we choose, it's something to take into consideration.That said and depending on what your micing needs are, there's always options if your USB mic works with ALSA and pulseaudio. While I wouldn't tell a musician to settle for less than DAW that can handle Jackd ...  I do believe that ALSA and PA handles podcasting, screencasting, and streaming live audio  pretty well. I think that might be one reason to see if Ardour4 (since it doesn't have to use Jackd ... but don't quote me, since I use Jackd), or another ALSA or pulseaudio application can suit you better.

---

### Post by Nosphky on 2016-02-11
Thanks marseille2 for the links.  There's a wealth of info out there but it doesn't always jump out to meet you.

I accept that usb mic is not the recommended way to go.  But life's like that.  Generally speaking, whatever equipment you already have is 'not the way to go'.  Unless you have a packet of money available, most of us can't start a new learning situation from a blank sheet and those who do pose a similar question on the various forums (fora ?) - "I'm thinking of going into xyz, what is the best pc and ancillary equipment to buy ?" generally get a range of often conflicting advice in the replies.

With repeated thanks for the help from all, I'm going to mark this problem as solved for me and my case and continue down the path of discovery.

---

