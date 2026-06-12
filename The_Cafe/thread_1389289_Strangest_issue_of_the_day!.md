---
title: "Strangest issue of the day!"
date: 2010-01-24
forum: The Cafe
---

### Post by warfacegod on 2010-01-24
This gets my vote.

>  Re: How could I get answers here?
Introduction: the headphones are still not working

I opened a Gnome session and I was surprised to see it saying it was not up-to-date. Updates done in Ubuntu used to update the whole system but not anymore. Now it seems I ll have to open a Gnome session periodically to update it. Do you thing Xfce will also have to be updated individually?

If you wonder why I keep session types I seldom use, it is for security. It has happened to me that one session type stopped working so I could at least use the others (for example to come here to ask for help).

After updating Gnome it wanted to be rebooted and - HORROR! - it didn t even reach the login screen. It said : Ubuntu is running in low graphics mode. Your screen graphics could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself.

I tried Configure, test the current settings, and there I was offered to go back to the previous settings. I clicked on that and the screen went black. I could see part of the display only after going over it with the mouse. Like a foggy window, you can only see through it in the places where you wipped it with your hand. There I was wipping the black off with the mouse pointer (which had become a large X). I powered off manually and after reboot the display was OK. What a relief!

This problem came from nvidia 173.14.12. When booting if it says it is going to use this module the display is unusable. When it is not using the module the display is OK. It doesn t matter if the module is installed and it doesn t matter if when you are booting you see a screen with the nvidia logo. As long as in hardware drivers it says that the module is not being used it is OK. So if you have the same problem just try to find system/hardware drivers (if you can still see enough of your screen to reach that) disable the module and reboot.

Now for what I was told to do under Gnome.

e-Gee, right clicking on the speaker icon gives me access to preferences and there I have volume control preference only.
Select device: I have HDA Intel (Alsa mixer)

Below I have:
Master
PCM
Front
Front Mic
Front Mic Boost
Surround
Center
LFE
Side
Line-in
CD
Microphone
Mic Boost
PC Speaker
Capture
Capture 1

I thought Line-in could be it but it wasn t. Selecting Line-in made no difference. So I put it back to Master like it was before.

Roger Allott
System > Administration > Hardware Drivers
Only has:
NVIDIA accelerated graphics driver (latest cards)
Which is disabled

The *** nvidia has the cheek to say:
This driver is required to fully utilise the 3D potential of NVIDIA graphics cards, as well as provide 2D acceleration of newer cards.
If you wish to enable desktop effects, this driver is required.
If this driver is not enabled, you will not be able to enable desktop effects and will not be able to run software that requires 3D acceleration, such as some games.

A black desktop which has to be wipped with the mouse pointer and comes out completely distorted after that is what they mean by desktop effects. Some effects.

They should say:
If this driver is enabled, you will not be able to get rid of crappy desktop effects and will not be able to run software that requires 3D acceleration. As far as games are concerned you will not even be able to play freecell.

Summary: the headphones are still not working

Mariane
__________________
The result of the "make" command:
- Sitting bored in front of a computer
- Watching abstruse output scrolling upwards too fast to be read
- And waiting for something to go wrong 

Found here: [http://ubuntuforums.org/showthread.php?t=1388490]("http://ubuntuforums.org/showthread.php?t=1388490")

---

### Post by audiomick on 2010-01-24
Hmmm... sounds weird.

---

### Post by Swagman on 2010-01-24
> **audiomick said:**
> Hmmm... sounds weird.

I think that's the issue !!

---

