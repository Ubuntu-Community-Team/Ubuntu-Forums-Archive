---
title: "When something locks and crashes; how do I investigate it?"
date: 2013-01-12
forum: Ubuntu Development Version
---

### Post by nomenkultur on 2013-01-12
EDITED:

 lightworks, cheese and kazam were all functioning perfectly in 12.04 and I would like to figure out why they no longer do in 13.04 ... intel centrino platform laptop (all intel chips and drivers)


 Lightworks:

[http://i.imgur.com/3P7mH.png](http://i.imgur.com/3P7mH.png)  

 (logs in page 2)

 12.04 worked well, 13.04 freezes when starting won't even let you force quit.


 Cheese:


 12.04 worked perfectly, 13.04 no input from webcam, shows a blank window


 Kazam:

 12.04 ditto, works fine except it won't accept line-in audio (meaning it only records from microphone and not stereo mixer "monitor of built in stereo" it calls it)


 chromium: John_Swing figured the way to get access to chromium

---

### Post by John_Swing on 2013-01-12
The ppa you mentioned doesn't support raring yet, but you can open software sources, edit the line where you ppa is and change "Distribution" to quantal.  Then you can install the last version of chromium.

---

### Post by zika on 2013-01-12
> **nomenkultur said:**
> keep in mind that I'm new to ubuntu:


 I have a program that was working rather well under ubuntu 12.04.01 and elementary but when I try to start it in 13.04 it simply locks as it's starting up and refuses to force quit

[http://i.imgur.com/3P7mH.png](http://i.imgur.com/3P7mH.png)

 it most have something to do with the hard drive (???) is there a way to find out what is going on?



 
 another question: 

 I was running chromium 24 under ubuntu 12.04 but when I activate 

repository ppa:a-v-shkop/chromium-dev

 and install chromium the same way I did in 12.04, I get chromium 22 instead of 24 :( :( :/


 so I removed it from software center and deleted the repos and someone gave me chromium 26

[http://download-chromium.appspot.com/](http://download-chromium.appspot.com/)

 now the thing is that it's just a zip file

 so I just unzipped it to /etc/ where all the programs seem to be and then run a terminal and type:

./chrome --user-data-dir=~/.config/chromium-canary

 and it launches chromium and it works wonderfully and all is well


 but if I close the terminal chromium quits... if I try to lock the chromium to the taskbar it's useless and there's no 'installed' chromium anywhere to be seen

 what's the terminal command I have to use to make chromium 26 work like chromium 22/24 did?
Starting from terminal would be:
```
./chrome --user-data-dir=~/.config/chromium-canary [COLOR=Red]&[/COLOR]
```

---

### Post by nomenkultur on 2013-01-12
thanks but it launches chromium but if I quit the root terminal it simply shuts chromium down plus doesn't 'install' it (only the terminal launches it).


 ... alas I just have too many programs that lock or not behave properly, I jumped too early on u13.04 gonna wait for the betas 

 take care everyone

---

### Post by zika on 2013-01-12
> **nomenkultur said:**
> thanks but it launches chromium but if I quit the root terminal it simply shuts chromium down plus doesn't 'install' it (only the terminal launches it).


 ... alas I just have too many programs that lock or not behave properly, I jumped too early on u13.04 gonna wait for the betas 

 take care everyoneThat is why I added "[COLOR=Red]&[/COLOR]" to the end of Your cmd-line...
Try it...

---

### Post by cariboo on 2013-01-12
Have you tried pressing Alt-F2, and running zika's command without the &?

When manually installing packages, they should be installed in either /usr/bin/local, or /opt. /etc, is where all the program configuration files are located, but you shouldn't find any executables there.

You said you were running chromium from a root terminal, this may lead to problems, if you actually open a web site that has malicious scripts embedded in the page.

---

### Post by zika on 2013-01-12
> **cariboo907 said:**
> Have you tried pressing Alt-F2, and running zika's command without the &?That is not „my command“ that is his command... ;)
I (maybe wrongly) assumed that he prefers (or is confined to) Terminal command and that he complaints about closing widow app (Chromium) when Terminal window is closed...

---

### Post by cariboo on 2013-01-12
> **zika said:**
> That is not „my command“ that is his command... ;)
I (maybe wrongly) assumed that he prefers (or is confined to) Terminal command and that he complaints about closing widow app (Chromium) when Terminal window is closed...

Opps, I guess I missed that :-D,

---

### Post by VinDSL on 2013-01-12
I must be missing something...

When I check for errors/warnings in Chromium 25 (currently) I simply type:

```
chromium-browser
```

... from CLI.

Does this not work with Chromium 26?

And, when I close the terminal window, Chromium continues to run.

Hrm...

**EDIT**

Oops!  My bad!

Closing the terminal window DOES shutdown Chromium.  Never noticed that before - wonder if it's a new prob.

I'm going hunting for Chromium 26, after I submit this edit.  :)

---

### Post by cariboo on 2013-01-12
What's the difference between the Chromium browser in the ppa's and the repositories? Are there any new features? Or do the ppa versions just have higher version numbers?

---

### Post by zika on 2013-01-13
> **cariboo907 said:**
> Opps, I guess I missed that :-D,:lolflag:
> **cariboo907 said:**
> What's the difference between the Chromium  browser in the ppa's and the repositories? Are there any new features?  Or do the ppa versions just have higher version numbers?As far as I remember they stopped upgrading at some time so ppa's are for newer (and higher) versions...

---

### Post by cariboo on 2013-01-13
There was a new maintainer appointed not to long ago, so the repository version, should be fairly close to the daily version.

**Edit:** I just installed the daily version from the ppa, and I can't see any differences, I guess I'm going to have to look at the changelog. :)

---

### Post by zika on 2013-01-13
> **cariboo907 said:**
> There was a new maintainer appointed not to long ago, so the repository version, should be fairly close to the daily version.

**Edit:** I just installed the daily version from the ppa, and I can't see any differences, I guess I'm going to have to look at the changelog. :)I've not used Chromium for a while, since last reinstall (after couple of years) month or two ago, so... Cutting the number of possible toys to play in order to get some real work done...

---

### Post by nomenkultur on 2013-01-13
chromium 26 

[http://download-chromium.appspot.com/dl/Linux_x64](http://download-chromium.appspot.com/dl/Linux_x64) 

is a no go as you have to launch a terminal and run it from there, it's just a zipped folder


 John Swing figured the way to install chromium 24 and that is perfect:

 I do wish they updated chromium in software center like they do firefox.


 anyway I think what's crashing lightworks is a badly functioning sound driver, I've noticed that programs like kazam aren't able to record line-in audio (monitor of stereo blabla) 

0.190    : R3D SDK license #R86, licensed to 'Lightworks UK LTD'
g_dbus_connection_real_closed:  Remote peer vanished with error: Underlying GIOStream returned 0 bytes  on an async read (g-io-error-quark, 0). Exiting


 I leave the logs here in case someone smarter figures it out

 ```


ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
Compiling shader : /usr/share/lightworks/Shaders/flip.fx .. done
Compiling shader : /usr/share/lightworks/Shaders/posterize.fx .. done
Compiling shader : /usr/share/lightworks/Shaders/flop.fx .. done
Compiling shader : /usr/share/lightworks/Shaders/alphakey.fx .. done
Compiling shader : /usr/share/lightworks/Shaders/ColTemp.fx .. done
Compiling shader : /usr/share/lightworks/Shaders/dve1.fx .. done
Compiling shader : /usr/share/lightworks/Shaders/VideoAnalyserHelpers.fx .. done
Compiling shader : /usr/share/lightworks/Shaders/shapes2.fx .. done
Compiling shader : /usr/share/lightworks/Shaders/null.fx .. done
Compiling shader : /usr/share/lightworks/Shaders/squeeze.fx .. done
Compiling shader : /usr/share/lightworks/Shaders/blend.fx .. ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
done
Compiling shader : /usr/share/lightworks/Shaders/greyscale.fx .. done
Compiling shader : /usr/share/lightworks/Shaders/wipes.fx .. ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Lightworks No. 110 : Beta release Lightworks 11.1.D Build 48522 dated Dec 12 2012
Starting at Fri Jan 11 22:49:37 2013

Available memory      : 1.4 Gb
Total memory          : 2.9 Gb
Virtual Address Range : 2.9 Gb
Number of CPUs        : 2
User has admin rights : No

Setting project base directory /home//Lightworks/Projects/
-0.000   : ---
Plugins loaded: 19 (full: 19, demo: 0, free: 0)
PortAudio version number = 1899
PortAudio version text = 'PortAudio V19-devel (built Oct  8 2012 16:37:35)'
Number of devices = 9
--------------------------------------- device #0
Name                        = HDA Intel: ALC268 Analog (hw:0,0)
Host API                    = ALSA
Is full duplex              = 1
Is input only               = 0
Is output only              = 0
Max inputs = 2, Max outputs = 2
Default low input latency   = 0.01161
Default low output latency  = 0.01161
Default high input latency  = 0.0464399
Default high output latency = 0.0464399
Default sample rate         = 44100
--------------------------------------- device #1
Name                        = sysdefault
Host API                    = ALSA
Is full duplex              = 1
Is input only               = 0
Is output only              = 0
Max inputs = 128, Max outputs = 128
Default low input latency   = 0.0426531
Default low output latency  = 0.0426531
Default high input latency  = 0.0464399
Default high output latency = 0.0464399
Default sample rate         = 44100
--------------------------------------- device #2
Name                        = front
Host API                    = ALSA
Is full duplex              = 0
Is input only               = 0
Is output only              = 1
Max inputs = 0, Max outputs = 2
Default low input latency   = -1
Default low output latency  = 0.01161
Default high input latency  = -1
Default high output latency = 0.0464399
Default sample rate         = 44100
--------------------------------------- device #3
Name                        = surround40
Host API                    = ALSA
Is full duplex              = 0
Is input only               = 0
Is output only              = 1
Max inputs = 0, Max outputs = 2
Default low input latency   = -1
Default low output latency  = 0.01161
Default high input latency  = -1
Default high output latency = 0.0464399
Default sample rate         = 44100
--------------------------------------- device #4
Name                        = surround51
Host API                    = ALSA
Is full duplex              = 0
Is input only               = 0
Is output only              = 1
Max inputs = 0, Max outputs = 2
Default low input latency   = -1
Default low output latency  = 0.01161
Default high input latency  = -1
Default high output latency = 0.0464399
Default sample rate         = 44100
--------------------------------------- device #5
Name                        = surround71
Host API                    = ALSA
Is full duplex              = 0
Is input only               = 0
Is output only              = 1
Max inputs = 0, Max outputs = 2
Default low input latency   = -1
Default low output latency  = 0.01161
Default high input latency  = -1
Default high output latency = 0.0464399
Default sample rate         = 44100
--------------------------------------- device #6
Name                        = pulse
Host API                    = ALSA
Is full duplex              = 1
Is input only               = 0
Is output only              = 0
Max inputs = 32, Max outputs = 32
Default low input latency   = 0.01161
Default low output latency  = 0.01161
Default high input latency  = 0.0464399
Default high output latency = 0.0464399
Default sample rate         = 44100
--------------------------------------- device #7
Name                        = dmix
Host API                    = ALSA
Is full duplex              = 0
Is input only               = 0
Is output only              = 1
Max inputs = 0, Max outputs = 2
Default low input latency   = -1
Default low output latency  = 0.0426667
Default high input latency  = -1
Default high output latency = 0.0426667
Default sample rate         = 48000
--------------------------------------- device #8
[ Default Input, Default Output ]
Name                        = default
Host API                    = ALSA
Is full duplex              = 1
Is input only               = 0
Is output only              = 0
Max inputs = 32, Max outputs = 32
Default low input latency   = 0.01161
Default low output latency  = 0.01161
Default high input latency  = 0.0464399
Default high output latency = 0.0464399
Default sample rate         = 44100
----------------------------------------------
0.184    : PortAudio is using [default](8) for OUTPUT
0.184    : PortAudio is using [default](8) for INPUT
0.190    : R3D SDK library version = 4.2
0.190    : R3D SDK header version  = 4.2
0.190    : Library & header versions match
0.190    : R3D SDK license #R86, licensed to 'Lightworks UK LTD'
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.


Lightworks No. 110 : Beta release Lightworks 11.1.D Build 48522 dated Dec 12 2012
Starting at Sat Jan 12 10:11:09 2013

Available memory      : 990.4 Mb
Total memory          : 2.9 Gb
Virtual Address Range : 2.9 Gb
Number of CPUs        : 2
User has admin rights : No

Setting project base directory /home//Lightworks/Projects/
-0.000   : ---
Plugins loaded: 19 (full: 19, demo: 0, free: 0)
PortAudio version number = 1899
PortAudio version text = 'PortAudio V19-devel (built Oct  8 2012 16:37:35)'
Number of devices = 9
--------------------------------------- device #0
Name                        = HDA Intel: ALC268 Analog (hw:0,0)
Host API                    = ALSA
Is full duplex              = 1
Is input only               = 0
Is output only              = 0
Max inputs = 2, Max outputs = 2
Default low input latency   = 0.01161
Default low output latency  = 0.01161
Default high input latency  = 0.0464399
Default high output latency = 0.0464399
Default sample rate         = 44100
--------------------------------------- device #1
Name                        = sysdefault
Host API                    = ALSA
Is full duplex              = 1
Is input only               = 0
Is output only              = 0
Max inputs = 128, Max outputs = 128
Default low input latency   = 0.0426531
Default low output latency  = 0.0426531
Default high input latency  = 0.0464399
Default high output latency = 0.0464399
Default sample rate         = 44100
--------------------------------------- device #2
Name                        = front
Host API                    = ALSA
Is full duplex              = 0
Is input only               = 0
Is output only              = 1
Max inputs = 0, Max outputs = 2
Default low input latency   = -1
Default low output latency  = 0.01161
Default high input latency  = -1
Default high output latency = 0.0464399
Default sample rate         = 44100
--------------------------------------- device #3
Name                        = surround40
Host API                    = ALSA
Is full duplex              = 0
Is input only               = 0
Is output only              = 1
Max inputs = 0, Max outputs = 2
Default low input latency   = -1
Default low output latency  = 0.01161
Default high input latency  = -1
Default high output latency = 0.0464399
Default sample rate         = 44100
--------------------------------------- device #4
Name                        = surround51
Host API                    = ALSA
Is full duplex              = 0
Is input only               = 0
Is output only              = 1
Max inputs = 0, Max outputs = 2
Default low input latency   = -1
Default low output latency  = 0.01161
Default high input latency  = -1
Default high output latency = 0.0464399
Default sample rate         = 44100
--------------------------------------- device #5
Name                        = surround71
Host API                    = ALSA
Is full duplex              = 0
Is input only               = 0
Is output only              = 1
Max inputs = 0, Max outputs = 2
Default low input latency   = -1
Default low output latency  = 0.01161
Default high input latency  = -1
Default high output latency = 0.0464399
Default sample rate         = 44100
--------------------------------------- device #6
Name                        = pulse
Host API                    = ALSA
Is full duplex              = 1
Is input only               = 0
Is output only              = 0
Max inputs = 32, Max outputs = 32
Default low input latency   = 0.01161
Default low output latency  = 0.01161
Default high input latency  = 0.0464399
Default high output latency = 0.0464399
Default sample rate         = 44100
--------------------------------------- device #7
Name                        = dmix
Host API                    = ALSA
Is full duplex              = 0
Is input only               = 0
Is output only              = 1
Max inputs = 0, Max outputs = 2
Default low input latency   = -1
Default low output latency  = 0.0426667
Default high input latency  = -1
Default high output latency = 0.0426667
Default sample rate         = 48000
--------------------------------------- device #8
[ Default Input, Default Output ]
Name                        = default
Host API                    = ALSA
Is full duplex              = 1
Is input only               = 0
Is output only              = 0
Max inputs = 32, Max outputs = 32
Default low input latency   = 0.01161
Default low output latency  = 0.01161
Default high input latency  = 0.0464399
Default high output latency = 0.0464399
Default sample rate         = 44100
----------------------------------------------


```

---

### Post by zika on 2013-01-13
> **nomenkultur said:**
> chromium 26 

[http://download-chromium.appspot.com/dl/Linux_x64](http://download-chromium.appspot.com/dl/Linux_x64) 

is a no go as you have to launch a terminal and run it from there, it's just a zipped folder
No, You do not have to start it from terminal... You can start it from any prompt (even in GUI) avilable...
@cariboo907 showed You how...
I thought that You had another (plausible) reason for starting it from CLI...
I'm using FF that way for years (nightly channel) and lot of SW is distributed that way...
You've made me DL that archive... There is something fishy about it, I'll investigate further...
I would sincerely avoid that implementation of Chromium... I'd wish I'm wrong...
Any reason why not You use [https://launchpad.net/~a-v-shkop/+archive/chromium-dev](https://launchpad.net/~a-v-shkop/+archive/chromium-dev) ...?

Update&#8321;: No, it is OK... I'm writing this from &#8222;Your&#8220; version of Chromium, started in awesome through Run dialog in GUI, not using Terminal...
Update&#8322;: Now I have to force myself to stop using Chromium again... ;)

---

### Post by VinDSL on 2013-01-13
> **zika said:**
> Any reason why not You use [https://launchpad.net/~a-v-shkop/+archive/chromium-dev](https://launchpad.net/~a-v-shkop/+archive/chromium-dev) ...?
Nope. No reason(s) not to use it.

I've been using Alex's dev PPA for a while now...

> **zika said:**
> Update: Now I have to force myself to stop using Chromium again... ;)
Heh! I must admit, I love Chromium!

The only thing I use Fx for, these days, is DL'ing important things, e.g. via the Fx DTA ([DownThemAll]("http://www.downthemall.net/")) extension.

IMO, Chromium has been outshining Fx for a couple of years, and it just keeps getting better n' better. 

Fx, one the other hand, seems to be sliding off the backside of the table... ;)

---

### Post by zika on 2013-01-13
> **VinDSL said:**
> Nope. No reason(s) not to use it.

I've been using Alex's dev PPA for a while now...


Heh! I must admit, I love Chromium!

The only thing I use Fx for, these days, is DL'ing important things, e.g. via the Fx DTA ([DownThemAll]("http://www.downthemall.net/")) extension.

IMO, Chromium has been outshining Fx for a couple of years, and it just keeps getting better n' better. 

Fx, one the other hand, seems to be sliding off the backside of the table... ;)
Yes, but Alex's dev PPA is a bit outdated... That did drive me away from chromium for some time...
I'm thankfull to @nomenkultur that pointed me to this new resource of newest version of Chromium... It took a while before I've got enough trust to try it on working machine but... It is OK... I must be honest: I love these apps that are only un-zipped... Easy to get rid of them... But those do stay to the last minute of the life of an install...

---

### Post by VinDSL on 2013-01-13
> **zika said:**
> Yes, but Alex's dev PPA is a bit outdated... That did drive me away from chromium for some time...

I'm thankfull to @nomenkultur that pointed me to this new resource of newest version of Chromium...
WoW!  They did it again!  :D

Chromium is getting slicker, all the time!


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-13-jan-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-13-jan-2013-1.png")[/INDENT]

---

### Post by VinDSL on 2013-01-13
> **zika said:**
> No, You do not have to start it from terminal...

You can start it from any prompt (even in GUI) avilable...

@cariboo907 showed You how...
Been playing with Chromium 26 for a few hours.  Works great!  Flash apps run much better than on Chromium 25.

The only extension I cannot live without is Ghostery.  Installed it.  Don't mind ads (kinda like them), but I hate trackers.

Switched to one of my favorite themes -- Ubuntu Black Magic.

Imported my bookmarks, and tweaked a few settings, blah, blah, blah.

As far as starting Chromium 26 goes...

To recap:

[LIST]
[*]I downloaded **[COLOR="Navy"]chromium.zip [/COLOR]**from the link above.
[*]Extracted chromium zip to: **[COLOR="Navy"]/home/vindsl/chrome-linux[/COLOR]**
[*]Renamed resultant folder from: **[COLOR="Navy"]chrome-linux -> .chrome-linux[/COLOR]** (e.g. hid it).
[*]Created an empty config folder: **[COLOR="Navy"]/home/vindsl/.config/chromium-canary[/COLOR]**
[*]Created a .desktop file: **[COLOR="Navy"]/home/vindsl/.local/share/applications/chromium-canary.desktop[/COLOR]**
[*]Here's the command I used:  **[COLOR="Navy"]./.chrome-linux/chrome --user-data-dir=~/.config/chromium-canary %u[/COLOR]**
[*]Made **[COLOR="Navy"]chromium-canary.desktop[/COLOR]** executable: "**[COLOR="Navy"]Allow executing file as program[/COLOR]**" (in Nautilus).
[*]Added: **[COLOR="Navy"]chromium-canary.desktop[/COLOR]** to my Gnome-Shell Favorites.
[/LIST]
Loads, runs, shuts down, just like any other proggie...  ;)

---

### Post by VinDSL on 2013-01-13
w00t!  Native RTC channels work...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-13-jan-2012-3(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-13-jan-2012-3.png")[/INDENT]


Plus, YouTube streaming speeds are up +17%. 

Back on topic... :)

---

### Post by zika on 2013-01-14
> **VinDSL said:**
> Been playing with Chromium 26 for a few hours.  Works great!  Flash apps run much better than on Chromium 25.

The only extension I cannot live without is Ghostery.  Installed it.  Don't mind ads (kinda like them), but I hate trackers.

Switched to one of my favorite themes -- Ubuntu Black Magic.

Imported my bookmarks, and tweaked a few settings, blah, blah, blah.

As far as starting Chromium 26 goes...

To recap:

[LIST]
[*]I downloaded **[COLOR="Navy"]chromium.zip [/COLOR]**from the link above.
[*]Extracted chromium zip to: **[COLOR="Navy"]/home/vindsl/chrome-linux[/COLOR]**
[*]Renamed resultant folder from: **[COLOR="Navy"]chrome-linux -> .chrome-linux[/COLOR]** (e.g. hid it).
[*]Created an empty config folder: **[COLOR="Navy"]/home/vindsl/.config/chromium-canary[/COLOR]**
[*]Created a .desktop file: **[COLOR="Navy"]/home/vindsl/.local/share/applications/chromium-canary.desktop[/COLOR]**
[*]Here's the command I used:  **[COLOR="Navy"]./.chrome-linux/chrome --user-data-dir=~/.config/chromium-canary %u[/COLOR]**
[*]Made **[COLOR="Navy"]chromium-canary.desktop[/COLOR]** executable: "**[COLOR="Navy"]Allow executing file as program[/COLOR]**" (in Nautilus).
[*]Added: **[COLOR="Navy"]chromium-canary.desktop[/COLOR]** to my Gnome-Shell Favorites.
[/LIST]
Loads, runs, shuts down, just like any other proggie...  ;)
Why all that? It works just with ```
~/chromium/chrome
```What am I missing? You have Chromium (&#8222;regularly&#8220;) installed so You do not want it to use same ~/.config folder?
Thank You for reminding me of Ghostery...

---

### Post by VinDSL on 2013-01-14
> **zika said:**
> Why all that?
Well...

My understanding is, there are four levels in the Chrome/Chromium testing hierarchy, and "canary" is untested/not guaranteed to even work.

I thought it might be a good idea to have two completely separate installs, e.g. two different "regular" and "canary" configs.  One install can be updated via a third-party PPA in Synaptic.  The other, I can wash, rinse, and restyle via Archive Manager, e.g. overwrite the core program using the latest .zip file, while leaving the configs unmolested.

Dittos, for the .desktop file(s).  I can load/run one or the other install, or both at the same time, by simply clicking one or the other icon, from the Dash.

Make sense?!?!?

---

### Post by zika on 2013-01-14
> **VinDSL said:**
> Well...

My understanding is, there are four levels in the Chrome/Chromium testing hierarchy, and "canary" is untested/not guaranteed to even work.

I thought it might be a good idea to have two completely separate installs, e.g. two different "regular" and "canary" configs.  One install can be updated via a third-party PPA in Synaptic.  The other, I can wash, rinse, and restyle via Archive Manager, e.g. overwrite the core program using the latest .zip file, while leaving the configs unmolested.

Dittos, for the .desktop file(s).  I can load/run one or the other install, or both at the same time, by simply clicking one or the other icon, from the Dash.

Make sense?!?!?Yes, as I assumed, You have &#8222;regular&#8220; Chromium installed... As CLI-guy I'm ascetically-oriented... No icons, etc... ;)
For example, I still do use Java from a folder where I unpack current EarlyEdition (now it is 8...) and all necessary packages are registered through update-alternatives... So, if I want/need to switch Java off I just rename that folder... Easier than working_with/waiting_for .deb... ;)

---

### Post by VinDSL on 2013-01-14
Heh!  I'll tell you what...

Chromium 26 rawks!  :)

