---
title: "Jack probs"
date: 2012-06-05
forum: Ubuntu Studio
---

### Post by Oberon2 on 2012-06-05
I am new to Linux and new to Precise Pangolin. I want to use this machine as a dedicated internet broadcast machine using the IDJC.  Now I have set jack up in all the recommended ways and most times when I started qjackctl jack started OK but when firing up IDJC that just sat there and did nothing. as you can imajgin I have fiddled arou with it a bit got no joy and have un-installed and reinstalled both IDJC and QJACKCTL and now QJACKCTL crashes completely. 
Here the error report
16:27:13.332 D-BUS: JACK server is starting...
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:27:13.426 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
Tue Jun  5 16:27:12 2012: Starting jack server...
Tue Jun  5 16:27:12 2012: JACK server starting in non-realtime mode
Tue Jun  5 16:27:13 2012: control device hw:0
Tue Jun  5 16:27:13 2012: control device hw:0
Tue Jun  5 16:27:13 2012: Acquired audio card Audio0
Tue Jun  5 16:27:13 2012: creating alsa driver ... hw:0,0|hw:0,0|128|2|22050|0|0|nomon|swmeter|-|32bit
Tue Jun  5 16:27:13 2012: control device hw:0
Tue Jun  5 16:27:13 2012: configuring for 22050Hz, period = 128 frames (5.8 ms), buffer = 2 periods
Tue Jun  5 16:27:13 2012: ALSA: final selected sample format for capture: 32bit integer little-endian
Tue Jun  5 16:27:13 2012: ALSA: use 2 periods for capture
Tue Jun  5 16:27:13 2012: ALSA: final selected sample format for playback: 32bit integer little-endian
Tue Jun  5 16:27:13 2012: ALSA: use 2 periods for playback
Tue Jun  5 16:27:13 2012: graph reorder: new port 'system:capture_1'
Tue Jun  5 16:27:13 2012: New client 'system' with PID 0
Tue Jun  5 16:27:13 2012: graph reorder: new port 'system:capture_2'
Tue Jun  5 16:27:13 2012: graph reorder: new port 'system:playback_1'
Tue Jun  5 16:27:13 2012: graph reorder: new port 'system:monitor_1'
Tue Jun  5 16:27:13 2012: graph reorder: new port 'system:playback_2'
Tue Jun  5 16:27:13 2012: graph reorder: new port 'system:monitor_2'
Tue Jun  5 16:27:14 2012: Saving settings to "/home/steve/.config/jack/conf.xml" ...
16:27:20.635 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
Cannot read socket fd = 22 err = Success
JackSocketClientChannel read fail
Cannot open qjackctl client
Tue Jun  5 16:27:20 2012: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: Driver is not running[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: Cannot create new client[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: Abort![0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: info.si_signo = 6[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: info.si_errno = 0[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: Segmentation Fault![0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: info.si_signo = 11[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: info.si_errno = 0[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: info.si_code  = 1 (SEGV_MAPERR)[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: info.si_addr  = 0x64656c69[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[00]       = 0x00000033[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[01]       = 0xc1570000[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[02]       = 0x0000007b[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[03]       = 0x0000007b[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[04]       = 0x64656c69[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[05]       = 0xb031c7c0[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[06]       = 0xb031c788[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[07]       = 0xb031c1e0[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[08]       = 0x00addff4[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[09]       = 0x00000000[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[10]       = 0xffffffff[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[11]       = 0x00000000[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[12]       = 0x0000000e[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[13]       = 0x00000004[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[14]       = 0x00982b8e[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[15]       = 0x00000073[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[16]       = 0x00210246[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[17]       = 0xb031c1e0[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: reg[18]       = 0x0000007b[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: Stack trace:[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR:  1: 0x982b8e <_IO_vfprintf+21406> (/lib/i386-linux-gnu/libc.so.6)[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR:  2: 0xa3b438 <__vsnprintf_chk+232> (/lib/i386-linux-gnu/libc.so.6)[0m
Tue Jun  5 16:27:20 2012: [1m[31mERROR: End of stack trace[0m
16:27:28.181 D-BUS: JACK server is stopping...
Tue Jun  5 16:27:28 2012: ------------------
Tue Jun  5 16:27:28 2012: Controller activated. Version 1.9.8 (4653) built on Fri Feb 10 15:04:03 2012
Tue Jun  5 16:27:28 2012: Loading settings from "/home/steve/.config/jack/conf.xml" using expat_2.0.1 ...
Tue Jun  5 16:27:28 2012: setting parameter 'engine':'driver':'(null)' to value "alsa"
Tue Jun  5 16:27:28 2012: setting parameter 'engine':'realtime':'(null)' to value "false"
Tue Jun  5 16:27:28 2012: setting parameter 'engine':'verbose':'(null)' to value "false"
Tue Jun  5 16:27:28 2012: setting parameter 'engine':'client-timeout':'(null)' to value "500"
Tue Jun  5 16:27:28 2012: setting parameter 'drivers':'alsa':'device' to value "hw:0,0"
Tue Jun  5 16:27:28 2012: setting parameter 'drivers':'alsa':'rate' to value "22050"
Tue Jun  5 16:27:28 2012: setting parameter 'drivers':'alsa':'period' to value "128"
Tue Jun  5 16:27:28 2012: setting parameter 'drivers':'alsa':'nperiods' to value "2"
Tue Jun  5 16:27:28 2012: setting parameter 'drivers':'alsa':'hwmon' to value "false"
Tue Jun  5 16:27:28 2012: setting parameter 'drivers':'alsa':'hwmeter' to value "false"
Tue Jun  5 16:27:28 2012: setting parameter 'drivers':'alsa':'duplex' to value "true"
Tue Jun  5 16:27:28 2012: setting parameter 'drivers':'alsa':'softmode' to value "false"
Tue Jun  5 16:27:28 2012: setting parameter 'drivers':'alsa':'monitor' to value "true"
Tue Jun  5 16:27:28 2012: setting parameter 'drivers':'alsa':'dither' to value "n"
Tue Jun  5 16:27:28 2012: setting parameter 'drivers':'alsa':'shorts' to value "false"
Tue Jun  5 16:27:28 2012: Listening for D-Bus messages
Tue Jun  5 16:27:28 2012: Ignoring JACK server stop request because server is already stopped.

I am using and old  P4 2.40GHz with 2G RAM

Hope you can help ... O2

---

### Post by Sylos on 2012-06-06
Hello there.

Just took a quick look at your output and saw this:

```
Tue Jun 5 16:27:13 2012: configuring for 22050Hz, period = 128 frames (5.8 ms), buffer = 2 periods

```

Seems like an odd number for your sample rate. Have you tried at a standard 44k in your Qjackctl settings?

Cheers

---

### Post by Oberon2 on 2012-06-06
Hi ... Yea I've tried all sorts. I wasn't sure if it was JACK or ALSA or IDJC that was the prob so I used AUDACIOUS  which plays fine configured for ALSA, to fire up using JACK ... and got no reaction . The track loads like it did in IDJC but just sits there,like it did in IDJC . here's the message from the last try with AUDACIOUS :-

     p, li { white-space: pre-wrap; }  loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|512|2|44100|0|0|nomon|swmeter|-|16bit
 control device hw:0
 configuring for 44100Hz, period = 512 frames (11.6 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 16bit little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 16bit little-endian
 ALSA: use 2 periods for playback
 [COLOR=#999999]20:29:48.883 JACK was started with PID=4636.[/COLOR]
 [COLOR=#9999cc]20:29:50.945 JACK connection change.[/COLOR]
 [COLOR=#999933]20:29:50.950 Server configuration saved to "/home/steve/.jackdrc".[/COLOR]
 [COLOR=#999999]20:29:50.956 Statistics reset.[/COLOR]
 [COLOR=#999999]20:29:50.962 Client activated.[/COLOR]
 [COLOR=#996633]20:29:50.996 Buffer size change (512).[/COLOR]
 [COLOR=#cc66cc]20:29:51.013 XRUN callback (1).[/COLOR]
 [COLOR=#cc99cc]20:29:52.973 XRUN callback (96 skipped).[/COLOR]
 [COLOR=#cc99cc]20:29:54.981 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:29:56.988 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:29:58.996 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:30:01.004 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:30:03.015 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:30:05.024 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:30:07.033 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:30:09.042 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:30:11.050 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:30:13.058 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:30:15.066 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:30:17.075 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:30:19.082 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:30:21.090 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:30:23.099 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:30:25.110 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#cc99cc]20:30:27.117 XRUN callback (95 skipped).[/COLOR]
 [COLOR=#999999]20:30:27.654 Client deactivated.[/COLOR]
 [COLOR=#999999]20:30:27.661 JACK is stopping...[/COLOR]
 jack main caught signal 15
 [COLOR=#999999]20:30:27.768 JACK was stopped successfully.[/COLOR]
[COLOR=#999999][/COLOR]

---

### Post by Sylos on 2012-06-07
Can you confirm that this isnt related to the track itself (try it with some others)?

All those Xruns are a sure sign that there is a deeper issue here. Im afraid my knowledge is very limited so Im running out of ideas.

If all else fails you could try sudo apt-get purge --remove jackd     then try reinstalling all the jack stuff again from scratch.

Cheers


EDIT: What soundcard are you running?

---

### Post by BcRich on 2012-06-07
Hi Oberon2
In your initial post it seems that JACK was started with non-realtime support, on the IDJC  website it's seems to imply that realtime support in jack is necessary [http://idjc.sourceforge.net/install_first_run.html](http://idjc.sourceforge.net/install_first_run.html)
you can avoid the configuration in that guide as when you installed jackd you should have an option to enable it for realtime processing. This automates manually setting the configuration in that guide (of which I'm not too sure about as my /etc/security/limits.d/audio.conf has the changes listed in the authors' /etc/security/limits.conf ).
Add yourself to the audio group (in "users and groups"), once installation is complete (or you could just do so now, if you already installed Jackd with realtime support).
If you are using pulseaudio with jack you'll need something like pulseaudio-module-jack installed, you can use Ubuntu Software Center or Synaptic to check if you have it installed.

---

