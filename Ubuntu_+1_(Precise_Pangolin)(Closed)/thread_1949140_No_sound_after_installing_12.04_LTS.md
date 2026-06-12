---
title: "No sound after installing 12.04 LTS"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by yaacovk on 2012-03-29
Hello.
after installing the 12.04 LTS from scratch.
i cannot hear any sound when i try to hear some music or any alarm.
Of course that the first time i go to the setting up the sound in the system setting.
need your help.
Regards.
Yaacov.

---

### Post by PhantomTurtle on 2012-03-29
Is your sound detected by Ubuntu(is it in sound settings). Also you can find out the model of sound card by:
```
cat /proc/asound/card0/codec* | grep Codec
```
I had a problem like this too. I needed the Realtek HD Audio drivers. I just downloaded the drivers from the realtek site and installed them.

---

### Post by Elfy on 2012-03-29
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by yaacovk on 2012-03-30
> **PhantomTurtle said:**
> Is your sound detected by Ubuntu(is it in sound settings). Also you can find out the model of sound card by:
```
cat /proc/asound/card0/codec* | grep Codec
```
I had a problem like this too. I needed the Realtek HD Audio drivers. I just downloaded the drivers from the realtek site and installed them.

can yo please send me the Realtek link?
the link that i have is for .exe files.
my codecs are:

Codec: Realtek ALC887-VD
Codec: Intel IbexPeak HDMI

Yaacov.

---

### Post by PhantomTurtle on 2012-03-30
Here you go, [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2"). Those are the Realtek HD AUDIO drivers. Download the one that says Linux 3.0, which is the one you want. To install, you have to run the install script in the extracted folder with root permissions. So run it in terminal with sudo.

Not sure if you want this one but these are the AC'97 drivers: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#2") (I don't know the difference, but I know I needed the HD Audio one for my motherboard).

---

### Post by yaacovk on 2012-04-01
Thank you very much.

---

### Post by james0658 on 2012-04-13
> **yaacovk said:**
> Hello.
after installing the 12.04 LTS from scratch.
i cannot hear any sound when i try to hear some music or any alarm.
Of course that the first time i go to the setting up the sound in the system setting.
need your help.
Regards.
Yaacov.

(I'm using Beta 2 Final, and this is what I come up with)No need to listen to anyone's confusing crap about audio drivers, just go to your dash home and type Pulse Audio, apparently this was a quick fix for the developers.  Under the configuration tab there will be a drop down menu just select one of the audio options.  Ubuntu 11.10 didn't have this problem.  The sound preferences in 12.04 have absolutely no selections.  I don't know why they would mess around with the audio settings with the new release.  It's confusing everyone.  I couldn't get audio through HDMI on my tv with messing around with the regular sound settings.  It wouldn't even read that there was an HDMI cable plugged in for the audio.  I had to do it through the pulse audio program.  If you don't have it just install it through Software Center.  Hope this helps.  If not, my bad. :confused:  Or better yet if you want to install Pulse audio do it through synaptic manager, then you can select the extras that you need.  :popcorn:

Also sometimes once selecting this you might have to restart and go through and check that your audio settings are in the settings you want.  It's what I had to do, after selecting the proper audio output in pulse audio.  I'd stay away from the audio settings in system settings all together and just use the Pulse Audio.

---

### Post by cariboo on 2012-04-13
> **james0658 said:**
> (I'm using Beta 2 Final, and this is what I come up with)No need to listen to anyone's confusing crap about audio drivers, just go to your dash home and type Pulse Audio, apparently this was a quick fix for the developers.  Under the configuration tab there will be a drop down menu just select one of the audio options.  Ubuntu 11.10 didn't have this problem.  The sound preferences in 12.04 have absolutely no selections.  I don't know why they would mess around with the audio settings with the new release.  It's confusing everyone.  I couldn't get audio through HDMI on my tv with messing around with the regular sound settings.  It wouldn't even read that there was an HDMI cable plugged in for the audio.  I had to do it through the pulse audio program.  If you don't have it just install it through Software Center.  Hope this helps.  If not, my bad. :confused:  Or better yet if you want to install Pulse audio do it through synaptic manager, then you can select the extras that you need.  :popcorn:

Also sometimes once selecting this you might have to restart and go through and check that your audio settings are in the settings you want.  It's what I had to do, after selecting the proper audio output in pulse audio.  I'd stay away from the audio settings in system settings all together and just use the Pulse Audio.

What application are you actually using, as when I type ***Pulse*** in the Dash I get a noting found message.

---

