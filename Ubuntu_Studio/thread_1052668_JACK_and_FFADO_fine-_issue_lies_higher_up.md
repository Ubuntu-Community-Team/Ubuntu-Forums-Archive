---
title: "JACK and FFADO fine- issue lies higher up"
date: 2009-01-28
forum: Ubuntu Studio
---

### Post by kvk on 2009-01-28
I'm running:

UbuntuStudio 8.10
kernel 2.6.27-3-rt
FFADO 2.0-beta7
JACK 0.116.1
Intel-Penryn E8200 Dual Core processor

ffado-test detects the soundcard - Presonus FP10

Onboard sound has been disabled in the BIOS- only the FP-10 is enabled.

When JACK is started from the JACK Control GUI or the terminal, everything appears to be working smoothly, no Xruns or error messages, but as yet I am unable to either record from the FP-10 in Ardour, or playback from a given audio app- no sound output or input. I have set all Sound Preferences to OSS, as no ALSA support was indicated in the FFADO documentation.

I note that the "RT Patched" status in the FFADO-diag returns FALSE, even though the rt kernel is in operation. 

It also returns:
Base system...
  kernel version............ 2.6.27-3-rt
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... True
  old 1394 stack loaded..... True
  new 1394 stack present.... False
  new 1394 stack loaded..... False
  /dev/raw1394 node present. True
  /dev/raw1394 permissions.. True

with no new 1394 stack present. But it concludes with:

FireWire kernel drivers:
[PASS] Kernel modules present and correctly loaded.
[PASS] /dev/raw1394 node present and accessible.

I sent a .zip file of a number of diagnostics to Pieter a week ago for analysis to figure out if the issue does indeed lie with something in FFADO that I have misconfigured. I know he's busy and overworked, so I can wait a bit more.

I'm wondering if my error lies in not configuring the JACK-app interface for whatever sound app. I'm trying to use. I set the Patchbay to connect all the input/output listings when Ardour was open.

Am I missing something in terms of the ALSA/OSS issue as they relate to JACK? Or have I just not figured out how to run things correctly here?

Thanks so much!!

KVK

---

### Post by Stochastic on 2009-01-28
Just a couple quick troubleshooting questions: 
-Does the light on the FP10 turn Blue?
-are you able to get sound recorded using freebob drivers?
-do you have the realtime option enabled in jack (either the checkbox in qjackctl settings, or the -R flag from command line)?
-can you post a screenshot of whichever app you're using to make the connections to ardour (patchage or qjackctl)?  (after you've made the connections of course)
-can you post a screenshot of ardour as it's recording (or attempting to record)?
-can you record from other jack applications?  if so, which ones?

---

### Post by kvk on 2009-01-28
Hi Stochastic~

I was hoping you'd drop by! :)

Okay~

1. Yes, Das Blinkenlight is blue once JACK is running;

2. No, I wasn't able to do anything under freebob at all- JACK returned a number of X-runs;

3. Yes. realtime is enabled in the qjackctl settings;

6. I've also tried recording using Audacity, but it has the same result as Ardour- inert. No JACK errors, but no input or output.

I'm assuming I need to interface JACK with all my audio applications. Since the onboard sound is disabled, I need to run everything through the FP-10, and the studio monitors (only speakers I have) are connected to the FP-10. Is this an ALSA issue? 

Thanks so much!

EDIT: Screenshots below!

---

### Post by kvk on 2009-01-28
Okay- there are the screenshots! :-)

---

### Post by Stochastic on 2009-01-29
Can you post a screenshot of the "connections" window in qjackctl, not the "patchbay" window?  That's where connections should be made.

Also can you post a screenshot of the Ardour load session / new session dialog that you get as it starts up?

I think I see the source of your error, but these screenshots should clarify/solidify things.

---

### Post by kvk on 2009-01-29
Here are the screenshots.

When Ardour is started, the 'ALSA' error log I posted earlier is also present.

In the Connections tabs, the ALSA windows are empty; the MIDI windows contain fire pcm clients, but they are not connected.

Thanks so much!!

---

### Post by kayosiii on 2009-01-29
I have an FP10 working here on Ubuntu 8.10 with ffado... you had to compile jack from source to get all this to work right and you probably left the preinstalled version of jack in because you didn't want to uninstall all your apps. the problem arises from the fact that all the precompiled apps are linked to the older version of jack so when you start up the newer version of jack they don't connect. To get around this you could compile the apps you need also from source they will link against the newer version of jack.... or you can take to your system with a hatchet (figuratively) - and this is what I did. Figure out the version numbers of libjack in preinstalled version (use synaptic and see what files are in the package)... write these names down. Manually delete the files without removing the package. reinstall the source version of libjack and create symbolic links using the names you wrote down so that you have the old file names actually pointing to the new version of jack.
Ugly and could potentially break things - but it works.

---

### Post by kvk on 2009-01-29
That's a possibility- that I've left some older version operating somewhere. But I did go in and remove everything that had been installed from Synaptic prior to installing and compiling from the source for both JACK and FFADO. And when I compiled from the source I overwrote whatever earlier packages were still existing in the directory, although there shouldn't have been any.

