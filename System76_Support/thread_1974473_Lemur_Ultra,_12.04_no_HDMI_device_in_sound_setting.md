---
title: "Lemur Ultra, 12.04: no HDMI device in sound settings"
date: 2012-05-06
forum: System76 Support
---

### Post by shochatd on 2012-05-06
I tried the HDMI output today on my new Lemur Ultra (I had not tried it before upgrading to 12.04). Picture was fine but no audio. I tried sound settings, but there was nothing obvious there to help. I found this addressed on the troubleshooting list on the System 76 support area, but it claimed that there would be a HDMI device listed under the output tab in sound settings. But I see no such devide -- only speakers and headphones. Is there some package I need to install? I did run the "restore" function in the System 76 Driver after upgrading.
-- David

---

### Post by shochatd on 2012-05-06
After a restart, I tried again and this time the HDMI device was there. So I selected it and it worked. No idea what caused the situation to change.

---

### Post by brdmn on 2012-05-07
I tried arandr -- available in the standard repository, and a useful alternative, especially if you're using a variant distro like Xubuntu.  Among other things, it lets you "activate" HDMI.  See [http://www.ubuntugeek.com/arandr-a-simple-visual-front-end-for-xrandr.html](http://www.ubuntugeek.com/arandr-a-simple-visual-front-end-for-xrandr.html)

---

### Post by jaychandran_s on 2012-05-12
Even I was having the same problem. The best method(that worked for me) was to update the entire OS, and then Restart the computer. I know this sounds a little stupid, but it **did** work for me, and even **now**, sometimes when I get the same problem, I follow the same procedure.

Hope this Helps!! ;)

---

### Post by shochatd on 2012-05-12
My current understanding is that while the video subsystem notices instantly when an HDMI device is connected or disconnected, the audio is not so smart. The OS has to be restarted to detect either transition. I think it's safe to consider this a bug, and I assume it will be fixed some time in the future.
-- David

---

### Post by shochatd on 2012-05-27
I guess it's time to write this up as a bug in launchpad, but I don't know what package it should be written against. Is it a kernel problem, an alsa problem, a pulse-audio problem, or something else? Again, I can get it to work, but only by restarting with the HDMI plugged in (which makes the HDMI show up in Sound Settings). Since the video subsystem obviously detects the HDMI immediately, the audio should as well.
-- David

---

### Post by isantop on 2012-05-30
> **shochatd said:**
> I guess it's time to write this up as a bug in launchpad, but I don't know what package it should be written against. Is it a kernel problem, an alsa problem, a pulse-audio problem, or something else? Again, I can get it to work, but only by restarting with the HDMI plugged in (which makes the HDMI show up in Sound Settings). Since the video subsystem obviously detects the HDMI immediately, the audio should as well.
-- David

I would report it against the kernel. If that ends up being the wrong project, it will be marked against the correct project and marked invalid as a kernel bug.

---

### Post by shochatd on 2012-06-17
I just discovered a couple of things that may shed light on this problem: First, if I kill and then restart pulseaudio, that will make it "notice" the HDMI and it will then show up in sound settings. Still not a solution, but better than restarting the OS. The other thing is that if I monitor the output devices tab of pavucontrol during all this, there is only one device listed at a time, namely the one I have selected in sound settings. It seems to me that implies that the selection is done at a lower layer than Pulse Audio. But if that's the case, it's surprising that restarting PA forces the HDMI to be "noticed". When I use this method, I sometimes get an error dialog saying that "Ubuntu 12.04 has experienced an internal error" involving gnome-control-center, but things continue to work in spite of this.

---

### Post by shochatd on 2012-07-07
Slight correction to my last post, which may shed some light: I did another test today to confirm that the problem is still present: If I plug in the HDMI cable (with TV on at the other end), the video reconfigures immediately, but the HDMI does not show up in the Output tab of Sound Settings. So as before, I tried pulseaudio --kill. Immediately, I saw the HDMI added to the list of outputs, *even before I restarted pulseaudio*. So it isn't really *restarting* PA that makes the HDMI get "noticed", but rather it's the killing of PA that does it. To me, that puts a whole new slant on the problem. It's as if PA is interfering with the refreshing of the list of outputs, so when it is killed, that process can proceed. Does that imply that the bug/blame goes to Pulse Audio?

---

### Post by isantop on 2012-07-09
> **shochatd said:**
> Slight correction to my last post, which may shed some light: I did another test today to confirm that the problem is still present: If I plug in the HDMI cable (with TV on at the other end), the video reconfigures immediately, but the HDMI does not show up in the Output tab of Sound Settings. So as before, I tried pulseaudio --kill. Immediately, I saw the HDMI added to the list of outputs, *even before I restarted pulseaudio*. So it isn't really *restarting* PA that makes the HDMI get "noticed", but rather it's the killing of PA that does it. To me, that puts a whole new slant on the problem. It's as if PA is interfering with the refreshing of the list of outputs, so when it is killed, that process can proceed. Does that imply that the bug/blame goes to Pulse Audio?

My guess is that this is related to the Intel Graphics issue. Try fixing that problem and see if that comes back.

---

### Post by shochatd on 2012-07-09
> **isantop said:**
> My guess is that this is related to the Intel Graphics issue. Try fixing that problem and see if that comes back.
What intel graphics issue?

