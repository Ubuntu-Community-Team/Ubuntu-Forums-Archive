---
title: "No sound in WoW"
date: 2010-01-23
forum: Wine
---

### Post by dazer26 on 2010-01-23
Hey,  starting a while back I haven't had any sound when running wow through wine.  I'v messed with the wow sound settings and the wine sound settings with no luck.  I do seem to have strange sound issues on this desktop tho (Kubuntu 9.10).  For example if i'm watching tv on my computer nothing else is able to use the sound.  Songbird will share the sound with other other apps, but amarok won't always.  

My wine sound settings are the following
 -Alsa and OSS checked (tried using just on or the other, no luck)
 -Hardware accel = emulation (tried full)
 -sample rate = 44100
 -default bits = 16

Below is my SESound.log from my wow directory with the error.

1/23 13:26:58.708  => Version 3.3.0 (11159) Dec  9 2009
1/23 13:26:58.789   
1/23 13:26:58.830  => Setting up Game Sound:
1/23 13:26:58.872   - SESound Engine Init
1/23 13:26:58.914   - FMOD Memory Init
1/23 13:26:58.955   - FMOD System Create
1/23 13:26:59.000   - FMOD version 00040907 detected
1/23 13:26:59.039   - Hardware is ENABLED
1/23 13:26:59.080   - Reverb is ENABLED
1/23 13:26:59.122   - 1 Output drivers detected
1/23 13:26:59.164   --- [0] System Default
1/23 13:26:59.206   -######## FMOD ERROR! (err 37) An invalid parameter was passed to this function. 
1/23 13:26:59.206  .\SoundEngine.cpp(2513)
1/23 13:26:59.247   -###########################################################################################
1/23 13:26:59.289   -######## FMOD ERROR! (err 37) An invalid parameter was passed to this function. 
1/23 13:26:59.289   -######## ERROR INITIALIZING. ALL GAME SOUND DISABLED.
1/23 13:26:59.289  .\SoundEngine.cpp(2514)
1/23 13:26:59.330   -###########################################################################################
1/23 13:26:59.372  => Game Sound Init Failed.
1/23 13:26:59.414   
1/23 13:26:59.459  => User Settings Report:
1/23 13:26:59.489   - ========= PLAYBACK =========
1/23 13:26:59.523   - Enable All Sound         [1]
1/23 13:26:59.564   - Enable SFX               [1]
1/23 13:26:59.606   --- Enable Error Speech    [1]
1/23 13:26:59.648   --- Enable Emote Sounds    [1]
1/23 13:26:59.689   - Enable Music             [1]
1/23 13:26:59.731   --- Loop Music             [1]
1/23 13:26:59.773   - Enable Ambient Sounds    [1]
1/23 13:26:59.814   - Sound at Character       [1]
1/23 13:26:59.856   - Sound in Background      [1]
1/23 13:26:59.898   - Enable Reverb            [1]
1/23 13:26:59.939   - Enable Software HRTF     [0]
1/23 13:26:59.981   - Sound Quality            [0]
1/23 13:27:00.023   -
1/23 13:27:00.064   - ========== VOLUME ==========
1/23 13:27:00.106   - Master Volume         [1.00]
1/23 13:27:00.148   - SFX Volume            [0.60]
1/23 13:27:00.189   - Music Volume          [0.20]
1/23 13:27:00.231   - Ambience Volume       [0.60]
1/23 13:27:00.272   -
1/23 13:27:00.314   - =========== MISC ===========
1/23 13:27:00.356   - Sound Channels          [64]
1/23 13:27:00.397   - Use Hardware             [1]
1/23 13:27:00.439   - Mix Mode 2               [0]
1/23 13:27:00.481   - DSP Buffer Size       [AUTO]
1/23 13:27:00.524   - Armor Foley SFX (Self)   [1]
1/23 13:27:00.564   - Armor Foley SFX (Others) [1]
1/23 13:27:00.606  => End of User Settings Report
1/23 13:27:12.107   
1/23 13:27:12.168  => Shutting Down Game Sound
1/23 13:27:12.219  => Done Shutting Down Game Sound

---

### Post by Pikestaff on 2010-01-23
There is a known issue with Kubuntu Karmic where only one open application can play sound at a time: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/447844](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/447844)

My guess is that you're not getting WoW sound because you have some other program open that is using the sound.  Run **lsof | grep pcm** in terminal and see if anything else is using the sound (that should output a list of open programs "tying up" the sound.)  Then you can kill those programs (except Kmix) and see if it will get you WoW sound.

If that works, then it is simply the known issue I mentioned.  So far the only fix I have discovered for being able to, say, listen to music on Amarok while playing WoW-- while keeping Karmic-- is to install Gnome and use that instead of KDE until they (hopefully) fix it next distro upgrade.

---

### Post by dazer26 on 2010-01-23
thx for the reply, the output I got for lsof | grep pcm is :

kded4      2992       mike  mem       REG       8,33     22164     210138 /usr/lib/alsa-lib/libasound_module_pcm_pulse.so


So nothing but kde itself using the sound I guess.

---

### Post by Pikestaff on 2010-01-24
I did some Googling and found this: [http://www.linuxquestions.org/questions/linux-software-2/sound-doesnt-work-in-flashplayer-and-some-media-players-775162/](http://www.linuxquestions.org/questions/linux-software-2/sound-doesnt-work-in-flashplayer-and-some-media-players-775162/)

Maybe try some of the fixes they suggest in that thread?

---

### Post by 68pontiac on 2010-01-27
If you haven't figured it out your problem yet, check to see which version of Windows Wine is "emulating". Windows Vista will not produce any sound in WoW I've noticed. If it's anything but XP, set it to XP.

---

