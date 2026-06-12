---
title: "Amplitube Metal with Wine"
date: 2009-04-26
forum: Ubuntu Studio
---

### Post by Snowlord on 2009-04-26
Hi guys,

I've just set up Ubuntu 9.04 and tried to install my beloved Amplitube Metal (virtual guitar-amp) using wine. It starts fine but doesn't seem to read any Audio-signal from ALSA. The program seems to fire up well, but the only sound I hear from my guitar is the one from the ALSA input (basically my clean guitar without any effects and so).

What do I have to do to get the Audio-input from ALSA inside of a wine-program?

I don't know what infos to post, so if you need sth, just tell, I'll provide it as good as I can.

thx in advance for any help,
Snowlord

*EDIT:* Forgot to mention, I also tried to install Amplitube under WinXP in vmware without any result :(

---

### Post by Snowlord on 2009-05-05
anybody? :(

---

### Post by thorgal on 2009-05-05
the only route I know for your type of sgnal processing is JACK and WINEASIO.

- you need to select ALSA in the winecfg audio tab (winecfg allows you to set up your fake windows environment, it's a GUI that comes with wine).

- don't select anything else in the audio tab (even jack).

Then, you need wineasio installed. It's a piece of runtime library that will show up as an asio device in the audio device config of your wine app (Amplitude app of yours).

Make sure you get jackd up and running beforehand.
So, when you select wineasio, it will connect to the jackd server. In the jack graph (try qjackctl GUI frontend and select connection window), you will see your wineasio jack client (Amplitude) and you can connect its output ports to system: playback_1/2 (if your speakers are connected to these system outputs).

That's how one can use wineasio. You can also get a VST version of Amplitude and run it via dssi-vst or fst. But that's another story. Try the wineasio route first.

---

### Post by Snowlord on 2009-05-08
Hi there,

thx for your reply ...

The audio-settings in winecfg are set to ALSA only, but I get stuck at loading the wineasio driver:

```
 regsvr32 wineasio.dll
err:process:__wine_kernel_init boot event wait timed out
Successfully registered DLL wineasio.dll
```

Could this be an issue due to my AMD64-architecture?

cheers,
Snowlord

---

### Post by thorgal on 2009-05-08
I have no idea, I work in a 32bit environment. I would not be surprised if that was the case.

---

### Post by Snowlord on 2009-05-08
God dammit :(

---

### Post by B4RR13N705 on 2009-05-08
Why dont you try "Creox c"? i use this software for my guitar effects, and its native, so you will not have any problems.
```
 sudo apt-get install creox 
```
Also you can try Jack-rack. :guitar:

---

### Post by kruschev on 2009-05-24
I am trying to run Amplitube 2 with wine 1.0.1 and jaunty on a 64bit laptop. the program start and then immediately shows an error message "Microsoft Visual c++ Runtime Error". Can anyone report which versions of wine they got this running with, and the steps they took to get it going? Please help me I am desperate!

---

### Post by thorgal on 2009-05-24
I downloaded the demo and gave it a try. I works fine :) from installation to usage.

My system (32bit):
- Intel MOBO, CPU Intel Core 2 Duo E6600 (2 x 2.4 GHz)
- OS: debian sid
- kernel: 2.6.29.4-rt15 (home-compiled)
- wine 1.1.21, packages for debian sid from winehq
- wineasio 0.7.4 (home compiled)
- jack2 (aka jackdmp) version svn @ 3540 (home compiled)

I tried it as a VST as well through FST and DSSI-VST. It works but not as good. I can hear some noise from time to time.

wine 1.1.21 and wineasio 0.7.4 (or latest svn dev version) are making this windows app work nicely with jack2. The whole windows is responsive and displays info in realtime (VU meter, CPU load). When I play, there's no glitches even at ~ 1ms latency. However, when you change preset, I get a xrun. But that's not happening during the playing so it can be ignored.

Nice little app by the way :)

---

### Post by kruschev on 2009-05-26
Thanks for the tips. I got the latest wine using this howto:

[http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)

and the demo opens fine, and even sees an asio device, but there are no outputs to select in the audio setup. 

i got the wineasio source at [http://sourceforge.net/projects/wineasio](http://sourceforge.net/projects/wineasio)  and the asio sdk (for asio.h) from [http://www.steinberg.net/en/company/3rd_party_developer/sdk_download_portal.html](http://www.steinberg.net/en/company/3rd_party_developer/sdk_download_portal.html)

but i cannot compile my own wineasio because of a compilation error. 

is it possible to get a binary version somewhere for 64 bit somewhere?

also, it'd be fantastic if you could tell me which steps need to be taken in both jackd/amplitube in order to select a different input. as you can guess i am a beginner on both programs... :(

---

### Post by thorgal on 2009-05-26
try to compile this one:

```

svn co https://wineasio.svn.sourceforge.net/svnroot/wineasio/trunk/wineasio64 

```

copy the asio.h file into it and see if it works.

---

### Post by kruschev on 2009-05-30
wow, amazing! :D that compiles. thanks very very much! 

for reference for other suckers like me, i had to copy the steinberg asio.h into the directory created by that svn checkout, compile wineasio, copy the dll with "sudo cp wineasio.dll.so /usr/lib32/wine/", then type regsvr32 wineasio.dll. then i ran "jackd -d alsa" followed by jackbridge (another binary created by the above compile). then you go into qjackctl and lo and behold there is some real stuff to connect due to the appearance of jackbridge. next, in qjackctl you hit connect and connect some inputs and outputs (always connecting from system to jackbridge). then, run amplitube with wine and select asio in sound preferences and you're ready to rock and roll. 

i have one problem though: I can only see my webcam mic in jack, not my normal 3.5mm input jack! hence I cannot connect my guitar... :o

EDIT:

in qjackctl I only see under readable clients (on the left in connections) capture_1 and capture_2 (both under "system"). My webcam has two inputs (I checked using amplitube, both these devices are the webcam capture). hence there should be a third for the 3.5mm input, but it doesn't appear. I'm not sure how to fix this, arecord tells me that:

~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
~$ 

which seems to indicate there are 3 inputs but qjackctl only shows two. what would be super useful is some tool which shows the input meter level on all inputs in realtime using alsa... is there such a thing?

so close but so far!

---

### Post by thorgal on 2009-06-02
hi there.

Don't understand your h/w. Are you using an onboard chip (Intel HDA) ? what's your webcam doing in this ?

If you want to use more than one soundcard, you'd need to use "netjack" on top of jack. Jack1 shoudl come with netjack with stuff called alsa_in and alsa_out. Jack2 (aka jackdmp) comes with an in-process client called net_manager

I have a post about this somewhere in this forum but honestly, you would have to spend some time to retrieve it. I wrote it about 1 or 2 months ago ...

---

### Post by kruschev on 2009-06-06
thorgal, i really appreciate your help, thanks. i have a dell xps m1730 laptop. i'm not sure how helpful these specs are, but:

[http://www.dell.com/content/products/productdetails.aspx/xpsnb_m1730?c=us&l=en&s=dhs](http://www.dell.com/content/products/productdetails.aspx/xpsnb_m1730?c=us&l=en&s=dhs)

like most recent laptops it has a built in webcam with a condenser mic on it. actually this one has two condenser mics, presumably to give people some depth to their skype calls. i can select either of these two inputs in jack, but not the input i need for my guitar, the 3.5mm microphone input (which i want to use until the line6 guitar port i ordered arrives). the only two inputs which appear in jack are the built in mics, and i don't know where to start debugging this. do do you think netjack is the way to go?

EDIT:

perhaps this helps: i ran alsa-info.sh from here: 

[http://www.alsa-project.org/main/index.php/Help_To_Debug](http://www.alsa-project.org/main/index.php/Help_To_Debug)

and it put some debugging info here:

[http://www.alsa-project.org/db/?f=506a6f1fcedb10f5b3ce83b95485cda0ffbace36](http://www.alsa-project.org/db/?f=506a6f1fcedb10f5b3ce83b95485cda0ffbace36)

RE-EDIT:

Note that in qjackctl, under "setup->settings->input device" if i click the little arrow on the right it show two options: hw:0 (HDA Intel) and hw:0,0 (STAC92xx Analog). Hence hw:0,0 seems to be choice, but selecting it and restarting jackd (and jackbridge) has no effect.

---

### Post by thorgal on 2009-06-06
hi there,

mmmm, could you post the output of this terminal command:
```

lspci

```

thanks.

I saw this in your alsa check:
```

Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 14 [100%] [21.00dB] [off]
  Front Right: Capture 14 [100%] [21.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 14 [100%] [21.00dB] [off]
  Front Right: Capture 14 [100%] [21.00dB] [off]

```

capture 1 and capture 2 are off. capture 0 is on.
Not sure how all this works, I use a completely different system (RME HDSP) controlled by a dedicated mixer app (hdspmixer). I am not familiar with the workings of the Intel HDA and integrated webcam mics.

I am a bit surprised that webcam and line in are driven by the same onboard chip but again, it could be perfectly normal.

---

### Post by kruschev on 2009-06-06
here it is...

programs$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
02:00.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
02:01.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8700M GT (rev a1)
05:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
05:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
05:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
05:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
05:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

### Post by thorgal on 2009-06-06
ok, so you've got only one sound chip, namely Intel HDA.
Your ALSA check reported the correct number of IOs.

Could you post your jackd setting ? say you start jackd from qjackctl (the GUI), could you post the output of
```

ps xa | grep jackd

```

I would also be nice to have the output of
```

jack_lsp

```
(which list ports)

and the jackd startup messages (either from the command line or from qjackctl's message window.

thanks.

---

### Post by kruschev on 2009-06-06
Here is the info. First, the process is like this (-Chw:0 naturally changes with the input device selected in qjackctl, to -Chw:0,0):

18282 ?        Ssl    0:00 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -D -Chw:0

Next, jack ports:

wineasio64$ jack_lsp
SSE2 detected
system:capture_1
system:capture_2
system:playback_1
system:playback_2
system:playback_3
system:playback_4
system:playback_5
system:playback_6
system:playback_7
system:playback_8


Finally, qjackctl message window output (is artsshell important? i didn't notice this!):

15:09:15.113 artsshell -q terminate
sh: artsshell: not found
15:09:15.519 Startup script terminated with exit status=32512.
15:09:15.519 JACK is starting...
15:09:15.520 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -D -Chw:0
15:09:15.526 JACK was started with PID=18425.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
15:09:17.677 Server configuration saved to "/home/chwa/.jackdrc".
15:09:17.681 Statistics reset.
15:09:17.697 Client activated.
15:09:17.702 JACK connection change.
15:09:17.708 JACK connection graph change.
SSE2 detected

---

### Post by kruschev on 2009-06-06
By the way, is there a better way to monitor the inputs? Right now I am actually using amplitube through wine to check which input is getting through, which is absurd. Ideal would be a simple program which shows a real time input meter for each and every "readable client" under "system" on the left in qjackctl. surely someone has such a tool?!

---

### Post by thorgal on 2009-06-06
mmm, strange. If ALSA reports 3 inputs and jackd starts up with 2 only, this is definitely weird ...

try to set up jackd so that you run it like this:
```

/usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2

```

I believe you would get this setup in qjackctl by not using explicit "input" and "output" devices. Use the default.

As to monitoring every readable client ports, you can use an app called meterbridge like this:

```

meterbridge -t dpm system:capture_1 system:capture_2 someclient:input_x

```

it will show up with as many strips as you declared ports to listen to and display the levels on the fly.

I am thinking about hacking this app to make it a bit more smart, namely only use the 'dpm' style and connect to every readable audio ports by default, and such that it self-updates when some ports show up or disappear. It shouldn't be too hard given the excellent jack API.

---

### Post by kruschev on 2009-06-06
thanks again thorgal, meterbridge is perfect. alas running your jackd command directly doesn't seem to help - i started qjackctl after running your command, but it still only found system:capture_1 and system:capture_2. 

out of desperation i tried selecting capture_0 and capture_3 in meterbridge but it naturally reported that these cannot be found... i am completely defeated! damn it!!! i am going to make a new partition and install ubuntu studio, let's see. it's a pity as the linux-rt kernel in the repos seems to work perfectly on my system.

---

### Post by kruschev on 2009-06-08
Here's a very sad FYI: I tried Ubuntu studio (amd64 version 9.04, jaunty) and it also fails to see the 3.5mm mic input. But here's the thing: after getting seriously frustrated I decided to try it with windows vista, and it also fails to see the mic, and does exactly the same thing in the you can only see the crappy webcam mics both in the amplitube demo and in e.g. "windows sound recorder". I'm not sure what's next, maybe I need to contact Dell.

I should mention that installing ubuntu studio on the xps m1730 laptop  failed until I tried booting from the dvd WITH THE NETWORK CABLE PLUGGED IN - ie. it seemed to require network connectivity for updated packages to intall properly, otherwise the installer showed a red screen and an error message and aborted.

---

### Post by thorgal on 2009-06-08
wow, that sucks ... so you cannot use your line-in ??

how did you buy the laptop ? with Ubuntu pre-installed ? You gotta blame Dell for that I think. They cannot ship products with half-functioning things, that is, unless your vista install did not include the right sound driver. I know Dell provides driver packages on their website. I have an old Dell Latitude D800 (intel ICH5 ... quite old by now) and I fetched a few stuff from their ftp site (bios update, etc). Talking about BIOS, is it something you could look into ?

---

### Post by kruschev on 2009-06-08
No it came with vista. Regarding the bios, I did check and I cannot see any relevant options... and the laptop is pretty recent so surely a bios update won't help? maybe i could try...

---

### Post by kruschev on 2009-06-30
By the way the mic is easy to fix when you know how. By following these instructions:

[http://ubuntuforums.org/showthread.php?t=616845&highlight=ALC883](http://ubuntuforums.org/showthread.php?t=616845&highlight=ALC883)

I found that I just needed to add the line "options snd-hda-intel probe_mask=1 model=3stack" to the end of /etc/modprobe.d/alsa-base.conf 

Why don't laptop manufacturers put this kind of thing in the manual? Am I missing something?

---

### Post by sgx on 2009-06-30
> **kruschev said:**
> By the way the mic is easy to fix when you know how. By following these instructions:

[http://ubuntuforums.org/showthread.php?t=616845&highlight=ALC883](http://ubuntuforums.org/showthread.php?t=616845&highlight=ALC883)

I found that I just needed to add the line "options snd-hda-intel probe_mask=1 model=3stack" to the end of /etc/modprobe.d/alsa-base.conf 

Why don't laptop manufacturers put this kind of thing in the manual? Am I missing something?

IK Hendrix, Metal etc etc work fine with a desktop athlon64, maudio 24/96 pci, nvidia graphics, wine 1.0, and Reaper/Cantabile, probably EXT2 also.
To keep your sanity, I would try to obtain these basics, keeping in mind an older used maudio 24/96 is the one to go for, not new off-the-shelf, as
they likely will fail. 
To be honest, I now prefer the sounds of Rakarrack for guitar/synth fx, which says a lot, because Hendrix/Metal are bristling with great sound.
I also love using three daisy-chained CMFuzz plugins for punch-n-crunch rythms.
To get you a daw in linux, keep it extremely simple, no-net, no-cams, no 3d, no big office/graphics/video/games. Consider it a music instrument,
use the laptop for the other fun things!

Linux must be used considering hardware first, since drivers are sporadic
and coders rarely have funding. If you buy something without reading that it works for linux people in multiple scenarios, you lose.

---

### Post by kruschev on 2009-07-01
Hmm. I basically have everything working pretty well, except one thing: wine is a bit unstable on amplitube. I actually had to experiment with compiling different wine versions to get it to work at all. Is there something special about wine 1.0? Why do you mention that?

I am also unsure of the best approach to recording. My current idea is: use jack to send a signal from amplitube to the soundcard, for monitoring, while sending a dry signal to ardour which I can record and then fine tune later. Since VST is impossible in 64 bit ardour, I'd use open source plugins to get decent guitar sounds on the existing tracks before recording additional tracks in the same way just described. The open source effects are just to make the existing tracks sound decent as a backing while recording new tracks. Then, for the final mixdown, I'd run the individual tracks through amplitube, send the output to a new track which records the result, repeat for all tracks requiring vst effects, mix down, done. Is this very good? It seems good to me as it retains flexibility, but I may be overlooking some simpler solution. The only really annoying part would be the mixdown phase, but I'd imagine this could be pretty fun regardless, if you have some nice stuff to mix down!

I understand it's a pity to involve vst plugins, and it really messes up the normal ardour pipeline, but I cannot imagine the open source stuff is anywhere near amplitube etc. Am I right?

I actually don't get why the vst plugin people don't support linux - by doing so they would reduce the profits of their competitors who also sell daw packages, and thereby give themselves an advantage? Plus, they would increase their market as people who cannot afford expensive daw programs could use linux and only pay for a couple of plugins!

---

### Post by sgx on 2009-07-01
Hi. My setup is stable, and I can record at will with cantabile 1.2 and reaper 2.56 as vst hosts, and the wine version, though old, works, wineasio version is 7.3, jackd is 1.16-2, qjackctl is 3.4xxx. Stock kernel 2.6.28 is fine for 7 or 8 vsts, but for cpu munchers, I use an RT variant. 
Try rakarrack, 10 fx in one gui, 80 presets for examples, changeable colors on gui,
I run the line out of a Spider amp into the line-in of the maudio card for guitar, and couldn't be happier. Works great for keys and synths too.

I also enjoy using creox for quick tremolo/echo/phaser setups.

Zynaddsubfx is one of the best softsynths anywhere, and running a few
of its guitar patches (being multi-timbral) into rakarrack, is sonic heaven.

For drums, I use EZDrummer, hydrogen, Addictive Drums, and some great free Pettinhouse percussion soundfonts, which when played by the Atomic sequencer from AlgoMusic, are my favourites.
 I never bother with ardour, too many dependancies for my mini-linux, and between reaper, cantabile, and audacity, everything is well covered, and I can play studio engineer, instead of sysadmin/bug-catcher.
I also reboot before recording if I used the net.
Hope you get some good tunes going this week!

---

### Post by sgx on 2009-07-01
> **kruschev said:**
> Hmm. I basically have everything working pretty well, except one thing: wine is a bit unstable on amplitube. I actually had to experiment with compiling different wine versions to get it to work at all. Is there something special about wine 1.0? Why do you mention that?

I am also unsure of the best approach to recording. My current idea is: use jack to send a signal from amplitube to the soundcard, for monitoring, while sending a dry signal to ardour which I can record and then fine tune later. Since VST is impossible in 64 bit ardour, I'd use open source plugins to get decent guitar sounds on the existing tracks before recording additional tracks in the same way just described. The open source effects are just to make the existing tracks sound decent as a backing while recording new tracks. Then, for the final mixdown, I'd run the individual tracks through amplitube, send the output to a new track which records the result, repeat for all tracks requiring vst effects, mix down, done. Is this very good? It seems good to me as it retains flexibility, but I may be overlooking some simpler solution. The only really annoying part would be the mixdown phase, but I'd imagine this could be pretty fun regardless, if you have some nice stuff to mix down!

I understand it's a pity to involve vst plugins, and it really messes up the normal ardour pipeline, but I cannot imagine the open source stuff is anywhere near amplitube etc. Am I right?

I actually don't get why the vst plugin people don't support linux - by doing so they would reduce the profits of their competitors who also sell daw packages, and thereby give themselves an advantage? Plus, they would increase their market as people who cannot afford expensive daw programs could use linux and only pay for a couple of plugins!

Way too complex for recording. I start jackd, start Reaper, load an instrument(s) and fx plugins, and hit the record button. Then I render it,
import it in audacity, edit, normalize, and export as .wav, 320 mbit mp3, and 145-185mbit vbr mp3. I can reload the 320 mp3 back in reaper, and add more sounds if I want. I can also route the wineasio output to Rakarrack or creox for certain favourite fx presets.

Money is the reason vsts are not written for linux. VST codersfeeding their families and paying the bills have a very limited commercial market, one with fierce competiton, not to mention stellar freeware apps being released every few days. Since most of their products already work well enough with wine to allow basic multitrack recording in linux, there is no justification for the professional coder to work for free for a few dozen musicians who actually record in a linux environment, when many skilled freeware devs have the market saturated with great apps. Look at the windoze apps in the latest ComputerMusicMagazine DvD, lots of really great instruments/fx, all bundled up for only $18. Look at rekkerd.org for
amazing freeware, we are very blessed that the wine team, and wineasio team have made their work public, and we can all hit the keys and strings with those plugins.
The reaper forum has a pretty good thread where several linux users present their tips and workarounds, and there are youtubes for new reaper users, it really is only an hour or two of of brain-stretching to have that daw in your system with all the lights flashing. 
Cheers

---

### Post by kruschev on 2009-07-05
> **sgx said:**
> Way too complex for recording. I start jackd, start Reaper, load an instrument(s) and fx plugins, and hit the record button. Then I render it,
import it in audacity, edit, normalize, and export as .wav, 320 mbit mp3, and 145-185mbit vbr mp3. I can reload the 320 mp3 back in reaper, and add more sounds if I want. I can also route the wineasio output to Rakarrack or creox for certain favourite fx presets.


Well, IMHO your approach is more complex than mine, with the exception of the vst part. I can set up the qjackctl patchbay to achieve most of what I want with just a few clicks, all in one program, namely ardour (again, with the exception of the vst/wineasio stuff, ie amplitube). But, I am a (sort of) programmer so maybe I am more courageous than many in this way. It'd be nice if some other experienced folks could add their mustard here.

---

### Post by sgx on 2009-07-05
> **kruschev said:**
> Well, IMHO your approach is more complex than mine, with the exception of the vst part. I can set up the qjackctl patchbay to achieve most of what I want with just a few clicks, all in one program, namely ardour (again, with the exception of the vst/wineasio stuff, ie amplitube). But, I am a (sort of) programmer so maybe I am more courageous than many in this way. It'd be nice if some other experienced folks could add their mustard here.

Here is some good news, as I type, I have the newest Reaper, 3.05, with a legato/retrigger lead patch in ZebraCM, going into 3 daisychained IK Hendrix instances, and also into rakarrack. There also is an audio track receiving the output of my SpiderIII guitar amp, playing simultaneously, to the extent I can switch between the keyboard and guitar, at least. A second musician would be awesome at this point! This is on a stock 2.6.28
kernel, priority in qjackctl is at 60. I made a little track last night with 6 synth plugins, all rendered as expected, so this latest Reaper gets
***** out of ***** stars from me! It may be you could qjack this output into ardour for more processing, but I am happy as a clam at high tide
in the morning. The alien command works to make a .deb from an.rpm, if anyone is interested in rakarrack. 
Cheers

---

