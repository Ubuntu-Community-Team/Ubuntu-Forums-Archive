---
title: "Edirol UM-2 seems to be recognized, but nothing happens when hitting keys"
date: 2011-12-18
forum: Ubuntu Studio
---

### Post by BeanAcres on 2011-12-18
Hi folks,

I'm pretty new to Ubuntu Studio, JACK/ALSA and all that, and trying to get my old Edirol UM-2 USB MIDI interface working. I've seen some claims out on the web that it worked for folks on Linux without a hitch. I am an old veteran keyboard player who's been a bit inactive for the past fifteen years or so, and looking to explore the Linux route for composition and sound design. Unfortunately my old DX7-II is on the fritz, so I've got this little cheapo Casio home keyboard that has MIDI ports on it that I'm using to drive the UM-2. My simple goal is to just drive the ZynAddSubFX soft synth using this setup.

I've also got a bit of a software background, so I'm trying to get up to speed on just how US/JACK/ALSA do things within the filesystem. I'm just a newbie to the particulars of JACK/ALSA etc.

I've noticed that, depending on when I hook up the UM-2 with respect to whether JACK / JACK Control is started affects whether or not I can hook up ZynAddSubFX as an output on the Audio tab. Most of the time, everything seems to show up on the ALSA tab. If things don''t appear on the Audio tab, I'm not even able to get ZynAddSubFX to produce any sound using its own little virtual keyboard. I haven't figured out the pattern here yet.

The UM-2 seems to get recognized by the system. Here are a few commands I tried:

chuck@WURLY:~$ cat /proc/asound/cards
 0 [I82801BAICH2   ]: ICH - Intel 82801BA-ICH2
                      Intel 82801BA-ICH2 with AD1887 at irq 17
 1 [UM2            ]: USB-Audio - UM-2
                      EDIROL UM-2 at usb-0000:00:1f.2-2, full speed
chuck@WURLY:~$ ls /proc/asound
card0  card1  cards  devices  hwdep  I82801BAICH2  modules  pcm  seq  timers  UM2  version
chuck@WURLY:~$ ls /proc/asound/UM2
id  midi0  usbbus  usbid
chuck@WURLY:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio capture
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control
  8: [ 1- 0]: raw midi
  9: [ 1]   : control
chuck@WURLY:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio capture
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control

I've had the UM-2 for a decade or so, and used to use it on Win2K. It's been a while, but I don't recall any major problems then. Recently I had tried to use it on our newer Vista machine, but the latency was like a half-second, which is unusable. I had no luck working around that on Vista, so I decided I should try it with the Ubuntu Studio box.

I think I'm hooking things up intuitively; with the current crop of what appears on the various tabs (which I've already hinted as seeming to change with no explanation) I've got the following:

Audio tab:

ZynAddSubFX : out_1  --> system : playback_1

MIDI tab:

(nothing available on the "Readable clients" side; ZynAddSubFX shows up on the "Writable Clients" side with "midi_input" as the only entry under it)

ALSA tab:

"20:UM-2":"0:UM-2 MIDI 1" --> "131:ZynAdSubFX":"0:ZynAddSubFX"
"20:UM-2":"1:UM-2 MIDI 2" --> "131:ZynAdSubFX":"0:ZynAddSubFX"

(on the ALSA tab, I figured I'd just hook both UM-2 outputs to the synth, to just avoid any guessing. I've tried with one or the other only, to no effect).

I noted that on the Windows platform, that the UM-2's "OUT1" light would light when I would hit the keys on the Casio; this doesn't happen now on Linux. Not sure if that is any sign of trouble, or just a difference.

I'm not sure how to monitor the UM-2 from the command line to try to tell if it is in fact receiving anything. I noted that folks in netland seem to claim that (perhaps only for some other distros) that I should see something show up as /dev/midi, but I've got no such device.

Also, in the JACK setup, I noted that there is a "MIDI Driver" drop-down control, with options "none", "raw" and "seq". I think I've tried these as well, to no avail.

I hope I'm earning enough self-help credits here and providing good information beyond "My setup doesn't' work!" :-) Any tips or hints would be greatly appreciated. I'm sure I'm just missing something basic. Everything seems so close to working.

Thanks,
Chuck

---

### Post by sgx on 2011-12-19
Hi, go to the qjackctl wiki, and use the 8th and 4th links,
they will have tutorials/screenshots showing the connections,
and jackd settings, with zynaddsubfx as the example.
The periods/buffer setting in qjackctl should be 3,
if the um-2 is a usb midi interface.


Cheers

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

---

### Post by BeanAcres on 2011-12-26
Hi again,

Occam is laughing at me, rightly!

I am pleased to report that all is in fact working now MIDI-wise, as far as I can tell, after double-checking my hardware connections only to note that I had in fact plugged the MIDI out on the external keyboard to the MIDI "OUT1" (vs "IN1") on the UM-2.

File under "DUH"!!!

I am also happy to report that the horrific half-second delay I had experienced on Vista with the UM-2 is completely absent on Ubuntu Studio.

Thanks for your help.
Chuck

---