I'm glad the OP started this thread.

I wonder if I should treat that download link as I would a "daily".

Timestamps inside the .zip indicate it's updated frequently.

---

### Post by zika on 2013-01-15
> **VinDSL said:**
> Heh!  I'll tell you what...

Chromium 26 rawks!  :)

I'm glad the OP started this thread.

I wonder if I should treat that download link as I would a "daily".

Timestamps inside the .zip indicate it's updated frequently.Yes... It is even more than daily... Ideal for my CUD (Compulsive Upgrade Disorder)...
With Pepper inside Chromium it becomes a winning combination for weaker machines...
Thank You [@Dundo](http://forum.ubuntu-rs.org/User-dundo) for a push... ;)

---

### Post by VinDSL on 2013-01-19
Thought maybe I should mention this, while I'm thinking about it...  :)

I just upgraded to "Chromium Version 26.0.1389.0 (177850)", but not without some drama.

I used the link (above) but the chrome binary wouldn't fire up.  Hrm...

Doing some forensics, I figured out the link (above) is for the 64-bit Linux version -- and I have a 32-bit machine.

Doh!

Thinking back on what I did last Sunday... I evidently used the parent link:

[INDENT][http://download-chromium.appspot.com/]("http://download-chromium.appspot.com/")[/INDENT]

...which, AFAIK, auto-magically ascertains the correct version to  download, for your particular rig (linux, winders, mac, 32/64 bit, et cetera).

When I used this link to download Canary, everything went as planned.

Just saying...  ;)

---

### Post by VinDSL on 2013-01-19
> **zika said:**
> Thank You for reminding me of Ghostery...
My pleasure!

Just added TinEye -- another must-have extension, for me.  ;)

