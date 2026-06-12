---
title: "ardour DAW kills any other application using sound output"
date: 2016-01-30
forum: Ubuntu Studio
---

### Post by Nosphky on 2016-01-30
Using UbuntuStudio 14.04.3 and ardour3 3.5.403~dfsg-3~ubuntu14.04.1

I've just started to try to use the ardour DAW and I find that after starting ardour, no other application requiring sound works correctly.  This includes videos in Firefox, music in Audacity and in Audacious.  Not only doesn't the sound work but the file fails to start up in the applications.

Closing ardour seems to leave the jack process still running but even when I stop jack, I still can't get the other applications to function.  My only workaround seems to be to reboot the pc.  

I have heard about jack and pulseaudio  having problems in older versions of Ubuntu but supposed that had been fixed from 13.04 onwards, especially in UbuntuStudio which makes special claims about having the audio set up correctly.

Suggestions about where to look to correct this would be appreciated. Thanks.

---

### Post by yoshii on 2016-02-01
I don't use Ardour so I don't know the exact issue.  But I do know that if I select ALSA in some music jukebox programs, then I can't simultaneous use any other audio programs.  But if I select PulseAudio, then I can share the audio functionality.  I know you may not want to use PulseAudio for Ardour, but that seems to be a similar type of issue.  Maybe this will provide some clues.

---

### Post by Nosphky on 2016-02-02
Thank-you yoshi2.  I've tried a few experiments without understanding everything, it must be said.

I checked on Audacious (a sort of juke box player) and it uses Pulseaudio by default.  I set it to Jack and tried to start Jack from Qjackctl but got a fail - unable to start jack.  Another problem to be investigated.  Tried alsa and Audacious played ok.

I then started Ardour3 DAW.  It automatically starts jack (so that gets me around the problem of starting jack).  Ardour3 plays ok.  I went back into Audacious and it would no longer play using alsa (or pulseaudio).  Changed Audacious to jack and it plays fine.

I closed Ardour3 and Audacious carries on working ok on jack but not on pulseaudio or alsa.

I used Qjackctl to stop jack - Audacious continues to work on jack but not on pulseaudio or alsa.  I tried several times to stop jack without success. Finally I went to system monitor and killed the jack process. That got audacious back to playing under alsa and pulseaudio.

So, for me, this confirms that 'jack' is a bastard.  He doesn't like anything else.  And it looks like I have some problem with starting jack (other than thro Ardour3) and some problem in stopping it using Qjackctl.  

Or maybe I'm misunderstanding the role of Qjackctl ?

---

### Post by marseille2 on 2016-02-02
Some trouble-shooting tips [for a default UbuntuStudio 14.04LTS install]...

If Qjackctl can't start or shut Jackd off... **control Jackd from the command line or use another GUI**.[INDENT]

There have been issues with Ubuntu's 14.04 package (maybe even before). For instance... I can't use it to change the sample/bit rate and period buffer, or restart Jackd. If I try to use the button to stop Jackd, Qjackctl crashes. I have to X out to avoid that. So essentially, I avoid Qjackctl and just use the command line or another GUI. (Personally, I've grown to really like [Cadence]("http://kxstudio.linuxaudio.org/Applications:Cadence"). It's in the [KX-Studio repos]("http://kxstudio.linuxaudio.org/Repositories")).

[/INDENT]


FIRST things first...** delete QjackCtl.conf in /home/user/.config/rncbc.org **and[B] conf.xml in ./config/jack. 
[/B][INDENT]This resets QjackCtl and Jackd, and makes it easy to use Qjackctl's patchbay and connections *later (when things get sorted)*, and start over with Jackd at the sample/bit you want (default is 48khz). 


[/INDENT]
[INDENT]*Example to start Jackd from the CLI using card 4 (USB DAC), and setting sample rate to 44.1khz:*[INDENT]
```
$cat /proc/asound/cards
```

[/INDENT]
[INDENT=2]4 [UA700          ]: USB-Audio - EDIROL UA-700[/INDENT]
[INDENT=2]Roland EDIROL UA-700 at usb-0000:00:12.0-1, full speed[/INDENT]
[INDENT]

```
$ jackd -d alsa -C hw:4 hw:4 -r 441000
```[/INDENT]
[/INDENT]


