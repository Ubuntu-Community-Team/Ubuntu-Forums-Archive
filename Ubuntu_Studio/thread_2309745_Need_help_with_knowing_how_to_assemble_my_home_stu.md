---
title: "Need help with knowing how to assemble my home studio with what gear I have"
date: 2016-01-13
forum: Ubuntu Studio
---

### Post by J_Coppi_S on 2016-01-13
To start, the gear i presently have is a ZOOM g2.1 Nu an acoustic guitar and an electric guitar and some old headphones. I have managed to record with these using ARDOUR. To be honest, I havent used ARDOUR 3 yet.

Quite recently, I have heard of MIDI controllers and what wonders they could do, after saving up for a couple of months for an electric piano.

My planned gear to obtain are the following:

a MIDI controller, M audio axiom 49 or 61

a DAW interface, which I assume can be LMMS or Ardour3

additional cables

new headphones

microphones

Now, do i need an audio interface to plug the electric guitar + zoom combo i have into the laptop I have as well? will it conflict if I also plugged in the M audio into the mix? Where do i get decent patches for the other instruments i want to play via MIDI controller?

my genre of interest varies but it would focus more on guitars, piano, and drums. That's why i need the MIDI controller to compensate for the instruments I dont have at the moment. Even those instruments that would prolly be needed in film soundtrack attempts etc.

How do i connect all these up and be sure that I can use the MIDI controller to its full potential? I dont know how to get the MIDI controller on the ready with a bunch of patches, mic and guitar combo ready. Will i be needing a direct box for the guitar? 

I've done some research and I could see blurred answers only. So I ask. Thanks

---

### Post by yoshii on 2016-01-14
I can't answer all your questions, but I can tell you from experience researching that the M-Audio Axiom and the M-Audio KeyStation keyboards are USB Class Compliant, so they will work OK after they are plugged in and on for about 2 minutes.  No driver installation is needed.  Also, those MIDI USB Controllers won't interfere with anything at all.  

However, you will need to find an audio interface that either has modern Linux drivers available from the manufacturer, or get a USB audio interface which is also USB Class Compliant.  Otherwise, it just won't work.  
The audio interface is for recording and playing back of digital audio.  The MIDI controller is for triggering MIDI software.  

Personally, I am using Alesis M1Active 320 USB speakers which have a built-in audio interface because the whole thing is USB Class Compliant.  There might be some other more pro quality stuff out there that is similar to those.  The M1Active 320s (and 520s) are more semi-pro because they are only 16-bit and not 24-bit.  But I don't mind.  

Just so you know, Ardour and LMMS are not interfaces.  They are Digital Audio Workstation programs.  The interface is hardware, those DAWs are software.  

Sorry I can't be more helpful about this.

---

### Post by J_Coppi_S on 2016-01-15
> **yoshi2 said:**
> I can't answer all your questions, but I can tell you from experience researching that the M-Audio Axiom and the M-Audio KeyStation keyboards are USB Class Compliant, so they will work OK after they are plugged in and on for about 2 minutes.  No driver installation is needed.  Also, those MIDI USB Controllers won't interfere with anything at all.  

However, you will need to find an audio interface that either has modern Linux drivers available from the manufacturer, or get a USB audio interface which is also USB Class Compliant.  Otherwise, it just won't work.  
The audio interface is for recording and playing back of digital audio.  The MIDI controller is for triggering MIDI software.  

Personally, I am using Alesis M1Active 320 USB speakers which have a built-in audio interface because the whole thing is USB Class Compliant.  There might be some other more pro quality stuff out there that is similar to those.  The M1Active 320s (and 520s) are more semi-pro because they are only 16-bit and not 24-bit.  But I don't mind.  

Just so you know, Ardour and LMMS are not interfaces.  They are Digital Audio Workstation programs.  The interface is hardware, those DAWs are software.  

Sorry I can't be more helpful about this.

I can't buy studio monitors yet, too pricy, so i stick to headphones for now. Does that mean mean with an audio interface, I could plug the guitar and mics in, depending on the number of ports? I am actually considering USB class compliants that are within my price range. The audio interface will solely be for the mic/s and guitar inputs, whilst the midi controller is for everything I don't have. 

Do i need Qjacktl to connect the audio interface via usb as well? Thank you. Learned something there.

Does Ardour and LMMS work well with all the stuff?

---

### Post by jejeman on 2016-01-16
QJackctl is for managing JACK server. USB audio devices are handled with ALSA. JACK can use this device if you want.
Well, for microphone you need audio interface, but for electric guitar you can record via Zoom device you already got. Yes, you can utilize all input ports on audio interface at the same time.

LMMS does not record external audio, Ardour does. LMMS is somehow closed system.
Ardour3+ has MIDI support, you can activate LV2 or VST instruments in it, which can be controlled by MIDI.

---

### Post by marseille2 on 2016-01-16
Ardour 3/4 has presets for controllers, as well as a midi learn function, and the option to make your own map. I've had better luck with the midi learn function in LMMS, but for recording ... I wish I would have seen Ardour's controller presets to avoid another shopping trip. So I thought I'd share a shot of them in Ardour4:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=266784&d=1452974399[/IMG]

---

