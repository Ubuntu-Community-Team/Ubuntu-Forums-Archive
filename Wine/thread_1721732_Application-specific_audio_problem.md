---
title: "Application-specific audio problem"
date: 2011-04-04
forum: Wine
---

### Post by /bee/ on 2011-04-04
I'm studying music in college and I've been having a slight issue with using the antiquated little ear training app on the CD that came with one of my [textbooks]("http://search.barnesandnoble.com/Music-for-Ear-Training-3rd-Edition/Michael-Horvit/e/9780495565710").  I can run it through VirtualBox OSE without any insurmountable problems, but I want to know why I can't get it to work through WINE.

I removed every hidden trace of WINE from my computer and reinstalled it so I would know that it was indeed fresh and I hadn't mucked anything up accidentally.

I opened winecfg and went to the Audio tab.  Clicked on Test Sound and I can hear the sound it's making.

I kept the ALSA driver enabled and started the app through Terminal.  It works, except there's no sound.

Reading through the Terminal output, I saw this curious line:

```
fixme:mixer:ALSA_MixerInit No master control found on QuickCam Pro 9000, disabling mixer
```

QuickCam Pro 9000 is my webcam.  I unplugged the webcam's USB connection and started the app through Terminal again.  Now this is the output:

```
bee@frich:~$ wine /media/MusicET/MusicET.exe
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x161ba0,0x161b10): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x161810,0x1625a0): stub
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
```

Unplugging and removing my webcam from the picture got me a step further.  In the application's preferences menu, it now shows two entries.  (With the webcam plugged in it was showing nothing.)

[img]http://i.imgur.com/9I8TP.png[/img]

I tried selecting both and testing the audio in the program.  No joy.

Then I read that a lot of people have trouble with pulseaudio.  Disabling pulseaudio did nothing to help me.

I also tried using the OSS, JACK, NAS & EsounD drivers.  None of them worked.

The Control Panel button on the Audio tab of winecfg launches a Fixme window saying: Launching audio control panel not implemented yet!

Any thoughts or ideas on why I can't get the sound to work?

System information:
Ubuntu 10.10 Maverick Meerkat
2.6.35-28-generic kernel
Wine 1.2.2
nVidia GeForce GTS 250 (proprietary drivers)
lspci: 01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce GTS 250] (rev a2)

---

