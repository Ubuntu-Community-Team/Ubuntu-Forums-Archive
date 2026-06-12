---
title: "Ubuntu 19.10 Beta Chrome Video Playback Issue"
date: 2019-10-14
forum: Ubuntu Development Version
---

### Post by MrRubik on 2019-10-14
Hi all. I am on the Ubuntu 19.10 Beta and I'm having issues with video playback in Chrome. Youtube videos are an example. When watching, it will play fine for 30 seconds or so, and then suddenly the video will just turn completely pink. This happens on almost all videos that I watch in Chrome. Any suggestions? Thanks.

---

### Post by dino99 on 2019-10-14
If it first works, then got pink, that is making me feeling about a video driver fallback. Which one is supposed to run on your system ? Check it activation inside System Settings.

---

### Post by MrRubik on 2019-10-14
I am using the Nvidia proprietary driver, version 435. I will change to the Nouveau driver and see if that helps. Thanks. Please let me know if you have any other suggestions, though.

---

### Post by #&amp;thj^% on 2019-10-14
I was able to reproduce the issue as well _by checking_ the "**Enable Stereoscopic 3D" option in the NVIDIA control panel**. I don't believe this is driver version specific as I can get it to happen with the latest drivers. See if it is enabled, if so disable/un-check.

---

### Post by MrRubik on 2019-10-14
> **MrRubik said:**
> I am using the Nvidia proprietary driver, version 435. I will change to the Nouveau driver and see if that helps. Thanks. Please let me know if you have any other suggestions, though.

I'm not sure what's going on but I can't get to my Nvidia control panel. My only option is the Nvidia X Server control panel, where it only gives me 3 profiles to choose from. Nothing else. Any suggestions on this?

---

### Post by #&amp;thj^% on 2019-10-14
Paste back the return for:
```
grep "NVIDIA(GPU-0)" /var/log/Xorg.0.log |head -17| cut -d\: -f2
```
I have to go to work but I'll leave with a try and see option:
If Needed You can try
```

sudo nvidia-xconfig --stereo=0
```

To disable and then reboot the pc.

---

### Post by MrRubik on 2019-10-14
> **1fallen said:**
> Paste back the return for:
```
grep "NVIDIA(GPU-0)" /var/log/Xorg.0.log |head -17| cut -d\: -f2
```
I have to go to work but I'll leave with a try and see option:
If Needed You can try
```

sudo nvidia-xconfig --stereo=0
```

To disable and then reboot the pc.

The grep command you had me run returns 
```
Deleting GPU-0
```

The 2nd command you had me run returns what's below. If you have anymore suggestions, they would be appreciated. Thanks.
```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

---

### Post by MrRubik on 2019-10-14
> **1fallen said:**
> Paste back the return for:
```
grep "NVIDIA(GPU-0)" /var/log/Xorg.0.log |head -17| cut -d\: -f2
```
I have to go to work but I'll leave with a try and see option:
If Needed You can try
```

sudo nvidia-xconfig --stereo=0
```

To disable and then reboot the pc.

Alright, so i tried several things, including purging all Nvidia drivers and reinstalling, and nothing was giving me my full Nvidia control panel back. So, I just decided to wipe my hard drive and do a fresh install of 19.10. This time, instead of having Ubuntu install proprietary drivers during the install, I install the open source version of 435 from the PPA, and everything is working great now. Thanks so much for all your help. If I end up having problems again, it's very good to know that enabling stereoscopic 3D should fix this issue. However, just to make sure I could find it, I went into my Nvidia control panel and looked for this settings. I can't find it anywhere. When you get a chance, please let me know where it's at so I'll know. Just in case I need to change it. Thanks so much for all your help.

---

### Post by deadflowr on 2019-10-15
>  I install the open source version of 435 
Anything nvidia-### is closed source. It shows as open source in Additional Drivers because they're from unofficial sources:
[https://askubuntu.com/questions/891968/there-is-no-nvidia-proprietary-driver-in-additional-drivers]("https://askubuntu.com/questions/891968/there-is-no-nvidia-proprietary-driver-in-additional-drivers")

---

### Post by #&amp;thj^% on 2019-10-15
I was a bit taken back by the return from those commands i gave, not expected at all.
My Nvidia card is on my server so I can't show you the expected results, But you seem to have it sorted now.
The "Stereoscopic 3D" was disabled by default on my system so I would not worry much about that for the sake of sanity. :)
BTW The Control Panel is "nvidia-settings" but you knew that. ;)
Kind Regards And +1 for deadflowr's post

---

### Post by MrRubik on 2019-10-15
> **deadflowr said:**
> Anything nvidia-### is closed source. It shows as open source in Additional Drivers because they're from unofficial sources:
[https://askubuntu.com/questions/891968/there-is-no-nvidia-proprietary-driver-in-additional-drivers](https://askubuntu.com/questions/891968/there-is-no-nvidia-proprietary-driver-in-additional-drivers)

You are right and I have read this before. Just wasn't thinking

> **1fallen said:**
> I was a bit taken back by the return from those commands i gave, not expected at all.
My Nvidia card is on my server so I can't show you the expected results, But you seem to have it sorted now.
The "Stereoscopic 3D" was disabled by default on my system so I would not worry much about that for the sake of sanity. :)
BTW The Control Panel is "nvidia-settings" but you knew that. ;)
Kind Regards And +1 for deadflowr's post

Thanks for all your help! It's very much appreciated! Figuring out it was drivers issues immediately got me on the right path.

---