---

### Post by zika on 2013-01-20
> **VinDSL said:**
> My pleasure!

Just added TinEye -- another must-have extension, for me.  ;)
After playing with chrome://flags I can not catch up with Chrome... It is faster than my eyes... ;)
Now that I've found working way of restoring flags if I overdo it, I'm even feeling comfortable playing with all these tweaks... Nice...
Update&#8321;: Speed increase is big enough to counteract if I turn off any disk cache for Chromium... That was a lacmus (litmus) test for me all these years... This is the (kind of) first time browser passed it...
Update&#8322;: For quite some time I'm ridden with guilt that we've slipped in offtopic in this thread and that I'm one of guilty ones...

---

### Post by VinDSL on 2013-01-20
> **zika said:**
> Update&#8322;: For quite some time I'm ridden with guilt that we've slipped in offtopic in this thread and that I'm one of guilty ones...
IMO, the title is sufficiently broad, and generic, to include our discussion(s).  

It's up to the mods/admins, really, to judge our actions.  It shouldn't be self-imposed/self-limiting.

Defense of Position:  Are we not demonstrating how to investigate Chromium locks and crashes?

I spent many hours conjuring up a workaround so Chromium 26 (.zip install) would not lock/crash et cetera. You came up with a simpler, but equally effective solution.  And, I think we've done a pretty good job of documenting the process.