But if you've gotten the FP10 to work (which I haven't yet!) I'll double check just to mke sure.

---

### Post by Stochastic on 2009-01-29
Yeah, it looks like Jack is working with FFADO, but there seems to be an issue with apps finding the running jackd.  Ardour does seem to notice jack, but it's unable to link to it...

What I would recommend as a solution:
WARNING: I have not tried these packages myself, but I do trust them.
-go into the folders where you've built ffado and jack and do ```
make uninstall
```
-do ```
sudo gedit /etc/apt/sources.list
```
-add the following lines to this file ```
deb http://ppa.launchpad.net/khashayar/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/khashayar/ppa/ubuntu intrepid main
```
-do ```
sudo apt-get update
```
**AT THIS POINT YOUR SYSTEM IS IN PERIL, ONLY DO THE FOLLOWING AND NOTHING ELSE!**
-do ```
sudo apt-get install jackd libjack0 ffado-dbus-server ffado-mixer-qt4 ffado-tools libffado2
```
-do ```
sudo gedit /etc/apt/sources.list
```
-remove the two lines you had previously added
-do ```
sudo apt-get update
```
Your system should be back to normal now and you can try running jack

Now, in theory, you could just uninstall jack and ffado, reinstall jack from the repository and use the freebob driver if you want to be safer (this should fix your jack linking problem, and work fine with your FP10), but who wants to be safe and run old software. ;)
If the ffado package still gives you errors, then you can downgrade to the standard jack and freebob from the official repo, and it should all work out.

---

### Post by kvk on 2009-01-29
Things are getting interesting! :-)

Everything ran smoothly (what were those repositories and why so dangerous?) until reboot. At this point, the system hangs both on shut down and reboot, and requires manual shut down and boots automatically into the verbose readout and then into the recovery console. Nothing seems to be harmed, and it might be connected with the new kernel updates, even though the rt kernel isn't touched.

I checked /etc/default/jackd:

#Set to 'yes' to start JACK at boot
START_DAEMON=no

#The jackd process will run under the user
USER=fred (I am assuming this is a default joke from the jack people!)

#Options to pass to jackd:
OPTIONS= " -R -d alsa -d hw"

I haven't yet checked JACK functionality- I'll get to that ASAP this evening.

Thanks so much for the help so far!!

---

### Post by Stochastic on 2009-01-29
> **kvk said:**
> Everything ran smoothly 

Does that mean you were able to start jack?  Could you post the logs of those commands you executed?  Did apt-get want you to install any extra packages?  Why did you reboot (not trying to imply it's bad to reboot, just wanting to know why/when)?

Does behavior continue to happen on reboot/shutdown?

Those repositories contain a number of highly volatile backport packages, so we only wanted the packages described.

I'm worried that you've downloaded some other packages from those repositories (such as alsa libraries...).  That would explain an issue with booting/shutdown.

I'd recommend opening up Synaptic package manager, and marking all jack packages you have for re-install if this behavior continues.  Then use freebob libraries from now on.

---

### Post by kvk on 2009-01-29
Sorry- I should have been more detailed.

By 'smoothly' I meant that the uninstallations went fine (I used 'scons -c uninstall' for the FFADO removal), and the new downloads from the selected repositories went fine as well- nothing blew up.

Once I had removed those repositories, running 

sudo apt-get update

produced a large number of files to be updated/downloaded, including the newer kernel headers and upgrades, after which rebooting was required. It was at that point I noticed the hang.

I just tried starting JACK from the terminal:

```
arctos@arctos:~$ jackd -d firewire
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
02432357892:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.38- built Jan 10 2009 17:21:45
02432762796: Debug (bebob_mixer.cpp)[ 126] addElementForAllFunctionBlocks: Adding elements for functionblocks...
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.

