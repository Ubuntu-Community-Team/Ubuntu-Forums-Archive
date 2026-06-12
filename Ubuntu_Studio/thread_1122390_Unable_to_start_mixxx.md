---
title: "Unable to start mixxx"
date: 2009-04-11
forum: Ubuntu Studio
---

### Post by elliotn on 2009-04-11
I have installed mixxx ran it then i clicked vinly Control but I dont have it. Now am unable to ru mixxx

Error.. Terminate called after throwing an instance of 'int'&#8233;
Aborted

---

### Post by elliotn on 2009-04-11
If I unistall it would I need to re download it again.

And would it solve it

---

### Post by djbushido on 2009-04-11
Try going to synaptic and do this - click and check "Completely Remove" or something like that, let it finish, and then re-install it.
If that still doesn't work, look into something like bpmdj, found [here]("http://bpmdj.yellowcouch.org/index.html"). I personally like bpmdj more. Also, terminatorx, or something like that.
And did you get the error by running in terminal and outputting that? If not, do this - "gnome-terminal -e mixxx".

---

### Post by m83 on 2009-04-11
elliotn: try to delete all the .mixxx* config files from the root of your home folder. I have tha following files: .mixxxbpmscheme.xml, .mixxx.cfg, .mixxxtrack.xml. Delete them and start mixxx. This should reset the config.

---

### Post by elliotn on 2009-04-12
None of the above worked, btw I couldnt find the confiq files plz some1 help

---

### Post by elliotn on 2009-04-15
Any1 plz help on this matter

---

### Post by Stochastic on 2009-04-15
Try running ```
sudo apt-get purge mixxx
``` then re-install it.

---

### Post by elliotn on 2009-04-16
K I would try that and come back

---

### Post by elliotn on 2009-04-16
That didnt  work either

---

### Post by Stochastic on 2009-04-16
Okay, a few questions, please answer them all.

1) What version of Ubuntu are you running?

2) What method are you using to re-install mixxx?

3) If you're using a package manager of any kind, what does your /etc/apt/sources.list file say?

4) What is the terminal output of ```
sudo apt-get purge mixxx
```

5) When you start mixxx in a terminal what's the output of that terminal?

---

### Post by wsonar on 2009-04-16
What box for vinyl control are you using I'm currious is it serato?

I was going to try it with my serato box

but using mixx when I had serato software already was kinda pointless

basicly in my opinion serato is the best vinyl control program for djing

---

### Post by elliotn on 2009-04-17
I am running 8.10 and I use the debs that was stored after I installed mixxx  from the parkage manager, purge removes all then it ask me to an auto remove.

---

### Post by elliotn on 2009-04-20
I dont have vinly's btw

---

### Post by Stochastic on 2009-04-20
> **Stochastic said:**
> 5) When you start mixxx in a terminal what's the output of that terminal?

?

---

### Post by elliotn on 2009-04-21
> **Stochastic said:**
> ?

```
elliotn@elliotn:~$ mixxx
Debug: Mixxx 1.6.0~beta3 "" is starting... 
Debug: SoundManager::SoundManager() 
Debug: SampleRate 44100 
Debug: Latency 64 
Debug: SoundManager::queryDevices() 
Debug: SoundManager::clearDeviceList() 
Debug: SoundManager::closeDevices() 
Debug: type signal
Debug: type marks
Debug: type signal
Debug: type marks
Debug: Loading playlists and library tracks from XML... 
Debug: Track::readXML "/home/elliotn/.mixxxtrack.xml" 
Debug: Break 
Debug: Found promo track: "Carlo Carosi - Stonewalled.mp3" 
Debug: Found promo track: "promo.xml" 
Debug: Could not parse "promo.xml" 
Debug: Found promo track: "UgressFeatChristineLitle-Redrum.mp3" 
Debug: Promo playlist has 2 songs. 
Debug: Constructed LibraryScanner!!! 
Debug: No playlists, returning 
Debug: FIXME: Need to tell the m_pPlaylistListModel to refresh in src/track.cpp on line: 1284 
Debug: Starting Library Scanner... 
Debug: Trying to add 27 songs to the library playlist 
Debug: Adjusting column widths: tracktable width = 582  1% of that is: 5.82  FIXME: this should be done when initalizing the skin. 
Debug: Shrinking Title/Comment for small screen...  
Debug: FIXME: repaintEverything switches table model and shouldn't do that when viewing the playlist model in  src/wtracktableview.cpp:  203 
Debug: selectedAPI is:  "ALSA" 
Debug: SoundManager::getDeviceList 
Debug: SoundManager::getDeviceList 
Debug: SoundManager::getDeviceList 
Debug: PowerMate: write():  Bad file descriptor 
Debug: PowerMate: write():  Bad file descriptor 
Debug: HerculesLinux: Constructor called 
Debug: m_pHercules init:  QThread(0xa385348) 
Debug: Starting Hercules DJ Console detection 
No Hercules DJ Console found
Debug: Sorry, no love. 
Debug: isRMX =  false 
Debug: Midi OK (Workaround not required) 
Debug: setupMappings( "/usr/share/mixxx/midi/Akai MPD24.midi.xml" ) 
Debug: loadSettings: 1 0 "SlowFade" 
Debug: slotApply crossfader: 1 "SlowFade" 
Debug: BpmSchemes::readXML "/home/elliotn/.mixxxbpmscheme.xml" 
Debug: SoundManager::setupDevices() 
Debug: Xwax Vinyl control starting with a sample rate of: 44100 
Debug: Building timecode lookup tables... 
Allocating 2097152 slots (8192Kb) for 20 bit timecode (Serato 2nd Ed., side A)
Debug: Created new VinylControlXwax! 
Debug: Xwax Vinyl control starting with a sample rate of: 44100 
Debug: Building timecode lookup tables... 
Allocating 2097152 slots (8192Kb) for 20 bit timecode (Serato 2nd Ed., side A)
Debug: Created new VinylControlXwax! 
terminate called after throwing an instance of 'int'
Aborted
elliotn@elliotn:~$ 

```

this what I get

---

### Post by Stochastic on 2009-04-21
Hmm, yeah it's pretty clear that undoing the configuration would take care of it.  'apt-get purge mixxx' should wipe all configuration files but it's clearly not doing this.  Maybe after running 'apt-get purge mixxx' you should run 'locate mixxx' and manually delete any files it finds.  Then do a re-install and see where that lands you.

Should that not work out, I'd say you should take this issue to the mixxx tech support forums: [http://www.mixxx.org/forums/viewforum.php?f=3](http://www.mixxx.org/forums/viewforum.php?f=3) and describe all that you can (including that terminal output).  The mixxx developers will be lurking on those forums.

As a side note, I did manage to find a .mixxx.cfg file but it was in a really old home directory backup, so it looks like those files no longer are used by mixxx.  I think most stuff has been moved to /usr/share/mixxx

Edit: come to think of it, if apt-get purge mixxx isn't clearing the config files, chances are that there's a bug in the mixxx package in Ubuntu.  Please post back here when you find the fix to this problem.

---

### Post by elliotn on 2009-04-22
Ok problem solved I just had to locate .mixxx.cfg which was hidden and delete it. After that it was ok. Problem Solved

---

### Post by Stochastic on 2009-04-22
> **elliotn said:**
> Ok problem solved I just had to locate .mixxx.cfg which was hidden and delete it. After that it was ok. Problem Solved

where was the .mixxx.cfg ?

---

### Post by elliotn on 2009-04-23
It was at /home/user/&#8233;
I used terminal to locate it

locate .mixxx.cfg&#8233;
In terminal and it displayed the locatiom

---

