---
title: "How to configure Ardour and JACK???"
date: 2011-08-27
forum: Ubuntu Studio
---

### Post by toughdee on 2011-08-27
Hey guys, thanks for reading and helping if possible. I am very new to Ubuntu and Ardour. In fact I have never really used Ardour because I cant get some stuff working. I am going to give as much info as possible, hoping that you will be able to shed some light on a few questions.
I have been able to get the "Jack Was Unable to Start" error to go away by using this command: jackd -d alsa -d hw:1
When I start ardour it already picks up my desktop microphone. When I select a new track and record, it picks it up. However when I push play it doesn't work. What can I do to setup my audio settings so that it plays?
I am trying to use a Mustang I amplifier (has USB connection) with Ardour. I have found the input in QjackCtl setup, but when I try to get it to connect within Ardour or on the main Jack audio interface page I cannot find it. Is there something else I need to do in either to get it recognized and able to record?
What do I select as my output? Or how do I find this information? The names all just look like gibberish to me.
To be honest I have no idea what I am doing, and even though the things I posted in some cases may sound like it, I don't really know much more than what I posted and everything there is just from research not actual knowledge. :P
I am hoping someone will be willing to walk me through some steps very slowly to get JACK and Ardour set up properly so I can get it to work.
I am using Ubuntu Studio, no external sound card (just a basic Creative inside card), a basic midi connection cable (though doesnt apply a ton here), Mustang I amp.
Ask for more info you need, please be simple but explain what you are asking me to do. Thank you so so so much.

---

### Post by jejeman on 2011-08-27
Which version of ubuntu studio you are using?
Whats is this Mustang thing, and what you want to do with it?
Explain more your hardware audio setup, and what you trying to achive.
Give the output from command:
```
aplay -l|grep card
```

---

### Post by toughdee on 2011-08-30
card 0: SB [HDA ATI SB], device 0: VT1708B Analog [VT1708B Analog]
card 0: SB [HDA ATI SB], device 1: VT1708B Digital [VT1708B Digital]
card 2: CA0106 [CA0106], device 0: ca0106 [CA0106]
card 2: CA0106 [CA0106], device 1: ca0106 [CA0106]
card 2: CA0106 [CA0106], device 2: ca0106 [CA0106]
card 2: CA0106 [CA0106], device 3: ca0106 [CA0106]


that is the response to the requested command.  The mustang is the Fender Mustang I amplifier which has a USB output which allows for recording via USB. I am using Ubuntu release 11.04 (natty) Kernal Linux 2.6.38-11-generic Gnome 2.32.1.  My hope is to use Ardour to record and mix music, but I am having a hard time getting audio to even work from within the program.

---

### Post by jejeman on 2011-08-31
So, that mustang has usb audio card inside which you want accasionaly to use, right? When you issued the command Mustang wan't connected?
Do you have sound in youre sistem, over all, thru that creative card?
For now you have 2 soundcards, the usb would be third one.
Jack can use only one card at the time. So if you want to use usb card, if it is supported, you have to choose it in qjackctrl setup.

Plugin the usb audio card, and issue command again. And also command
```
lsusb
```
also give us the screenshot from qjackctl showing aviable audio devices. something like picture below.

It's bit tricky to take screenshot of the menu use the command below
```
gnome-panel-screenshot --delay 10
```

---

### Post by sgx on 2011-08-31
> **toughdee said:**
> Hey guys, thanks for reading and helping if possible. I am very new to Ubuntu and Ardour. In fact I have never really used Ardour because I cant get some stuff working. I am going to give as much info as possible, hoping that you will be able to shed some light on a few questions.
I have been able to get the "Jack Was Unable to Start" error to go away by using this command: jackd -d alsa -d hw:1
When I start ardour it already picks up my desktop microphone. When I select a new track and record, it picks it up. However when I push play it doesn't work. What can I do to setup my audio settings so that it plays?
I am trying to use a Mustang I amplifier (has USB connection) with Ardour. I have found the input in QjackCtl setup, but when I try to get it to connect within Ardour or on the main Jack audio interface page I cannot find it. Is there something else I need to do in either to get it recognized and able to record?
What do I select as my output? Or how do I find this information? The names all just look like gibberish to me.
To be honest I have no idea what I am doing, and even though the things I posted in some cases may sound like it, I don't really know much more than what I posted and everything there is just from research not actual knowledge. :P
I am hoping someone will be willing to walk me through some steps very slowly to get JACK and Ardour set up properly so I can get it to work.
I am using Ubuntu Studio, no external sound card (just a basic Creative inside card), a basic midi connection cable (though doesnt apply a ton here), Mustang I amp.
Ask for more info you need, please be simple but explain what you are asking me to do. Thank you so so so much.
I also have the great Mustang amp, study this link for connections:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

In qjackctl setup page, you must use your soundcard/motherboard chip for the output device, and the Mustang for the input device.
Click the   > 
widgets by 
Input Device  >
Output Device >

and a dropdown list will appear showing the Mustang, and your sound devices as hw:0,0   hw:1  or whatever. These can change if different
hardware is connected between boots.

You can also record from the amps headphone output, to your line-in.
This lets you physically control volume. With the usb connection, levels are controlled by the software. Use timemachine for simple recordings, ardour has lots of youtubes showing details of it's multi-track and advanced usage.

Rakarrack is great with the Mustang. Make a clean preset with the Twin Reverb amp and no fx, then use your others to :guitar:

Cheers

in ardour, you create a project, create a track, set up monitoring to hear it, arm the track, press record, then press play to begin recording. Check it's menu for preferences and settings, to use the gear you desire for that session.

If you want simple multi-track recording, use timemachine to record a track, import that w64 or wav file into audacity, export as mp3 or wav,
load it in aqualung player, which uses jackd in qjackctl, connect the
output to timemachine, along with your guitar setup, press record in timemachine, and play in aqualung, and :guitar:

---

