---
title: "Ventrilo on Pangolin"
date: 2009-03-28
forum: System76 Support
---

### Post by ResumeMan on 2009-03-28
Hi all,

Has anyone had success using Ventrilo on the Pangolin? The program installs just fine in Wine, and I can hear people talk. But it doesn't respond when I push a hotkey for PTT. Simply nothing happens. It does accept the input in settings (i.e. the program thinks it has a PTT key), but when I close settings it doesn't recognize it.

I have done a bit of fiddling, including the howtos [here]("http://http://ubuntuforums.org/showthread.php?t=41737&highlight=pyvent.py") and [here]("http://ubuntuforums.org/showthread.php?t=1010743&highlight=ventrilo"). I also looked at the WineHq page [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9832").  However I'm not sure I've delved into all the options and haven't read all the threads completely.

I just figured I would check in with S76 users to see whether there were any specific workarounds. Is it a PulseAudio issue? If so what's to be done about it?

FWIW it isn't the hardware. I ran Vent on a VM, and it works fine. But I'd much prefer to run it natively.

Thanks

---

### Post by thomasaaron on 2009-03-28
Honestly, I don't know much about wine. I typically refer folks to wine's forums. I hate to punt like that, but wine requires to much configuration per application for me to keep up with.

---

### Post by betrunkenaffe on 2009-03-28
I wiped Pulseaudio from my system after being unable to use many things in wine properly. Vent was one of them.

Sans-PA, worked fine for me on my desktop.

---

### Post by ResumeMan on 2009-03-31
> **betrunkenaffe said:**
> I wiped Pulseaudio from my system after being unable to use many things in wine properly. Vent was one of them.

Sans-PA, worked fine for me on my desktop.

Hmmm...ok two questions:

1. How exactly would you do that?
2. What are the implications? Would some other sort of driver need to be re-configured? Essentially, my question is would I be disabling some sort of important functionality?

Note, that the PTT key doesn't even seem to be acknowleged by Vent, so I'm wondering if the audio is maybe not the issue?

Thanks

---

### Post by ResumeMan on 2009-04-01
OK so at least in part, PulseAudio WAS the issue. Disabling it allows Vent to recognize the PTT key (and my microphone turns green). Nobody could hear me when I tried it last night, but I didn't have time to troubleshoot so maybe theres a setting off somewhere

But PulseAudio definitely seems to have been what kept Vent from "seeing" the key...

---

### Post by betrunkenaffe on 2009-04-02
Sorry, forgot to check back on this. Umm, there's instructions on these forums

[http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637)

The problems I ran into were:

a) Couldn't get it to recognize the key press (like you)
b) Couldn't be heard by others.
c) Once was able to be heard by others, could only do so when Vent was only thing using audio. If I tried anything else, they either didn't work or worked fine and Vent would send pure scratchiness to others when I was talking.

I know I had it working on desktop (I've installed Fedora since then as experiment so can't check settings) and that didn't have PA on it at the time. I ran into issues when I upgraded to 8.10 and PA was installed with the upgrade.

---

### Post by ResumeMan on 2009-04-02
So I haven't had a chance to continue pursuing this (I just bought WotLK, and have had trouble getting it installed, so that's taken my focus). But regarding the only-talk-in-focus problem, see here:

