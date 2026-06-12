---
title: "Multiple Problems On Update"
date: 2008-11-03
forum: System76 Support
---

### Post by jpoRS on 2008-11-03
Hey Folks,

I have had several problems since I upgraded to Intrepid.  I don't know if they are related, or just coincidental, but they all showed up after updating.  I have my system completely up to date, including the latest System76 driver.  O, and it is a three month old Pangolin (panp4i).

1. [Solved] Sound:  I can't get most sounds.  I get system beeps, and when I run beep in terminal I get sound, but FF, Amarok, VLC, Totem, etc, don't give me anything.

Solution: [http://ph.ubuntuforums.com/showthread.php?t=941376](http://ph.ubuntuforums.com/showthread.php?t=941376)
Volume controls were hidden on update.

2. Display: After fixing a [self-inflicted issue]("http://ubuntuforums.org/showthread.php?t=967213"), I am back to the problem that started the whole debacle.  The computer will only recognize resolutions up to 1024x768, leaving a quite grainy image on my 1280x800 screen.  I have my desktop set up fine now, but my login screen and secondary accounts are still set up wrong.  I have tried dpkg-reconfigure xserver-xorg, but the monitor selection part seems to be missing.  I still configure my mouse and keyboard, but no display.

3. [Solved] CPU:  I seem to be constantly running around 50% of my processor, where as I usually maxed out around 10% before.  Is Intrepid really that much more processor intensive?

Solution: Solved itself!

4. Evolution:  While I use Thunderbird for e-mail, I still use Evolution's calender to organize my life.  But all of my appointments are now gone, but I think I know the reason.  When I look at the screen my "Personal" calender check box is off, but when I click it, nothing happens.

Solution: Download Sunbird.

Sorry for the litany of grievances.  I just didn't know if any of them are related, so I figured it would be useful to have them all in one place.

thanks,
jim

---

### Post by Lee_Machine on 2008-11-03
I hear ya man, I am experiencing many problems too. From now on i'm not installing the new version until i know it is safe to do so.

At least on my need to work, must have for school, laptop.

My wife is getting annoying at me using her Macbook.

The irony of this is that upon me buying a new laptop a few weeks ago she told me to get the new macbooks and I was like "no I want a system76 with ubuntu" now she just laughs at me:lolflag:

---

### Post by jdb on 2008-11-03
> **jpoRS said:**
> Hey Folks,


4. Evolution:  While I use Thunderbird for e-mail, I still use Evolution's calender to organize my life.  But all of my appointments are now gone, but I think I know the reason.  When I look at the screen my "Personal" calender check box is off, but when I click it, nothing happens.

thanks,
jim

I switched from evolution to thunderbird about a year ago.
Mozilla also makes a nice calendar/appointment package called sunbird, if your tired of evolution you might want to take a look at it.
I could be confused, but I'm pretty sure I was able to import my appointments from evolution.

jdb

---

### Post by thomasaaron on 2008-11-03
jpoRS,
> 
1. Sound: I can't get most sounds. I get system beeps, and when I run beep in terminal I get sound, but FF, Amarok, VLC, Totem, etc, don't give me anything.

Try going to System > Prefs > Sound and setting everything to Pulse Audio.

2. Display: After fixing a self-inflicted issue, I am back to the problem that started the whole debacle. The computer will only recognize resolutions up to 1024x768, leaving a quite grainy image on my 1280x800 screen. I have my desktop set up fine now, but my login screen and secondary accounts are still set up wrong. I have tried dpkg-reconfigure xserver-xorg, but the monitor selection part seems to be missing. I still configure my mouse and keyboard, but no display.

I'm not clear on this. Are you trying using an external monitor too? Try this. If you are using an ext. monitor, disconnect it. Go to a terminal and run:

sudo apt-get --reinstall install xserver-xorg-video-intel
sudo dpkg-reconfigure xserver-xorg
sudo reboot now

Does that give you the 1280x800 option?

3. CPU: I seem to be constantly running around 50% of my processor, where as I usually maxed out around 10% before. Is Intrepid really that much more processor intensive?

run...
top
...in a terminal. Can you see what process is hogging cpu time?

---

### Post by jpoRS on 2008-11-03
1. Sound: Everything is set to Pulse Audio, and I have tried all of the other options as well.  Still no sounds, but it does make a loud beep whenever I shut the computer down.

2. Display: No I am not using a external monitor, it appears to be the same issue phyzome is having [here]("http://ubuntuforums.org/showthread.php?t=968856").  I will try your advice there as soon as I have a chance.

3. CPU: This one has appeared to solve itself.  Back down to normal operating levels today.  Probably just a fluke, sorry.

4. Evolution:  I think I just need to accept that Evolution (in my experience) is buggy.  Sunbird here I come.

Thanks,
jim

---

### Post by jpoRS on 2008-11-03
The Sound Problem:  I went back into System>Preferences>Sounds to poke around and see if I could find anything.  When I clicked the "Test" button next to the first drop menu, this error came up

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

```
Is that diagnostically useful?

Thanks,
jim

---

### Post by thomasaaron on 2008-11-04
Here is a thread dealing with the same problem. There are a couple of fixes suggested there.

[http://ph.ubuntuforums.com/showthread.php?t=941376](http://ph.ubuntuforums.com/showthread.php?t=941376)

Double-click your speaker icon, then click the Preferences button. Make sure all checkboxes are selected. Make sure PCM, Front, and Master are not muted. If you have a Digital slider, uncheck it.

---

### Post by jpoRS on 2008-11-04
Thanks Tom.  Sound is back!

jim

Woo 100th Post!

---

