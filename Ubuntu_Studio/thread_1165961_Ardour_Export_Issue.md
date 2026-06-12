---
title: "Ardour Export Issue"
date: 2009-05-21
forum: Ubuntu Studio
---

### Post by dawiba on 2009-05-21
Hello again ;)

On Tuesday night a friend came round and we worked on an idea and just quickly sketched it out using Ardour. I exported the result and converted to mp3 and emailed it to him so he could play it on his computer.

So far so good.

Last night, I went back to the session and re-recorded a couple of parts to tidy them up and added a couple of new ones. Then I tried to export. Ardour went through the process but seemed to stall right at the end and then just disappeared! Jack also hung after Ardour disappeared and some of the text in the display window had changed. I tried again but got the same result, the only difference was that this time after Jack hung, the computer locked up and I had to switch off using the power button.

The good news is that the file exported okay and I was able to convert and send it in an email.

Out of interest, I tried booting into the normal kernel, started Ardour and exported the file. No problems at all!

I looked on the Ardour site, but no-one there has this problem, it seems to be exporting to silence that is the problem for some. A quick Google gave the same result.

So, has anyone here had this? Any ideas how to fix it?

Thanks

---

### Post by kayosiii on 2009-05-21
That is probably a question best answered on ardour.org....
You should see if the problem is reproducible first.

---

### Post by uPilger on 2009-05-28
> **kayosiii said:**
> That is probably a question best answered on ardour.org...

I've got the same Problem after I updated to 9.4. Perhaps, its not a ardour-problem, also Audacity freezes after this update.
What are possibilities to solve 
 this problem?
Regards

---

### Post by dawiba on 2009-05-28
I posted on the Ardour forum and someone else had the same problem as me except his problem happened when using the regular kernel and not the rt kernel. The opposite to me!

Anyway, one suggestion was to try changing Jack settings (Frames/Period and/or Period/Buffer) before exporting to see if that made a difference. I haven't used Ardour for a couple of days but I will try later tonight to see if it works. The logic for this is it seems that the processor is completely maxed out (Jack's window shows 1e+02 instead of a percentage figure) during the export for some reason and possibly changing these settings might help.

The guy on the Ardour forum ended up compiling his own (non rt) kernel and solved his problem that way, but that is beyond my scope and interest.

---

### Post by uPilger on 2009-06-13
> **dawiba said:**
> 
Anyway, one suggestion was to try changing Jack settings (Frames/Period and/or Period/Buffer) before exporting to see if that made a difference. I haven't used Ardour for a couple of days but I will try later tonight to see if it works. The logic for this is it seems that the processor is completely maxed out (Jack's window shows 1e+02 instead of a percentage figure) during the export for some reason and possibly changing these settings might help.


It seems, that for me the Problem is fixed:
So far, I used the non RT Kernel.
After istall the RT and prepare the 
/etc/security/limits.conf [FONT=Verdana]

like this doc:[/FONT][https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

Ardour exports fine. However, i can't use de RT-Mode in Jack.

---

### Post by trulan on 2009-06-14
I have the same issue.  It behaves in exactly the same way every time I export a file.  (I recorded about 10 demos, then went through and then attempted to export them all in one evening.  Made for a long one)

My exported files are always fine, and I can always save my session, but both Jack and Ardour have to be restarted before it will work again.  (Thankfully, I've never had to restart my system.)  I started my own thread here: [http://ubuntuforums.org/showthread.php?t=1185935](http://ubuntuforums.org/showthread.php?t=1185935) but I would have posted in this thread instead had I seen it before.

I tried increasing the buffering settings in JACK but it didn't change anything except noticeably increasing my latency, so I put the settings back to the way I had them.

I also tried stopping Jack to do the export, but Ardour wouldn't let me.  Is there any way to pause JACK, or make it run in the background or something, that would let Ardour do its thing without persistently crashing?  Or maybe lowering the priority settings in Jack or unlocking the memory would help?

The whole point of my installing Ubuntu in the first place was for reliable low-latency multitracking with my firepod (which Windows refused to give me) so I'd rather live with this issue than move away from the real time kernel.  But if we can figure out a workaround that would be even better.
__[]("http://ubuntuforums.org/showthread.php?t=1185935")

---

### Post by trulan on 2009-06-14
If I de-select 'real time' and set the frames/period to 1024 in JACK conrol, JACK remains usable after mixing down, but Ardour still crashes.  It's not exactly an improvement but it is a change, which gives me a little hope.  So maybe the settings can be tweaked, and simply having settings saved for recording and for mixing down could be a workaround.

Or maybe I'll have to install a regular kernal as well, and boot into that for mixing down.  That sounds like a pain though.

Ideas, thoughts, and suggestions are welcome.

---

### Post by kayosiii on 2009-06-15
If you really need a workaround - and this is a lame workaround not a solution. Try this...
1) Start Patchage (or jack control) and Time Machine.
2) Use Patchage and wire Ardours outputs into time machines inputs.
3) hit playback in Ardour and then record in Time Machine. You have 10 seconds to get record going - Time machine starts recording 10 seconds before you push the record button.
4)Take the file that TimeMachine produces and open it in Audacity the default filetype is w64 and it will be in your home folder.
5) trim off the unnessary start and end and save as an MP3.

