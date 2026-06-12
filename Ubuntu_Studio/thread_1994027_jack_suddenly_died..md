---
title: "jack suddenly died."
date: 2012-06-02
forum: Ubuntu Studio
---

### Post by mjhouska on 2012-06-02
Not sure what i did. Alsa seems to still work(web audio and stuf).
i'm running studio 12.04
here's the qjack messages:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]13:54:58.797 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]13:54:58.812 Statistics reset.[/COLOR]
 [COLOR=#cccc99]13:54:58.823 ALSA connection change.[/COLOR]
 [COLOR=#999999]13:54:58.832 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]13:54:58.839 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]13:55:03.952 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Sat Jun  2 13:55:03 2012: Starting jack server...
 Sat Jun  2 13:55:03 2012: JACK server starting in realtime mode with priority 10
 Sat Jun  2 13:55:03 2012: control device hw:0
 Sat Jun  2 13:55:03 2012: control device hw:0
 Sat Jun  2 13:55:03 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory[0m
 Sat Jun  2 13:55:03 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
 Sat Jun  2 13:55:03 2012: [1m[31mERROR: Cannot initialize driver[0m
 Sat Jun  2 13:55:03 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
 Sat Jun  2 13:55:03 2012: [1m[31mERROR: Failed to open server[0m
 Sat Jun  2 13:55:05 2012: Saving settings to "/home/mjhouska/.config/jack/conf.xml" ...
 [COLOR=#ff0000]13:55:14.995 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started

i get this after hitting the start button in qjackctl

---

### Post by mjhouska on 2012-06-02
my MOBO is a Biostar A790L3G with the realtek ALC662 chipset .

---

### Post by mjhouska on 2012-06-02
now it appears to be workingafter i set frames to 512 but it wont let me go lower  i have a 3ghz 64 bit dual core though. weird
\

---

### Post by mjhouska on 2012-06-02
spoke too soon getting xruns. moving back  frames to 1024. my chippset supports 96 khz sample rate though too. any help to optimise jack would be apreciated.

---

### Post by sgx on 2012-06-02
Hi, look at the wiki, links 4 and 8 explain jackd
and qjackctl

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

run commands

aplay -l
arecord -l
cat /proc/asound/cards

the output should show your soundcard in brackets.
this name can be used (without the brackets) in qjackctl.

Click Setup on the main qjackctl gui. On the right side of the
setup panel

Input device >
Output device >

click the > widgets for the dropdown list, you should see
something similar to what is in brackets, or you can type it in.

xruns that are inaudible, are not important, and 96khz should
be tried after 44100 is shown to work. If you have a usb
soundcard, qjackctl Periods/Buffer setting should be 3.

Cheers

---

### Post by mjhouska on 2012-06-19
sorry for the delay. life stuf.  her's my output from the commands:

michael@michael-A780L3G:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
michael@michael-A780L3G:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
michael@michael-A780L3G:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe8f4000 irq 16

---

### Post by mjhouska on 2012-06-19
i used analog out to my  speakers so i picked hw:0,0

And i will use the front mic jack for input so i'm guesssing  hw:0.2

---

### Post by mjhouska on 2012-06-19
oops! now i'm getting this even with the default config. even after a fresh reinstall :(

---

### Post by mjhouska on 2012-06-19
p, li { white-space: pre-wrap; }  [COLOR=#999999]10:00:54.432 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]10:00:54.447 Statistics reset.[/COLOR]
 [COLOR=#cccc99]10:00:54.453 ALSA connection change.[/COLOR]
 [COLOR=#999999]10:00:54.462 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]10:00:54.471 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]10:00:56.485 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Tue Jun 19 10:00:56 2012: Starting jack server...
 Tue Jun 19 10:00:56 2012: JACK server starting in realtime mode with priority 10
 Tue Jun 19 10:00:56 2012: Jack: Create non RT thread
 Tue Jun 19 10:00:56 2012: Jack: ThreadHandler: start
 Tue Jun 19 10:00:56 2012: Jack: apparent rate = 44100
 Tue Jun 19 10:00:56 2012: Jack: frames per period = 1024
 Tue Jun 19 10:00:56 2012: Jack: capture device hw:0,2
 Tue Jun 19 10:00:56 2012: Jack: playback device hw:0,0
 Tue Jun 19 10:00:56 2012: Jack: playback device hw:0
 Tue Jun 19 10:00:56 2012: Jack: capture device hw:0
 Tue Jun 19 10:00:56 2012: Jack: JackDriver::Open capture_driver_name = hw:0
 Tue Jun 19 10:00:56 2012: Jack: JackDriver::Open playback_driver_name = hw:0
 Tue Jun 19 10:00:56 2012: Jack: Check protocol client = 8 server = 8
 Tue Jun 19 10:00:56 2012: Jack: JackEngine::ClientInternalOpen: name = system
 Tue Jun 19 10:00:56 2012: Jack: JackEngine::AllocateRefNum ref = 0
 Tue Jun 19 10:00:56 2012: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
 Tue Jun 19 10:00:56 2012: Jack: JackEngine::NotifyAddClient: name = system
 Tue Jun 19 10:00:56 2012: Jack: JackGraphManager::SetBufferSize size = 1024
 Tue Jun 19 10:00:56 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
 Tue Jun 19 10:00:56 2012: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
 Tue Jun 19 10:00:56 2012: Jack: JackDriver::SetupDriverSync driver sem in flush mode
 Tue Jun 19 10:00:56 2012: control device hw:0
 Tue Jun 19 10:00:56 2012: control device hw:0
 Tue Jun 19 10:00:56 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory[0m
 Tue Jun 19 10:00:56 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
 Tue Jun 19 10:00:56 2012: Jack: ~JackDriver
 Tue Jun 19 10:00:56 2012: [1m[31mERROR: Cannot initialize driver[0m
 Tue Jun 19 10:00:56 2012: Jack: no message buffer overruns
 Tue Jun 19 10:00:56 2012: Jack: JackPosixThread::Stop
 Tue Jun 19 10:00:56 2012: Jack: ThreadHandler: exit
 Tue Jun 19 10:00:56 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Tue Jun 19 10:00:56 2012: Jack: Succeeded in unlocking 82246176 byte memory area
 Tue Jun 19 10:00:56 2012: Jack: JackShmMem::delete size = 0 index = 0
 Tue Jun 19 10:00:56 2012: Jack: ~JackDriver
 Tue Jun 19 10:00:56 2012: Jack: Succeeded in unlocking 1040 byte memory area
 Tue Jun 19 10:00:56 2012: Jack: JackShmMem::delete size = 0 index = 1
 Tue Jun 19 10:00:56 2012: Jack: cleaning up shared memory
 Tue Jun 19 10:00:56 2012: Jack: cleaning up files
 Tue Jun 19 10:00:56 2012: Jack: unregistering server `default'
 Tue Jun 19 10:00:56 2012: [1m[31mERROR: Failed to open server[0m
 Tue Jun 19 10:00:58 2012: Saving settings to "/home/michael/.config/jack/conf.xml" ...
 [COLOR=#ff0000]10:01:05.180 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started

---

### Post by mjhouska on 2012-06-19
i wonder what directory it is looking for?

---

### Post by mjhouska on 2012-06-19
still no jack but sound has been working great. i hope it's something simple.  kill pulse on jack startup maybe?

---

### Post by mjhouska on 2012-06-19
started qjack wile pithos was playing and it killed sound. closed qjack and sound didn't return

---

### Post by mjhouska on 2012-06-19
> **mjhouska said:**
> started qjack wile pithos was playing and it killed sound. closed qjack and sound didn't return


fyi i reinstalled studio 12.04 without home directory encryption and  a;so set it toautologin and jack now works with it's default config. i goT  A FEELING IT WAS HOME DRECTORY encryption as that was the only difference from my first installation of studio 12.04 lts    where jack worked. i will nowset the I/0 as you requested and save it as a differet config

---

### Post by mjhouska on 2012-06-19
btw pithos sound did come back only after a reboot. if i knew the proper command, prolly wouldn't have neede a reboot.

---

### Post by mjhouska on 2012-06-19
if i didn't understand the possibilities  and flexibilityof this trio of terror audio system known as ALSA, PULSE, JACK , i  wouldn't be bothered. it is insanely ****** up complicated **** man

---

### Post by mjhouska on 2012-06-20
went to 48000  seems fine now. thanks.

---

