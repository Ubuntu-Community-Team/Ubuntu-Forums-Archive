---
title: "WoW crashes with Wine"
date: 2010-08-17
forum: Wine
---

### Post by Kenjitamura on 2010-08-17
For a while I had a problem whenever I played World of Warcraft specifically dealing with audio.  At first there was no audio at all, my default settings in winecfg were Windows Vista and ALSA audio.  I messed around with it a a bit and found that the audio worked if I changed the "Windows Vista" setting to "Windows NT 4.0".  However, the problems weren't completely solved.  My gameplay was very laggy and occasionally WoW would crash.  Sometimes I'd try to login and WoW would crash with an error and I'd have to restart to be able to play.  Found out pulseaudio was the culprit.

So after some googling I found my fix on this site [http://www.3spoken.co.uk/2009/08/making-wine-sound-work-with-pulseaudio.html]("http://www.3spoken.co.uk/2009/08/making-wine-sound-work-with-pulseaudio.html").  It's Wine with pulseaudio driver support now my FPS has improved and I no longer crash. In summary here is what needs to be done:
Open the terminal and
```
sudo add-apt-repository ppa:neil-aldur/ppa
```
```
sudo apt-get remove wine
```
```
sudo apt-get update
```
```
sudo apt-get install wine1.2
```

Now run winecfg and open the audio tab, select pulseaudio and unselect alsa.  Finally click apply and okay.  Hope this helps someone else.

Edit: Found out ppa:c-korn/ppa has more recent wine version.  However it is only for 10.04, I'm using 10.04 but when I installed the wine from the c-korn ppa my game started to crash again.  I recommend Neil Wilson's version.

---

### Post by cwwilson721 on 2010-08-18
> **Kenjitamura said:**
> For a while I had a problem whenever I played World of Warcraft specifically dealing with audio.  At first there was no audio at all, my default settings in winecfg were Windows Vista and ALSA audio.  I messed around with it a a bit and found that the audio worked if I changed the "Windows Vista" setting to "Windows NT 4.0".  However, the problems weren't completely solved.  My gameplay was very laggy and occasionally WoW would crash.  Sometimes I'd try to login and WoW would crash with an error and I'd have to restart to be able to play.  Found out pulseaudio was the culprit.

So after some googling I found my fix on this site [http://www.3spoken.co.uk/2009/08/making-wine-sound-work-with-pulseaudio.html](http://www.3spoken.co.uk/2009/08/making-wine-sound-work-with-pulseaudio.html).  It's Wine with pulseaudio driver support now my FPS has improved and I no longer crash. In summary here is what needs to be done:
Open the terminal and
```
sudo add-apt-repository ppa:neil-aldur/ppa
``````
sudo apt-get remove wine
``````
sudo apt-get update
``````
sudo apt-get install wine1.2
```Now run winecfg and open the audio tab, select pulseaudio and unselect alsa.  Finally click apply and okay.  Hope this helps someone else.

Edit: Found out ppa:c-korn/ppa has more recent wine version.  However it is only for 10.04, I'm using 10.04 but when I installed the wine from the c-korn ppa my game started to crash again.  I recommend Neil Wilson's version.Lots of things to pay attention to here:

[LIST]
[*]Run WoW as XP (Or good luck with sound)
[*]Pulse audio, if needed, works GREAT with korn version, which is now up to v1.3.0 But this is dependent upon your hardware (which the OP neglected to post...BAD OP!!!)
[/LIST]
So, anyone reading this, take it with a grain of salt. The OP made 2 mistakes: He didn't run WoW in wine under 'XP mode' (Which is a well known issue, and posted about many times), and didn't post any hardware specs (Nor any other software he was using, like Mangler or wine/Ventrilo, which will also affect sound and lag issues)

---

