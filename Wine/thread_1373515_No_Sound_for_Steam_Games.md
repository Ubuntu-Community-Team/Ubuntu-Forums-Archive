---
title: "No Sound for Steam Games"
date: 2010-01-05
forum: Wine
---

### Post by altp on 2010-01-05
[B]SOLUTION CAN BE FOUND BELOW THE ORIGINAL PROBLEM


ORIGINAL PROBLEM[/B]

I need help as I don't know what other options to pursue.  My Steam games lack sound, but the problem isn't localized to just Steam though it seems to be the crux of the problem.

I'm running a 64-bit Kubuntu Karmic installation with a standard Wine installation (i.e., not Wine64).  I installed Steam to its own wine prefix and the only winetricks I did were to install fonts.

When I load up Steam, sound dies.  Exiting Steam solves this problem and I can hear sound again.  This leaves me to believe this is a problem with my sound system but I do not know what could cause it.  Do note that since I'm using Kubuntu Karmic, it does not have PulseAudio installed by default.  I believe the sound system is ALSA still.

The act of starting up Steam causes the sound to die out.  I can't hear YouTube videos or anything.  I also have Guild Wars installed to a different wine prefix and it doesn't have any sound problems by itself or with other sources like YouTube.

Any help would be appreciated.  Thanks!


**SOLUTION**

Turns out it was a lack of a complete ALSA configuration.  An update for my sound card's drivers were in a newer kernel than released, so it was backported by the Kubuntu package managers.  You can install it with the following:

```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

For good measure, you can also backport other things if you wish:

```
sudo apt-get install linux-backports-modules-karmic-generic linux-backports-modules-headers-karmic-generic
```

---

### Post by altp on 2010-01-05
I should really add some information.

ATI Radeon HD 5750 with Catalyst 9.12
Wine 1.1.35
winecfg audio driver set to ALSA, Full Hardware right now.  I tried emulation and it didn't solve my problem.

Additionally, after playing Team Fortress 2 for about 10 seconds, my system goes into a hard lock and I can't do any operations as far as I can see (though the system still responds because I issued a REISUB command to restart the system).  This leads me to believe it's an fglrx bug.

---

### Post by Soulcage on 2010-01-05
Have you tried running steam from a terminal you can use: cd ~/.wine/drive_c/Program\ Files/Steam/ && wine Steam.exe
That might give you error messages to help solve the problem.

---

### Post by altp on 2010-01-06
I hadn't considered doing that and gave it a shot.  Ended up with a log filled with d3d errors, but no errors relating to sound as far as I could see.

I think this may be a problem with Kubuntu.  When I was searching for a solution, there were numerous posts about how Kubuntu developers were planning on phasing ALSA out in favor of PulseAudio in the next release and actually dropped parts of it in Karmic, which is rather painful to debug a problem like this.

Thanks for your help.  I hope someone else can offer some insight, but right now I'll probably downgrade to Jaunty or something.

---

### Post by gyebro on 2010-01-24
A couple of weeks ago I had similar problems running Steam games when audio was set to ALSA. Some of the games didn't even start, some of them started but without sound.

After some search I installed the alsa-oss package that includes the aoss wrapper script, set audio to OSS in winecfg and ran the Steam client through the aoss wrapper, something like this:
aoss wine ./Steam.exe

Sound is now working in all Steam-based games, using OSS instead of ALSA.

---