Of particular interest, to me, is how different testers use different tools.  That is, every magician has their bag of tricks -- different tools, different techniques, different mindsets -- all based on their experiences from the past.

Anyway, yes, now that we've accomplished this feat, cobbled together a workaround, and offered POC (proof-of-concept), it would probably be a good idea to spin-off this discussion to a separate thread, e.g. [INDENT]"HOWTO: Install/Maintain Chromium Canary in Raring"[/INDENT]
... or, whatever.

**EDIT**

Or... Simply change the title of this thread.  ;)

---

### Post by cariboo on 2013-01-20
As far as I'm concerned, the thread is fine as it is, the only thing I'm a bit concerned about, is the the op hasn't chimed in, in a while.

---

### Post by nomenkultur on 2013-01-28
I actually lost interest in chromium 26 as by editing the repos you can install chromium 24 and it's good enough for me.
 
 Cheese and kazaam I'm thinking the sound and webcam problems must be due to drivers and that's not something I can look up.
 
 as far as lightworks goes: 
 
 as is, it is just too alpha and raw .... I mean it's a really good video editing program, the only decent one available for Linux, but in order to get it to work in 13.04 I had to dpkg purge and reinstall, sometimes the install would fail other times it would crash and not start again and require another reinstall but hey I got it working a few times (freezes and crashes were common and it was frustrating actually editing with it) but still
 
