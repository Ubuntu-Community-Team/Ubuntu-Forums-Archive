---
title: "Is there audio with a VMware Ubuntu 7.10  install ?"
date: 2008-01-27
forum: Virtualisation
---

### Post by Beowulf.1000 on 2008-01-27
Do any Ubuntu users have audio working with VMware? That is what I need to know, to give me hope (I am going to try a VMware install, then install WinXP with it).  I really need audio with VMware, so I can hopefully install and run Sony ACID Pro in VMware in Linux (sound editor, loop music creation--leaps and bounds above anything available for Linux). My dream would also be to get Sony Vegas video editor working with VMware, but I will settle for getting ACID Pro working in VMware, that and Movie Magic screenplay writing software (bizarre keystroke behavior when installed with Wine so that is not an option).

---

### Post by Infinity-al on 2008-01-28
> **Beowulf.1000 said:**
> Do any Ubuntu users have audio working with VMware? That is what I need to know, to give me hope (I am going to try a VMware install, then install WinXP with it).  I really need audio with VMware, so I can hopefully install and run Sony ACID Pro in VMware in Linux (sound editor, loop music creation--leaps and bounds above anything available for Linux). My dream would also be to get Sony Vegas video editor working with VMware, but I will settle for getting ACID Pro working in VMware, that and Movie Magic screenplay writing software (bizarre keystroke behavior when installed with Wine so that is not an option).
Audio working fine for me... With WinXP Home Edition as guest

---

### Post by Nicu Alecu on 2008-01-28
For me too, although I couldn't care less about sound on the XP SP2 I run as a test machine in VMWare.
It does get a little bit messy if you have a lot of linux apps running alongside VMWare, but I guess that depends on system's hardware resources and the way you set up the VMWare machine.

---

### Post by fjgaude on 2008-01-28
Audio is good in VMware, WinXP, as long as I don't simultaneously try to use the audio in Ubuntu. <sigh>

---

### Post by mannheim on 2008-01-28
Sound does work in a Windows XP guest under VMWare, but I have experience "timing" issues when playing MIDI files (and I wonder if this might be an issue also for your intended application).

During playback of MIDI in the guest operating system, the tempo can be unstable over the course of one or two measures: something you wouldn't notice in recorded speech. 

This issue is described in [this document]("http://www.vmware.com/pdf/vmware_timekeeping.pdf") from WMWare, together with some workarounds (which I haven't tried). My system is rather old (a 2.4 GHz Pentium 4), and it may be that the effect would not be noticeable on a modern machine doing similar work.

---

### Post by fuzzyworbles on 2008-01-29
It doesn't seem as though the poster and I have the same luck as you folks. Sound didn't work out-of-the-box for me, but I'm currently looking for some other resources out there to point me in the right direction. All I have it what VM presents to me, which is "auto detect" or nothing. In the end all I get is nothing anyhow. 

I wonder if it has anything to do with OSS4...

---

### Post by dpj23 on 2008-01-29
Advise...

Make sure your host machine is not using any applications that require the sound card....

Make sure that you have the sound card enabled for the vm machine...

If this done and the install went smoothly you should be set right out of the gate...

make sure the driver is present in the quest operating system...

this may require you to install vmtools...


a couple of notes:

listening to music in a vm can be acceptable...  However, video can become a problem...  So, if you minimize the amount to resources you need in the vm machine it will greatly improve your performance...  An example would be turning off the visual displays that accompany many media players... This is un-needed over head which can max out the systems resources... 

I use the vm machine (XP) to stream music from the internet al most daily and never have an issue...  however, it can be one once extra's are turned on...

---

### Post by fuzzyworbles on 2008-01-29
huh.. i just typed in /dev/dsp for the audio device and it worked. how silly that it can't "autodetect" that.

---

### Post by eternal-one on 2008-02-05
dont need to...  just run Reaper under wineasio which is flawless. (basically an acid 'clone' but not to be taken lightly). 64-bit Sound engine, elastique timestretching (just alt-drag edge of clip, acid doesnt have this feature!) and much more. For Multitrack Video editing, try JahShaka.

[IMG]http://i120.photobucket.com/albums/o197/digipwn/reaperstealth.jpg[/IMG]

[IMG]http://i120.photobucket.com/albums/o197/digipwn/edit-multitrack-active.png[/IMG]

:guitar:

---

