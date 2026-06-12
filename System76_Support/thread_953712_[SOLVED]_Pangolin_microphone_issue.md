---
title: "[SOLVED] Pangolin microphone issue"
date: 2008-10-20
forum: System76 Support
---

### Post by christophermluna on 2008-10-20
Hey there,

I just got my Pangolin a little while a go, and I quite love it.  However, I am having an issue with the Pangolin microphone, a solution to which I have not been able to find on the forums.

To begin with, I would get nothing on the microphone input at all.  No static, no hum, no nothing.  This was tested both with the Gnome audio recorder, the Skype test call, and System > Preferences > Sound input device test.

So, I decided to search the forums.  My first search yielded the following thread:

[http://ubuntuforums.org/showthread.php?t=448025&highlight=Pangolin+microphone](http://ubuntuforums.org/showthread.php?t=448025&highlight=Pangolin+microphone)

This was for a Darter, but I figured that it might be useful anyway.  I was directed, from this thread, to check out [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) which I did.

From there, I figured that I might have to add an option model line to /etc/modprobe.d/alsa-base as perce did in the above thread.  I found out what codec my sound card was using, and consulted the list at [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt) trying various options for my codec.  Eventually, I rested on the 'auto' option, as the 3stack option didn't work.  Just for th sake of reference, the codec returned was 'ALC662.'

Now, with the option model line included in the file as 'auto', I got one main difference from no line in the file at all.  Now, when I adjusted the level of the microphones, I got static on the audio recorder instead of nothing.  When I took out the line and rebooted, even with the level of the mic turned up, I still got nothing.

I did a little more searching and read through this thread:

[http://ubuntuforums.org/showthread.php?t=925476](http://ubuntuforums.org/showthread.php?t=925476)

Figuring that it was possible that I was dabbling with things that were actually interfering with System76 Drivers or something, I decided to remove the option mode line, reinstall the System76 Drivers, and reboot.  I did so, and to no avail.  Back to nothing, not even static input.

So, the present state of affairs on my Pangolin has the option mode line in the file, and I get static on the mic feed.  To be specific, I have added the following line:

```
options snd-hda-intel model=auto
```

**EDIT** I actually have 'auto' above.  Before I had 'MODEL' written.

to the file '/etc/modprobe.d/alsa-base', and tested the sound recorder with both front mic and mic as possible input devices.  I have made sure the level of the front mic and the mic are both turned up.

Anyway, I wonder if there're any thoughts on this issue?

---

### Post by thomasaaron on 2008-10-20
Yes. Be VERY careful putting in model options in alsa-base. People have blown speakers doing that.

I'll image our shop Pangolin and test the mic. Mondays are hectic, so I'll get it done by tomorrow.

---

### Post by christophermluna on 2008-10-20
Yes, I figured after testing the first one and getting no sound that I shouldn't randomly try other models that I wasn't sure about.  But auto has worked fine.

Thanks in advance for your help!

---

### Post by thomasaaron on 2008-10-20
OK. Tell Carl thanks. It's solved.

Or, more accurately, it will be solved tomorrow when we update the System76 driver. You will be able to download it from the repositories. Just install, run, and reboot. 

It will be 2.2.6.

---

### Post by christophermluna on 2008-10-20
Being so new to this forum and System76, I don't know who Carl is.  But, thanks to you, and thanks to Carl.  I will update the driver tomorrow.

---

### Post by christophermluna on 2008-10-21
I have just marked the thread as unsolved again in case something doesn't work when the new driver is released.  I tried to update the driver this morning, but then I checked the number against the version you said it would be.

When the new driver is released, I'll install it and test, and if all goes well I'll post here to say so.

Thanks again!

---

### Post by thomasaaron on 2008-10-21
This is Carl:
[http://carlrichell.com](http://carlrichell.com)

---

### Post by thomasaaron on 2008-10-21
OK. It's up.

---

### Post by christophermluna on 2008-10-21
Tres bon!  It works beautifully.  Thanks again.

---

### Post by hvacr on 2008-10-21
I have followed this thread
[http://ubuntuforums.org/showthread.php?t=821389&highlight=mic](http://ubuntuforums.org/showthread.php?t=821389&highlight=mic)

installed the newest system76 drivers, and still no mic.

---

### Post by christophermluna on 2008-10-21
I had some trouble getting the newest drivers to download.  Even after following the directions on this thread ([http://ubuntuforums.org/showthread.php?t=954734](http://ubuntuforums.org/showthread.php?t=954734)), it didn't seem to quite work.

I had to go to Synaptic Package Manager, which still showed me as having the 2.2.4 driver.  I upgraded to the 2.2.6 package through Synaptic, then rebooted, then used the System > Administration > System76 Driver tool, and clicked on "Install Drivers."  Then I rebooted again, and this time the mic worked.

You might want to check to make sure you actually have 2.2.6.  You can see which version is installed by going to System > Administration > System76 Driver, clicking on the "Install Drivers" tab, and then clicking on "About."

I don't know if that will be helpful to you at all, but I figured I'd let you know since I had some issues getting the drivers installed.

Also, if you're talking about Skype specifically, I had to mess with the "Sound Devices" settings in Skype even after the mic was working.

On Skype, I clicked on the little Skype icon at the bottom left of the window, and clicked on "Options."

From there, I clicked on "Sound Devices."

Skype installed with the following settings:

Sound In: Default Device (default)
Sound Out: Default Device (default)
Ringing: Default Device (default)

I changed this to:

Sound In: HDA Intel (hw:Intel,0)
Sound Out: HDA Intel (hw:Intel,0)
Ringing: HDA Intel (hw:Intel,0)

At which point, I could hear and talk in Skype.

I hope any of this is helpful.

---

