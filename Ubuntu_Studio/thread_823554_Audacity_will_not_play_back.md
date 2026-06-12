---
title: "Audacity will not play back"
date: 2008-06-09
forum: Ubuntu Studio
---

### Post by Catalyst2Death on 2008-06-09
Hello,

I have been wrestling my Inspiron 1501's sound card for a while now, and I can't figure out how to get it to behave.  I'm trying to use audacity to remaster some .flac files I recorded from some old LP's.  The problem is that it will not playback at all, and this prevents me from being able to do any meaningful restoration.  I've tried ardour, and even reaper through wine, and I cannot get any playback.  

I've tried messing with which device was selected in sound (System>Preferences>Sound)  and also using the volume control on the gnome panel.  I've also tried combinations of:
```
$ aoss audacity
$ pasuspender -- audacity
```

at this point, I am looking for alternatives to audacity.  I need to be able to import flac, remove noise, possibly clicks, and then I need to be able to split the file up and export as ogg.

Failing this, what should my next step be?  Should I try and recompile/install ALSA??

I know that Audacity doesn't play well with pulse audio, is there a way I can eliminate pulse audio while I run audacity?

Here is the console output when I recieve the error:

```
Expression 'tempDevHandle = open( deviceInfo->name, flags )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 690

Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1034
Expression 'AlsaOpen( hostApi, parameters, streamDir, &pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1066

```

The gui error says:
```
Error while opening sound device. Please check the output device settings and the project sample rate.
```

I've search high and low for an answer, and I'm not really expecting one, however I would like advice on how to proceed from a problem solving point of view.  Should I tear apart audacity's code and try to fix the error, or should I begin the process of recompiling/installing the audio driver?

One more bit of information, the sound card is: ATI Technologies Inc SBx00 Azalia

---

### Post by Catalyst2Death on 2008-06-10
**bump**

really, all I need to know is where to look next...

---

### Post by Vivaldi Gloria on 2008-06-10
Pal, I don't know the answer to your problems, but have you seen these:

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

and 

[http://pulseaudio.org/wiki/PerfectSetup#ThirdPartyApplications](http://pulseaudio.org/wiki/PerfectSetup#ThirdPartyApplications)

Let me quote from the second one:

Using pasuspender to momentarily suspend pulseaudio is the most convenient way to use the non-beta versions (1.2.x) of Audacity at present. 

```
pasuspender -- audacity <argument>
```

---

### Post by Catalyst2Death on 2008-06-10
Its fixed!  Apparently jack was messing things up.  I found the fix here:
[http://xubuntu.wordpress.com/2008/04/28/how-to-get-audacity-working-after-a-hardy-upgrade/](http://xubuntu.wordpress.com/2008/04/28/how-to-get-audacity-working-after-a-hardy-upgrade/)

This is also worth noting:
[http://forums.debian.net/viewtopic.php?t=12497](http://forums.debian.net/viewtopic.php?t=12497)

---

