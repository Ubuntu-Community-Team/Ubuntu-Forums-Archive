---
title: "[Q] Using Peavey Vypyr/USB Audio Input?"
date: 2012-04-07
forum: Ubuntu Studio
---

### Post by Peperm1nt on 2012-04-07
Ok, I'm using: 

Peavey Vypyr 75W amp
Ubuntu Studio 11.10

Note: I have googled and searched here for my question with no luck.

Problem is that I can't get Jack to recognize the Vypyr's USB out for recording. I can get Audacity to recognize and record the audio(of course without JACK), but I'm trying to convert over to Aurdour because of latency and stability reasons. In the Pulse Volume Control, I can see the Vypyr in the Input Device settings but the ticker bar at the bottom will not pick up the audio(or at least it isn't showing the levels. I have tried to increase and decrease the input level within Volume control, and still see no rise or change in the levels. Also, in JACK when I connect system to system or system to ardour, there is a "static" sound or white noise sound playing in the speakers. I don't know if that has a connection or not. 

In the end, what do I have to do to get a Peavey Vypyr USB output to work with Jack?

Thanks in advanced.

---

### Post by sgx on 2012-04-07
I use a Fender usb amp for input, with no problems.

Use a Periods/Buffer setting in qjackctl of 3

Look at the output of

cat /proc/asound/cards
aconnect -i
arecord -l

Each should list the Peavey if the kernel does does see it.
If not, the Fenders are cheap, versatile, and work without issues,
and an editor has been written to access the 12 amp models, and
the various included fx.
The Peavey should be an easy sale, if cash is tight.
Cheers

[http://www.youtube.com/watch?v=Wl2Q8SNVnPU](http://www.youtube.com/watch?v=Wl2Q8SNVnPU)

This Fender demo is OK,
but the kid wrongly states there are 8 presets, when there
are 24, in three groups of eight, lit up in yellow, green or red
depending on the bank.
Cheers

---

### Post by Peperm1nt on 2012-04-08
> 
Look at the output of

cat /proc/asound/cards
aconnect -i
arecord -l


> peperm1nt@studio:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfeaf4000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfcf7c000 irq 19
 2 [Interface      ]: USB-Audio - VYPYR USB Interface
                      VYPYR USB Interface at usb-0000:00:12.0-2, full speed
peperm1nt@studio:~$ aconnect -i
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
peperm1nt@studio:~$ aconnect -i
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
peperm1nt@studio:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDpeperm1nt@studio:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfeaf4000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfcf7c000 irq 19
 2 [Interface      ]: USB-Audio - VYPYR USB Interface
                      VYPYR USB Interface at usb-0000:00:12.0-2, full speed
peperm1nt@studio:~$ aconnect -i
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
peperm1nt@studio:~$ aconnect -i
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
peperm1nt@studio:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888-VD Analog [ALC888-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Interface [VYPYR USB Interface], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
peperm1nt@studio:~$ 
A ATI SB], device 0: ALC888-VD Analog [ALC888-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Interface [VYPYR USB Interface], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
peperm1nt@studio:~$ 


That is the output. It shows the VYPYR 2 of the 3. aconnect doesn't display the device. I just rechecked in jack controls and in the Connections window, I only see: 

Readable Clients
PulseAudio JACK Sync
-Front, Rear, Side, and lfe speakers.
System
-Capture_1
-Capture_2

Writable Clients
PulseAudio JACK Source
-Front-Left
-Front-Right
System
-Playback_1 
-Playback_2
-Playback_3
-Playback_4
-Playback_5
-Playback_6
-Playback_7
-Playback_8

Non of which will give the output of the amp. Otherwise, the kernel recognizes the VYPYR. I'll double check once again for sound capture. on each channel. The only "success" I've had is use Audacity, which gives poor stability when multi track recording, and in Jack, I can route system to system and get white noise.

---

### Post by sgx on 2012-04-08
VYPYR USB Interface is seen in brackets.

In qjackctl setup page,

Input Device >

type in VYPYR USB Interface

to replace what is there now, hw1:  hw:0,0 etc etc

Items in brackets are usually what the kernel sees as
the products label, and how it should be presented.
My soundcard and amp both have their
name as seen in those brackets from those commands, in that
Input Device text field. 

If not, maybe pulse is an issue, so

edit /etc/pulse/client.conf and change from "; autospawn = yes" to "autospawn = no"

then in qjackctl Options tab to run script after startup, try
pulseaudio -k ; sleep 5

Hope it works!

---

### Post by Peperm1nt on 2012-04-10
Well, I got it working last night for like 10 minutes... afterwards it dont work. I was trying to increase the volume input because you could barely hear the thing record. Anyway:

In the Jack setup page, I changed input device to HW:2 I believe, there was a menu listing and it listed the VYPYR. Afterwards, I went into connections and went system-system and I got audio output on my speakers of the guitar. I also, tried the other changes you had mentioned prior to finding that menu listing and nothing worked so I changed it back to normal and then I found the listing and it worked.

SO further investigation of why it is not working..

I went into PulseAudio Volume Control and went to the input tab. The bar that displays the sound levels will change the first 1-3 seconds of me plugging the USB cable into the computer, afterwards the bar freezes. I believe PulseAudio is the issue in me not getting the amp input.

---

### Post by sgx on 2012-04-10
After changing the pulse settings so it won't restart itself,
run a system monitor like htop or top, or command

ps ux

to see if pulse is active. If it is, command

killall pulseaudio

Did you try replacing the hw:2 with text found in the brackets?
That is how my setup is working. That may survive reboots,
while numeric entries cam change, based on what is plugged in at
boot time.

Routing system to Rakarrack or Guitarix2 will get you lots of gain.
You can use a clean tone without cab-sim, if the Vypyr allows,
to hear linux fx presets as is. 

You can use audacity with jackd, select jackd in audacity prefs,
then press record, then press pause, then look in qjackctl for
portaudio, which will be audacity. Make connections, then press
pause again to resume recording.
then press pause

---

