---
title: "Ableton Live, Wine, Jack, and ALSA: an impossible combination?"
date: 2011-03-12
forum: Ubuntu Studio
---

### Post by iandunham on 2011-03-12
I'm currently running U. Studio 10.10 with Wine 1.3.12. My goal is to be able to Use Ableton Live 8.0.1, which currently runs fully functionally under Wine.

However, the conundrum lies in my inability to use MIDI and audio simultaneously. In the "audio" settings within Wine configuration, if I have Jack selected, then audio works perfectly. If I have ALSA selected, then MIDI works perfectly. However, I have yet to get the two working at the same time. If I select them both, then Jack seems to be dominant and ALSA MIDI connections don't show up at all.

I have attempted Wineasio to no avail, so I'd like to see if anyone might have a solution to this problem.

---

### Post by iandunham on 2011-03-19
bump

---

### Post by sgx on 2011-03-19
Hi, alsa and jackd are team-mates, not alternatives to one another.
Most people will select alsa. 

jackd is configured in the qjackctl gui. Might be called
Jack Connect in some linux. Press the connect button in the lower
right to open the three tab interface for

audio  (for soundcard i/o
midi   (for some midi connections)
alsa   (for the main midi connections, such as midi keyboards)

visit these links to see screenshots and details

[http://qjackctl.sourceforge.net/qjackctl-ss1.html](http://qjackctl.sourceforge.net/qjackctl-ss1.html)

[http://www.64studio.com/quickstart_jack](http://www.64studio.com/quickstart_jack)

There usually is an Alsa tab on the right, these sceens only show audio and midi tabs.

After starting jackd in qjackctl, there is a command

a2jmidid -j default

which opens a connection in the alsa and midi tab, and ms useful or needed for some linux instruments or gear combos.
It can be installed  from synaptic, or by downloading a .deb from a debian package site. Use this command for manual installs

sudo dpkg -i a2jmidid_6+20100828.git60f75d9-1~lucid1_i386.deb

More complex packages with depencies to check, should always be installed with synaptic, when possible.

Cheers

---

### Post by iandunham on 2011-03-20
Thanks for the reply, much appreciated.

I am currently using Jack Connection Kit, and have also tried a2jmidid.

The problem lies in that audio does not work under ALSA. When Live is first started, connections do temporarily show up in the "audio" tab, but then quickly disappear. The message that I get says "subgraph starting at alsa-jack.jackP.7067.2 timed out (subgraph_wait_fd=24, status = 0, state = Running, pollret = 0 revents = 0x0)," even when the timeout is set to 5000 milliseconds.

I have the sneaking suspicion that it has something to do with .asoundrc, but have no idea about how to configure that file.

---

### Post by sgx on 2011-03-20
did you run the command
regsvr32 wineasio.dll after installing wineasio?

Does wineasio show up in the Ableton asio device selector?

(wine commands should not be done as sudo, after the initial
installation of the main wine package)

(also, do wdm and directX for audio work in ableton?)

Is pulseaudio installed and running?

try the command  killall pulseaudio
If there is no text response in the terminal, it has been killed, then try your audio session.

For what it's worth reaper works fine for basic functions. A large topic evolved getting FLStudio to work, so be patient. There are lots
of time zones represented here!  
Cheers

---

### Post by iandunham on 2011-03-22
Hi SGX, thanks for helping me out once again.

I guess the problem starts with wineasio not loading correctly? Although Synaptic has said that it is installed, I get some troublesome output from the "regsvr32 wineasio.dll" command:

Failed to load DLL wineasio.dll

From reading through some forums it seems as though this may mean that the dll can't be found, but it does currently reside in /usr/lib/wine.

---

### Post by sgx on 2011-03-23
If you can, try to uninstall wine and wineasio with synaptic, then reinstall from a repository using synaptic, rather than compiling. You might also try a version 7 vintage wineasio, if the latest one is still at issue. You can rename your .wine folder to something without a dot, before uninstalling, and when the new
.wine folder appears, copy back non system files as desired.

I have even manually deleted the wine files in /usr/lib, /lib
/usr/share on occasion, just to make sure no stragglers or symbolic links got left behind by the removal.

It's also good to install the Microsoft and Webcore fonts packages
found in synaptic, or a PPA, as some windows dodgy apps need them,
and never at a time good for musicians.

Cheers

---

### Post by iandunham on 2011-03-24
Thanks again for your help. After looking around at some of the discussion around FL and Reaper, I finally convinced WINE to use the wineasio.dll - it required using the WINE command line and manually moving the dll to a different directory.

Anyhow, Live is working great with MIDI and Audio - really low latency, and works in conjunction with tools I was using already - LMMS, Hydrogen, Rosegarden, and SooperLooper.

---

### Post by torturedutopian on 2011-06-03
Hi ! 

Can you please explain us how you managed to have both ALSA midi events and JACK PCM  at the same time ? 

I use EarMaster (ear training program) which produces some PCM sound and sends event to fluidsynth. I can't get both to work at the same time : I have to disable (via the "Alsa Driver" key in regedit) the PCM output to get the midi to work properly ; and the other way around.

Any help would be MOST appreciated :-)

---

### Post by megamasha on 2011-07-19
Bump - I'm trying to get truepianos to work with wine, and either midi works but audio stutters with alsa, or audio works, but no midi connections show with jack.

Could you share how you fixed it?

---

### Post by sgx on 2011-07-19
> **megamasha said:**
> Bump - I'm trying to get truepianos to work with wine, and either midi works but audio stutters with alsa, or audio works, but no midi connections show with jack.

Could you share how you fixed it?

Hi, for most people, run winecfg, and in the audio panel choose alsa. This does not prevent jackd from working. wineasio should be installed and run the command 

regsvr32 wineasio.dll

The standalone .exe of truepianos is run with

wine insert-name-of-.exe

Reaper should be installed to host the plugin version. Create this path:

/home/user/.wine/drive_c/Program Files/Steinberg/VstPlugins

...and then run the installer of windows apps. Put the .dll
in the VstPlugins folder.

Your midi controller needs to be chosen in the qjackctl setup page

Input device >
Output device >     click the > widgets and choose your controller.

start jackd before running the standalone, and start reaper to load
the plugin version.

Cheers  (Pianoteq is another good piano option, with linux and windows versions.)

---