```

All of which look fine.

Trying to open JACK from the JACK Control GUI:

```
17:36:53.565 Patchbay activated.
17:36:53.615 Statistics reset.
17:36:53.617 Could not open ALSA sequencer as a client. ALSA MIDI patchbay will be not available.
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
17:36:55.247 Startup script...
17:36:55.247 artsshell -q terminate
17:36:55.658 Startup script terminated with exit status=256.
17:36:55.658 JACK is starting...
17:36:55.658 /usr/local/bin/jackd -R -P85 -dfirewire -dhw:0 -r44100 -p64 -n3 -o1
17:36:55.661 Could not start JACK. Sorry.
17:36:58.292 JACK was stopped with exit status=255.
17:36:58.292 Post-shutdown script...
17:36:58.292 killall jackd
jackd: no process killed
17:36:58.697 Post-shutdown script terminated with exit status=256.
```

which is a bit confusing.

---

### Post by Stochastic on 2009-01-30
Hm, okay well the good news is that those kernel upgrades etc... came from the official repos.  And likely the packages from the experimental backport PPA repo didn't cause your hang.

It looks like you have jack up and running from the command line.  Can you record?

If qjackctl isn't wanting to start jack for you, but you can get things running via command line, chances are that your settings in qjackctl aren't appropriate.  There could be other issues, but that's where I'd start.  Also the -v or verbose flag in qjackctl settings window often sheds more light on the situation.

---

### Post by kvk on 2009-01-31
Still no luck in configuring qjackctl- I have the same settings I was using before, but it won't run jack.

From the command line, various forms work fine- no Xruns, jack starts, Das Blinkenlight is blue.

But still unable to record or have any input/output. When I try to play something through an app. like Rhythmbox, I get a red stop-sign error message : "Could not open audio device for playback".

When running jack from terminal, opening qjackctl and then the Connections tab now shows no readable input/output ports or readable clients.

---

### Post by Stochastic on 2009-01-31
Please, until we get things working right on jack aware applications, only report things from jack aware apps.

Rhythmbox is not a jack application.

Play soundfiles out of Ardour.  Do you get any sound?  Are the Master Out's from Ardour connected to the 1 & 2 outputs of jack?  Can you post a screenshot from patchage of this?

---

### Post by kvk on 2009-02-02
Okay- my bad. I thought Jack was a general driver applicable to any sound app.

Ardour still refuses to record, and can't play a .wav file because it does not allow any importing of files to occur (screenshot Ardour Add existing audio). After reading on the Ardour site, I thought possibly I was missing a dependency (or more), so I downloaded the list of dependencies needed to run Ardour in addition to those needed to build it from source. I did not, however, try to uninstall and build the newer version from the tarball, as I wanted to check with you first before I went mucking about.

Jack will detect Ardour, however (screenshot JACK-Ardour), and connect with it.

Jack will also detect Audacity, and I am able to open audio files and play them in Audacity, and the sound runs fine through the studio monitors (screenshot JACK-Audacity). Audacity will not record, however. I have set the input and output to JACK-system in the preferences.

I also notice that I am experiencing a number of Xruns in Jack, which wasn't occuring before, but as progress is definitely occuring, I'll take things one at a time.

Thanks so much- I really appreciate your patience and help with this.

---

### Post by Stochastic on 2009-02-02
> **kvk said:**
> Okay- my bad. I thought Jack was a general driver applicable to any sound app.
It is a sound driver, in general terms, but because it is mainly only needed by musicians (for latency) rarely are general applications ever built with support for it.  If you want general sound to come out then you'll need to link ALSA, Pulse, OSS, Xine, or whatever your choice is, to Jack.  Please see other threads (or start your own) for that configuration.
> **kvk said:**
> Ardour still refuses to record, and can't play a .wav file because it does not allow any importing of files to occur (screenshot Ardour Add existing audio). After reading on the Ardour site, I thought possibly I was missing a dependency (or more), so I downloaded the list of dependencies needed to run Ardour in addition to those needed to build it from source. I did not, however, try to uninstall and build the newer version from the tarball, as I wanted to check with you first before I went mucking about.

Jack will detect Ardour, however (screenshot JACK-Ardour), and connect with it.
Okay, the import dialog is a [known bug in Intrepid]("https://bugs.launchpad.net/ubuntu/+source/ardour/+bug/279723") but you should still be able to drag and dropa file into Ardour to have it import and then play.

When you say that Ardour is not allowing you to record, I don't quite understand.  It should record silence even if nothing is connected.

Ardour looks like it's connected to your system's inputs, so I'm guessing your issues are stemming from a lack of understanding of the Ardour interface.  I'm also going by the fact that your recording screenshot you posted earlier didn't have any of the channel strips' record buttons selected.  Please take a quick read through sections [7.3.2]("http://www.out-of-order.ca/tutorials/ardour/#tracks-inputs") and [9]("http://www.out-of-order.ca/tutorials/ardour/#record") of this quick ardour tutorial: [http://www.out-of-order.ca/tutorials/ardour/](http://www.out-of-order.ca/tutorials/ardour/) (the whole thing is worth a skim if you have the extra time).
> **kvk said:**
> Jack will also detect Audacity, and I am able to open audio files and play them in Audacity, and the sound runs fine through the studio monitors (screenshot JACK-Audacity). Audacity will not record, however. I have set the input and output to JACK-system in the preferences.
Okay, so this shows that ffado(or freebob) and Jack are working together and things are successful.  I have a bias against Audacity (for no apparent reason) so I'm not the best to bug shoot your Audacity issues, please look to other threads (or start your own) to solve the Audacity input issue.  I personally use Rezound (you may need to tweak /home/user/.rezound/registry.dat to have jack first in the first setting) for my audio editing.

---

### Post by kvk on 2009-02-05
Thanks so much, Stochastic. It's been a hectic week so I haven't had the chance to test anything yet, but this weekend I'll get to reading through the tutorial and walking through the steps to see if I can get everything up and running, as well as eliminate those pesky Xruns. I really appreciate all your help!!

---

### Post by kvk on 2009-02-08
I got to test things today, and everything went very well! The input levels are rather low, and I'm still getting some Xruns, but I think some basic tweaking and exploring will solve those (I hope!).

Thanks again for all your help and walking me through this!

---

