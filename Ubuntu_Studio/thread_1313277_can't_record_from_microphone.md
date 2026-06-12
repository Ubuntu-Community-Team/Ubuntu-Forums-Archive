---
title: "can't record from microphone"
date: 2009-11-03
forum: Ubuntu Studio
---

### Post by tubunu on 2009-11-03
Whatever I do (and have tried) I cannot get anything recorded via microphone. I tried alsamixer (enabled everything), tried Sound Preferences (but there's nothing there, really), tried System/Preferences/Sound. 

I cannot record anything using a mic in Audacity, I also tried Ardour. 

My soundcard is Audigy 2 ZS. It works fine in Windows XP. I can't believe my Ubuntu cannot record a mic sound. Could anyone shed some light please?

BTW, I can hear myself talking to the microphone.

---

### Post by fredfelter on 2009-11-03
Me too. And Karmic does see my sound card.

A 1 hour search has not revealed any consistent fixes. This is a show-stopper for Ubuntu for me. There are hundreds of complaints re: this issue for every type of computer and the suggestions range from removing PulseAudio to adding lines to files to changing kernels. That is not a good sign that I am going to be able to solve this at my basic level.

Thinkpad T22

---

### Post by Jazzy_Jeff on 2009-11-04
> **tubunu said:**
> Whatever I do (and have tried) I cannot get anything recorded via microphone. I tried alsamixer (enabled everything), tried Sound Preferences (but there's nothing there, really), tried System/Preferences/Sound. 

I cannot record anything using a mic in Audacity, I also tried Ardour. 

My soundcard is Audigy 2 ZS. It works fine in Windows XP. I can't believe my Ubuntu cannot record a mic sound. Could anyone shed some light please?

BTW, I can hear myself talking to the microphone.



If you can hear yourself that means the mic is working. Now we need to find the right settings. First make sure you can't hear yourself. Click the little speaker below the microphone slider. Go into preferences and make sure you have either Microphone or Front microphone checked, depending on which one you are using. Also check the mic boost for which ever one you are using. Also check the Capture option and input source option.

Once this is done close preferences and then click on options. Make sure Mic is checked or front mic if that is being used. Also check some other option and then click back to the mic. Some times it is a little finiky. Let me know if this works.

---

### Post by tubunu on 2009-11-05
Thanks Jazzy_Jeff for your offer of help. 

Here are my settings from System/Preferences/Sound: 
Sound Preferences/Hardware lists Audigy 2 and the Profile pull down box has 18 different input options. None of the selected 18 inputs lists a device for sound input under the Input tab. Everything under Sound Preferences/Input is blank and greyed out. I assume this is the problem as Ubuntu doesn't see my microphone. Strange, because I *can* hear myself talking to the microphone. 

Gnome Alsa Mixer settings:
The soundcard listed there is not Audigy 2 but some SigmaTel STAC9750,51. Could that be the problem?

> Click the little speaker below the microphone slider. Go into preferences and make sure you have either Microphone or Front microphone checked, depending on which one you are using. Also check the mic boost for which ever one you are using. Also check the Capture option and input source option.

The problem is, there is no little speaker below the microphone slider. Are you talking about Sound Preferences in Karmic or Alsamixer (installed separately by me)? This used to be in Jaunty, but Karmic sound preferences is really weird, I just cannot wrap my head around it. It misses a lot of options that used to be there and it's like a step backwards. Am I missing something?

---

### Post by trulan on 2009-11-05
Jaunty used Alsamixer for those controls, in Karmic this has been turned over to Pulse Audio.  So the settings are going to look a lot different, and Alsamixer may not do what it used to.  I have had no trouble with Pulse, but I know there are quite a few Pulse haters around.  I know that's not too helpful, but it might explain why Alsamixer isn't working like it used to.

---

### Post by fredfelter on 2009-11-06
I appreciate the offers for help but after spending hours researching this issue and finding no consistent resolution, not even an official acknowledgement of it as best as I can tell, I've decided to abandon Ubuntu for having deceived me so badly on this "upgrade". I hope (probably in vain) that the developers who released Karmic see this and think twice next time before they screw up hundreds, if not thousands, of users with their sloppy script.

---

### Post by royleith on 2009-11-07
With all of the soundcards I have used, it is not possible to have Line In and Mic In enabled at the same time. I have had hours of fun helping a pal over the phone only to find that Windows has decided, off its own bat, to enable Line In and disable microphone input or vice verse.

Check in the mixer settings that both Line In, Mic, and Mic Boost are selected in Channels so that they appear in the Mixer and make sure that Mic is not muted and is set to a decent level with boost enabled. Make sure Line In is muted.

Then, of course, you have to set the record levels in your sequencer/recorder software.

Regards
Roy Leith

---

### Post by tubunu on 2009-11-07
> **royleith said:**
> Check in the mixer settings that both Line In, Mic, and Mic Boost are selected in Channels so that they appear in the Mixer and make sure that Mic is not muted and is set to a decent level with boost enabled. Make sure Line In is muted.

Then, of course, you have to set the record levels in your sequencer/recorder software.

That was the first thing I had done before I posted here asking for help... because it doesn't work! :(

---

### Post by tubunu on 2009-11-11
Can anyone shed some light on this?

I can hear myself in the microphone. I tried ALL Audacity settings (Recording devices), I have everything unmuted and at top volume in alsamixer. Yet I cannot record myself??

BTW, the mic records fine under Windows XP. :(

---

### Post by tubunu on 2009-11-11
Here is my setup: 

```
:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 2 ZS [SB0360]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [SB Audigy 2 ZS [SB0360]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [SB Audigy 2 ZS [SB0360]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [SB Audigy 2 ZS [SB0360]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```

:~$ lspci | grep -i audio
01:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)

```
```

:~$ cat /proc/asound/card*/codec#* | grep -i codec
cat: /proc/asound/card*/codec#*: No such file or directory

```

---

### Post by AutoStatic on 2009-11-12
Tubunu, which version of Ubuntu are you using? And this STAC thing, that's your internal soundcard. You could try disabling this by either disabling it in your BIOS or blacklisting it in /etc/modprobe.d/blacklist.conf by adding *snd-hda-intel* in that file.

---

### Post by tubunu on 2009-11-14
I'm on 9.10.

---

### Post by SlowYaRoll on 2009-11-14
I'm having a similar problem.  I can connect my mic and use sound recorder or skype.  When I'm in Sound Preferences looking at the Input option, I can see movement/sound.  The problem is, I don't hear anything through my speakers.  In order to hear, I have to record it then play it back.  

I'm using 9.10.  Any thoughts?

---

### Post by tubunu on 2009-11-17
> **SlowYaRoll said:**
> In order to hear, I have to record it then play it back. 


Sorry SlowYaRoll, but that's the opposite problem to what I'm experiencing. You can record, I can't. This thread is about not being able to record from microphone.

---

### Post by Thrash777 on 2009-11-20
Hello, i'm new to the forum and i believe i have the almost exact same problem as tubunu.

I know that the microphone works, but i am unable to use it in any application, such as audacity, skype, teamspeak, eve voice (internal voice system for eve-online, launched via cedega)...i can only hear myself over the speakers.

The microphone always seems to work for the first few seconds (i actually managed to record me speaking for 1 sec in audacity), but then goes completely dead.

I'm also fresh to Ubuntu so my limited knowledge doesn't help for sure.

Ubuntu: 9.10 karmic koala
Sound Card: integrated VIA VT1708/A

---

### Post by tubunu on 2009-11-20
I found a solution to the problem. :D

Install alsamixer, and launch it in Terminal
```
alsamixer
```

Change the view to Capture and make sure your Line In/Microphone is unmuted.

---

### Post by defaria on 2009-12-02
Damn! I had high hopes that this would work for me but alas it still doesn't. I have exactly tubunu's problem but with different hardware. I'm on 9.10 and I can hear myself through the mic but I cannot record it. I thought that perhaps alsamixer would work. It was not clear how to set the "Capture" view but typing tab did it. More about the alsamixer "interface" can be found in the man page.

I've also looked into amixer(1) which is a very primitive command line way of setting individual parameters. I've figured out that my mic is called 'Mic' - not 'Front Mic' because through amixer I can mute 'Mic' and I can no longer hear myself through the mic. (Muting 'Front Mic' does nothing). I assume that this means 'Mic' relates to the mic input in the back and perhaps there's a mic input on the front of the box that is for 'Front Mic'.

In any event I cannot record through the mic for the life of me. Nothing works. I can, however, record line in stuff. So I can, for example, record what Totem Movie Player is playing.

My audio device is ATI Technologies Inc SBx00 Azalia (Intel HDA). I'm on 9.10. I'm using pulseaudio and most things are working (I have had a problem with pluseaudio hogging the CPU and having to kill and restart it at times).

When I run PulseAudio Volume Control (pavucontrol) and then run Sound Recorder and attempt to record from the mic I can see under the Recording tab "Sound Recorder: Record Stream". There's a little speaker icon to mute the audio. When I click on that pavucontrol get a Segmentation fault.

Looking at Input Devices on pavucontrol I see "No input devices available" for all "Show" selections except "Monitors" and "All Input Devices". For that I see "Monitor of Internal Audio Analog Surround 5.1" a bunch of volume sliders (for Front L/R, Rear L/R, Front Center and Low Frequency". There are buttons for Mute, Lock and Set as fallback. When I select mute the mic does *not* mute. This makes me think that it is pulseaudio itself that is not connecting with the input device named 'Mic'.

If I run gnome-volume-control and go to the Input tab I see "Input volume" with a slider and mic icons and a mute toggle but it's all greyed out. There's an "Input level" label that is not greyed out but there's also a volume meter of sorts that appears to be greyed out. Under "Choose a device for sound input" there's nothing. I'm not sure if gnome-volume-control is the right application to investigate these settings.

---

### Post by bxcrx on 2009-12-04
We're all having the same problem here:

[http://ubuntuforums.org/showthread.php?t=1339409](http://ubuntuforums.org/showthread.php?t=1339409)

See if it works with the Live Karmic CD if it does then we all suffer from the same problem found here:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/460351](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/460351)

---

### Post by defaria on 2009-12-04
Thanks for the acknowledgement. Most people have laptops and are complaining about not being able to use the mic in Skype. I have a desktop and I'm just trying to do the basic thing of recording with sound recorder. Eventually, of course, I want to use Skype too but I figured just the basics to start. If I could record using my mic with Sound Recorder I'm sure Skype should work.

I also tried installing that backport thing to no avail. I will try a live CD boot. I suspect I'll be like you guys - works from the CD but not from the hard drive. I've already subscribed to the kernel bug. I hope they can get this fixed. It seems like such a trivial thing to have working!

---

### Post by ingeva on 2009-12-05
> **defaria said:**
> Thanks for the acknowledgement. Most people have laptops and are complaining about not being able to use the mic in Skype. I have a desktop ...

I have found a solution to this problem: Go back to earlier Ubuntu versions. It used to work with 9.04 (Not well, but it worked). :p

For security reasons, and because neither mic input nor Xscan (Scanner program) work in Karmic (9.10), I maintain a dual-boot system where I can boot 9.10 or Hardy (8.04). Actually, there are less problems with 8.04 than with 9.10. The reason why I use 9.10 anyway is that I like the interface better, plus it has more options.

So far I have never found a solution that works for 9.10, which means that if I want to use Skype I have to plan ahead. I can't receive calls unless I use only keyboard chatting (which I hate because it keeps me from doing anything else).
I'm a singer and for rehearsal purposes I want to record myself when practicing. I need to boot the other system to do that, but I have organized it so they share all relevant files and directories (the home directories are used for config files only).

If you think you have found a solution for 9.10: Please try it first so we all don't have to try the same thing and fail.

This is evidently a software problem. I have two very different computers, and they both behave the same way.

Let's hope the Ubunto people will fix this problem soon. :-\"

---

### Post by defaria on 2009-12-05
Going back to earlier versions of Ubuntu is not viable for me. First off my only earlier version is 9.04 and the mic didn't work there either. Secondly I'm not gonna be rebooting my system just to make phone calls. If I wanted to do that I'd just boot to the live CD.

However it's obvious that it's not "just" a software problem rather it must be a software (driver that is) **and** hardware problem in some combination. If it were just a software problem then everybody with 9.10 would have the same problem, yet many report their mics work for them. 

There is a bug reported on launchpad. Hopefully they'll fix the problem soon.

---

### Post by defaria on 2009-12-06
I wanted to add that when I ran from the Live CD I had a sound card that only had stereo controls. When I boot from my hard drive however I have 5.1 controls (I have a 5.1 sound card). So somewhere along the line I must have installed another driver to handle the 5.1'ness of the sound card. I suspect that that is indeed the culprit or at least the culprit in my case. 

OK, so given that I have an "ATI Technologies Inc SBx00 Azalia (Intel HDA)" sound card, how to I check that I have the proper driver installed?

Digging a little more it seems I have a ALC888 chipset but a "cat /proc/asound/card0/codec#0 | grep Codec" yields "Realtek ALC1200". According to [this]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false") page it seems to day for Linux that the driver is already built into the Linux kernel. So then I guess I need to wait until they fix it? Or should I submit another kernel bug for this hardware specifically?

Hmmm... I found this HD Audio Codec [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false"). Not sure if this is the latest driver that's appropriate for my card. The Readme.txt is saying for Ubuntu follow the manual install instructions which then references editing /etc/modules.conf (a file I don't have!) so I'm not certain I want to try that.

The driver that I downloaded seems to be "alsa-driver-1.0.21". How do I tell what I have installed?

---

### Post by ingeva on 2009-12-07
> **defaria said:**
> However it's obvious that it's not "just" a software problem rather it must be a software (driver that is) **and** hardware problem in some combination.The fact that it works fine with older software AND the same hardware indicates that it is "just" a software problem.
This is not to start a discussion, just to state the fact.

---

### Post by uberlube on 2009-12-07
Tubuntu, if your mic is a usb device you will have to create an .asoundrc that will point to the device to get it to work, a quick google will show u how to make one.

---

### Post by DerickX on 2009-12-07
If you want to do serious recording, I recommend to use JACK (qjackctl) and Ardour. When you do the setup the right way, you don't have problems with pulseaudio or something, cause JACK suspends pulseaudio.

---

### Post by defaria on 2009-12-07
> **ingeva said:**
> The fact that it works fine with older software AND the same hardware indicates that it is "just" a software problem.
This is not to start a discussion, just to state the fact.

Perhaps you are right. However why not discuss this if it will help lead to a proper characterization and perhaps a solution?

What I was saying is that there may be some hardware that work correctly with both older software and newer software. If that's the case then it's a combination of a driver bug on certain types of hardware. This seems reasonable because a driver writer can only really test his driver on hardware that he has access to - and I don't think he'd release a driver that fails for all known hardware. He has to rely on an assumption that other hardware will work in a similar manner or to a similar default spec. This is not always the case.

I'm not really trying to blame the hardware as it were, rather I'm just trying to help characterize the various variables involved.

---

### Post by shariyoun on 2009-12-11
up! 
I have the same problem with VT1708/A:(

---

### Post by shariyoun on 2009-12-11
> have you tried your mic in other systemyes ,it work perfectly in other system

---

### Post by williamson389 on 2009-12-12
This is annoying--i have the same problem hopefully they fix it soon.
I even tried a usb webcam/mic with no success. i have spent countless hours playing with preferneces and controls trying to fix it.  It seems like such a stupid thing to complain about, but its seems so simple it be working.
Good luck

---

### Post by dmalloch on 2010-12-21
If I go into Sound Preferences/Connector and select Analog microphone/Line-in/Microphone I can record from a source plugged into the Line-in jack.  If I instead choose Analog microphone/Microphone/Microphone I can record with the microphone plugged into the front microphone jack.  This works fine with Sound Recorder and with Audacity in Meerkat.

---

### Post by htsimps on 2010-12-26
Ok, I have basically the same hardware, and I was having the exact same problem -> could hear myself in the mic, but no device showing in Sound Preferences/Input. After a few hours of messing with everything and everyone's suggestions, here is what I did to fix it:

System->Synaptic Package Manager
    Search for padevchooser and install it.

Applications->Sound & Video->PulseAudio Device Chooser
    Takes a moment to start. When it does, a gray screen-like icon will appear in the upper
    task bar on the right. Putting your mouse over it will show PulseAudio Applet.

Left-click on that PulseAudio Applet and choose Volume Control.

Select Configuration Tab in the Volume Control.

Change Internal Audio to Analog Stereo Duplex and close the window.

Now click your little speaker icon in the top task bar and choose Sound Preferences.

Select the Input tab and select the button next to Internal Audio Analog Stereo to turn it on.

Slide the volume control to the right some to turn up the microphone volume and make sure the Mute checkbox is not checked. My connector showed Microphone 1, and I went with that. I set my slider to about 40% to start.

You can left-click on the PulseAudio Device Chooser in the upper right corner and quit out of it now.

You may or may not have to reboot. That is what fixed it for me. Hope it works for you all.

Basically, Pulse Audio was using the Audio Output device, but not one with a mic, so no device showed up in Sound Preferences/Input. The Audio Duplex selection tells Pulse Audio to use one with a mic (some of the other choices like Audio 5.1 with a mic also work). It was just a matter of finding a way to point Pulse Audio at the correct device, and that is what the PulseAudio Device Chooser allows us to do (via the PulseAudio Applet that it starts). Hope this all makes sense. Good luck!

---

### Post by marseille on 2010-12-30
OMG! It's taken forever to figure out why I can record with a [COLOR="Blue"]_[cheap logitech ``skype approved'' desktop *external* mic]("http://www.walmart.com/ip/Logitech-Desktop-Microphone/10992443")_[/COLOR] in Audacity (*using the* `[COLOR="Red"]MONO[/COLOR]' *setting*) but [COLOR="Blue"]_[not a peep out the mic from Sound Recorder or Skype]("https://help.ubuntu.com/community/SkypeTroubleshooting")_[/COLOR] ever since I upgraded -- *btw, for me 8.10 (regular gnome distro) and 7.04 (ubuntustudio) were rockin' ubuntu systems*.

htsimps explained the incomprehensible and tedious babble of pulseaudio/PulseAudioApplet/pavdevchooser and [COLOR="Red"]SOLVED my external mic skype chat nightmare[/COLOR] with his simple solution:

> **htsimps said:**
> 

PulseAudio Applet >> Volume Control >> Configuration Tab.

Change Internal Audio to Analog Stereo Duplex and close window.

task bar Speaker icon >> Sound Preferences >> Input tab >> Internal Audio Analog Stereo select button




It's worth mentioning ubuntu's [COLOR="RoyalBlue"][SKYPE TROUBLESHOOTING]("https://help.ubuntu.com/community/SkypeTroubleshooting")[/COLOR] documentation only helped where it said:

```
Skype tends to mess up the mixer settings. 
disable the automatic configuration of 
the mixer controls in Skype: 

right-click Skype icon in system tray >> 
Options >>  Sound Devices >> 
remove tick: Allow Skype to automatically 
adjust my mixer levels >> Apply >> Quit skype
```
[See [https://help.ubuntu.com/community/SkypeTroubleshooting]](https://help.ubuntu.com/community/SkypeTroubleshooting]).


And Notably, the recommended /etc/pulse/daemon.conf fix:

```
default-fragments = 8
default-fragment-size-msec = 5
```

is already set in Ubuntu 10.04 Lucid to:

```
default-fragments = 8
default-fragment-size-msec = 10
```


Additionally, I had already checked my [COLOR="Blue"]_[alsamixer]("http://ubuntuforums.org/showpost.php?p=9092124&postcount=6")_[/COLOR] settings long ago.


* * * hope this will help a fellow ubuntu user * * *

---

### Post by wiggie on 2011-01-23
I have had a similar problem. Whenever I opened the sound preferences from the ubuntu top panel in 10.04, I had to unmute the mic for it to record, or use skype. Unfortunately I would get a lot of feedback, and I could never wrap my head around it, why this was so.

Eventually I went to Applications > Sound & Video > PulseAudio Volume Control, and under the *Input devices* tab, I unmuted the mic. I could not find out how to do it with alsamixer in the terminal. Furthermore, all the changes I made in PulseAudio Volume Control I could see live in the open terminal with alsamixer running.

I hope this helps!

Also, an easy way of checking is to go to Sound & Video and use Sound Recorder to record little bits of sound as a check.

---

