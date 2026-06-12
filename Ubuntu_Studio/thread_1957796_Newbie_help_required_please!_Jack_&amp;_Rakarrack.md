---
title: "Newbie help required please! Jack &amp; Rakarrack"
date: 2012-04-13
forum: Ubuntu Studio
---

### Post by Face-Ache on 2012-04-13
Okay, i'm very much a Linux Newbie, and i need a bit of help!

I came across this Rakarrack program in the Ubuntu Software Centre, a virtual guitar effects processor, and it looks quite good, so i'd like to give it a try.

But i can't seem to get either it, or the Jack program to make any sound at all.

My setup is a Radeon HD5450 sound/videocard with output going to an Onkyo receiver via HDMI (Sounds etc, like MP3's are working fine).

I've tried plugging the guitar into the various mobo inputs, front-mic, rear-mic, and line-in, and using Ubuntu 11.10's Sound Settings to configure the input, but no joy.

I've looked at a few of the help pages/forums for the Jack program, but they all seem a bit old, and i don't get the same options that they list - for example;
[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections) - In Setup, i don't know which input and output options to select. In the Connections, i don't have any ALSA options in the Writable Clients/Input Ports window. I do however, have an additional ALSA tab (but i'm not sure what i should be doing/selecting)

I don't hear any sounds when i press the keys on the Virtual Keyboard and the Software Synthesizer doesn't show any activity on the volume meters no matter what sort of connections i make.

It's all getting a bit frustrating, and i suspect that it's ultimately probably going to be beyond my skill level to get it all working. But as a last ditch attempt at getting it working, i'm posting here.

Can anyone provide me with some help/advice?

---

### Post by sgx on 2012-04-13
Hi, do these two commands in a terminal, and look for the sound device
to appear in brackets.
aplay -l
cat /proc/asound/cards


 My output looks like

bash-4.1$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bash-4.1$ cat /proc/asound/cards
 0 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xac00, irq 17

My soundcard has two listings in brackets,

M Audio Audiophile 24/96, and ICE1712 multi 

both are shown in qjackctl at the
setup page on the right side in the dropdown list of

Input Device >
Output Device  >

click the > widgets to see the dropdown list. If nothing that is
listed there now works, in the line where it says hw:0 or similar, substitute what is found in the brackets.

The qjackctl wiki, links 4 and 8 will help set up jackd, and its
qjackctl gui, with screenshots, and info.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

You'll need a guitar interface, since the computer line-in ports
don't match the output of your pickups. This could be a $30 usb
device from Behringer, an inexpensive ART preamp, an mAudio Fastrack, or for $100 you can find a Fender Mustang 1 usb amp, that connects to linux by usb without fooling around, and more important, sounds great!.

In the meantime, if you have a mic that fits the jacks on the computer, you can start qjackctl, then rakarrack, which should connect
automatically in qjackctl, but might be mono by default,

so click
the little widget on the left side of  the listings in qjackctl
connection window + or >  it will expand the list, 
rakarrack will have one output going to the opposite stereo pair,

Like two mono rca cables, so you disconnect one rackarrack destination
and then reconnect it to the half of its stereo output that was not used by default. Give a steady sound source to the mic, as you try different ports, one should work, but on new hdmi hardware, linux may not choose as we might expect in surround-sound configurations.

Be patient, search for hydrogen and ardour in youtube, many videos
will show qjackctl and connections, since it is the first step
for nearly everything.

qjackctl mimics the real cables of the 70's  so use that old
sensibility, to conquer the new environment.

On the qjackctl Connect page, click to select an item, it highlights, then on the opposite side of that panel, click the item you want to connect to, it highlights, then click the connect button, and a line
is drawn between them.

There are three tabs on the Connection panel.

On the Audio tab, your soundcard input is System, on the left side.

The soundcard output is System on the right side of
the Audio tab. A big X will be drawn, when the In and Out of
rakarrack are connected to those.

The alsa tab holds midi connections for keyboards, synthesizers, the middle midi tab, connects jackd-aware midi items. 

:popcorn: cheers

---

### Post by zander1013 on 2012-04-14
this might be some help to you ...
[http://www.detector-pro.com/2008/11/how-to-connect-usb-guitar-pedal-or-any.html](http://www.detector-pro.com/2008/11/how-to-connect-usb-guitar-pedal-or-any.html)

---

### Post by Face-Ache on 2012-04-15
Thanks for the responses. I've got a mic, and i've given this a try.

My output looks like;
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I've tried the various selections in the qjackctl Setup panel, but i'm not sure whether they are working or not - how do i tell? For Input Device i have; hw:0, hw:0,2, plughw:0, /dev/audio, /dev/dsp, (default), and the one i entered from the Terminal output, HDA Intel PCH. For Output Device i have; hw:1,3, hw:0, plughw:0, /dev/audio, /dev/dsp, (default), and the one i entered from the Terminal output, HDMI 0.

I've no idea which of the items in brackets in the above output result to put into the Setup Input Device and Output Device options.

So i guess that until i get these input/output selections right, there's not much point in proceeding to the next step of the qjackctl Connections? However, I have had a look at those, and in Readable Clients/Output Ports on the left i have;
Rakarrack
- out_1
- out_2

In the right panel (Writable Clients/Input Ports), each of these are going to;
System
- playback_1
- playback_2

Also in Readable Clients/Output Ports on the left i have;
System
- capture_1
- capture_2

capture_1 has lines going to the right panel (Writable Clients/Input Ports), to;
Rakarrack
- in_1
- in_2
(there is also a 'aux' listed along with in_1 and in_2, but there are no 'lines'/connections to it)

Doesn't seem to matter which combinations of Input and Output Device in Setup that i choose, nor any Audio-tab combinations in Connect - i still don't get any sound at all.

Just so that you know exactly what my setup is like, the Sound/Videocard has HDMI, DVI and VGA outputs, all the input ports are on the mobo.

Thanks again for taking the time to write that comprehensive post above, sgx, and for your suggestion zander - i really do appreciate it.

As i say, i'm very much a "Linux Newbie" but i feel like i'm so close to 'getting it' - just need to gain a bit more understanding of how it all fits together.

So, any other suggestions? :)

---

### Post by sgx on 2012-04-16
Try giving the computer line-in port a constant sound source,
mp3 player, music CD etc

That music would go to qjackctl system capture 1,2

connect those to the rakarrack inputs, then rakarrack
outputs to system playback 1,2

if you still get no sound with the hw:0 type of entries,
put HDA Intel PCH in its place, stop qjackctl, and restart,
and if that doesn't help,
then try HD-Audio Generic

also, rakarrack has an inconspicuous little widget in the
upper right-hand corner, under the file menu,
which is off by default, to protect
speakers, ears, and fine china, it says FX On, with a tick-box
to mark before any sound gets processed.

the command lsmod list kernel modules, you'll likely see something like snd_intel-hda in its output, among the ones dealing with audio modules.

Cheers

---

