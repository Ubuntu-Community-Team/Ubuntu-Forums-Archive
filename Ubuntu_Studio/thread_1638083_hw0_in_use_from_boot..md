---
title: "hw:0 in use from boot."
date: 2010-12-05
forum: Ubuntu Studio
---

### Post by Sidar on 2010-12-05
I know this issue has been going around for some time and some have found their solution. Non of their solution worked for me.
Everything worked fine until installed the VST support for LMMS which installed Wine. After this things just went to hell.
I removed both Wine and the VST support. No changes there.

Not just with Jack, some other software that depend on the first selected hardware hw:0 won't boot either. 
Sometimes they do start, as if some software is playing games with me.

I tried 
```
$sudo alsa force-reload
```
and this to kill the running processes:
```
$sudo fuser /dev/snd/pcmC0D0p
```
with no success.


First thing Jack outputs is:

> 16:22:45.930 Patchbay deactivated.
16:22:45.936 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:22:46.018 ALSA connection graph change.
16:22:46.242 ALSA connection change.

But after hitting the start button it obviously states that the hardware is in use.

Im pretty sure i killed all processes that use the hardware.

Now please take note that this happens directly from the start, even when Jack is the first thing im running.

Im trying to stick with linux but these things really make it less appealing to me, i hope someone has a good solution to this.

edit:


```
$sudo alsa force-reload
```

gives

> Terminating processes: 6987 7089 7137 7185 (with SIGKILL:) 7214 (failed: processes still using sound devices: 7242(pulseaudio)).
/sbin/alsa: Warning: Processes using sound devices: 7242(pulseaudio). 
mkdir: cannot create directory `/var/run/alsa': Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-seq-dummy snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
mkdir: cannot create directory `/var/run/alsa': Permission denied
Loading ALSA sound driver modules: (none to reload).


It can't terminate pulseaudio though...

---

### Post by Sidar on 2010-12-05
Okai so ive been trying out some command line stuff.
At first it kinda messed up my system ( booting up takes longer now...) and It seems like that Jack can run, but not always at first attempt.

It still outputs 

> 18:38:07.761 Patchbay deactivated.
18:38:07.808 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

I feel like i messed up with my system...
Can someone please help me out on where to look for faults or errors in the system?

---

### Post by cchhrriiss121212 on 2010-12-05
You should just do a fresh install, it will be quicker in the long run. I went through a few installs myself when trying Ubuntu, it is easy if you make a separate home partition.

---

### Post by Sidar on 2010-12-05
But this install isn't so old, and I already did a fresh install on my previous break down recently.

I don't feel like reinstaling the OS every 3 weeks.
Getting al my settings back and preferences can be a pain.
( I take you meant that with an partition for my home...any links to how i can make that directory my standard account again?)

I would just like to know how i can see if my system is running to its full extend.
Basically I want to analyse my OS and hardware.
Is there a good tool for this? Which outputs error and such.
( also is there a way to clear the .cache folder in my home directory?)

edit:
So Basically when im running jack and its not working i can select
jackstart and then try to run it, it will say it can't start.
Setting it back to jackd does work...

But something is messing up with the system when its booting. How do i fetch this data. What is making use of hw:0?
Reinstalling seems like a cheap way out, but i rather understand the problem than to run from it.
I mean it could occur to me the next time as well...I don't feel like doing it over and over.

I feel really frustrated right now...I rather remove linux all together than to come back to this problem.
( and since i like all the tools i can get from Linux, I rather not....its a contradiction but you get the point)

edit 2:
Sunvox for example can't start eventhough jack can( sometimes) unless i run it in the terminal

---

### Post by cchhrriiss121212 on 2010-12-05
> But this install isn't so old, and I already did a fresh install on my previous break down recently.
It does not matter how old your install is, once you have gotten into a mess it is just easier to re-install than try and undo what you have done. From what you have posted it seems you have been experimenting with a lot of different things, there is nothing wrong with that, but unless you can remember *exactly* what you have changed, it is very hard to help troubleshoot.

> 
I don't feel like reinstaling the OS every 3 weeks.
You should not have to re-install that often, ask questions first and then you will have less chance of making mistakes.

> Getting all my settings back and preferences can be a pain.
( I take you meant that with an partition for my home...any links to how i can make that directory my standard account again?)
This is a good guide:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

