---
title: "mp3 playback crashes intermittently"
date: 2011-06-26
forum: Ubuntu Studio
---

### Post by jtpratt on 2011-06-26
I'm using 10.04 Ubuntu Studio, and for the most part everything works just fine.  One weird thing is my update manager says my system is up to date, and I update on a regular basis, but my "Ubuntu->About" says that my 10.04 LTS was released on April 2010.  So there is a new version my update manager isn't telling me about?

So, on with the mp3 playback issue: I use Pandora and Youtube (in Opera, Firefox, and Chrome), and Rhythmbox,  and Totem.  MP3 audio playback crashes intermittently on ALL.  It's very random, happens in all browsers and all apps.  I can listen 5 minutes or an hour, then every single app gives an error.  I just double click on the next or previous song (or reload the pandora page) and it's fine.  It's not a flash thing, it happens in all browsers, and audio apps.

Question is - what (in the system) plays the audio for ALL these things, and can I delete it / reinstall to make it more stable?  Has happened for about a year now - oh, it happens in Skype as well.

Any help appreciated...

thx in advance!

---

### Post by varunendra on 2011-06-26
Do you mean it does not suggest any updates at all? If so, check your 'Software Sources' (update manager > settings) to verify if all (or at least the default) repositories are 'checked'. If no repositories are enabled, then it obviously will not check any servers for updates.

As for MP3 issue, if it happens only with mp3 or a few certain file types, then it maybe a codec related issue. Installing/updating gstreamer plugins should fix this.

---

### Post by jtpratt on 2011-06-26
> **varunendra said:**
> Do you mean it does not suggest any updates at all? If so, check your 'Software Sources' (update manager > settings) to verify if all (or at least the default) repositories are 'checked'. If no repositories are enabled, then it obviously will not check any servers for updates.

As for MP3 issue, if it happens only with mp3 or a few certain file types, then it maybe a codec related issue. Installing/updating gstreamer plugins should fix this.

No, all repositories are checked, and I get software updates nearly every day, and take them all.  However, my "about Ubuntu" still says I'm at only 10.04 and that's now 2 versions behind - and update manager says I'm completely up to date?  I have all repositories checked in software source.

I'll try the gstreamer thing...thx!

---

### Post by varunendra on 2011-06-26
> **jtpratt said:**
> No, all repositories are checked, and I get software updates nearly every day, and take them all.  However, my "about Ubuntu" still says I'm at only 10.04 and that's now 2 versions behind - and update manager says I'm completely up to date?
I might not be correct, but I guess 10.04 being an LTS release may be the reason, although I doubt it myself. My profile shows I'm using 10.04, but actually currently I'm on 10.10, so don't remember how update manager in 10.04 behaved. Normally, the newer version is not included in the list of updates, but is 'suggested' above the list box with a button labelled "Upgrade" beside it.

But be cautious! Upgrading via update manager is not recommended as it is too prone to errors and breaking down a system!! Although the option is there, it is always recommended to do a fresh install to upgrade. Just download the desired iso (preferably desktop version to be able to test it in live mode, and via torrent), burn it to a cd, and boot with it into live mode to see if it properly supports your hardware. If it does, then make a fresh install - separately or overwriting your current installation.

Yes you'll need to do all the customization and reinstall all the applications again that you installed via synaptic, but you'll need to reinstall most of them anyway due to version/kernel upgrade - no matter you upgrade via update manager or a clean install. Just back up your user-data before doing a 'clean install'.

As a side note- 10.10 is working fine for me, while as per number of problem threads per day - 11.04 is not quite stable yet! For most people - 10.04.2 is best. So you may wish to make a [remastersys ]("http://www.geekconnection.org/remastersys/ubuntu.html")backup first before trying something else.

---

### Post by Pablo_F on 2011-06-27
> I'm using 10.04 Ubuntu Studio, and for the most part everything works just fine. One weird thing is my update manager says my system is up to date, and I update on a regular basis, but my "Ubuntu->About" says that my 10.04 LTS was released on April 2010. So there is a new version my update manager isn't telling me about?

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://wiki.ubuntu.com/TimeBasedReleases](https://wiki.ubuntu.com/TimeBasedReleases)

---

### Post by jtpratt on 2011-06-27
I reinstalled absolutely everything associated with "gstreamer" in Synaptic and mp3 playback still crashes.

Thanks for the update tips - I would never (EVER) intall a fresh copy of Ubuntu.  I have entirely too much data in Virtual Machines, history, saved password, bookmarks - all kinds of stuff that would take days to re-configure and setup (and some of it simply couldn't be).  I've been updating just fine for 2 years - I'll wait until the computer dies before I reformat...

=)

---

### Post by Pablo_F on 2011-06-27
It seems a pulseaudio issue. 

I suggest you test with mplayer from the command line:

mplayer -ao pulse audio.mp3

---

### Post by jtpratt on 2011-06-27
> **Pablo_F said:**
> It seems a pulseaudio issue. 

I suggest you test with mplayer from the command line:

mplayer -ao pulse audio.mp3

seems to work fine:

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 16monkeys.mp3.
Audio only file format detected.
Clip info:
 Title: 16 Monkeys
 Artist: Los Lonely Boys
 Album: Rockpango (Deluxe)
 Year: 2011
 Comment: 
 Track: 5
 Genre: Hard Rock
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 320.0 kbit/22.68% (ratio: 40000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...

except for the couple weird lines about the socket and no such file.  Other than that it played fine.  the crashes are intermittent and random.

any other suggestions?

---

