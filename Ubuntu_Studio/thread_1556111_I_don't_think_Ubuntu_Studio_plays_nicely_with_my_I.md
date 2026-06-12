---
title: "I don't think Ubuntu Studio plays nicely with my Intel..."
date: 2010-08-19
forum: Ubuntu Studio
---

### Post by dave.kts on 2010-08-19
Sorry, i figured the best thing to do is to start a thread, i have a few issues i'd like some assistance with, and i'm wondering if i should abandon ubuntu studio and revert to debian or something. So here goes:
    -installed on my peice together pc, trying to set it up for audio workstation... Intel D915GAG motherboard, Intel P4 3.2Ghz, 2 Sata drives, 1.5 gig ram (dual channel mode), cheap Nvidia/PNY quadro FX 550 vid card...(all i want is dual monitors)

1. Jack audio.. crashes.. used to work the first few times i used it, then it didnt like realtime mode, so i had luck with soft mode, now nothing. just crashes when i try to start. at one point i used synaptic manager to reinstall jack and anything associated. even when it was working it crashed once and took ardour out with it, wasnt even working on much yet.
As soon as i open Jack, my audio mutes from audatious if im playing tunes, and when i try to start it, it gives me this:
 p, li { white-space: pre-wrap; }  > 
[COLOR=#999999]23:56:50.411 Startup script...[/COLOR]
 [COLOR=#990099]23:56:50.412 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]23:56:50.815 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]23:56:50.815 JACK is starting...[/COLOR]
 [COLOR=#990099]23:56:50.816 /usr/bin/jackd -u -dalsa -dhw:0 -r48000 -p1024 -n2 -s[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    1157463
 [COLOR=#999999]23:56:50.843 JACK was started with PID=4787.[/COLOR]
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 48000
 creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|soft-mode|32bit
 control device hw:0
 [COLOR=#999999]23:56:51.153 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]23:56:51.155 Post-shutdown script...[/COLOR]
 [COLOR=#990099]23:56:51.156 killall jackd[/COLOR]
 [COLOR=#cc3366]23:56:51.157 JACK has crashed.[/COLOR]
 jackd: no process found
 [COLOR=#999999]23:56:51.566 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]23:56:53.867 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
and that "limits.conf" file isn't in my system

2. cant use xinerama mode, probably an issue with nvidia driver. It kills compiz and if the screensaver starts, it works the snot out of the processor and is all freezy... same thing with just having the preview window open, trying to deselect the screensaver or view different ones, just locks the whole thing up to a hard shut down... so i default to the double desktop setup with the two monitors, the screensaver was working real good and smooth but all of a sudden it starts acting up, running bad and eating the cpu again, and if i try the fullscreen preview, i get a jumble of pixellated madness with the toolbar broken up across the screen.  Log out and in and it might or might not work again. Compiz seems to be running fine as long as xinerama isnt selected.

3. Hibernation is kinda shady starting back up, sometimes have to just reboot. Dont seep to have a "sleep" option for this system.

4. i'm not sure what the right settings should be for the "ubuntu studio controls", or the right jack settings for my setup, i.e. memlock and latency settings..

5. I cant for the life of me figure out how to use the 5.1 channel audio built into my motherboard. somehow im supposed to be able to switch the jack stack configuration on the board to use 6 channel line out instead of the mic,line-out, line-in setup. (realtec ALC860, Intel HDA.. yes, ALC860, not 880. I cant find alc 860 info, google cant, the chip doesnt exist in time i guess haha. 

Well, i think i actually forgot something, but I'd love some help as it's kind of been a bit of a struggle learning linux, the whole dual-boot setup, learning the proper order for installing new drives on a new system with new software, and How grub works and how easy it is to do something in the wrong order! I really hope to get this running smooth, like i said most important is to get all the audio correct on it. I really dont want to have to but Windows 7, this seems promising and i want to use this..
Oh yeah, advantages of 64 bit, anyone? im compatible, but dont know if i should be concerned about it. 32 bit here.

---

### Post by AutoStatic on 2010-08-19
For your soundcard, try installing the alsa-backports package.

---

### Post by dave.kts on 2010-08-19
> 
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM surround51
Playback open error: -2,No such file or directory
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM surround51
Playback open error: -2,No such file or directory


-Trying to run the audio test found on alsa webpage. I get a lot of that, thats just a sample.

so the alsa-backports... im not sure what i should try, i see a list of different packages, but they all tell me the following:
> Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.

This package contains modules supplied by Ubuntu for Linux 2.6.32 ALSA
snapshots from [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

You likely do not want to install this package directly. Instead, install
the linux-backports-modules-alsa-generic meta-package, which will ensure that upgrades work
correctly, and that supporting packages are also installed.so i think im missing something cause i cant find this meta package its referring to. maybe im overlooking something simple. 
Also wondering if i need to be using the front audio panel connection on my board to enable the 5.1 on the rear jacks.

---

### Post by dave.kts on 2010-08-24
so now totem crashes upon loading any video, dvd, any size. all i can do on this machine now is surf and play tunes on audacity. Any advise? this is the 3rd or 4rth version of linux ive tried on this thing, each having pretty major problems and/or crashing completely. Lucid seemed to be working alright, not perfect from the beginning, but progressively worse. spend half my time on this getting everything straightened out.
Help me??  i dont wanna give up but now i gotta use XP to multitrack :(

---

### Post by AutoStatic on 2010-08-25
> **dave.kts said:**
> so the alsa-backports... im not sure what i should try, i see a list of different packages, but they all tell me the following:
so i think im missing something cause i cant find this meta package its referring to.You need **linux-backports-modules-alsa-lucid-generic**

---

### Post by byro-byro on 2010-08-25
My case is similar to those. The card is Intel 82801AA-ICH on MacBook  (white) and emulating Ubuntu 10.04 with vbox. 
My intent is to work  with QJackctl/Qsynth/Rosegarden. But even after many procedures I get no  sound.
 Let's try to organize by theme.
System - Following Ubuntu  Studio Preparation I made downloads and configs. In limits.conf I paste  rtprio... (although I see that if you're on 10.04 it's should be on  audio.conf). In alsa-base I put 'options snd_hda-intel index=0'. Maybe  something more ... 
Alsa - Testing on Terminal 'aplay xxx.wav' its  working. Is good to check alsamixer to if something is mutted.  
Jack  - At moment I don't need real time and, as it was crashing soon after  starts, I uncheck RT on Jack setup. I read about problems related with  pulseaudio - I purge it. (Don't know if it is related but the  loudspeaker on the menu disappear and going on pref/sounds the pannel  didn't come - just a sound test, and it's fine - is sounding.). Jack  seems working.
Qsynth - in the setup when I choose soundfonts  (fluidsynth) - comes a message "  p, li { white-space: pre-wrap; }  ALSA lib  pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave "


I get no sound in Rosegarden and Ardour. Login is  sounding, also for alsa test an system sound test.


Excuse-me I was long


Thanks for any help


Marcelo

---

### Post by AutoStatic on 2010-08-26
> **byro-byro said:**
> My case is similar to those. The card is Intel 82801AA-ICH on MacBook  (white) and emulating Ubuntu 10.04 with vbox.That's a completely diffent situation. You're running Ubuntu in a virtual machine so Ubuntu doesn't talk to the hardware directly.

---

### Post by byro-byro on 2010-08-26
you mean the virtual machine is causing the problems ?
As I said sounds of system are working (login, sound test...).
With "completely different situation" do you thing it's will be better  in a new thread ? 

thanks for your reply

---

### Post by dave.kts on 2010-09-04
thanks for your advise autostatic, hopefully you can work me through this.. so i installed that package but im still not sure where these options can be changed. When i boot XP, I can open my realtec console and switch things around, allowing me to play audio from a movie in WMP Classic through my big screen monitor 2 while i browse and play music routed through my main speakers and monitor 1... thats what im looking for here.

 But really thats the last i want to get working, i need to figure out why Jack is corrupted and i also noticed i cant open my pulse audio device manager now, it does nothing. Maybe i need to purge pulse audio from my system and see what happens, but then im confused on hoew i'd be able to adjust volumes on my system.

And i still cant play vids of any considerable resolution, instantly crashes totem.
Also, My login always comes up on my second monitor, halfway across the room, which is reeealy annoying. I cant do anything to change it, its sending the primary monitor thru the second vid card connector, not the first. Completely opposite of XP.

So anyone want to walk me through this, or should i re-install, or should i try ordering the Debian DVD set and try that out?
C'mon, help me out! with all these issues it's kept me right off of ubuntu untill i can fix this :(

---

### Post by cchhrriiss121212 on 2010-09-04
Given all the issues you are having over multiple installs I would say that either:
You're suffering hardware issues - your SATA drives might be getting on a bit, or possibly Linux just does not co-operate well with your specific setup, which sometimes happens.
You are not burning your images to CD/DVD at a slow enough speed (always use minimum).

If you still want to use Ubuntu or Debian then try getting the simple things going one at a time, and start thinking about dual monitors and multiple sound outputs once you have the basics down.

You can start separate threads for each issue in the relevant categories, i.e. hibernation issues might go in general help whereas totem crashing could go in multimedia & video. That way you get better help.  

But as you've said audio is the main thing we can continue with that: 
Are you getting any basic sounds from your system? Things like rhythmbox etc.
If not, is your soundcard displayed when you put aplay -l into a terminal window?

---

### Post by dave.kts on 2010-09-04
Yes, i have system, login, and audio playback sounds, and i can play a small res. vid file from my phone on totem, audio works, but any decent resolution crashes totem.
As soon as i open jack audio (without even starting the service yet) all audio output thru my speakers is dropped. if i try to "start" jack, it crashes.

at one point, everything was working the way it should, i just hadnt got into multitracking yet. I started playing around with one track on ardour in realtime, and it had a major crash, cause after that it never really worked again. The dual monitor setup works fine now, except annoyingly the main monitor (xscreen0) is displayed thru screen 2 out of my nvidia card. so i have to turn on my 2nd tv to login... but thats minor for now.


david@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

thats my soundcard.

is it possible my realtime kernal is bad or not cooperating with my pc? im not sure how all that works.

Today ive been surfing, playing audacity, encoding a dvd on OGMrip, all at the same time and everything is smooth.

---

### Post by cchhrriiss121212 on 2010-09-04
Glad to see you have got an improvement.
> is it possible my realtime kernal is bad or not cooperating with my pc? im not sure how all that works.
Yes that is a possibility, I had problems with the official rt kernel a couple releases back. You can try out other ones from [this PPA]("https://launchpad.net/%7Eabogani/+archive/ppa").

Before you do that I would delete your ~/.jackdrc file and do a reinstall of jack, then try starting it up again.

---

### Post by dave.kts on 2010-09-04
ill try reinstalling jack but im beginning to think its deeper than that. Now when going thru songs i was going thru and clicking opening thru totem by default, was playing them fine but i got to a certain album and it crashed after 1 second of playback. now efery song i open in totem crashes after a second, but plays fine on audacity. ill let you know if i have any luck with the kernal i guess, unless any other suggestions first.

---

### Post by dave.kts on 2010-09-05
i searched for that file and doesnt seem to exist... and i checked that link for the kernals but seems to be no download links... im wondering if these are available thru the synaptic manager? should i just try the low latency one instead of realtime?

just my logic, and limited understanding of computers, but seems to me maybe the memory isnt getting assigned correctly or something of that nature. I'm pretty sure i've installed the intel microcode package, and i think most of these problems also started happening after i threw in the nvidia card, but im not certain.

Ill work on this tonight i think, thanks everyone so far for your suggestions. 

And AutoStatic, bro is that a guitar or a bass?  pretty wild!

---

### Post by cchhrriiss121212 on 2010-09-05
To add a PPA just click the link on that page that says: ([Read about installing]("https://launchpad.net/+help/soyuz/ppa-sources-list.html")) and follow the steps.
After that the new packages will show up in synaptic package manager. I would try to use the rt kernel first and see how that goes.

I should have explained that ~/.jackdrc is a hidden file in your home folder (press ctrl+h to show them). For future reference ~/ is shorthand for your home folder, and any file that has a . as a prefix will be hidden.

---