> I would just like to know how i can see if my system is running to its full extend.
Basically I want to analyse my OS and hardware.
Is there a good tool for this? Which outputs error and such.
I'm not sure what you mean here, System Monitor will show you how much system resources you use up as well as basic info. 
> 
( also is there a way to clear the .cache folder in my home directory?)
Open up your home directory in Nautilus and press ctrl+h, you should see your .cache folder which you can delete like anything else.

---

### Post by Sidar on 2010-12-05
> You should not have to re-install that often, ask questions first and then you will have less chance of making mistakes.

Thats the thing, i didn't do much. There was nothing to ask about.
"is it safe to install VST support for LMMS" would be kinda... redundant dont you think?
I just installed the VST support which installed Wine.
I removed them both. and my system is still being a pain in the ***.

And since the beginning of my fresh install Jack already had trouble running the first time. hitting the run/start button for the second time does work(not always though).

I will not reinstall my OS until i know what is hogging my audio card from boot.

Everything now seems just as is before jack wouldn't run at all...yet something goes wrong at boot...

> I'm not sure what you mean here, System Monitor will show you how much system resources you use up as well as basic info. 
Im not looking for basic info, im looking for error logs, everything the OS doesn't see fit with.


> It does not matter how old your install is,

Obviously, but you said it yourself, you had to reinstall your OS several times as well. And it kinda SUCKS to do it over and over while i do not believe i messed with the system at all.

There is either just a major bug in the settings that come with Ubuntu-studio 64 or my hardware is causing this ( yet its software making use of my HW:0 and i have no clue what.

I'm asking you not to advice me to clean install it, cause i won't. I do not feel like searching the web endlessly for solutions that do not work for me. I want to know what is causing hw:0 to be in use.

( I appreciate your help though)

---

### Post by Pablo_F on 2010-12-05
Hi,

I don't know what this error means:
Cannot connect to server socket

I think it is related to dbus but I don't have a clue on how to debug it. I suggest you install jackd1 package. Then you will be running the original jack which, imho, is more solid and I think this problem will be gone.

You can always ask the devs in #jack channel at freenode.net 
[http://webchat.freenode.net/](http://webchat.freenode.net/)

Cheers! Pablo

---

### Post by cchhrriiss121212 on 2010-12-05
OK, I had taken from your posts that you had changed things around with the system, my mistake.

The problem could be hardware specific, so could I ask what sound card you are using? Type aplay -l into a terminal to find out. 

Could you post the messages that tell you hw:0 is in use?

---

### Post by Sidar on 2010-12-05
> **Pablo_F said:**
> 
You can always ask the devs in #jack channel at freenode.net 
[http://webchat.freenode.net/](http://webchat.freenode.net/)

Cheers! Pablo

Thats good one ill try that in a sec.



@chris
> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The weird thing is, that it sometimes does work and sometimes it just doesnt. 
It works fine now ( its running up and all)...but just not always the first time i hit the Run/Start button on jack.
( i know i keep repeating this, but i'm boggled by it).

When Ubuntu starts I hear the welcome theme, so sound is working fine though...

O and no problem, I'm just frustrated so I might come off weird. Sorry for that.

---

### Post by Pablo_F on 2010-12-05
Have you tried with jackd1?

---

### Post by Sidar on 2010-12-05
Ok i guess it had to do with PULSEAUDIO

pasuspender -- jackd

using this as the server path helps suspending pulseaudio i think.
It runs fine now =D

Thanks for trying to help me guys =) appreciated.

[http://jackaudio.org/pulseaudio_and_jack](http://jackaudio.org/pulseaudio_and_jack)

faq

---

### Post by Sidar on 2010-12-05
> **Pablo_F said:**
> Have you tried with jackd1?

No,
And if I do I feel like im messing with the system, again.
Plus, if i remove Jack which is currently installed i will loose lots of packages ( dunno why)

---

### Post by bikodog on 2010-12-11
> **cchhrriiss121212 said:**
> You should just do a fresh install, it will be quicker in the long run. I went through a few installs myself when trying Ubuntu, it is easy if you make a separate home partition.

Good advice. Putting /home on a separate partition means you can reinstall anytime, and it will only take ~10mins.

Reinstalling the OS is part of the learning process; you will find over time as you keep trying and troubleshooting your problems that you need to reinstall less-and-less, until the point when you dont do it at all :)

---