---

### Post by dawiba on 2009-06-15
I still have this problem when using the rt kernel, despite trying all sorts of different settings in Jack and/or Ardour.

The only successful method for me is re-booting into the regular kernel and exporting there. I suppose when it comes time for exporting, all your mixing etc is done, so there's no real need to be using the rt kernel.

---

### Post by thorgal on 2009-06-15
try this (when you have booted the RT kernel)

- inside ardour, disconnect from jack (in JACK menu in main taskbar)
- in qjackctl, stop jack
- untick RT mode
- set a large latency
- start jack again
- inside ardour, reconnect to jack
- export


to ease the procedure, save jack presets in qjackctl (I have quite a few jack setups for my own use, depending on the circumstances - very low lat full duplex, large lat and playback only for mastering, non RT and big client timeout for debugging ardour, etc, etc).

---

### Post by trulan on 2009-06-15
Well, that's a slight improvement.  It actually works for me if I follow those steps in that exact order.  I think the key is disconnecting Jack in Ardour before stopping it from qjackctl and changing the settings.  I hadn't thought to do it that way - I was just stopping Jack.  Ardour doesn't like that at all.

But I have yet to find a non-real-time combination of settings (even with ridiculously large latency) that will give a useable playback in Ardour.  If I un-tick real time in Jack I get lots and lots of x runs.

But at least I can do my mixing down using my usual settings, then change the settings and successfully export without crashing anything.  So thanks, thorgal.

---

### Post by dawiba on 2009-06-16
I tried Thorgal's suggestion with something that I'd previously recorded, but unfortunately, it didn't work.

I have to confess that I've used my Mac for the last couple of things because I find it easier and quicker just to get on and record something (and check emails at the same time :)), but I'll start something else tonight and see how I get on trying different ideas to export.

---

### Post by trulan on 2009-06-18
I'm curious, dawiba, uPilger, and anyone else having this issue, if our hardware has an impact.  It maybe doesn't matter, but I'm running an HP with:

AMD Athlon 64 3800+, 2.41GHz
1 Gb RAM (soon to be 2 Gb)
AMD64 Jaunty, of course.

And if all goes well I'll also be setting up a laptop with an Intel dual core to run 32 bit Jaunty.

I'll let you know if the memory has any effect, and also if the laptop deal works out, how it behaves.

---

### Post by dawiba on 2009-06-19
I've wondered if it might be this computer as well. But, given that I was able to export originally, then I have my doubts.

Recently I've tried uninstalling and reinstalling Ardour. I've also tried upgrading Ardour. None of these has been successful in letting me export while running in real time.

I've also changed the values in limits.conf and was able to get Ardour to export once (although Jack still crashed) running in real time, but it would only do it that once without everything locking up.

I tried different rt kernels (64 Studio and AV Linux 2.0), but my screen was a mess when I tried to use them.

At the moment I'm back with the version of Ardour from the repos and I'm able to export without problems running the generic kernel, so I'll stick with that and try other ideas as I get them

---

### Post by ussndmac on 2009-06-19
This is an known issue with firewire and is a kernel issue. Ardour puts the firewire interface in freewheeling mode during an export and when it tries to re-establish control it can't.

This was fixed at the firewire driver (ffado) level for a while, but is now reared again at a lower level.

Normally, if you start JACK with ALSA (instead of firewire) the export will complete just fine.

---

### Post by trulan on 2009-06-20
Oh OK, thank you very much.  I'm a bit surprised I haven't seen more current info on it if it is indeed a known issue.  Most of what I've found in my searching deals with freebob and older versions of Ardour, and the recommended fix was to upgrade.

