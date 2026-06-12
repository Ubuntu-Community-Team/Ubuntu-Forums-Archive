---
title: "Multiple sound devices SB Live and Focusrite Saffire"
date: 2008-07-19
forum: Ubuntu Studio
---

### Post by jukingeo on 2008-07-19
Hello all,

I am currently reconfiguring the sound on my machine.  I have a Dell Dimension 4600 that originally came with a Dell OEM Soundblaster Live card, but I switched it out for a SoundBlaster X-Fi due to the fact that unlike the store bought SoundBlaster Live, the Dell OEM version doesn't have an on-board soundfont synth.  That was with my Window set up because soft soundfont synths are known not to run well in Windows.  However, with making the switch to Linux I am faced with a few problems, one of which is that the X-Fi is really not very compliant with Ubuntu (hardy) even though I did manage to get it to run with the ALSA drivers here.  However, I don't have access to the soundfont synth.  Furthermore I am looking into other distrubutions of Linux and the card is not supported AT ALL in those distributions.

The other day I had an "accident" and wiped Windows out during a repartitioning of a USB stick.

I figured now would be the time to reconfigure my sound hardware before I reinstall Windows.  So being that the X-Fi isn't compliant with Linux, it is going bye bye.

Now I searched high and low for a good interface to replace the X-Fi.  I do want to do high end recording work and I want to use applications such as Ardour and Rosegarden.  Of course I need Jack to do so.

I found one that I really liked by a company called Focusrite and it is part of the Saffire series.  The problem is that this is a firewire device.  Hardware wise this isn't a problem for my machine as I do have a firewire ports on my machine.  However, it appears that firewire sound isn't really supported by Linux UNLESS you use Jack because of the necessity to use Freebob drivers.

The problem here is that I would not be able to play games or listen to streaming audio on the internet because programs/applications such as these do not go through Jack.

Being that Jack is really a virtual audio patch bay of sorts, I came up with this idea and I want to run it by anyone here that has knowledge in the following configuration.

What I propose to do is pull the X-Fi sound card and reinstall the old Dell OEM Soundblaster Live card that came with the machine. This card IS Linux compliant.  Next I want to buy the Focusrite Saffire and set it up through Jack/Freebob via the firewire port on my machine.

I am speculating that with a set up like this I should be able to route the output of the Saffire through an input on the SoundBlaster live, just for the sole purpose of monitoring what comes out of the Saffire through my machine.  The system sounds, internet sounds, and game sounds would all go through the Soundblaster live.  This in this case I figured I would solve all my problems.

Of course I figured the converse connection would work as well, if I could route the output of the Soundblaster through the Saffire, but in this way, I would need to have Jack running all the time.

So the question is this:

Can this be done?  Can a firewire and onboard PCI sound device be used at the same time?

I am open to advice and suggestions.

Thank You,

Geo

---

### Post by egrep on 2010-01-10
I just finished running alsamixer [gtk+ version] on the tower system I just built. I had 2 cards, and like you had issues. Three things;
1) Make sure you do not have cards in shared PCI slots - [http://www.euronet.nl/~mailme/index4.html#Device_busy](http://www.euronet.nl/~mailme/index4.html#Device_busy)
2) On one of the cards, move the jumper [JP1 I think] to the other pair of posts. This changes the interrupt vector of the second card.
3) Not sure it is needed, but consider disabling the onboard in BIOS. I will probably try and re-enable it once I reboot again...

I installed the ALSA Mixer GTK+ package via the software center and both cards are there, and the mixer lets you record 2 stereo tracks as far as I can tell. Will take some messing around. I am going to build a studio, ripping is not enough ;-]

Oh, and all of the Proteus [emu10k] pcm sounds are on the mixer too. Sweet. Now to find the DSP control program...

--egrep

---