With PulseAudio ... if you intend on running Jackd and listening to browser audio at the same time ... **pulseaudio's [jack sinks]("http://ubuntuforums.org/showthread.php?t=2261067&p=13208822#post13208822") must be installed**. The package description is [here]("http://packages.ubuntu.com/trusty/pulseaudio-module-jack"). Alternatively, you can kill pulseaudio at boot or login (don't remove it to avoid breaking apps that depend on it), and just use [ALSA loopback]("http://ubuntuforums.org/showthread.php?t=2309696") (it does work with ALSA/Jackd applications and browser audio, including Chrome and Vivaldi).[INDENT]
You can check if you have PA's jack sinks like [this]("http://ubuntuforums.org/showthread.php?t=2266159&p=13232072#post13232072"):
```
[COLOR=#000000][FONT=Ubuntu Mono]$pulseaudio --dump-modules[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]

[/INDENT]
**Install [pasystray]("http://packages.ubuntu.com/trusty/pasystray") to see your sinks and switch between them** as needed (Note: this is an unnecessary work-around for those who don't use pulseaudio).[INDENT]
The sinks in 14.04 LTS may need to be switched back and forth by you. With pasystray, it's a snap. (Note that *apps like audacious and VLC have their own audio device setting* which has nothing to do with pasystray ... but you must *set those apps to match what you're using, i.e. -- Jackd, ALSA, or Pulseaudio*).

If you still find that PA isn't as stable at it should be, sometimes the sinks need to be loaded [manually]("http://ubuntuforums.org/showthread.php?t=2261067&p=13208822#post13208822") with **pacmd**. For added insurance, you can also edit **/etc/pulse/default.pa** to load the sinks you want (technically it should be copy of default.pa in your home folder file, but I found that inconvenient with too many PA resets, which requires deleting PA cookies and folders, then relogging in ... at worst a reboot). 

But long story short... If Jackd is on, simple sound apps like browsers, media players, youtube, etc. -- need to be able to access those jackd sinks or the sound (and sometimes video) won't work. [*This stands in contrast to Ardour, which does not need pulseaudio to run*. So you might want to check if PA is even running after you're done using Jackd. If it's not ... fire it up as usual (provided that PA's daemon is running).]

Once Jackd is turned off, pulseaudio is suppose to seemlessly switch back to the regular sink, but if it doesn't... that's when pasystray comes in handy. It's also great for switching between multiple cards, mics, and bluetooth.[/INDENT]

---

### Post by Nosphky on 2016-02-02
Thanks marseille2.  Your reply is quite complex and gives me lots of stuff to look into.  A slight overload and it'll take me a while to come to terms with this lot in my spare time.  It's all rather disappointing considering the specificity of the UbuntuStudio offer regarding creativity and audio.

In a first time, I have a query :  the "pulseaudio --dump-modules" command gives me a lengthy list which includes modules jack-sink, jack-source and jackdbus-detect.  Does that mean they are loaded and ready for use or just available to be loaded if needed ?

The /etc/pulse/default.pa  has this conditional entry :

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect channels=2
.fail
.endif

I don't find a default.pa in my home directory - there is a .config/pulse/ directory but it's not in there.

---

### Post by Nosphky on 2016-02-02
I've followed your old thread (#2261067) and learned a bit more about how pa works and loading the jack-sink and jack-source modules.

I'll continue the explorations ....

---

### Post by marseille2 on 2016-02-02
By default, there is no "default.pa" in the home directory. Since that's a personal preference, it's a matter of copying the file from /etc/pulse and modifying it to place in the personal account.

Also... you do have the sinks (modules) installed. jack-sink is basically for playback, and jack-source is the mic.

As for the learning curve ... I will say that it's always been there with most of the Debian audio distros (with or without pulseaudio). But the upshot is that I also believe that it's gotten a lot easier. There was a time when we were facing OSS v. ALSA drama to battle with the browser adobe flash situation (LOL). So even though there are lots of negative reviews regarding pulseaudio, it's really not so bad. I think the pains are really about the way the baby sound server was integrated into Ubuntu, as well as the fact that the modules aren't really up to par.  Add to the fact that PA is a 3rd sound layer to cope with, and somebody is bound to pull their hair out if they don't know what's under the hood.


Probably ... we need better documentation on site since so much of it is scattered. Without reading the developer lists and the tutorials from both PA and linuxaudio, as well as checking various forums and askubuntu ... it's very easy to break a system, or rather ... *think* a system is broken when it's not. But if anything... **the problem rarely has anything to do with Jackd** (**it's usually PA or something to do with ALSA**). So IMO ... when understood, Jackd is definitely one of the best things about Linux pro-audio. 


In any case... I'd like to see a version of UbuntuStudio without pulseaudio or XFCE. I just can't get them to play well with Jackd. XFCE ignores my modules (so I use ICEWM), and PA produces distortion with certain manners of recording. So I'd like the option to have an audio distro that just uses ALSA loopback. I figure... UbuntuStudio was always meant for good audio, so why deal with pulseaudio if it's not ready for pro-audio? Plus... Lubuntu supposedly doesn't include PA, so why can't we do the same?

---

### Post by Nosphky on 2016-02-03
After a couple of hours experimentation, I now have an acceptable situation where I can get video from Firefox, sound from audacity and audacious, sound from ardour3.  And I can shut down and restart all or any of them without any adverse effects.  All these applications are now effectively using jack.

All I had to do was load the jack-sink and jack-source modules to Pulseaudio  [$ pactl load-module module-jack-sink  and then $ pactl load-module module-jack-source] 

Next move will be to add the 2 lines to PA's default.pa file and if that succeeds then I'll have 'cracked' the playback part of the audio - at least empirically and without necessarily having understood much of it.

The input side remains to be solved.  I can see (in the Sound Settings Volume Control/ 'Input devices')  the 'PulseAudio jack source' as well as my microphone using Analogue Mono.  If I talk into the mic, I see the input in the Volume Control on the analogue mono but I haven't yet found out how to get it into Ardour3 via jack source.

That looks like all I'll have time for today.  But it all represents progress.

---

### Post by marseille2 on 2016-02-03
Ok, that's a relief! So now the next step is to figure out your Ardour settings.
 

I can't remember too much about version 3, but you can open Qjackctl's 'connect' window (or the GUI you chose if you dropped Qjackctl), and verfiy that Ardour (as a readable audio client) is connected to the 'system' (writeable audio) sound. But for the most part ... you'll deal with your signal routing needs, and control the main volume in Ardour's mixer.

---

### Post by Nosphky on 2016-02-04
Oh that life were so simple !!   Yesterday I was happy that everything was working and that I could hear everything thro jack.  Last thing I did before shutting down was to add the following 2 lines to the end of the /etc/pulse/default.pa file as per thread :   [http://ubuntuforums.org/showthread.php?t=2261067](http://ubuntuforums.org/showthread.php?t=2261067)

load-module module-jack-source
load-module module-jack-sink

Today on booting up, nothing worked. The first thing I noticed was that the little loudspeaker icon on the panel
 (sound settings) was not displayed. Its regular space was there and I could start Audacious from its drop down
 menu but Audacious would not play.  Nor could I reset Audacious playback settings from jack to anything else.

I could not get the system 'sound settings' to display.  System monitor showed 3 Pulseaudio process running 
instead of the usual 1.

Clearly something had gone wrong with Pulseaudio's initialisation.

I restored /etc/pulse/default.pa to its original state and rebooted and everything is ok - back to where
I was yesterday.

So it would appear that adding those 2 additional lines to the end of default.pa was either wrong or not sufficient.

---

### Post by marseille2 on 2016-02-04
If I had to guess... PA needs to be reset.  So it's probably PA's cookies and folders in the home folder trying to remember your settings before logout. As a rule of thumb, when sound goes wrong:


[LIST=1]
[*]PA needs to stop autospawning (meaning ... PA's daemon will keep trying to start, and making a new pulse folder(s) in /home, which prevents us from restoring sound):

```
$ echo autospawn = no > $HOME/.config/pulse/client.conf
``` 
[*]Then kill it:

```
$pulseaudio -k
``` 
[*]its cookie file, and its folders in your home directory need to be deleted. [To see the cookie file, set Thunar to view 'hidden files' to see the pulse cookie file and delete it, if it's there. Delete the pulse folder in /home/user/.config; and *if* there's a pulse directory in /home/user ... get rid of that too.] 
[*]then logout and back-in OR reboot (normally, once your settings are in place and working fine ... resetting PA just requires logging out/in, but when it gets stubborn ... reboot. Just remember that unless you stop PA from autospawing, the reset procedure is in vain (which is why I just kill it on boot, and if needed then I can turn it on manually). OPTIONAL: to turn autospawn off *permanently*, edit /etc/pulse/client.conf:

```
$ sudo gedit /etc/pulse/client.conf
```

then uncomment this line by removing the semi-colon in front of it:

```
autospawn = no
``` 
[/LIST]
 

NOTE: When PA's volumecontrol doesn't pop-up, nothing is actually broken. It's just means that pulseaudio won't act right. In which case, check if it's on before trouble-shooting. It's also important to know if the is daemon running or not, if you keep autospawn in the default ON state.


To find out the various commands to control PA:

```
$ man pulseaudio
``` 

And to get inside even more settings of PA, take a look at its interactive command line:

```
$pacmd
```

---

### Post by Nosphky on 2016-02-05
I thank you for this detailed response, marseille2.  PA was certainly autospawning.

I carried out your steps 1, 2, 3.  Before rebooting, I replaced the 2 lines about loading the jack modules (sink, source) at the bottom of the default.pa file in /etc/pulse/.   I also checked /etc/pulse/client.conf to see what it said about autospawning.  However, there seemed no need to uncomment the line autospawn = no  because there wasn't that line.  

Since you described that part as optional, I rebooted and result was bad.  The loudspeaker icon of PA sound settings was again missing.  I watched in system monitor and saw that there were 3 successive pulseaudio processes, each the child of the previous one.  The 3rd PA process had two children, gconf-helper and a 4th pa process.   There was also a jackd process.

The life of these 4 pa processes and the jackd was only a matter of a few seconds, then they would disappear to reappear a few seconds later with an incresed set of pid numbers.   I left this for about 10 minutes to see if stability would eventually be restored.

I tried audacious but clearly PA was unable to run it.  After about 10 minutes, the pids had gone up from a set of four in the early 2000's to a set in the mid 4000's.

I went back into /etc/pulse/default.pa and removed the 2 lines about loading jack-sink/source modules and stability arrived straight away without needing to reboot.

(BTW - yesterday I did try placing a modified copy of default.pa in my $HOME/.config/pulse/ directory but the result was the same - instability.)

---

### Post by marseille2 on 2016-02-05
Ok, I have a little different set-up going... and no longer use pulseaudio. But I think before I upgraded, I did recomment the lines in default.pa since it seemed that pulseaudio did act a little better. But note that I didn't add anything to bottom of the /etc/pulse/default.pa. In the file, I just uncommented:

```
### use module-udev-detect -- see below -- for doing this automatically)#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
**load-module module-jack-source**
**load-module module-jack-sink**

