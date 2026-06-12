---
title: "complete novice help with jack support"
date: 2010-08-17
forum: Ubuntu Studio
---

### Post by simieon on 2010-08-17
hello and thanks in advance.
im not currently running the ubunto studio release, but i figured that since im trying to use the software included in the release this would be the right fora to ask for help in.

as for background knowledge, im running ubunto on my laptop (not my stationary) intel dual core cpu (should be 64bit compatible, but running 32bit i386 ubunto 10.4 LTS just to be safe), trying to produce on the onboard sound card. using the laptop is an experiment, if i can make it work i will make a full switch from micro****ed based software.
after a few months familiarizing myself with linux, basic use of the terminal etc, and custumizing my gnome environment ive come to like it, and decided it was about time to start producing music on it.

here comes the problem: im using the alsa drivers, input/output on one device. ardour tells me it could not start JACK and refuses to launch, lmms plain doesnt have any playback on audio, except for when playing sample sound of samples, hydrogen works without issues, muse rosegarden and sweep doesnt have any audio output at all. 

im assuming that ive done something wrong with jack (software center - search - JACK - installed everything that looked like i might need it), im allso assuming that it isnt a driver issue, as i have audio support on games, videos, and music playback without even trying. 

any help i could get would be appriciated, and will be tried, i am currently downloading both the 64bit and 32 bit ubunto studio release, but id rather not reformat my drive, as ive just managed to get it looking and feeling the way i like it :D

edit: spellchecking

---

### Post by cchhrriiss121212 on 2010-08-17
Jack is a sound server, and Ubuntu runs another sound server called pulse by default, so you need to tell jack when to take over and when to let pulse resume. You can do this using the GUI for jack called qjackctl, which you have already installed from the sound of it. When you open qjackctl press start, which will likely give you an error message saying the jack is not configured.

[This guide]("https://help.ubuntu.com/community/UbuntuStudioPreparation") will be help to you, although you may find it confusing at first. 
This step is essential (edited from the guide):
> Since Ubuntu 10.04 the permissions to enable real time access for "audio" group users are set in the file /etc/security/limits.d/audio.conf. In versions prior to 10.04 these settings were done in /etc/security/limits.conf

Open a terminal and paste this:
```
sudo gedit /etc/security/limits.d/audio.conf
```
Then paste these lines into the file:
```
@audio - rtprio 99 
@audio - memlock unlimited
``` 

Don't forget to add your username to the "audio" group (System - Administration - Users and Groups).
After this jack should run OK on default settings, then you can try lowering the latency in the settings window of qjackctl. You can get even lower latency if you install an rt kernel which is what studio uses.

You also do not need download 2 studio images, you can upgrade your existing Ubuntu into something like studio (or exactly like it if you install the meta package in the repos).

---

### Post by simieon on 2010-08-17
besides from two minor issues, i found your help to be more than just a little usefull.  /bow

im currently installing the packages i need to update from 10.04lts to 10.04 lts studio.

/quote First of all, check on this page if your card is supported : [http://alsa-project.org/main/index.php/Matrix:Main](http://alsa-project.org/main/index.php/Matrix:Main) /quote
this part is a bit of a problem, since the soundcard on my laptop is onboard, and i have no clue as to how to get the exact model and make displayed under linux. should i ignore this part, and hope for the best, and then assume the problem is here if it doesnt work later? or is there a trick to checking?

edit, i asked stupid questions.

edited it to 
@audio   -  rtprio     100
@audio   -  memlock    unlimited
@audio   -  nice      -10

as the jack application told me to, but i still dont have any connection through.
thanks thanks thanks again :D

---

### Post by cchhrriiss121212 on 2010-08-17
If your audio works for regular things like you mentioned in the first post, then you can get it working with jack. You can check your device by using "aplay -l" in a terminal.
The only thing is that onboard audio may not be able to handle some of the heavier/intensive production duties without glitches. Did you ever use an interface/external soundcard with windows?  

Edit:
What is jack telling you in the message window?

---

### Post by simieon on 2010-08-17
never had problems under windows, and never had to use an external for making music on the go (i travel a lot, and most of it by train, so most of my best work was done on the laptop) on my stationary i have a 16 bus external, with midi, optical, and analog ports, as well as a analog pipe amplifier for the mic in, optical connected hardware compressor for reduction of electrical noise, and about a million other gadgets.

jack says:
 p, li { white-space: pre-wrap; }  JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]16:55:33.057 JACK was started with PID=8794.[/COLOR]
 [COLOR=#999999]16:55:33.076 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]16:55:33.077 Post-shutdown script...[/COLOR]
 [COLOR=#990099]16:55:33.078 killall jackd[/COLOR]
 [COLOR=#cccc99]16:55:33.209 ALSA connection change.[/COLOR]
 jackd: no process found
 [COLOR=#999999]16:55:33.488 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]16:55:35.215 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

but both lines are added in the conf file


edit: im aware that some apps might be heavy on the cpu's and ram consumption, but the puter should be up for it.

---

### Post by simieon on 2010-08-17
thank you very much. i made it work, apparently i made the sillyest mistake of all, i forgot to reboot the comp. /bow and thanks a lot for the help :D

---

