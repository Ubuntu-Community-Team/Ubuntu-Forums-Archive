---
title: "ViaVoice + Ubuntu 9.04"
date: 2009-10-08
forum: Wine
---

### Post by Pengwyn44 on 2009-10-08
I am trying to run ViaVoice Pro USB edition, using Wine 1.0.1-oubuntu6.
I went through the Setup program with no problems at all. My dictation input was accepted to set up my personal voice profile, again with no problems.
However when I tried to start the program proper all I get is the initial white box screen and nothing more.

I started the program in a terminal and got the following error results.

bryan@pcSpecialist:~$ env WINEPREFIX="/home/bryan/.wine" wine "C:\Program Files\ViaVoice\bin\SpeechBar.exe" -L En_UK
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:msvcrt:__lconv_init stub
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ntdll:RtlpWaitForCriticalSection section 0x7bc932a4 "loader.c: loader_section" wait timed out in thread 0021, blocked by 0020, retrying (60 sec)
errle:CoGetClassObject no class object {942d9d55-90cb-11d1-b908-0004ac349fa2} could be created for context 0x7
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
wine: Unhandled page fault on read access to 0x00000018 at address 0x62624833 (thread 0026), starting debugger...
Unhandled exception: page fault on read access to 0x00000018 in 32-bit code (0x62624833).

Perhaps someone can suggest what the problem might be.

---

