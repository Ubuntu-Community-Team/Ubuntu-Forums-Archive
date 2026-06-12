---
title: "Viavoice 98 in Wine issue"
date: 2009-06-09
forum: Wine
---

### Post by Glaciusor on 2009-06-09
I'm having an odd issue with running ViaVoice 98 in WINE on Ubuntu 9.04 Desktop. Everything seems to be working fine, except it is forcing me to do the audio setup and I can't override that. The problem is when it makes me test the speakers, I can hear the test sound however the "next" button is disabled, and I can't find a way to enable it. I can't seem to find anybody who had this problem online either. I also tried finding a configuration file of some sort to see if I could make it think I already set up my audio devices. Does anybody have any ideas?

---

### Post by hikaricore on 2009-06-09
I'm not sure how useful a voice recognition suite will be through WINE.
I mean I doubt you'll be able to control your linux deskop with it.

The appdb page is pretty empty and the results are from an old version: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=7215](http://appdb.winehq.org/objectManager.php?sClass=application&iId=7215)

---

### Post by Glaciusor on 2009-06-09
Yeah, I figured as much. They did advertise that it worked though, and I would at least like to try. I got this one cheap off of Amazon and thought it would work with WinXP since it was listed to work with NT... I don't want to give up on it though. I can't seem to find anything good for Linux that does what ViaVoice does, although Perlbox is kinda ok I guess... I just want a way to control one of my 2 computers verbally (I use a Windows and a Linux machine simultaneously).

---

### Post by NightMKoder on 2009-06-09
You can try winetricks comctl32 (or whatever common controls are). You might want to give us a log here.

---

### Post by Glaciusor on 2009-06-09
I just tried that, and the problem is still there. There really isn't any log I can give, it's just that the button is disabled. There's only 4 buttons and a slider, and that's all the user has to interact with. One button is to play a test song, the slider is for volume control, and the 3 other buttons are back, next, and cancel. When I click that first button the back button is disabled. The next button is never enabled, and I have to click that get to the next step.

---

### Post by NightMKoder on 2009-06-09
I think it may be the apps way of telling you that you don't have a microphone. Try fiddling with your sound driver in winecfg.

---

### Post by Glaciusor on 2009-06-09
It's not in the microphone part of the process though, it's when I'm testing audio output is the problem. Although, I am noting some odd sound issues. I installed Audacity (the one for Win32) in Wine, just to see if my audio input and output settings are working, and they are; audacity records and plays back just fine.
 
I did manage to get the training program open in ViaVoice without having to go through their configuration program (the one I can't get through), and it says that there is no audio input after I start reading the training sentence out loud. It might actually have to do with my audio drivers after all, but they appear to be working for other applications. Any ideas on why ViaVoice can't get any audio input?
 
Another note is that when I get the option to choose between configuring my microphone and the sound levels, the bubble for the sound levels is also disabled.
 
 
Edited Later: Ok, I got the input working but now it complains about the mixer device not working. I will keep playing and see if I can find a combination that works... but I'm still open to any input that might help ^_^.

---

### Post by Glaciusor on 2009-06-10
Ok, I got it working... more or less. It's not that great in Linux I'm afraid (of course, when I used it on Windows a while back it wasn't that great either). Thank you for your help all the same ^_^.

---

### Post by GordonPeckham on 2009-09-07
I have exactly the same problem.  How did you get it working?
Regards,
Gordon


> **Glaciusor said:**
> Ok, I got it working... more or less. It's not that great in Linux I'm afraid (of course, when I used it on Windows a while back it wasn't that great either). Thank you for your help all the same ^_^.

---

### Post by Pengwyn44 on 2009-10-07
I am trying to run ViaVoice Pro USB edition, using Wine 1.0.1-oubuntu6.   
I went through the Setup program with no problems at all. My dictation input was accepted to set up my personal voice profile, again with no problems.
However when I tried to start the program proper all I get is the initial white box screen and nothing more.

I started the program in a terminal and got the following error results.

bryan@pcSpecialist:~$ env WINEPREFIX="/home/bryan/.wine" wine "C:\Program Files\ViaVoice\bin\SpeechBar.exe"   -L En_UK
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:msvcrt:__lconv_init  stub
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ntdll:RtlpWaitForCriticalSection section 0x7bc932a4 "loader.c: loader_section" wait timed out in thread 0021, blocked by 0020, retrying (60 sec)
err:ole:CoGetClassObject no class object {942d9d55-90cb-11d1-b908-0004ac349fa2} could be created for context 0x7
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
wine: Unhandled page fault on read access to 0x00000018 at address 0x62624833 (thread 0026), starting debugger...
Unhandled exception: page fault on read access to 0x00000018 in 32-bit code (0x62624833).

Perhaps someone can suggest what the problem might be.

---

