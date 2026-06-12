---
title: "jack going crazy"
date: 2010-09-03
forum: Ubuntu Studio
---

### Post by foxruns on 2010-09-03
ive been using jack for months with my fast track pro for recording audio into ardour and for some reason its decided to stop working
this is what i get in the message window

 p, li { white-space: pre-wrap; }  [COLOR=#990099]21:29:11.707 killall jackd[/COLOR]
 [COLOR=#FF0000]jackd: no process found[/COLOR]
 [COLOR=#999999]21:29:12.117 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]21:29:13.698 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#999999]Cannot connect to server socket[/COLOR]
 [COLOR=#999999]jack server is not running or cannot be started[/COLOR]
 [COLOR=#FF0000]21:29:18.109 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#999999]Cannot connect to server socket[/COLOR]
 [COLOR=#999999]jack server is not running or cannot be started[/COLOR]




im on the latest ubuntu idk what other information anyone would need to reply
anything would help thanks

---

### Post by Pablo_F on 2010-09-03
Hi,

Please paste all the lines from the messages window.  
Cheers! Pablo

---

### Post by foxruns on 2010-09-06
what i posted above is all i get

---

### Post by foxruns on 2010-09-06
alright so for an interface there has always been 'usb 1' and 'fasttrackpro' ive always used usb 1 as the interface and changed the output to fasttrack pro
thats how i used to have it running..
i tried to delete some stuff a while ago and now its not starting when i have fasttrack pro set as the output
if i set everything to usb 1 then jack runs, i just have no playback.
so if anyoneeee can help me figure out how to get jack to recognize the fasttrack as a playback source again it would be much appreciated
help meeee

---

### Post by foxruns on 2010-09-06
what its saying now-

>   p, li { white-space: pre-wrap; }  [COLOR=#FF0000]21:03:25.411 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#CCCC99]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#CCCC99]Cannot connect to server socket[/COLOR]
 [COLOR=#CCCC99]jack server is not running or cannot be started[/COLOR]
 [COLOR=#FF0000]21:03:43.131 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#FF0000]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#FF0000]Cannot connect to server socket[/COLOR]
 [COLOR=#FF0000]jack server is not running or cannot be started[/COLOR]


---

### Post by Pablo_F on 2010-09-07
Hi,

what is the jackd command?

cat .jackdrc

Maybe try to get help at IRC #ubuntustudio channel? It is difficult to help you if you don't provide more info. The message window tells nothing else?

Cheers! Pablo

---

### Post by AutoStatic on 2010-09-07
Please tick 'Verbose messages' in the Setup window of QjackCtl and post the output again. Also please post what is in the field 'Server Path' of that same Setup window.

---

### Post by foxruns on 2010-09-07
thanks auto
here it is guys-

>   p, li { white-space: pre-wrap; }  [COLOR=#999999]21:14:22.600 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]21:14:22.633 Statistics reset.[/COLOR]
 [COLOR=#999999]21:14:22.688 Startup script...[/COLOR]
 [COLOR=#990099]21:14:22.688 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66CC99]21:14:22.694 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]21:14:23.090 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]21:14:23.090 JACK is starting...[/COLOR]
 [COLOR=#990099]21:14:23.090 /usr/bin/jackd -v -p128 -m -dalsa -dhw:4,1 -r44100 -p256 -n2 -D -Phw:4 -m -S[/COLOR]
 [COLOR=#999999]21:14:23.093 JACK was started with PID=13089.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.5
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2009 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 Jack: Create non RT thread
 Jack: ThreadHandler: start
 Jack: JackSocketServerChannel::Open
 Jack: Bind: addr.sun_path /dev/shm/jack_default_1000_0
 Jack: JackSocketServerChannel::BuildPoolTable size = 1
 Jack: JackEngine::Open
 Jack: Connect: addr.sun_path /dev/shm/jack_default_1000_0
 Jack: playback device hw:4,1
 Jack: capture device hw:4,1
 Jack: apparent rate = 44100
 Jack: frames per period = 256
 Jack: playback device hw:4
 Jack: JackDriver::Open capture_driver_name = hw:4,1
 Jack: JackDriver::Open playback_driver_name = hw:4
 Jack: JackEngine::ClientInternalOpen: name = system
 Jack: JackEngine::AllocateRefNum ref = 0
 Jack: JackFifo::Allocate name = /dev/shm/jack_fifo.1000_default_system
 Jack: JackEngine::NotifyAddClient: name = system
 Jack: JackGraphManager::SetBufferSize size = 256
 Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
 Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
 Jack: JackDriver::SetupDriverSync driver sem in flush mode
 control open "hw:4" (No such file or directory)
 control open "hw:4" (No such file or directory)
 audio_reservation_init
 Acquire audio card Audio-1
 creating alsa driver ... hw:4|hw:4,1|256|2|44100|0|0|nomon|swmeter|-|16bit
 control open "hw:4" (No such file or directory)
 Jack: JackDriver::Close
 Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 0
 Jack: JackGraphManager::DisconnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
 Jack: JackEngine::ClientCloseAux ref = 0
 Jack: JackGraphManager::RemoveAllPorts ref = 0
 Jack: JackFifo::Destroy name = /dev/shm/jack_fifo.1000_default_system
 Jack: ~JackDriver
 Cannot initialize driver
 Jack: JackEngine::Close
 Jack: JackClientSocket::Close
 Jack: JackServerSocket::Close /dev/shm/jack_default_1000_0
 Jack: no message buffer overruns
 Jack: JackPosixThread::Stop
 Jack: ThreadHandler: exit
 JackServer::Open() failed with -1
 Jack: Succeeded in unlocking 17370908 byte memory area
 Jack: JackShmMem::delete size = 0 index = 0
 Jack: ~JackDriver
 Jack: JackEngine::~JackEngine
 Jack: Succeeded in unlocking 1012 byte memory area
 Jack: JackShmMem::delete size = 0 index = 1
 Jack: cleaning up shared memory
 Jack: cleaning up files
 Jack: unregistering server `default'
 Failed to start server
 [COLOR=#999999]21:14:23.183 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]21:14:23.183 Post-shutdown script...[/COLOR]
 [COLOR=#990099]21:14:23.183 killall jackd[/COLOR]
 [COLOR=#CCCC99]21:14:23.292 ALSA connection change.[/COLOR]
 jackd: no process found
 [COLOR=#999999]21:14:23.594 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]21:14:25.295 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#FF0000]21:14:29.722 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started


ive seen people put in message info and command line inputs in a special box in the forums i hope you can see it all when i just quote it or idk if quoting it is what they do lol

---

### Post by AutoStatic on 2010-09-08
```
control open "hw:4" (No such file or directory)
control open "hw:4" (No such file or directory)
```You don't have a soundcard with hardware index 4. Could you post the outcome of the terminal command **aplay -l**?

---

### Post by foxruns on 2010-09-08
```
brandon@brandon-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Pro [FastTrack Pro], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 3: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by AutoStatic on 2010-09-08
Then try ```
hw:Pro
``` instead of hw:4, then JACK will always pick the Fast Track Pro.

---

### Post by foxruns on 2010-09-09
i got it to run by shutting everything else that i had open..i never had to do that before but i guess i have to now? i dont know what was changed
thanks for your help guys

---

### Post by AutoStatic on 2010-09-09
What are your current JACK settings? Could you post a screenshot of the QjackCtl Setup window?

---

### Post by foxruns on 2010-09-09
[IMG]http://i56.tinypic.com/2dc92e8.jpg[/IMG]

---

### Post by AutoStatic on 2010-09-10
Thanks! You do need memory locking so it's better to untick that option. And try a Sample Rate of 48000 and a Periods/Buffer of 3. And if you change the hw:4 designations to ```
hw:Pro
``` your Fast Track Pro will be used by JACK automatically, no matter in which USB port you stick it, no matter how many other soundcards are available on your system.

---

### Post by foxruns on 2010-09-10
alright thanks, and how do i do that last part??

---

### Post by Pablo_F on 2010-09-10
Just write it down in the "interface" field, "settings" tab.

---

### Post by foxruns on 2010-09-11
working fine now, thanks both of you

---

