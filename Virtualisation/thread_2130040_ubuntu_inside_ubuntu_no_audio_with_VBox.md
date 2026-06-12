---
title: "ubuntu inside ubuntu: no audio with VBox"
date: 2013-03-28
forum: Virtualisation
---

### Post by ayvango on 2013-03-28
I have xubuntu (technically ubuntu with xubuntu-desktop installed) as a host system and minimalistic ubuntu as guest. Both uses ALSA. I've deinstalled pulse audio from host in purpose of making environment clear after discovering audio dysfunction. In both host and guest system user is a member of audio group and may use alsamixer freely (all channels are enabled). VirtualBox OSE is configured to use ALSA and provide Intel HD audio card. dmesg from guest tells me that it has successfully initialized Intel HD Audio card.

I've got sample mp3, it was perfectly played in host machine. I've tried mpg321, mplayer and alsaplayer, they all ceased to play the mp3 file on guest. Alsaplayer given me most usefull error description: "No stream found". I've searched google and find some threads about dmix, such as [https://bbs.archlinux.org/viewtopic.php?id=91692](https://bbs.archlinux.org/viewtopic.php?id=91692) I've tried all solutions, but nevertheless failed to fix the bug. I suppose that the error mechanics is similar to dmix cases but does not exact match them.

I've googled a lot but still has no clue what should I diagnose further and how fix the bug.

P.S.
I want to describe the use case for those, who is curios why I need to install ubuntu inside ubuntu and want to suggest more clear solution. I simply want to use skype in my open source system not tainting it with proprietary binary. To keep system and my privacy safe I'd like to isolate skype in a its own virtual box instance.

---

### Post by sudodus on 2013-03-28
I have an Ubuntu host system with pulseaudio (the default settings). The audio in my guest systems in VirtualBox works. Maybe you have cleaned out something important in your minimalistic ubuntu as guest, maybe pulseaudio will be better than alsa in this case.

---

### Post by ayvango on 2013-03-28
Audio on guest system does not work with either Pulse audio or ALSA on host system. It is very difficult to clean something out in minimalistic ubuntu since the distribution itself installs almost nothing. It is possible not to install something essential.

---

### Post by sudodus on 2013-03-28
> **ayvango said:**
> Audio on guest system does not work with either Pulse audio or ALSA on host system. It is very difficult to clean something out in minimalistic ubuntu since the distribution itself installs almost nothing. It is possible not to install something essential.
I see. I just tested with a live xubuntu session as guest in vbox. And it could play music from an ogg file out of the box (but not mp3 because the proprietary codec package was not there).

Maybe your problem is with the host system. It is hard for me to give detailed help, I have pulseaudio and you have 'only' alsa. [COLOR=#ff0000]Let us hope someone else running ***alsa*** can help you.
[/COLOR]
Otherwise, you can consider ultra light-weight, yet complete host and OSs, for example Lubuntu. Then I'm pretty sure you will get sound in your guest systems.

Another option is dual boot:

- One system with only free software
- One system with Skype, non-free codecs for multimedia, ...

This will give you full performance in both systems. (Guest systems will be slower due to the virtual machine interface.)

*Edit*: Why so minimalistic system(s)?

---

### Post by ayvango on 2013-03-28
> **sudodus said:**
> 
*Edit*: Why so minimalistic system(s)?
System is needed only to start single program.

I will install full featured xubuntu to a virtual box container to determine if guest system, host system, or virtual box itself causes problems.

---

### Post by sudodus on 2013-03-28
Do you plan to use this virtual system ***only*** for Skype? And this is the reason you want to keep it as small as possible. Do you want it small

- to save disk space or
- to be able to run it with a small amount of RAM or
- to be able to run it virtually with a weak cpu

in other words, is it necessary to keep it minimal or is it because you enjoy the process to make it minimal?

It is probably more efficient to built a small system from below (start with a mini iso file and add programs and settings). But it is probably easier to build it from above (start with a standard desktop system, make it do what you want, and remove programs until it breaks (and then reinstall what was needed). One important reason is that a standard system is thoroughly tested in vbox as well as on actual hardware. And the Ubuntu flavours are verified to work with Skype.

---

