---
title: "Microphone Static Issues"
date: 2010-02-10
forum: Wine
---

### Post by Aiello on 2010-02-10
I'm having some problems using my microphone in Wine applications. It seems that all the microphone is able to produce is static under Wine applications, making such things as Ventrilo and the voice-recognition software in Rosetta Stone unusable. My mic works fine in native Linux apps, like Audacity and the GNOME voice recorder. I'm using a microphone that plugs into the "microphone port" in the front of the computer, not a USB microphone. 

I'm running Ubuntu 9.04 and using the latest version of Wine from the Wine Jaunty repos. 

Does anyone else have a problem like this? Any suggestions on how I could fix it?

Thanks!

---

### Post by Aiello on 2010-02-10
After some playing around in the ALSA mixer, it appears I can either have Wine pickup static or nothign at all. This is directly related to the PCM mixed setting. At or below a -5.00dB adjustment, Rosetta Stone can not detect any sound. At or above a -4.00dB adjustment, Rosetta Stone picks up wild fluctuations in volume even if I'm not producing any sound. I have a HDA Nvidia soundcard chipset if that helps at all. Again, native Linux apps pick up my voice fine. I REALLY would like to be able to use the voice recognition software in Rosetta Stone? Any suggestions? Please?! haha

---

