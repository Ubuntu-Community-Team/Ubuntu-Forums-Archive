---
title: "Unfortunately, your browser does not support video playback."
date: 2020-03-19
forum: Ubuntu Development Version
---

### Post by VMC on 2020-03-19
I get this error on videos on **Ubuntu **only. **Xubuntu** & **Kubuntu** , which has the exact same Firefox version, has no problem running the videos. I use msn.com videos section for example.

I thought it might be Flash, but the others don't need it. I installed it anyway. No difference.
```
apt show firefox
``` was identical on all three versions.

---

### Post by Frogs Hair on 2020-03-19
Is it DRM content ?

---

### Post by VMC on 2020-03-19
*Play DRM-controlled content* is checked on all three distros.

---

### Post by Frogs Hair on 2020-03-19
I just tested on U Budgie development release and the videos play just fine. ???

---

### Post by corradoventu on 2020-03-19
I have no problems playing msn.com video on my Ubuntu 20.04 with firefox 
```
corrado@corrado-x5-ff-0309:~$ apt policy firefox
firefox:
  Installed: 74.0+build3-0ubuntu1
  Candidate: 74.0+build3-0ubuntu1
  Version table:
 *** 74.0+build3-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-x5-ff-0309:~$ 
```

---

### Post by VMC on 2020-03-19
I dont need mines fine comments, i'm looking for ideas. I have the latest iso installed. same error as yesterdays. x, k ubuntu works. ubuntu doesn't

---

### Post by VMC on 2020-03-19
I just tested "prefs.js" form both ubuntu and xubuntu line 12 was the only difference so far. I'm going to try and cmp "about:config"  on both. See if I can find something different. Also ubuntu iso fails on flash using firefox.

---

### Post by Frogs Hair on 2020-03-19
Have you tried a new profile ?

---

### Post by VMC on 2020-03-19
> **Frogs Hair said:**
> Have you tried a new profile ?

The thing is, even using the flash ISO and not installing it fails. I just installed Manjaro gnome and it also works flawlessly. Checking all settings. Can't find anything relative to firefox.

---

### Post by Frogs Hair on 2020-03-19
What is listed in extensions> plugins ?

---

### Post by Irihapeti on 2020-03-19
It looks as though I can verify VMC's problem.

I have a full install of Xubuntu installed in a VM, and fully updated. I can play non-drm .mp4 files in Firefox on it.

I also have a minimal install of Ubuntu in a VM, which won't play the same .mp4 files in Firefox. Thinking that maybe the minimal install was the problem, I tried the latest live ISO, which also won't play these files. It just offers to download them.

(The files are in a local website on my hard drive, which I have for testing purposes.)

---

### Post by VMC on 2020-03-19
I have no extensions

---

### Post by VMC on 2020-03-19
> **Irihapeti said:**
> It looks as though I can verify VMC's problem.

I have a full install of Xubuntu installed in a VM, and fully updated. I can play non-drm .mp4 files in Firefox on it.

I also have a minimal install of Ubuntu in a VM, which won't play the same .mp4 files in Firefox. Thinking that maybe the minimal install was the problem, I tried the latest live ISO, which also won't play these files. It just offers to download them.

(The files are in a local website on my hard drive, which I have for testing purposes.)

I don't use VM's but that's an interesting test. Maybe I'll check mp4. I could never get Ubuntu to play mkv files. Oddly manjaro gnome does. I'm sure they added support. Thanks.

---

### Post by VMC on 2020-03-19
@[B]Irihapeti,
[/B]Thanks for the info. I didn't realize firefox had the ability to play mp4. I tried using Ubuntu's firefox, nothing happened. rebooted to Kubuntu. Tried using its firefox and it worked perfectly!

---

### Post by Irihapeti on 2020-03-19
I wouldn't expect the VM install to make much difference in a case like this.

I have to say that, after the recent libcrypt debacle, I'd be very reluctant to use anything other than a VM.

---

### Post by mc4man on 2020-03-20
> **VMC said:**
> @[B]Irihapeti,
[/B]Thanks for the info. I didn't realize firefox had the ability to play mp4. I tried using Ubuntu's firefox, nothing happened. rebooted to Kubuntu. Tried using its firefox and it worked perfectly!

