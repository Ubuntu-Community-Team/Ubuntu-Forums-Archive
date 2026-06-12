---
title: "Just got my Pangolin Performance last night!  Many updates"
date: 2009-04-13
forum: System76 Support
---

### Post by UnkeptSpatula on 2009-04-13
15.4 inch monitor, 4G ram, 7200rpm 320 HardD

I turned it on this morning to check it out before class. Out of the box everything is working great. I took it to class and spent the whole time tinkering with the CompizConfig, fun stuff.

1) Just turning on the computer for the first time there were already 16 updates available, should I download all of these? I haven't messed with any of the updating options yet. Do you suggest that I download all updates that pop up? I think it's fine, but I've been using windows forever and just blinding doing updates with them I started getting a bunch of pop-ups and stuff that I didn't need. 

2) This is my first laptop. I would just let my desktop run for days...I'm sure that's not so good for the laptop though right? I don't think turning it on and off all the time is good either. If I am going to be using multiple times over a several hour period is it ok to just let it run? Should I put it in hibernate or suspend mode if I am going to take a break for an hour or two instead of turning it off and then back on again?

The computer looks and feels great, I look forward to diving into ubuntu

Thank you,
U. Spatula 
):P

---

### Post by thinman1189 on 2009-04-13
Welcome to ubuntu, UnkeptSpatula!

1) Typically with linux updates are safe if they're from the official repositories. You can add more in System > Administration > Software Sources, or by modifying the file in your text editor of choice. Only add repositories if you trust them. If they're official, then you're fine, just take them. 

2) I typically set it to suspend when I'm carrying to to classes, then resume when I get there. If I'm going to be back within 30mins to a few hours I do the same, but I always turn it off at night. I don't recommend just leaving it on if you're not using it. I don't really have any heat issues with my Serval unless I'm gaming for 5+ hours, but I usually just take that as a cue to break for a bit. Hibernate didn't work for me out of the box, but I haven't tried it in months so it may be fine for me now. Choice is up to you.

Enjoy ubuntu!

---

### Post by 3Miro on 2009-04-14
I always install all Updates for Linux. If you look at the official repository, pretty much all software there is open source and one cannot put spyware/bloatware or whatever such stuff in a OS program.

I use suspend -> resume -> hibernate -> resume cycles, depending on where and how I am laving it. If it is going to stay off on my desk hooked up to power, then I suspend. If I will be moving it around in my backpack, I use hibernate. And so on.

---

### Post by UnkeptSpatula on 2009-04-14
Thanks 3miro and thinman....it froze up the first time i tried hibernate so i think i'll cycle through suspend>resume.

a problem has developed, out of the box i was able to go to pandora.com and listen to music or watch youtube. Now I can not do either. When I try listening to music at pandora, the screen fades to gray and locks up and i have to force quit. when i try and do youtube there is no sound(i checked to make sure everything wasn't muted) I tried opening somethings in the movie player and it also just fades to gray and locks up. i tried listening to youtube with the headphones attatched to see if it made any difference, nope.

i tried going systems > preferences > sound  and running a test but it says "...failed to connect to stream, invalid argument" then i can't close it and i have to restart the computer to get the box closed. since i just got the computer a couple of days ago i haven't downloaded anything or saved anything important on it yet. i tried going to system76 through admin and downloading the drivers to see if it made a difference, nope. so i thought maybe i should do system>admin>system76>restore. that restores everything to how it was when i recieved the computer right? so it would delete any downloads, codecs or settings i've changed? 

the only things i've done really are download some codecs to watch videos on yahoo and tinkered with the graphic stuff in CompizConfig

the greeting sound work when i log in

i through in an audio cd and it's not even playing...so i couldn't check for sound...could be the cd or player, gotta go to class so will look into that one more later

help help i do so want sound.
thanks people):P

---

### Post by thomasaaron on 2009-04-14
Did you try re-starting the computer?

If you don't have sound after restarting, follow these instructions...

> First, run your System76 Driver (System > Administration > System76 Driver > Install Tab > Install Button) and reboot your computer.

Second, double-click on the speaker icon in the upper right corner of your screen. In the resulting Sound Control Panel, make sure your Sound Device is set to "HDA Intel (Alsa Mixer)." Then go to Edit > Preferences. (If you are using Ubuntu 8.10, you will have to click the Preferences button.) Make sure all available checkboxes have been selected. This will make more sliders available on the sound control panel. On the sound control panel, make sure that PCM, Master and Front (or whatever combination of these you have) are not turned down too low or muted.

Third, go to System > Preferences > Sound. Make sure all drop-down selectors are set to ALSA. (If you are using Ubuntu 8.10, make sure all of them are set to Pulse Audio instead.) Click the first Test button to see if you now have sound.   

---

### Post by UnkeptSpatula on 2009-04-14
> **thomasaaron said:**
> Did you try re-starting the computer?

If you don't have sound after restarting, follow these instructions...

i"ve tried all of that, all of my sounds settings are now set to pulse. i restarted and the same problems still exist. when i went to shut it down it said a program was still running bt not responding. "genome-sound-preferences"

