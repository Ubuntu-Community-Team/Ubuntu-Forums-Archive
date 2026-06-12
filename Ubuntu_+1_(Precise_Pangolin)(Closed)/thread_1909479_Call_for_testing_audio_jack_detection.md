---
title: "Call for testing: audio jack detection"
date: 2012-01-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by MacUntu on 2012-01-15
Forwarding a mail by David Henningsson to the ubuntu-devel mailing list:

> Hi!

Jack detection - what happens when you plug your headphones in - has been improved in kernel 3.3, and I hope we can have that functionality in Ubuntu 12.04 as well. It is e g one of the components needed to successfully have different volumes for headphones and speakers, and to have your media keys controlling your headphone volume when your headphones are plugged in, and your speakers when they're not.

However, the kernel team has asked for some specific testing before they are willing to merge the new jack detection stuff into the 12.04 Ubuntu kernel, and I'm hoping that you would be willing to help us out with testing.

[https://wiki.ubuntu.com/Audio/PreciseJackDetectionTesting](https://wiki.ubuntu.com/Audio/PreciseJackDetectionTesting)

Do remember, that if you find a kernel regression, that we have a way of contacting you, so we can figure out what went wrong and hopefully fix the bug.

Thanks in advance! 

---

### Post by clivejo on 2012-01-15
Tried it.  Doesnt work for me :(

---

### Post by geojorg on 2012-01-15
Can someone update the name of the columns to fill in the info.

---

### Post by MacUntu on 2012-01-15
> **clivejo said:**
> Tried it.  Doesnt work for me :(
Same here. :KS

> **geojorg said:**
> Can someone update the name of the columns to fill in the info.
Everybody can, I did. ;)

---

### Post by clivejo on 2012-01-15
PulseAudio wont even start for me !!


[B]uname -a
[/B]```
Linux P500 3.2.0-8-generic #14+jackdetection2-Ubuntu SMP Wed Jan 11 16:18:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

[B]pacmd list-cards
[/B]```
No PulseAudio daemon running, or not running as session daemon.

```

---

### Post by xyzzyman on 2012-01-15
Breaks pulseaudio for me also. :( alsainfo is also hanging up on me.

---

### Post by MacUntu on 2012-01-17
*bump*

---

### Post by mc4man on 2012-01-17
I've noticed that with the ppa pulse packages I don't have a headphone anymore in sound pref's > output (though headphones still work
will have to ck. on live session to see if orig pulse showed headphones

(the detection failed as no headphone jack was even found..

---

### Post by clivejo on 2012-01-17
Ive managed to get some sounds working  but no volume control or mute, I dont think its via  PulseAudio.  I have some media shortcut keys on the side of the keyboard for volume and mute, none of these work either.  I dont have a login to update the wiki, maybe someone could do this for me.

Ive uploaded alsa-info, results are here - [http://www.alsa-project.org/db/?f=33fad1c13aacc1d1a8174f82dfb9909773159139](http://www.alsa-project.org/db/?f=33fad1c13aacc1d1a8174f82dfb9909773159139)

I think I'm going to remove this kernel as I'm getting the ears blown off me.  Maybe when it works better Ill try again.

---

### Post by xyzzyman on 2012-01-19
David Henningsson used my log file and was able to fix the problem with pulseaudio and the update is up on the PPA. 

With model=auto in my alsa modprobe file headphone jack detection works great but it kills my internal subwoofer. No model line in my modprobe file kills headphones, and setting it to the closest available to my computer kills headphones but allows my subwoofer to work... Hopefully this feature will be able to be worked out, as it sounds like the kernel guys aren't as enthused as the pulseaudio team.

---

### Post by MacUntu on 2012-01-19
The model=auto option works here too. Similar, model=thinkpad shows no difference. No subwoofer, so I'm good. :P

---

### Post by xyzzyman on 2012-02-02
Bumping this as the jack detection routines have been backported to the kernel as of 3.2.0-11.19. On a fresh install for me w/o the PPA added my headphone jack now fails to mute the speakers, even with model=auto and ones more specific, or the default of nothing.

So even those who haven't installed the pulseaudio update that are running the latest repo kernel which is 3.2.0-12.21 as of the time of this please report back here weather things work properly or not for you? That way I can let David Hessington know if it's just my 
Acer Aspire 6930G being a pain or if others are having this problem. The 3.3 had a lot of changes to the auto-parser apparently so this was a big backport.

---

### Post by neu5eeCh on 2012-02-03
I can test this on my laptop (the jack has never worked) but I won't have time until later this evening or tomorrow morning. Is this too late?

---

### Post by xyzzyman on 2012-02-03
No, we're just in alpha 2 so tons of time. :) After David Hessingson pointed me to the jack redirection program I've finally got a grasp on how alsa and pulseaudio work in regards to headphones, etc, so if you're still having problems we can see what's going on with your system. Especially on laptops, even if you have the same model audio processing chip the pin-outs are all so different and there's no set database or anything so it's something that you aren't sure it works on a particular model until it's tried.

At the very least if it can't auto detect to set separate volumes for internal speakers or headphones, it should at least fail gracefully so that's why the more people who can take the 30 seconds to plug in headphones even if they normally don't use them will mean alot.

---

### Post by neu5eeCh on 2012-02-03
OK, I'll have a result sometime this evening, I hope. Stay tuned.

**Edit:** Sorry to be so witless, but it occurred to me that you're looking to test the audio jack. The problem I have is not with the audio jack, but the mic jack. Is this a separate issue or does the testing also cover the mic jack?

---

### Post by xyzzyman on 2012-02-03
> **VTPoet said:**
> OK, I'll have a result sometime this evening, I hope. Stay tuned.

**Edit:** Sorry to be so witless, but it occurred to me that you're looking to test the audio jack. The problem I have is not with the audio jack, but the mic jack. Is this a separate issue or does the testing also cover the mic jack?

This was for the headphone jack. The backports from 3.3 for alsa aren't geared towards the mic jacks but it's possible they have affected them.

---

### Post by shaneo1 on 2012-03-02
I too have the issue with the headphone jack not muting the speakers when headphones plugged in.  I am now running the beta and still have the issue.  

```
*-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:47 memory:db300000-db303fff

```

I raised a bug last week if anyone would like to attach themselves to it.
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/941219](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/941219)

I have an Acer Aspire 8930g

---

