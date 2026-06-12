---
title: "System 76 internet audio recording"
date: 2012-09-14
forum: System76 Support
---

### Post by kend650 on 2012-09-14
Does anyone know how to record audio off of the internet?  I've tried the Sound Recorder app and all I get is static, even though I can listen to it while recording through the desktop speakers and it sounds fine.  The meter on the Sound Recorder seems to be keeping track of the audio.

I'm running Ubuntu 12.04 on a Bonobo 5 laptop.

Are there any other simple apps that allow internet recording?

Audacity doesn't work either.

This is amazingly frustrating for something that should be so simple...

Thanks in advance for any help!!

---

### Post by Carborundum on 2012-09-15
Install PulseAudio volume control
```
sudo apt-get install pavucontrol
```Start both pavucontrol and Sound Recorder, and start recording sound with Sound Recorder. Go to the Recording tab in pavucontrol, and make sure "Applications" is selected in the drop down menu in the bottom right corner. Sound Recorder should now show up. In the drop down menu next to Sound Control, choose "monitor of build-in audio analog stereo". All internal audio, including audio from the internet, will now be recorded by Sound Recorder.

---

### Post by kend650 on 2012-09-15
Thank you so much Carborundum!  That seems to have done the trick, although I did not change any of the settings, and the pavucontrol was already installed and the latest version, so I'm not sure what actually happened to allow me to record.

That being said, I'm finally glad to put this issue to bed!!

Thanks again for your help!!

kend650

---