[http://ubuntuforums.org/showthread.php?t=1010743&highlight=pyvent](http://ubuntuforums.org/showthread.php?t=1010743&highlight=pyvent)

It's a python script for capturing the keyboard input and sending it to Vent when it's not the focus application.

I can say that it works for me, in so far as I hear the PTT noise when vent isn't in focus. But as I said above my voice still isn't being transmitted either way.

But I thought that there's a good chance this could solve YOUR problem.

---

### Post by betrunkenaffe on 2009-04-02
Yeah, I saw that script. I don't use Vent anymore so never really a problem.

The no sound could be audio settings, make sure you have sound in a Linux sound capture program, check alsamixer if you don't. If you do have it working in a Linux native sound capture then try running wine with padsp.


padsp winecfg (configure it)
padsp wine PROGRAM_INFO (run it)

That solved my no audio issue which is when I ran in the 3rd issue.

---

### Post by ResumeMan on 2009-04-03
So it appears that PulseAudio was indeed the problem. And I must have had a setting wrong for volume, because it is possible to be heard. But I have to stick my face right up in the mic. But I think that's the hardware; I've seen elsewhere that the Pangolin mic is crappy.

I think I'll go get myself a headset/mic thingy. I understand that they don't all play well with Ubuntu. Can anyone recommend one that does?

So -- I clearly don't want to be using PulseAudio when I'm playing WoW. I don't see any reason to keep it. Is getting rid of it as easy as uninstalling the package in Synaptic? Or do I need to do something else?

Thanks

---

### Post by darkknight045 on 2009-04-03
If you just get a Non-USB headset, the ones with 1/8" jacks instead there will be no problems.  Its the USB sets that Ubuntu seems to dislike.

---

### Post by thomasaaron on 2009-04-03
> I think I'll go get myself a headset/mic thingy. I understand that they don't all play well with Ubuntu. Can anyone recommend one that does?

That is incorrect. I've had no problems with headphones/mics at all. Send me an email (support(at)system76(dot)com), and I'll send you screenshots of how to set up for internal and external mics.

Also, I don't think I'd delete pulseaudio. That sounds like a recipe for future problems.

---

### Post by betrunkenaffe on 2009-04-03
I linked how to remove it previously. Talk with thomas first, see if you can get it resolved. I removed it because I didn't like all the issues I was having (that I could directly attribute to it).

I have had some difficulties with the Pangolin mic but I fixed them with some fiddling, it does still seem a little quiet but I can't jack it up without having the machine screech at me when I close the laptop lid :)

---

### Post by ResumeMan on 2009-04-03
> **betrunkenaffe said:**
> I linked how to remove it previously. Talk with thomas first, see if you can get it resolved. I removed it because I didn't like all the issues I was having (that I could directly attribute to it).

Ah, so you did! Sorry, I didn't realize what that link was for.

[quote=thomasaaron]That is incorrect. I've had no problems with headphones/mics at all. Send me an email (support(at)system76(dot)com), and I'll send you screenshots of how to set up for internal and external mics.[/quote]

Good to know. I'll do that.

[quote=thomasaaron]Also, I don't think I'd delete pulseaudio. That sounds like a recipe for future problems. [/quote]

OK, but do you have any suggestions for how to get PA working with Wine applications? I'm not enthusiastic about disabling a key component of the OS, but I do want to have Vent working.

I will also try rebooting and try vent again with PA enabled and see if there's any adjustments I could make. I'd appreciate any guidance.

---

### Post by thomasaaron on 2009-04-03
```
OK, but do you have any suggestions for how to get PA working with Wine applications?
```

I don't think disabling pulseaudio is a bad idea, as you can always re-enable it. I just think that removing it altogether is likely to lead to issues down the road.

As for wine, I hate to punt, but I don't know much about it. It requires too many application-specific tweaks for me to track.

This thread talks quite a bit about pulseaudio and wine. Maybe it would be a good starting point...
[http://ubuntuforums.org/showthread.php?t=609166](http://ubuntuforums.org/showthread.php?t=609166)

I see your email, I'll send the screenshots.

---

### Post by betrunkenaffe on 2009-04-04
Wine doesn't like pulseaudio, there are some solutions in the works from what I understand.. Hopefully soon the issues will be resolved.

---

### Post by ResumeMan on 2009-04-04
Thanks for those screenshots Tom. I didn't have a bunch of those tabs turned on, so I couldn't even see the settings.

Now, Vent simply doesn't work when Pulseaudio is active. I entered "sudo killall pulseaudio" and it works fine. But is there a setting I can establish so it'll stay turned off when I reboot? That is, without actually uninstalling?

Thanks

---

### Post by ResumeMan on 2009-04-04
Another question would be, any setting I could adjust to prevent the hideous squeal of feedback when I shut the lid? :)

---

### Post by betrunkenaffe on 2009-04-05
You have the volume too high on the microphone playback. Reduce it to around 26.

That's a setting in alsamixer, there is the mic for playback and the mic for capture, you don't want to mess with the capture one.

---

### Post by Lee_Machine on 2009-04-05
Resumeman,

To auto kill pulseadio when you boot up do this:

System >> Preferences >> Startup Applications 

Click Add

Give it any name you want say Ventrilo, and for command put sudo killall pulseaudio

This way when the system starts up it will disable pulseaudio.

---

### Post by ResumeMan on 2009-04-05
betrunkenaffe: thanks that seems to have done it

Lee: err....I can't find a "startup" entry on either the preferences or admin menu. Is it called something else? Or perhaps have I gone blind...?

---

### Post by betrunkenaffe on 2009-04-06
System>>Preferences>>Sessions

Instructions as provided by Lee

---

### Post by ResumeMan on 2009-04-06
Aha! Thank you, that was what I couldn't figure out! :)

---

### Post by ResumeMan on 2009-04-17
> **betrunkenaffe said:**
> System>>Preferences>>Sessions

Instructions as provided by Lee

OK so I found the place for this on the menu. But...it doesn't seem to work...

When I rebooted Vent was borked again. I opened a terminal and did the kill pulseaudio command and vent worked again.

Am I missing something?

BTW does anyone know if the latest Wine release does anything to make it more compatible with PulseAudio?

---

### Post by thomasaaron on 2009-04-17
OK, I've not been following this thread very closely, since it pertains to wine, but your command in sessions should probably be something like...

kill pulsaudio; wine vent...

...or whatever command you are using to open ventrilo. Basically, you would be running two commands. That's what the semicolon is for.

---

### Post by ResumeMan on 2009-04-17
Well I don't necessarily want to run Vent on startup. I just want to disable Pulse so I CAN run Vent when I want to.

But looking at the first part of your suggestion, do you think the command should just be "kill pulseaudio" as opposed to "killall pulseaudio"? I have no clue what the difference is between the two commands.

---

### Post by thomasaaron on 2009-04-17
killall pulseaudio is the correct command. Sorry.

You also might want to just create a custom launcher on one of your panels that run that command. That way pulseaudio isn't killed by default. But only when you choose to kill it. It's not all bad.

---

