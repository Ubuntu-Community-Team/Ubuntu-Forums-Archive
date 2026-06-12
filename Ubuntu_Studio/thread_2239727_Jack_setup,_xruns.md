---
title: "Jack setup, xruns"
date: 2014-08-15
forum: Ubuntu Studio
---

### Post by Patrick_strm on 2014-08-15
Jack does not seem to want to cooperate with me, setting the cpus on 'performance' didn't help. Jack starts, then xruns start coming, about one every second and after a few seconds it shuts down. I've got the same jack configuration and hardware that worked fine when I was using the Tango Studio distro. I have tried with more latency - doesn't seem to help. What to do?

---

### Post by Patrick_strm on 2014-08-15
...and like magic i somehow got it to work. Before it ran for a few seconds and died, now it has been working perfectly for...several minutes.

---

### Post by Patrick_strm on 2014-08-16
Yesterday it worked, for hours. TOday when i tried to start up jack I get this:

 [COLOR=#999999]17:45:15.601 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]17:45:15.611 Statistics reset.[/COLOR]
 [COLOR=#cccc99]17:45:15.668 ALSA connection change.[/COLOR]
 [COLOR=#999999]17:45:16.000 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]17:45:16.008 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]17:45:27.864 D-BUS: JACK server is starting...[/COLOR]
 Sat Aug 16 17:45:24 2014: Starting jack server...
 Sat Aug 16 17:45:24 2014: JACK server starting in realtime mode with priority 10
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#999999]17:45:27.879 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).[/COLOR]
 Sat Aug 16 17:45:27 2014: graph reorder: new port 'firewire_pcm:0040ab0000c35de6_MicIn1 left_in'
 Sat Aug 16 17:45:27 2014: New client 'firewire_pcm' with PID 0
 Sat Aug 16 17:45:27 2014: Saving settings to "/home/patrick/.config/jack/conf.xml" ...
 Sat Aug 16 17:45:27 2014: graph reorder: new port 'firewire_pcm:0040ab0000c35de6_MicIn1 right_in'
 Sat Aug 16 17:45:27 2014: graph reorder: new port 'firewire_pcm:0040ab0000c35de6_LineIn 3+4 left_in'
 Sat Aug 16 17:45:27 2014: graph reorder: new port 'firewire_pcm:0040ab0000c35de6_LineIn 3+4 right_in'
 Sat Aug 16 17:45:27 2014: graph reorder: new port 'firewire_pcm:0040ab0000c35de6_SpdifIn left_in'
 Sat Aug 16 17:45:27 2014: graph reorder: new port 'firewire_pcm:0040ab0000c35de6_SpdifIn right_in'
 Sat Aug 16 17:45:27 2014: graph reorder: new port 'firewire_pcm:0040ab0000c35de6_MidiPort_1_in'
 Sat Aug 16 17:45:27 2014: graph reorder: new port 'firewire_pcm:0040ab0000c35de6_LineOut 1+2 left_out'
 Sat Aug 16 17:45:27 2014: graph reorder: new port 'firewire_pcm:0040ab0000c35de6_LineOut 1+2 right_out'
 Sat Aug 16 17:45:27 2014: graph reorder: new port 'firewire_pcm:0040ab0000c35de6_LineOut 3+4 left_out'
 Sat Aug 16 17:45:27 2014: graph reorder: new port 'firewire_pcm:0040ab0000c35de6_LineOut 3+4 right_out'
 Sat Aug 16 17:45:27 2014: graph reorder: new port 'firewire_pcm:0040ab0000c35de6_SpdifOut left_out'
 Sat Aug 16 17:45:27 2014: graph reorder: new port 'firewire_pcm:0040ab0000c35de6_SpdifOut right_out'
 Sat Aug 16 17:45:27 2014: graph reorder: new port 'firewire_pcm:0040ab0000c35de6_MidiPort_1_out'
 Sat Aug 16 17:45:27 2014: New client 'PulseAudio JACK Sink' with PID 1797
 Sat Aug 16 17:45:27 2014: Connecting 'PulseAudio JACK Sink:front-left' to 'firewire_pcm:0040ab0000c35de6_LineOut 1+2 left_out'
 Sat Aug 16 17:45:27 2014: Connecting 'PulseAudio JACK Sink:front-right' to 'firewire_pcm:0040ab0000c35de6_LineOut 1+2 right_out'
 Sat Aug 16 17:45:27 2014: New client 'PulseAudio JACK Source' with PID 1797
 Sat Aug 16 17:45:27 2014: Connecting 'firewire_pcm:0040ab0000c35de6_MicIn1 left_in' to 'PulseAudio JACK Source:front-left'
 Sat Aug 16 17:45:27 2014: Connecting 'firewire_pcm:0040ab0000c35de6_MicIn1 right_in' to 'PulseAudio JACK Source:front-right'
 [COLOR=#9999cc]17:45:32.370 JACK connection change.[/COLOR]
 [COLOR=#999933]17:45:32.371 Server configuration saved to "/home/patrick/.jackdrc".[/COLOR]
 [COLOR=#999999]17:45:32.372 Statistics reset.[/COLOR]
 [COLOR=#999999]17:45:32.377 Client activated.[/COLOR]
 [COLOR=#cc9966]17:45:32.383 JACK connection graph change.[/COLOR]
 Sat Aug 16 17:45:32 2014: New client 'qjackctl' with PID 2216
 [COLOR=#cc66cc]17:45:35.671 XRUN callback (1).[/COLOR]
 Sat Aug 16 17:45:36 2014: ERROR: JackFFADODriver::ffado_driver_wait - unhandled xrun
 Sat Aug 16 17:45:36 2014: ERROR: firewire ERR: wait status < 0! (= -1)
 Sat Aug 16 17:45:36 2014: ERROR: JackAudioDriver::ProcessAsync: read error, stopping...
 [COLOR=#999999]17:46:00.507 Client deactivated.[/COLOR]
 [COLOR=#999999]17:46:06.650 D-BUS: JACK server is stopping...[/COLOR]
 Sat Aug 16 17:45:59 2014: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Sat Aug 16 17:45:59 2014: ERROR: JackEngine::ClientDeactivate wait error ref = 5 name = qjackctl
 Sat Aug 16 17:46:00 2014: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 1000000 err = Connection timed out
 Sat Aug 16 17:46:00 2014: ERROR: JackEngine::ClientCloseAux wait error ref = 5
 Sat Aug 16 17:46:00 2014: Client 'qjackctl' with PID 2216 is out
 Sat Aug 16 17:46:00 2014: Stopping jack server...
 Sat Aug 16 17:46:05 2014: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Sat Aug 16 17:46:05 2014: ERROR: JackEngine::ClientDeactivate wait error ref = 2 name = dbusapi
 Sat Aug 16 17:46:05 2014: ERROR: failed to deactivate dbusapi jack client. error is -1
 Sat Aug 16 17:46:05 2014: Client 'firewire_pcm' with PID 0 is out
 Sat Aug 16 17:46:05 2014: Client 'PulseAudio JACK Sink' with PID 1797 is out
 Sat Aug 16 17:46:05 2014: Client 'PulseAudio JACK Source' with PID 1797 is out
 [COLOR=#999999]17:46:06.659 D-BUS: JACK server was stopped (org.jackaudio.service aka jackdbus).[/COLOR]
 Sat Aug 16 17:46:06 2014: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 1000000 err = Connection timed out
 Sat Aug 16 17:46:06 2014: ERROR: JackEngine::ClientCloseAux wait error ref = 2
 Sat Aug 16 17:46:06 2014: ERROR: Cannot write socket fd = 46 err = Broken pipe
 Sat Aug 16 17:46:06 2014: ERROR: CheckRes error
 Sat Aug 16 17:46:06 2014: ERROR: Could not write notification
 Sat Aug 16 17:46:06 2014: ERROR: ClientNotify fails name = system notification = 1 val1 = 0 val2 = 0
 Sat Aug 16 17:46:06 2014: ERROR: Cannot write socket fd = 48 err = Broken pipe
 Sat Aug 16 17:46:06 2014: ERROR: CheckRes error
 Sat Aug 16 17:46:06 2014: ERROR: Could not write notification
 Sat Aug 16 17:46:06 2014: ERROR: ClientNotify fails name = system notification = 1 val1 = 0 val2 = 0
 Sat Aug 16 17:46:06 2014: ERROR: Cannot write socket fd = 46 err = Broken pipe
 Sat Aug 16 17:46:06 2014: ERROR: CheckRes error
 Sat Aug 16 17:46:06 2014: ERROR: Could not write notification
 Sat Aug 16 17:46:06 2014: ERROR: ClientNotify fails name = freewheel notification = 1 val1 = 0 val2 = 0
 Sat Aug 16 17:46:06 2014: ERROR: Cannot write socket fd = 48 err = Broken pipe
 Sat Aug 16 17:46:06 2014: ERROR: CheckRes error
 Sat Aug 16 17:46:06 2014: ERROR: Could not write notification
 Sat Aug 16 17:46:06 2014: ERROR: ClientNotify fails name = freewheel notification = 1 val1 = 0 val2 = 0

So...What to do?

---

### Post by jejeman on 2014-08-17
Which version of Ubuntu studio?
Which audio card?
Which firewire card?

---

### Post by Patrick_strm on 2014-08-17
It's Ubuntu studio 14.04, audio card is Edirol FA.66 and the firewire card is (lspci gives this) FireWire (IEEE 1394): Texas Instruments XIO2200A IEEE-1394a-2000 Controller (PHY/Link) (rev 01). I think the hardware should be compatible, it worked pretty well with Tango Studio which is an Ubuntu based distro, and I got Jack to run, once, and it worked just beautifully even when I had synths, Hydrogen, Jack and web browser running simultaneously. Now it just doesn't want to cooperate at all.

---

### Post by jejeman on 2014-08-17
I also have FA-66 (I assumed that you too have one), and it doesn't work on my pc with NEC firewire card. And I blame it on NEC. Of course in 12.04 it works flawlessly.
For now, on one computer with VIA firewire card, it works in 14.04.
Also it doesn't work on my laptop with MSI chip.

My observation is that since kernel 3.5 (12.10) FA-66 doesn't work. Don't know why, but I guess something changed inside the kernel.

I would say that you are lucky that you have TI chip, but guess not...

I was planning to go with FFADO and JACK developers to find out what is going on, but just didn't have the will. Maybe it is easier to buy a USB card.

---

### Post by Patrick_strm on 2014-08-17
Yeah...I don't know what to do. But, the weird thing is that it worked great, once...

---

### Post by jejeman on 2014-08-17
Well, since the FFADO utilities and test works, then, something is happening when JACK comes to play. One should be patient and start the comunication with both JACK nad FFADO developers in order to find out what is happening.

---

### Post by Patrick_strm on 2014-08-18
This is weird, I'm creating a bootable usb drive and started Jack at the same time....and it works. Then after a reboot, with nothing else running, it doesn't. (I booted into Ubuntu Studio, didn't use the usb drive.)

---

### Post by Nistegmos on 2014-09-02
@Patrick_strm:   I tried running a bootable USB drive and it quickly got corrupted.  I honestly think from both experiences and stuff I've read that USB drives are innappropriate for operating system installs because the troubles they during writes.  I highly discourage you from using that;  your data will get all messed up and the drive will fail eventually.  OSes do way too much writing to their drives for flash drives to handle.  

But otherwise, good luck.

---

