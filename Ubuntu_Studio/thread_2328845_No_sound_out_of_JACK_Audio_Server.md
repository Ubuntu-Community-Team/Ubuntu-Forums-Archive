---
title: "No sound out of JACK Audio Server"
date: 2016-06-24
forum: Ubuntu Studio
---

### Post by ignitionn on 2016-06-24
I'm running a mostly fresh install of Ubuntu Studio 16.04 LTS 64-bit, and over the past few days I've been trying to set up a pro audio environment for live performance on my laptop. Ultimately I want to get JACK and PulseAudio working together, but the top priority is getting JACK working at all. To reduce the number of moving parts, I've temporarily disabled PulseAudio by killing the process, and preventing it from respawing by writing "autospawn = no" in ~/.config/pulse/client.conf. With that out of the way, I start JACK from qjackctl with default settings. The result is discouraging (this isn't complete error output, let me know if you want to see the whole thing):

```
[COLOR=#ff0000]19:29:32.003 D-BUS: JACK server could not be started. Sorry[/COLOR]
Cannot connect to server socket err = No such file or directory
```

I figured out eventually that this error was a result of the output and input devices set for JACK. They were set to entries that simply say "(default)", which are evidently nonexistent, so JACK can't connect to them. The other entries in the Output Devices list are:


[LIST]
[*]hw:HDMI,3 - HDMI 0 (hw:0,3) 
[*]hw:HDMI,7 - HDMI 1 (hw:0,7) 
[*]hw:HDMI,8 - HDMI 2 (hw:0,8) 
[*]hw:HDMI - HDA Intel HDMI (hw:0) 
[*]hw:PCH - HDA Intel PCH (hw:1) 
[*]hw:PCH,0 - ALC283 Analog (hw:1,0) 
[/LIST]

The Input Devices list is the same, but only has the final three entries.

The HDMI entries all cause the same error (which I assume is expected because I don't have anything plugged into my HDMI port), but JACK boots fine when set to any combination of the two hw:PCH devices. Unfortunately, none of those combinations produce audio out of my laptop speakers or headphones. I'm testing it out using Hydrogen, which I can confirm is properly connecting to JACK.

Not too long ago, it worked, sort of. With input and output devices set to hw:1, Hydrogen gave me sound out of speakers, but not headphones. That was one reboot ago, and I don't quite remember what I changed unfortunately. So at least for the speakers, I know it's not a hardware problem.

I've checked for any sources of silence I could find. I'm a member of the "audio" group. In alsamixer under HDA Intel PCH, all four of Master, Headphones, Speaker, and PCM are all turned up and unmuted.

Any advice for what to do next? I'm under a deadline and I really need to get this working in a few days :( Any help is appreciated.

---

### Post by ignitionn on 2016-06-25
Somehow I didn't think to check whether ALSA is producing sound. It isn't. If I killall jackd and run the following test case, it appears to be working but produces no audible output on speakers or headphones:

```
speaker-test -c2 -D default:CARD=PCH
```

For reference, here's the output of "aplay -l":

```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC283 Analog [ALC283 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

and "lspci -nn | grep -i audio":

```
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)
```

---

### Post by CrocoDuck on 2016-06-25
Pretty weird. Let's have a look at the whole hardware:

```

lspci -vnn

```

What laptop are you using? Few have speaker - headphone auto-switching problems. Most have just a switched headphone connector, so problems can originate by connector damage. Other actually need the switching to be done by software and properly configured. There should be threads and documentation about this around. I am wondering whether you have two different audio devices for speaker and headphones, since you have two controllers. The command above should shed some light.

---

### Post by ignitionn on 2016-06-25
Thanks for the reply, crocoduck. Just this morning I solved it.

I edited /etc/modprobe.d/50-alsa.conf to add

```
options snd-hda-intel hw:1,0
```

which got the alsa test working on both speakers and headphones. Fired up JACK and it's working :)

A little bit of extra fiddling got PulseAudio working alongside JACK. A bit off topic, but it was impossible to find complete, correct, and up-to-date instructions on how to set this up, so I'll post this here to help future Googlers:

[LIST]
[*]Write down everything you do so you can easily retrace your steps for the sake of reproducing, troubleshooting, or helping others.
[*]Make sure JACK is running: "ps aux | grep [j]ackd" should produce output. If not, start it from qjackctl.
[*]Install pulseaudio-module-jack if you haven't already. (Ubuntu Studio has this by default.)
[*]Add "load_module module-jack-sink" and "load_module module-jack-source" to /etc/pulse/default.pa, right after a bunch of commented-out load_module lines.
[*]Add "set-default-sink jack_in" and "set-default-sink jack_out" to the end of the same file.
[*]"pulseaudio --kill". If you've turned off PulseAudio autospawn, also run "pulseaudio --start".
[*]You should see PulseAudio's JACK sink and source as devices in JACK. You can view those in the qjackctl connections window. I personally check it out in Patchage.
[*]The next step is to get JACK to start automatically. qjackctl writes a shell command for starting JACK to ~/.jackdrc. Mark that file as executable, and add it to Session and Startup -> Application Autostart. (Unfortunately qjackctl has some trouble working with this autostarted JACK process, so you may have to killall jackd to restart JACK for the first time after boot... not sure how to fix this yet)
[*]Reboot your machine to make sure everything sets up properly when you restart it.
[/LIST]

I'm not quite out of the woods yet, since I still have to try this out with my external audio interface. I'll make another thread if I encounter any problems with that.

---

