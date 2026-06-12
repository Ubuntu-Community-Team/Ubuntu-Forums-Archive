---
title: "WoW + wine1.2 = no sound"
date: 2010-05-27
forum: Wine
---

### Post by Lolpanda on 2010-05-27
Get the details pounded out first...

Wine Version: 1.1.31 (Wine1.2 in the karmic repos)
Wine Sound Driver: Alsa
WoW = Latest patch
OS: 9.10 x64

Okay, my problem is that whenever WoW loads. It kills all sound, including itself. If Chrome is playing a youtube video, it kills the sound. If I have music playing from my music folder,  it kills the music. The youtube / Music video are still playing, but the sound card isn't processing the sound and pushing it through the speakers. 

I've tried OSS in Wine (no change), but didn't touch ESound or JACK.

 I know in the past Alsa and PulseAudio have had issues with Wine apps, and so I was wondering if this was a known bug with a known work around. Or if this was one of those "life sucks, get used to it." moments where there was no fix. 

If anyone knows of a fix, whether it be short and simple or long and complicated, I'd love to hear it. I have no issues with long and complicated fixes, bearing that someone is willing to walk me through the steps. 

Considering Alsa, wine, Ubuntu and 90% of everything else running on my system is open source, I'd find it hard to believe however that there is NO fix available / possible. 

If anyone has some ideas, I'd be more than willing to hear them out and give them a shot. Cheers!

---

### Post by rJ~ on 2010-05-28
This works for me:
Set Wine windows version to Windows XP
Set sound to OSS
Start WoW with
```
padsp wine Wow.exe
```

padsp lets Wine work with the Pulseaudio sound server. I believe there's a way to patch Wine to work with Pulseaudio as well, but the above works fine for me.

---

### Post by Cresho on 2010-05-28
go back to wine 1.1.37

---

### Post by Lolpanda on 2010-05-28
If you were talking to me Cresho, 1.1.37 is only available through the wine PPA -- something I'm avoiding until I test a few programs. So there is no 'going back' 1.1.31 is the most recent Ubuntu 9.10 will probably get considering Ubuntu's update policy of if an app starts with 1.1.x it will STAY on 1.1.x and not move to 1.2.x or 2.x.x in order to keep stability.

---

### Post by cwwilson721 on 2010-05-30
If ANYONE has sound issues w/WoW in wine:

Use XP as the operating system

Use Alsa ONLY as the sound driver.

You can use the "padsp wine Wow.exe" if you wish (I don't, and I have no issues)

---

