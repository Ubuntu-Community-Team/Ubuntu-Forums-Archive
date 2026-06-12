---
title: "Why is PulseAudio the default mixer in Ubuntu?"
date: 2013-12-27
forum: Ubuntu, Linux and OS Chat
---

### Post by symphonius on 2013-12-27
I just switched to Ubuntu from Windows and then I switched to Xubuntu because Unity's Laucher takes up valuable space on my screen.
While searching stuff about Ubuntu I saw a lot of posts about switching to Alsa. I was using headphones the whole time and when I used my laptop's speaker, I couldn't hear anything. I purged every PulseAudio package in synaptic and installed Alsa Mixer and my speaker works again \\:D/

With so many posts about people switching from PulseAudio, why is it the default mixer installed in Ubuntu?:confused:

---

### Post by monkeybrain20122 on 2013-12-27
I don't know. I never have any problem with pulseaudio which cannot be fixed by simply changing a few settings (and that is for other distros, with Ubuntu even that is very rare). I know that there were many posts back in the time of 9.10 or something like that saying that pulseaudio was buggy, but that was a long time ago. 

Somehow there are people who are still stuck in 2009 and they continue to advise others to remove pulseaudio whenever there is any issue with sound and end up messing the system up even more. After messing up my 10.04 sound by removing pulseaudio following one of these people's advice (the problem turned out to be quite easily fixed) I have since followed the policy of ignoring anyone who tells others to remove pulseaudio because the person is likely clueless and probably running an unsupported OS. :)

Not knowing any detail I can't say what was wrong with your system, but probably could be fixed by changing a few settings in pauvcontrol or alsamixer without having to remove pulse (I experienced something like that in Manjaro Linux with xfce, some messing with pauvcontrol fixed it)

---

### Post by symphonius on 2013-12-28
When I searched I didn't see anything that could solve it, and I tried some solutions to no avail and well, I can't check if it would work with me messing around because I don't remember what packages I removed.

Most of the problem on the internet were about sounds not working, mine was working when I have my headphones plugged in but it wouldn't work with the laptop's speakers.

---

### Post by mikewhatever on 2013-12-28
Alsa doesn't always work for everyone, so why is it the default choice? In fact, why anything is?

---

### Post by QIII on 2013-12-28
Not a support request.  

*Moved to **Ubuntu, Linux and OS Chat***

---

### Post by squakie on 2013-12-28
You did open the mixer and check to see what the volume levels where set at (including the page you have to scroll over to), if anything was muted, etc., right?  Under sound settings, what was the default output?

---

### Post by 3rdalbum on 2013-12-28
There's no reason why your laptop speakers would work with Alsa and not with Pulseaudio.

Pulseaudio is just a layer on top of Alsa. Pulseaudio doesn't contain any drivers, it just mixes sounds together and feeds them to Alsa. I suggest that you probably just needed to change a wonky default setting in the Pulseaudio mixer.

The reason why Pulseaudio is default in Ubuntu is simply because it allows for additional features that can't be done, or can't be done easily and reliably, in Alsa. The reason you see so many people saying that they remove Pulseaudio is because it didn't work so well in 2008, and even people whose audio works perfectly well in Pulseaudio today will remove it because that's what they used to have to do.

---

### Post by buzzingrobot on 2013-12-28
> **jgj.adaoag said:**
> ... Unity's Laucher takes up valuable space on my screen.


The Launcher is easily set to autohide with one click in Settings.

(Headphones and speakers are often listed as two separate audio output devices. If sound is not configured properly (again, in Settings, and the mixer), then one or both may not be correctly set as an output device for Pulse or Alsa.  And, as suggested above, a common source of no sound is simply forgetting to turn the volume up.)

---

### Post by philinux on 2013-12-28
Unity launcher icon size can be reduced too. Vertical space is not an issue for me on a wide screen monitor or laptop.

---

### Post by symphonius on 2013-12-28
After all those replies, I decided to give PulseAudio another chance and look for the settings.

I reinstalled PulseAudio, force reloaded alsa, rebooted and for some magical reason it works with my speakers on the spot without changes. I did this a while back (purging Pulse then reinstall) and it didn't work. I think when I manually removed everything with PulseAudio using synaptic I may have removed the problem.

> **buzzingrobot said:**
> The Launcher is easily set to autohide with one click in Settings.

(Headphones and speakers are often listed as two separate audio output devices. If sound is not configured properly (again, in Settings, and the mixer), then one or both may not be correctly set as an output device for Pulse or Alsa.  And, as suggested above, a common source of no sound is simply forgetting to turn the volume up.)

I didn't knew about that autohide, but I don't want something to pop out when I accidentaly move my mouse to the side and there are times when I can't reach the keyboard (lying on the bed, laptop on table) so I use the mouse a lot and currently, I have a bottom panel with 20 launchers with the top panel for a list of open programs and other stuff. I don't want a launcher(unity) cramped with launchers(launchers)

Btw, I checked everything properly during the time of problem, the volume was set to 100% and the output device is not a dummy.

---

### Post by monkeybrain20122 on 2013-12-28
> **jgj.adaoag said:**
> 
Most of the problem on the internet were about sounds not working, mine was working when I have my headphones plugged in but it wouldn't work with the laptop's speakers.

That was the same problem I had when I installed Manjaro, as I said messing with some settings solved it.:)

---

### Post by symphonius on 2013-12-28
> **monkeybrain20122 said:**
> That was the same problem I had when I installed Manjaro, as I said messing with some settings solved it.:)

My problem vanished for some reason, for future reference could you tell me what settings you messed with? I tried to change some stuff in PulseAudio Volume Control and Sound Settings but didn't solve the problem at the time.

---

### Post by monkeybrain20122 on 2013-12-28
> **jgj.adaoag said:**
> My problem vanished for some reason, for future reference could you tell me what settings you messed with? I tried to change some stuff in PulseAudio Volume Control and Sound Settings but didn't solve the problem at the time.

I am afraid I can't remember, it has been a while. Something to do with switching playback output on pauvcontrol I think.

---

### Post by mörgæs on 2013-12-28
If people for some reason want a system without Pulseaudio they could try Lubuntu.

---

### Post by dominiquedesforges on 2013-12-28
i have living the same issue if any tips twel mi  bless:p:p;);)

---

### Post by symphonius on 2013-12-29
> **monkeybrain20122 said:**
> I am afraid I can't remember, it has been a while. Something to do with switching playback output on pauvcontrol I think.

If you mean pavucontrol, that's the sound settings I was talking about. Looks like the what I do in windows works in linux. (reinstalling the whole thing to fix a problem)

> **mörgæs said:**
> If people for some reason want a system without Pulseaudio they could try Lubuntu.
For me, I'll just stick with Xubuntu, Xubuntu looks like it is more customizable and Lubuntu does not look user friendly.

> **dominiquedesforges said:**
> i have living the same issue if any tips twel mi bless:p:p;);)
All I did was purge pulseaudio and then installing it again and then I force reload alsa

---

