---
title: "Banshee stutters during playback"
date: 2009-12-08
forum: System76 Support
---

### Post by gruntlips_ on 2009-12-08
When I play mp3 files in Banshee under Karmic 9.10 the sound skips/stutters randomly during the song (every 30 sec to 1 minute). I did not have this problem in 9.04. I have read about memory leaks etc with banshee but I haven't noticed any spikes in memory usage during playback when the stuttering occurred and my total system memory being used was pretty reasonable (~20%) during the time when bashee was doing this. I installed ubuntu restricted extras to play music but no other codecs, etc. I might have installed other codecs in 9.04 but I can't remember off-hand. This started right away after a fresh install of 9.10 about 2 weeks ago and has persisted since.
 
Thanks for your help!  Sorry in advance if the answer is really obvious or if I am not providing the right information.

- Chris

My specs:
9.10 + Gnome 2.28
Serval System76 laptop (serp4)
Core2 Duo 2.5o GHz
nVidia GeForce 8600M GT
4G ram

---

### Post by gruntlips_ on 2009-12-08
I forgot to mention. The same stuttering problem also occurs in Rhythmbox as well.

- Chris

---

### Post by Lee_Machine on 2009-12-08
Well since you already installed the Restricted Extras that would leave out a codec problem. 

Just make sure by checking in Synaptic for 

"ubuntu-restricted-extras"



Play a song using mplayer, and see if you get the stuttering.

Also, try out Exaile. It's another great music player.

---

### Post by gruntlips_ on 2009-12-09
Yes, ubuntu restricted-extras is checked in synaptic. I tried mplayer as well and get the same skipping. 

Anybody have any ideas?

- Chris

---

### Post by Lee_Machine on 2009-12-09
Do you get the same skipping while watching videos?

---

### Post by gruntlips_ on 2009-12-10
Yes it does it while playing video on VLC (although it seems less) and while streaming video content through the web browser.

Could this be related to issues with pulse audio? I am pretty surprised nobody else on this forum appears to be having any problems with audio stuttering in 9.10 a system76 computer.

- Chris

---

### Post by gruntlips_ on 2009-12-10
I found this guide in the main forum which mentions correcting audio stuttering by altering the default-fragments and default-fragment-size-msec default values in the file /etc/pulse/daemon.conf. I have experimented with different values and this seems reduce the stuttering somewhat, but not eliminate it.  The guide suggests values are sound card specific.  Does anyone have a suggestion for what to set these values to for the the serval soundcard - HDA Intel Realtek ALC268?

[http://ubuntuforums.org/showthread.php?t=789578&highlight=pulse+audio+guide](http://ubuntuforums.org/showthread.php?t=789578&highlight=pulse+audio+guide)

---

### Post by marshmallow1304 on 2009-12-10
For the purposes of ruling in/out pulseaudio as the culprit, do this:

```
gksudo gedit /etc/pulse/client.conf
```
Change
> ; autospawn = yes
to
> autospawn = no
save, and exit.

Then
```
killall pulseaudio
```

and see what happens if you open some audio in VLC.

---

### Post by gruntlips_ on 2010-01-04
Yes marshmallow, when I do this the stuttering stops. So it appears that pulseaudio is the culprit. 

So, what is the deal here?  Do I not use pulseaudio despite the numerous posts out there telling me I need to learn/understand/make peace with pulseaudio as it is an integral part of ubuntu? And, if I do not use pulseaudio is my system less stable?

Or, do I tweak the pulseaudio configuration to make it work properly, and if so how?

---

### Post by calbaker on 2011-12-07
Bump.  I'm having this problem in 11.10 with a brand new Lenovo ThinkPad E420.  Any thoughts?  I'm trying to be like this guy: :guitar:, but the best I can do is this: :confused:.

---

### Post by isantop on 2011-12-08
I don't think this is the same problem, since these were all resolved for us with 11.04 and 11.10. Unfortunately, I'm not at all familiar with ThinkPad hardware, and can't point to what might be causing your problem.

---

### Post by Ranko Kohime on 2012-01-02
> **calbaker said:**
> Bump.  I'm having this problem in 11.10 with a brand new Lenovo ThinkPad E420.  Any thoughts?  I'm trying to be like this guy: :guitar:, but the best I can do is this: :confused:.
Having the same issue with the same laptop, but mine is a full system stutter: the mouse actually locks for a fraction of a second, then releases, in time with the audio stutter.  Video is the same.

I have conky running, with a list of CPU hogs, and immediately after the stutter, I'll see "wpa_supplicant" at the top of that list.  This occurs ONLY if I'm connected to a WPA encrypted network, (but is not bandwidth dependent, happens as frequently at idle as when transferring large files), OR if the wireless is enabled, but not connected, and the stutter appears to happen exactly when the list of AP's is refreshed.  Does NOT happen when connected to an unencrypted network, or with wireless disabled.

Going to report this to be split to Hardware, as I think ours is more appropriately an issue with Ubuntu's WPA program, and the Thinkpad's wireless NIC.

---

### Post by lisati on 2012-01-02
Please start a new thread. Things change in the technology world quite quickly.

---

