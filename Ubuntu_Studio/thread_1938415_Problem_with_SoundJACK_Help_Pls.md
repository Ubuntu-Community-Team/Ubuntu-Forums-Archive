---
title: "Problem with Sound/JACK Help Pls"
date: 2012-03-09
forum: Ubuntu Studio
---

### Post by quakig on 2012-03-09
I did a fresh and clean installation of Ubuntu Studio on a new partition on my desktop.(I did a MD5 checksum before installtion and there was no error whatsoever during installation)

Everything works well, except that there is no sound and JACK does not start.. gives some kind of socket error.

There is no sound at the time of login/ no sound if i try to play some CD/ online radio music and the Jack does not start. 

My speakers are connected properly and play perfectly well if i switch back to windows.


I am new to Linux and would really appreciate any guidance whatso ever. 

I have played with Jack settings but to no avail. My sound card details are as follows: 


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1705 Analog [VT1705 Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1705 Digital [VT1705 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I tried several configurations in JACK with the input/output device/interface and other parameters.

Am pretty exhausted and nothing seems to work.. Please help

Thanks a Lot:D

---

### Post by quakig on 2012-03-09
Here are some more issues that i see:

When I click on **settings >>linux audio conifuration**
I get the following error: 
> JACK can only be configured with a loaded and stopped studio. Please create a new studio or load and stop an existing one.


The  command  $ sudo qjackctl & gives messages like
> quakig@ubuntu:~$ sudo qjackctl &
[1] 2190
quakig@ubuntu:~$

If i try to start JACK from the GUI, i get the following 2 messages:

> D-BUS: JACK server could not be started. Sorry

Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.


The message box gives the follwoing details
> 
01:32:41.473 Patchbay deactivated.
01:32:41.498 Statistics reset.
01:32:41.529 ALSA connection change.
01:32:41.555 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
01:32:41.741 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
01:32:41.782 ALSA connection graph change.
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: driver "alsa" selected
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Saving settings to "/home/quakig/.config/jack/conf.xml" ...
Sat Mar 10 01:32:41 2012: Starting jack server...
Sat Mar 10 01:32:41 2012: JACK server starting in realtime mode with priority 10
Sat Mar 10 01:32:41 2012: [1m[31mERROR: control open "/dev/dsp" (No such file or directory)[0m
Sat Mar 10 01:32:41 2012: [1m[31mERROR: control open "/dev/dsp" (No such file or directory)[0m
Sat Mar 10 01:32:41 2012: Acquired audio card Audio-1
Sat Mar 10 01:32:41 2012: creating alsa driver ... /dev/dsp|/dev/dsp|1024|15|44100|0|0|hwmon|swmeter|soft-mode|16bit
Sat Mar 10 01:32:41 2012: [1m[31mERROR: control open "/dev/dsp" (No such file or directory)[0m
Sat Mar 10 01:32:41 2012: [1m[31mERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[0m
Sat Mar 10 01:32:41 2012: [1m[31mERROR: Cannot initialize driver[0m
Sat Mar 10 01:32:41 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Sat Mar 10 01:32:41 2012: [1m[31mERROR: Failed to open server[0m
01:33:15.512 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started


---

### Post by gordintoronto on 2012-03-09
What version did you install? Do you see a speaker icon near the top-right of your screen? Can you run Sound Preferences, and see what hardware is being used? Connector? Is it muted, or is the volume turned way down?

Why did you zero in on Jack? I don't use Studio, I don't think I have Jack as part of any of my five different Ubuntu versions.

---

### Post by Sylos on 2012-03-10
There is almost always a conflict between Pulseaudio and Jack in terms of accessing the soundcard when you first install. There are work arounds to make pulse run through jack I think (I never bother, I always remove Pulse immediately as I dont use it - BUT DONT DO THAT UNLESS YOU UNDERSTAND WHAT YOU DOING! - it wont break things but it can really annoy some people to suddenly find the consequences.


Just to see if this is the problem, could you try the following:

```
sudo killall pulseaudio
```

This will kill pulse (only for a limited time as the little pecker keeps respawning!)

Imediately after the first command has executed successfully try launching qjackctl from the terminal.

Post up whatever results you get.

Cheers

---

### Post by sgx on 2012-03-11
> **quakig said:**
> I did a fresh and clean installation 
I tried several configurations in JACK with the input/output device/interface and other parameters.

Am pretty exhausted and nothing seems to work.. Please help

Thanks a Lot:D

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

links 4 and 8 show the
basic setup and config for jackd

look at the output of the commands (below). The portions
in brackets are also shown in qjackctl setup page, in the dropdown lists of

Input Device  >
Output Device  >    click the  > widgets to see and edit the list

Insert the results found in the brackets from your own command output
aplay -l
arecord -l


bash-4.1$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

bash-4.1$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 

Yours should mention your Intel chip.
Cheers

---

### Post by chkneater on 2012-05-30
If the default settings for your in/ouput devices (in the jack setup screen) have not worked, or are not set to default, do so now.  You must quit and restart each session when you make changes or you will Tebow yourself.

After restoring ALL settings to default and restarting, disregard any error messages for the moment and click the start button on the top left.  Does it start?  If no, my next suggestion would be to go to settings and change the input and output devices ONLY!!  You may want to also change the driver to ALSA on the top right to make things simpler to diagnose.  That should put you BACK at square one and at least give some sound.

Another thing, always quit ALL OTHER jack apps first, then quit Jack by clicking the... you guessed it QUIT button.  Believe it or not many people mess their system up by just closing out the GUI not realising Qjackctl still runs in the background, and they wonder 'why no sound'.  Good luck.

---

### Post by chkneater on 2012-05-31
Also, just found this out, starting qjackctl as root from a terminal *usually* (at least for me) fixed this socekt err/ server connection issue

Also it looks like you might need to change your in/out settings - hw:0 should work for both if not default settings, but you can see in the messages it can't create the drivers for Jack to use because it was routed to dev/dsp which is not used commonly.

---

### Post by d_in_Conduct on 2012-06-03
Often when you shut down Jack, jackdbus stays running.  (I think this is a known bug.)  So then you have to go into Task Manager (or just use a terminal window) and kill it.  It shows up in Task Manager as 'jackdbus auto'.

---

### Post by chkneater on 2012-08-11
I've found that jackdbus will mess with pulse *sometimes* but not if jack is not running.

start jack from term: sudo qjactl

Ignore error messages and click setup.  Make sure under interface it either says your card name OR default.  If it says default, check the capture and playback settings directly below the interface and make sure they are routed to the righ card also.  This is the cause of the majority of this type of problem.  Ignoring error messages hit start.

Now, Quit qjacktl by first hitting STOP (you should start jack if it doesn't start automatically before this step) , THEN hitting Quit.

Now, start jack from the accessories menu, and you should have success.  If not, check the interfaces while ignoring the error messages that pop up.  And when you quit jack, STOP  FIRST, then Quit.

This has not failed me once, I can open Hydrogen, Zynadd, Ardour, and play music on Audacious without a single Xrun!!

---