---

### Post by thomasaaron on 2009-04-14
Please double-click your speaker icon and take screenshots of each tab of the volume control and attach them to this post.

Applications > Accessories > Take Screenshot

---

### Post by UnkeptSpatula on 2009-04-15
screen shot 1 is the volume 2,3,4 are what happens when i try to play the music.

on the screen shots i've included some txt to describe what's going on

thanks for the effort in trying to resolve my issues, it really makes me appreciate buying my pc from system76

---

### Post by UnkeptSpatula on 2009-04-15
this is what the camera looks like after i try to take a photo. the photo is captured but screen stays white

before and after

---

### Post by thomasaaron on 2009-04-15
Everything looks in order. Please reboot your computer, and then go straight to System > Preferences > Sound and click the first "Test" button.

I need to figure out if it is a problem with the computer itself or an issue with one of the webistes. Also, if you're opening a bunch of applications that require sound at one time, that could be causing a problem.

---

### Post by UnkeptSpatula on 2009-04-15
i tried that but i get the same error message as shown in the screen shots in the previous post

---

### Post by thomasaaron on 2009-04-15
OK, I think I see the problem now. I missed it before. Under System > Preferences > Sound, set the Default Mixer Tracks Device to HDA Intel (Alsa Mixer). See screenshot...

---

### Post by UnkeptSpatula on 2009-04-15
tried  that already too. i tried all three device options, then i tried alta instead of pulse with all 3 devices, no fix

---

### Post by thomasaaron on 2009-04-16
Try muting everything but PCM, Master, and Front. Why do you have surround cranked all the way up? Are you using external speakers? Also, please post screenshots of the other two tabs on your sound control panel. (Switches, Options, Recording, etc...).

---

### Post by thomasaaron on 2009-04-16
Also, I'm researching some bugs that deal with flash freezing and sound dying. 

Please confirm you are not using vmware or virtualbox.

---

### Post by UnkeptSpatula on 2009-04-16
> **thomasaaron said:**
> Try muting everything but PCM, Master, and Front. Why do you have surround cranked all the way up? Are you using external speakers? Also, please post screenshots of the other two tabs on your sound control panel. (Switches, Options, Recording, etc...).

there was no change with muting the other options. I turned up all of the volumes after the sound went out while trying to get some sound. i plugged in headphones to see if maybe i could get sound through there, nothing

---

### Post by UnkeptSpatula on 2009-04-16
> **thomasaaron said:**
> Also, I'm researching some bugs that deal with flash freezing and sound dying. 

Please confirm you are not using vmware or virtualbox.

I am not using vmware or virtualbox. Out of the box all I had done is ComizConfig and while i tried to watch some videos i downloaded some codecs that came up in the search...and i think i didn't even get the codecs until after the volume went out. I think i did try installing a flash while trying to get a video to play

---

### Post by thomasaaron on 2009-04-16
OK, I've got my shop pangolin set up exactly like yours, and I can't reproduce the problem to save my life.

There's a chance that one of the codecs you downloaded has hosed something. Generally, this is the best way to get all of your restricted codecs running...

[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

If you can remember what you downloaded, it would be a good idea to go to Synaptic Package Manager and uninstall it, and then run the tutorial.

If you can not remember, maybe try to run the tutorial anyway.

Also, since you're having flash problems too, I'd recommend uninstalling the flash plugin. The tutorial above will re-install it.

sudo apt-get --purge remove flashplugin-nonfree

---

### Post by UnkeptSpatula on 2009-04-16
Yea I did not think it was a sound setting. It is probably linked to the video bug. I can not play any video in any progrom or website (excluding youtube oddly) without the window graying out and freezing. 

Since the system is only a couple of days old if I did the system restore it would set everything back to how I received the laptop, correct? including deleting any codec, update or flash program i installed? i think it might be better just to scrap it and start from ground zero since i don't have anything important on the computer yet

Ill try the tutorial and see how things work

---

### Post by thomasaaron on 2009-04-16
Running Restore from the System76 Driver would not do that. You would have to re-image the machine. If that's what you mean, here is the tutorial...

[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

---

### Post by UnkeptSpatula on 2009-04-16
Yea I think I want to just re-image it. Just to be sure, that would set back the system to how it was once I pulled it out of the box correct? So I would have the option still to go to System>Admin>S76 Drivers and re-install your drivers afterwards?

---

### Post by thomasaaron on 2009-04-16
Exactly.

---

### Post by UnkeptSpatula on 2009-04-16
downloading 8.10 from the website you have to select a place to download it from(e.g. united states xmission or united states mit lab) does the option i select change the program i get? or are they the same it's just coming from a different place?

if there is a difference do you have a preference?

i tried running the tutorial but the problems still there

---

### Post by thomasaaron on 2009-04-17
It doesn't matter which site you download it from. Make sure you select the 64-bit version. It's further down the page.

---

### Post by UnkeptSpatula on 2009-04-17
thanks for trying to work it out, i downloaded ubuntu from the site and mae a CD. after reformating and downloading the drivers and updates again, everything works 

thanks for the help thomas

---