To avoid having to convert sampling rates and potentially lose some quality, I am recording at 44100 (goal-cd audio).  Running Jack with ALSA works but my soundcard will only give me 48000 (Soundblaster 24 bit.  It will play at 44100 but only duplex at 48000 and I haven't been able to get Jack to use it at 44100 even if I set it for playback only).  So that's not really going to work for me.

So I guess I could:
1. Downgrade to Hardy.
2. Buy a soundcard that will duplex at 44100 for mastering/exporting.

And it would fix this.  Or, I can just live with it.

---

### Post by dawiba on 2009-06-20
I downloaded the latest generic kernel using Synaptic and now I can run Jack, with realtime enabled, while running the generic kernel. I double checked I was actually running the generic kernel using uname -r.

So this means that without making any choices in grub, I can just let the computer boot, which boots into the latest generic kernel by default, start Jack (with realtime enabled), which starts my firewire interface, work on whatever I'm doing in Ardour, save, quit Jack, export from Ardour and I'm done!

I had assumed that to use the realtime option in Jack that you had to be running the rt kernel. I don't know how or why I can use realtime in this way while running the generic kernel, but I'm not complaining!

---

### Post by thorgal on 2009-06-20
the RT kernel is optimized for close to hard realtime operations. The generic kernel has some of the RT stuff as well but is not as good as the RT patched kernel. However, both have a task scheduling system with different priority bits

There's one thing that users tend to confuse:
- RT operations
- task scheduling priorities

The normal user cannot usually have access to the task scheduling priority SCHED_FF (normally, only root can). The /etc/security/limits.conf stuff enables such a usage from a non root user.

Now, what the kernel scheduler does might be different depending on whether the kernel is RT patched or not. Accessing SCHED_FF task sched priority is one thing, another is to have the kernel optimized for RT stuff when tasks are launched with such a task sched priority.

So it is no wonder you can use the generic kernel with RT mode enabled. What you actually enable is the task scheduling priority SCHED_FF for the jackd audio thread. This is required for giving priority to the audio thread but is not a complete garanty that the kernel will behave nicely. The RT patch ensures the latter.

---

### Post by trulan on 2009-06-20
So what we're after is ensuring that the kernel behaves nicely.  First importance is that it works absolutely flawlessly while recording.  And so far it seems to indeed do that.

If this export issue is a kernel issue, is it being worked on?  I am learning about the open source concept but I was wondering if there was somewhere we could watch the progress/state of this issue?  I mean, does this need to be fixed at the Ardour level, the JACK level, the FFADO level, or the kernel level?  I realize that this may not be known and that's okay.  I'm just curious.

---

### Post by dawiba on 2009-06-20
Thorgal - thanks for explaining the difference and I understand the difference now.

I need to say though, that when running the rt kernel, I can pretty much only record music. If I try to do other stuff, check emails, write replies in forums etc, it's only a matter of a short time before my computer freezes. If I have Ardour and Jack already open, then a freeze will follow *very* shortly if I try to do anything else.

Over the last day and a bit, running the generic kernel, I can now play music in Audacious (routed through Jack), have Ardour open, be recording/editing and have Entourage and Firefox open in the background. No freezes, no crashes and no glitches (so far anyway!). I know which kernel I'll be using for the foreseeable future, because I can just get on with things now.

Trulan - I'm subscribed to the UbuntuStudio mailing lists (just to try to follow what's going on) and in one of the recent posts there, someone (one of the devs I think) asked if they actually needed the rt kernel. The response seemed to be that it *is* required (at least for those doing audio). I also read somewhere that someone is tasked with working on the rt kernel, so can only assume it will be updated in the way the generic kernel was and hopefully soon.

---

### Post by thorgal on 2009-06-20
I wish I knew more about kernel stuff. To be honest, it can change from version to version. I am actually running an RT kernel (compiled myself) and I have absolutely no issue whatsoever. It's a bit of a lottery, unfortunately. But really, it seemed that the Ubuntu Studio guys have been more than unfortunate in their packaging of the RT kernel. One thing that strikes me is that Jaunty is shipped with 2.6.28 when the RT patch was "resumed" from the 2.6.29 serie (and at a speed that is rather impressive). I hope the next US iteration will be more fortunate (2.6.30 or 31 ?). But not everything is to be blamed on the RT patch. Hardware configuration, device drivers, etc, play a significant role in how the system will perform. But the generic kernel seems to be more and more efficient in RT operations. Some RT stuff is making it to the baseline, so I hope that in the not so long run, RT will be a matter of switching a kernel option either at boot or from a running state. I think this has been / is being discussed in the kernel dev sphere.

---

### Post by sgx on 2009-06-21
> **dawiba said:**
> Thorgal - thanks for explaining the difference and I understand the difference now.

I need to say though, that when running the rt kernel, I can pretty much only record music. If I try to do other stuff, check emails, write replies in forums etc, it's only a matter of a short time before my computer freezes. If I have Ardour and Jack already open, then a freeze will follow *very* shortly if I try to do anything else.