Anyway, my previous post is bogus. I have since realized that when I issue the pulseaudio --kill command, it does kill the daemon, but it then starts right back up under a new pid. So I really was *restarting* it without realizing it. I guess my next attempt will be to see if there is some sort of udev event when I plug in the HDMI cable. If so, it might be possible to create a rule which restarts pulseaudio. Seems kludgy, but it ought to work.

---

### Post by isantop on 2012-07-10
> **shochatd said:**
> What intel graphics issue?

Anyway, my previous post is bogus. I have since realized that when I issue the pulseaudio --kill command, it does kill the daemon, but it then starts right back up under a new pid. So I really was *restarting* it without realizing it. I guess my next attempt will be to see if there is some sort of udev event when I plug in the HDMI cable. If so, it might be possible to create a rule which restarts pulseaudio. Seems kludgy, but it ought to work.

Please see this thread: [http://ubuntuforums.org/showthread.php?t=2014669](http://ubuntuforums.org/showthread.php?t=2014669)

---

### Post by Newbunto on 2012-07-10
> **shochatd said:**
> when I issue the pulseaudio --kill command

In case it helps anyone else, you have to issue that command as the logged in user, not as root.

For me, while this correctly makes the HDMI sound device appear, it does not make HDMI sound output work. That is, using Settings/Sound and then selecting the HDMI device and then using "Test Sound" produces no sound (whereas selecting Headphones or selecting Analogue Output and using "Test Sound" produces sound and from the correct place).

Any suggestions?

---

### Post by isantop on 2012-07-11
> **Newbunto said:**
> In case it helps anyone else, you have to issue that command as the logged in user, not as root.

For me, while this correctly makes the HDMI sound device appear, it does not make HDMI sound output work. That is, using Settings/Sound and then selecting the HDMI device and then using "Test Sound" produces no sound (whereas selecting Headphones or selecting Analogue Output and using "Test Sound" produces sound and from the correct place).

Any suggestions?

Please test the sound using an audio file or video, as the test sound item has been known to be unreliable when using configurations with more than two audio channels.

---

### Post by Newbunto on 2012-07-13
Unfortunately, no difference. Using Rhythmbox on an MP3 file. Plays fine through Headphones (really external speakers) or built-in speakers. No sound through HDMI.

The Sound Output device is showing as:

HDMI / DisplayPort 2
GF116 High Definition Audio Controller

The mode is "Digital Stereo (HDMI) Output".

NB: This is a bonp5.

---

### Post by jbelmonte on 2012-07-13
> **Newbunto said:**
> Unfortunately, no difference. Using Rhythmbox on an MP3 file. Plays fine through Headphones (really external speakers) or built-in speakers. No sound through HDMI.

The Sound Output device is showing as:

HDMI / DisplayPort 2
GF116 High Definition Audio Controller

The mode is "Digital Stereo (HDMI) Output".

NB: This is a bonp5.

What is your bonp5 connected to via HDMI?

Is the TV/Monitor set to play sound from the HDMI?

Are you sure that the HDMI cable is good and [_compatible_]("http://en.wikipedia.org/wiki/HDMI#Audio.2Fvideo") with both the bonp5 and the TV/Monitor?

---

### Post by Newbunto on 2012-07-18
> **jbelmonte said:**
> What ...?

All good questions and they did lead to the answer. Thanks!

I am embarrassed :oops:  to admit that the explanation was very simple ... monitor does not have  built-in speakers (I assumed it did) and I did not have speakers  plugged in to the audio-out connector of the monitor.

Plugging speakers into the monitor confirms that sound via HDMI does work.

So,  yes, sound is enabled on the monitor (there is mute and volume control)  and the HDMI cable is adequate for this combination (I haven't heard of  an HDMI cable where sound doesn't work - as far as I know sound data is  just carried on the same pins as video data, interspersed).

(Like  the person who started this thread, the HDMI device does not appear for  me automatically in the Sound settings but we have a workaround for  that.)

---

### Post by isantop on 2012-07-18
> **Newbunto said:**
> All good questions and they did lead to the answer. Thanks!

I am embarrassed :oops:  to admit that the explanation was very simple ... monitor does not have  built-in speakers (I assumed it did) and I did not have speakers  plugged in to the audio-out connector of the monitor.

Plugging speakers into the monitor confirms that sound via HDMI does work.

So,  yes, sound is enabled on the monitor (there is mute and volume control)  and the HDMI cable is adequate for this combination (I haven't heard of  an HDMI cable where sound doesn't work - as far as I know sound data is  just carried on the same pins as video data, interspersed).

(Like  the person who started this thread, the HDMI device does not appear for  me automatically in the Sound settings but we have a workaround for  that.)

I believe they're separate pins, but the same cable. ;-)

Sounds good, I'm glad you got it figured out. That's one thing you do have to be careful for.

---

### Post by shochatd on 2012-10-06
I decided to give this one more try before 12.10 comes along and it appears to be fixed. I have taken numerous updates (including several kernel updates) since I last tried so no idea when exactly the fix arrived. Now, plugging in the HDMI cable (attached to my TV at the other end) causes the HDMI to appear as an available output in Sound Settings. No restart required. No killing of Pulse Audio required. There is still the minor issue that *unplugging* the HDMI does not revert things completely -- the HDMI stays on the list and the Workspace Switcher thinks the display is still extended. But it seems that all it takes is one sleep/wakeup cycle to get things back to the no HDMI one-display state. However, this thread was about the HDMI not becoming available when first connected to the Lemur Ultra, so that appears to be fixed.

---

