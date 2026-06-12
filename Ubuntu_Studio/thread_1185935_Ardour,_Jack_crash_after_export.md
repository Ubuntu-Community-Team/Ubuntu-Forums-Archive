---
title: "Ardour, Jack crash after export"
date: 2009-06-12
forum: Ubuntu Studio
---

### Post by trulan on 2009-06-12
I'm thoroughly enjoying my new setup, recording is much more stable than Windows XP which I was using until recently.

My System:  AMD Athlon 64 3800, 1gb ram
 - Ubuntu Studio 9.04
 - Presonus Firepod
 - JACK control 0.3.4
 - Ardour 2.7.1

I'm recording to my windows drive (200gb SATA, over 100gb free) while US resides on a separate 100gb IDE.  Jack is set up for as low latency as I can get (2.18 ms@44100)  Recording is rock-solid, I've never had an x run during recording.  (I rarely had an entire song without at least one pop on Windows.)  So I'm not complaining.

I have one recurring issue.  Every time I export a wave file (ie, mix down a song) Jack and Ardour crash.  As soon as Ardour starts exporting my WAV file, the DSP percent goes to 100 and the light on the firepod turns red.  When exporting is complete, the light turns blue again, but after a few seconds Ardour gives a message about Jack being shut down.  Both Jack and Ardour must be shut down and restarted, and often I have to kill Jack using the system monitor (Can you tell I'm a Windows user?)  I can usually restart them both and go right back to what I was doing, but sometimes it take several tries to get Jack running again.

The exported file will be fine, and I can always save my session, so no data is being lost.  But the constant crashing and restarting of the programs makes my evening's work (mixing down tracks for a demo CD) take much longer than it should have to.

I searched for other reports of this issue but everything I found dealt with older versions of Jack and Ardour.  Any ideas would be greatly appreciated.

---

### Post by demios on 2009-07-01
If it makes any difference, I have almost the identical setup (firepod, jaunty studio, ardour etc) and the same thing happens to me. just as a bump.

the terminal command for killing a process is killall, so to shut down ardour without going into system monitor, bust out a terminal (or even hotkey it) and put in
```
killall ardour
```

also, if you're having problems with the ubuntu-rt kernel, try using the one mentioned in the thread at [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/366352](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/366352)  I've been using it for a few months now with my dell inspiron 1520 and I've had no xruns.

good luck.

---

### Post by trulan on 2009-07-01
Thanks for the reply.

It seems that this is a known issue, after I started this thread I found another one:
[http://ubuntuforums.org/showthread.php?t=1165961](http://ubuntuforums.org/showthread.php?t=1165961)

Also thanks for the tip.  I'll check it out.

As far as un-freezing the system,
```
killall qjackctl.bin
```
was what I needed - Ardour kills itself quite effectively without my input.

---

### Post by fedexnman on 2009-07-01
hey trulan, have you got things exporting now ?? i have yet to try thorgal's method in the previous thread youve mentioned.( im using firewire device ) i wonder what higher latency setting he's using, i dont mind a workaround if it works !!

---

### Post by trulan on 2009-07-02
I can export without the crash, but I can't get usable playback - way too many x runs.  But it will export without hanging.

When real time is unchecked in Jack Controls, I am unable to get it to sync with large buffering settings.  I set them fairly small and watch the xruns add up.  They don't appear to affect the exporting though.  So I wouldn't say it's a great workaround.  SGX's method of looping Ardour's outputs into Time Machine, or into another stereo track in Ardour, might be a better way to go and is starting to make more sense as I learn how to use Jack with Patchage.  It's a pretty amazing setup.

The root of this export issue is in the Jaunty kernel.  I haven't messed with testing other kernels, but there are some on the float that claim to fix a lot of audio related problems.  But that's a little deeper than I care to go just yet - I'm still way too new at this.

Edit:  Maybe the kernel isn't completely to blame.  I am setting up a laptop for recording purposes and am using Hardy on it as Jaunty was pretty unstable.  Jack will crash on that too after an export, but Ardour does not, and jack can be re-started from Jack Control, then re-connected in Ardour and it will work again.

---

