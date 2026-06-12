---
title: "Microphone + Wine"
date: 2009-10-13
forum: Wine
---

### Post by Rosemachinegun on 2009-10-13
Hi everyone. I'm trying to get my microphone to work with Wine, so I can use Rosetta Stone's voice recognition features. Everything in RS works fine except the microphone recognition. I'm using ALSA as my driver and Wine doesn't recognize my USB mic at all, though ALSA has no trouble finding it outside of Wine. 

 I know it's a common problem and so I googled around for a solution. I thought I found one [here]("http://www.nabble.com/Re%3A-Rosetta-Stone-Microphone-Detection-p19342002.html"), which suggests making a .asoundrc file and declaring the address of my mic... 

pcm.!default { 
type asym 
playback.pcm { 
type plug 
slave.pcm "hw:0,0" 
} 
capture.pcm { 
type plug 
slave.pcm "hw:1,0" 
} 
} 

... and it actually does recognize it. Trouble is, once the mic is recognized it fails to recognize my playback device, even though when left to default it has no trouble finding it. Thus I'm left confused and with the lesser of two evils, no mic at all, again. 

I'm at my wit's end with this, so I hope a more sagacious user can help me out here. Thanks for reading. :)

---