Over the last day and a bit, running the generic kernel, I can now play music in Audacious (routed through Jack), have Ardour open, be recording/editing and have Entourage and Firefox open in the background. No freezes, no crashes and no glitches (so far anyway!). I know which kernel I'll be using for the foreseeable future, because I can just get on with things now.

Trulan - I'm subscribed to the UbuntuStudio mailing lists (just to try to follow what's going on) and in one of the recent posts there, someone (one of the devs I think) asked if they actually needed the rt kernel. The response seemed to be that it *is* required (at least for those doing audio). I also read somewhere that someone is tasked with working on the rt kernel, so can only assume it will be updated in the way the generic kernel was and hopefully soon.

Using a very lean non-ubuntu linux, I can confirm that the newer stock kernels do work well for low latency audio. Lightweight hosts Reaper and Cantabile with wineasio allow you to render or record live output, I then import the audio into audacity, bypassing the complexities/issues sometimes found with ardour altogether.
Cheers (I'd use ubuntu, but they still don't fix the ubiquitus nvidia 6100 graphics to go past 800x600, while other distros are fine :confused:

---

### Post by trulan on 2009-06-21
I must be unusually fortunate then.  I have had no NVidia issues (onboard 6150 LE), and I've never had a system crash.  After reading around I think I'd better just leave my hands off and use it as it is.  My Ubuntu Studio setup does work remarkably well, especially considering how prone the current RT kernel seems to issues.  Like I said before, even with this issue I am not complaining.

---

### Post by kayosiii on 2009-06-21
> **trulan said:**
> Oh OK, thank you very much.  I'm a bit surprised I haven't seen more current info on it if it is indeed a known issue.  Most of what I've found in my searching deals with freebob and older versions of Ardour, and the recommended fix was to upgrade.

To avoid having to convert sampling rates and potentially lose some quality, I am recording at 44100 (goal-cd audio).  Running Jack with ALSA works but my soundcard will only give me 48000 (Soundblaster 24 bit.  It will play at 44100 but only duplex at 48000 and I haven't been able to get Jack to use it at 44100 even if I set it for playback only).  So that's not really going to work for me.

So I guess I could:
1. Downgrade to Hardy.
2. Buy a soundcard that will duplex at 44100 for mastering/exporting.

And it would fix this.  Or, I can just live with it.

Try the workaround I posted earlier (you will learn a lot about the inherit flexibility of jack ;) ). 

Or alternatively from within Ardour
create a new stereo track and route it's inputs to your master outputs.
to this tracks inputs. Arm only this new track and hit record and playback. 

this will bounce everything down to a stereo track that will be in the interchange folder of your project. Open this with your favourite Audio Editor and convert to MP3.

---

### Post by sgx on 2009-06-21
> **trulan said:**
> I must be unusually fortunate then.  I have had no NVidia issues (onboard 6150 LE), and I've never had a system crash.  After reading around I think I'd better just leave my hands off and use it as it is.  My Ubuntu Studio setup does work remarkably well, especially considering how prone the current RT kernel seems to issues.  Like I said before, even with this issue I am not complaining.

Wise penquin not fix what ain't broken :)
It seems the 6100 graphics chips, and some older monitors only get
'configured device' status in xorg.conf
I have replaced the ubuntu xorg with one from a distro where everything works, the video is ok then, but the mouse is frozen, so I went back to making music instead of higher blood pressure. Maybe U10 will get it right. And to be fair, it is more a hardware detection issue, than anything specific to Ubuntu, as only 2 of 7 distros I tested got everything right. I still have patches where the hair hasn't grown back   yet ;-) But then I discovered Rakarrack, and using it restored my sanity.

---

### Post by trulan on 2009-06-28
Well, I said I would update on equipment changes, so here we go:

Adding more memory to my desktop did not noticeably affect anything at all in Ubuntu.  Windows is happier though, but I don't trust it with my audio anymore.

I got the laptop (Dell inspiron E1505) and had Jaunty Studio on it, but it liked to freeze at random intervals when running Jack.  This is not the only Dell laptop to behave this way.  I am now running 64studio 2.1 with apparent good success.  It took a bit of fiddling to get a reliable configuration.  (Not to mention needing to overcome the install bug in 64studio 2.1 which requires setting your CPU clock back a few years if you want it to actually install properly.  Not exactly confidence-inspiring to run into this on a distro that is supposed to be rock solid.)

As expected, Ardour exports fine on this setup.  The desktop behaves as described earlier.

---

### Post by fedexnman on 2009-06-28
im glad i seen this thread today, im running jaunty 64bit with rt kernel n ubuntustudio added on, im using a firewire audio device. ardour crashes n jack disconnects when exporting right as it ask me to donate to ardour.

---