Firefox should play .mp4 and most .webm video files. (- .mkv container isn't supported
Did you try a new profile as mentioned? or simply rename ~/.mozilla folder or if same FF version rename ~/.mozilla folder  & copy that folder from another install. Then open FF and see..

---

### Post by VMC on 2020-03-20
> **mc4man said:**
> Firefox should play .mp4 and most .webm video files. (- .mkv container isn't supported
Did you try a new profile as mentioned? or simply rename ~/.mozilla folder or if same FF version rename ~/.mozilla folder  & copy that folder from another install. Then open FF and see..

As I said, from the booted ISO FF fails. I found that out after I install ubuntu and it failed. But I will re-install using two different users to satisfy my mind. Irihapeti's reply was first time reading about ability of FF and mp4, which fails only on ubuntu.

---

### Post by VMC on 2020-03-20
I just updated my ISO to today's and booted to "Try Ubuntu Before Install" from ISO. Opened FF, went to msn.com videos. It failed. Then downloaded Budgie Try before, it worked. Instlled and FF works just as X & K works. I'll miss Ubuntu :(

---

### Post by mc4man on 2020-03-21
Just tried current image, correct, no video on that and likely other sites.
Easy fix..
```
sudo apt install gstreamer1.0-libav
```

---

### Post by VMC on 2020-03-21
> **mc4man said:**
> Just tried current image, correct, no video on that and likely other sites.
Easy fix..
```
sudo apt install gstreamer1.0-libav
```

Thanks for the input. I'll try it.

---

### Post by Irihapeti on 2020-03-21
> **mc4man said:**
> Just tried current image, correct, no video on that and likely other sites.
Easy fix..
```
sudo apt install gstreamer1.0-libav
```

That worked on my Ubuntu VM.

If this applies to the live ISO, should someone report a bug?

---

### Post by VMC on 2020-03-21
It works with my installed partition, but budgie, xubuntu, kubuntu don't have *libav*:

ubuntu gtstreamer before:
```
dpkg --get-selections | grep gstreamer
gir1.2-gstreamer-1.0:amd64            install
gstreamer1.0-alsa:amd64                install
gstreamer1.0-clutter-3.0:amd64            install
gstreamer1.0-gl:amd64                install
gstreamer1.0-gtk3:amd64                install
gstreamer1.0-packagekit                install
gstreamer1.0-plugins-base:amd64            install
gstreamer1.0-plugins-base-apps            install
gstreamer1.0-plugins-good:amd64            install
gstreamer1.0-pulseaudio:amd64            install
gstreamer1.0-tools                install
gstreamer1.0-x:amd64                install
libgstreamer-gl1.0-0:amd64            install
libgstreamer-plugins-base1.0-0:amd64        install
libgstreamer-plugins-good1.0-0:amd64        install
libgstreamer1.0-0:amd64                install
```

After the libav was added and it worked.

---

### Post by mc4man on 2020-03-21
Actually after taking a look it's libavcodecXX that firefox needs for such vids, local or online.
By default it can play webm so it works without libavcodecXX on youtube or on any webm file, vp8/9 or av1, opus audio.

---

### Post by VMC on 2020-03-21
> **mc4man said:**
> Actually after taking a look it's libavcodecXX that firefox needs for such vids, local or online.
By default it can play webm so it works without libavcodecXX on youtube or on any webm file, vp8/9 or av1, opus audio.

Why does Budgie work without it?

---

### Post by mc4man on 2020-03-22
> **VMC said:**
> Why does Budgie work without it?

According to manifest it ships with libavcodec58:amd64 (7:4.2.2-1ubuntu1
You don't have it installed?

---

### Post by VMC on 2020-03-22
> **mc4man said:**
> According to manifest it ships with libavcodec58:amd64 (7:4.2.2-1ubuntu1
You don't have it installed?

Correction, I do: ```
$ dpkg --get-selections | grep libavcode
libavcodec58:amd64                install
```

update:So that means Budgie has that codec, ubuntu doesn't. I need to check x/kubuntu also.

---

### Post by zika on 2020-03-22
Two things migh help (even though old... ;))
1. try to install libavcode-extra
2. firefox about:config media.libavcodec.allow-obsolete false>true
No promises, no guarantee. ;)

---

### Post by VMC on 2020-03-22
On my Budgie ,*media.libavcodec.allow-obsolete = "false"*, and the web videos work.

---

