---
title: "Software Centre disappears (crashes) a few secs after appearing"
date: 2016-11-27
forum: Ubuntu Studio
---

### Post by shaunthesheep on 2016-11-27
I am using Ubuntu Studio 16.04.1. 

Since installing US 16.04.1, Software Centre (re-named 'Software') has been rather clunky. Until today, it took a around 10-15 seconds to fully launch and then the progress bar didn't work properly when installing software, which was rather confusing as it was not clear when, or if, the process was complete.  Now, after trying to uninstall EchoMixer, Software (Centre) appears momentarily then disappears (crashes) every time it is launched. 

I can, however, launch Software (Centre) successfully using the terminal with:

```
~$  gnome-software
```

The EchoMixer appears to have been uninstalled as it has disappeared from the Software > Audio Production > Mixers and cards list. 

Background

I was trying to solve an audio problem by reinstalling EchoMixer. I clicked on 'uninstall' EchoMixer and nothing happened. The progress bar didn't move. 

 In the past week, I've been getting terrible audio distortion when playing back  videos on the Web, usually while using Firefox on YouTube. It is OK to begin with then the distortion kicks in for no apparent reason. After rebooting the problem goes away for a while, then the same problem recurs. The distortion is also present when playing back audio files in VLC too. I am using EchoAudio Mia 24/96 soundcard. I wondered if is a problem with the audio drivers, hence the attempt to install and re-install EchoMixer. 

Question: does this just reinstall the Echomixer or does it reinstall the EchoAudio drivers too? 

However, when I search for 'EchoMixer' in the Software (Centre), it doesn't appear. Can anyone suggest how I can re-install from the command line? Update: I found the command for this which has re-installed the EchoMixer.

```
sudo apt-get install alsa-tools-gui
```

Any help appreciated.

---

### Post by ajgreeny on 2016-11-27
This is a known problem and bug that is asked about many times in the forum.

See [https://ubuntuforums.org/showthread.php?t=2344562&p=13575306#post13575306](https://ubuntuforums.org/showthread.php?t=2344562&p=13575306#post13575306) where I mention one way round this using synaptic.

---

### Post by jimmypants on 2016-12-01
I am experiencing a similar symptom, among 3 other crash problems.  All problems popped up after I did an update after my fresh install of 16.04.1 LTS.  (No problems before the update.)

---

### Post by jimmypants on 2016-12-02
My problem (16.04.1) was fixed by today's update.  Woohoo!  Details:
[https://ubuntuforums.org/showthread.php?t=2345319](https://ubuntuforums.org/showthread.php?t=2345319)

---

