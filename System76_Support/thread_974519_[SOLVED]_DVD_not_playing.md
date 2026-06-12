---
title: "[SOLVED] DVD not playing"
date: 2008-11-07
forum: System76 Support
---

### Post by ewg on 2008-11-07
System 76 Sable
Ubuntu 8.04 (NOT 8.10)

I've never had any trouble playing CDs or DVDs. But just today, when I insert a DVD, the Totem screen comes up and immediately closes.If I try to open with xine, I get a fatal error message = segmentation fault.

Thanks for any suggestions,

---

### Post by thomasaaron on 2008-11-07
Please have a look at this thread...
[http://ubuntuforums.org/showthread.php?p=738069](http://ubuntuforums.org/showthread.php?p=738069)

Does that sound like your problem? And, if so, does the fix mentioned in it fix the problem?

If not, please attach the files created on your desktop by this command...
```

cat /var/log/messages > ~/Desktop/messages.txt
```

---

### Post by ewg on 2008-11-07
It did not help. I tried to attach the file you requested but message said file was too big for forum.

---

### Post by ewg on 2008-11-07
Thomas, I copied the section from that file that applied to Totem and it's attached.
OK?

Thanks,

---

### Post by ewg on 2008-11-08
I'll email the full file to System76 support.  New Linux kernal last week could be the culprit?

Thanks,

---

### Post by thomasaaron on 2008-11-10
Thanks.

1. Did you just upgrade to 8.04?

2. Double-click your speaker icon. In the resulting window, go to File > Device and make sure it is set to ALSA. Does that fix it?

3. Go to System > Preferences > Sound and make sure all of the drop-downs are set to ALSA. If that doesn't fix it, try setting them all to Pulse Audio.

3. If #1 and #2 do not fix it, try re-installing totem..
```
sudo apt-get --reinstall install totem
```

---

### Post by ewg on 2008-11-10
1 I've had 8.o4 since the release

2 I can't find any speaker icon except in the preference drop down

3 I tried both ALSA and Pulse and Totem still won't open

I tried your suggested code to reinstall but Totem still will not open

I am using VLC to watch movies but my concern is something bigger may be wrong.

Thanks,

---

### Post by ewg on 2008-11-10
Could the new kernal be what's messing me up?

Thanks,

---

### Post by SunnyRabbiera on 2008-11-10
> **ewg said:**
> Could the new kernal be what's messing me up?

Thanks,

I dont think so, kernel updates usually dont do crap like this

---

### Post by ewg on 2008-11-11
thomasaaron...should I give up on this and just use VLC?

Thanks for your suggestions,

---

### Post by thomasaaron on 2008-11-11
I'm not finding much on this one.

Try booting into your previous kernel (press Esc when you see the grub countdown and select the second non-recovery mode kernel).
Does Totem work in that one?

---

### Post by ewg on 2008-11-11
I finally upgraded to 8.10 and it seems to work. Any reason for that?

Thanks for all your help.

---

### Post by thomasaaron on 2008-11-11
8.10 installs a new version of ALSA.
Probably wiped some hosed configuration or something.

---

### Post by ewg on 2008-11-12
Thanks for all your help.

---