[http://youtu.be/P2kzqvPAVt0](http://youtu.be/P2kzqvPAVt0)
 
Unfortunately I was one of the many that ran into problems with anaconda and had to wipe out my hard drive so I lost my u13.04 install.
 
I'm going to install it again but want to install it to an sd card in order to avoid more hard drive partitioning issues

---

### Post by VinDSL on 2013-09-14
> **zika said:**
> Thank You for reminding me of Ghostery...
WoW!

[INDENT][ATTACH=CONFIG]246227[/ATTACH][/INDENT]

How about that new Ghostery 'findings panel' ?!?!?

---

### Post by cariboo on 2013-09-14
vBulletin allows connections to external sites, we have chosen not to enable them. The screenshot is just a small snippet of your profile in the admincp,

---

### Post by VinDSL on 2013-09-14
Hrm...

I'm showing an embedded connection (via javascript) to:

[LIST]
[*][http://connect.facebook.net/en_US/all.js#appId=&xfbml=1](http://connect.facebook.net/en_US/all.js#appId=&xfbml=1)
[/LIST]
And a hard link to:

[LIST]
[*][https://www.facebook.com/ubuntu.forums.official](https://www.facebook.com/ubuntu.forums.official)
[/LIST]

No big deal.  I'm not stirring the pot.  ;)

I was referring to the great new look of the Ghostery findings panel in Chromium/Saucy.

The Ghostery extension used to be sort of a kludge, you know?

---