```

Technically *we shouldn't have to do this*, since the goal with PA is for the sinks to shift seemlessly (as indicated in the /etc/pulse/default.pa file). So I would stick to your method, but use this for reference in case you run into a problem ... with one caveat. If the sinks are in use, Jackd is always on. So if you're system doesn't boot with Jackd on (mine is always on), then you want to keep things the way they are, and *DON'T* uncomment the lines.

---

### Post by Nosphky on 2016-02-06
Hi, marseille2.   It all hangs on a little subtle difference : the smallest things can screw up the system.  

You definitely said in the older thread, in the final post in Jan 2015 :

"I can also confirm that editing **/etc/pulse/default.pa** to [COLOR=#ff0000]add these lines to the end of the file[/COLOR] worked *after* killing then restarting pulseaudio (*see [old thread]("http://ubuntuforums.org/archive/index.php/t-1470407.html")*):

      Code:

     load-module module-jack-source
load-module module-jack-sink"

I took it literally because the red colour seemed to make it important and added the lines right at the end of default.pa   Your 
post to this thread today caused me to look up the block of code you posted and I found it early on in the file (starting 
line 46). But in my file, the last two lines were not present (even commented out).  Out of curiosity (and not being a programmer)
I tried pasting them in where your code sample showed them.

I rebooted - no instability, jackd was started, everything works.  Happiness seems to be restored.

I had made myself a workaround by running a script to load the 2 jack modules to PA at boot startup and that also worked ok but
I think I'll leave it to default.pa to take care of it now.  

Both methods give a system with jackd running at startup whereas previously it wasn't running and I could not get qjackctl to start it.  So this a little bonus.

Thanks for all the help.  I have learned a bit about the audio on the journey. I'll consider this thread 'solved' and see where
linux life leads me.

---

### Post by marseille2 on 2016-02-06
Alright!:) I'm glad you're up and running...

---

