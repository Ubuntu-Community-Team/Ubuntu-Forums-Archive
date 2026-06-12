---
title: "Rhythmbox (random) crashes when playing mp3 files from NAS"
date: 2012-07-19
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-07-19
Tested over cifs, sshfs, nfs: not only it seems to crash when reading large media directories (like 1.000 folders), but it also crashes quite regularly after about 8 hours when playing large queues. The message is always the same:

```
[ 1405.412529] aqueue:src[19056] general protection ip:7f4cc8e8429c sp:7f4c7bffd248 error:0 in libgobject-2.0.so.0.3303.0[7f4cc8e52000+4e000]

```

In parallel, I just found out that VLC (2.0.2) on Realtek ALC892 (Asus M4A89GTD PRO/USB3 AMD890GT chipset) fills the first &#8776; 30s to 1m of every track with loud static noise when playing mp3/ogg audio files (local/network). 

Regards,
Effenberg

---

### Post by mc4man on 2012-07-22
> **effenberg0x0 said:**
> 
In parallel, I just found out that VLC (2.0.2) on Realtek ALC892 (Asus M4A89GTD PRO/USB3 AMD890GT chipset) fills the first &#8776; 30s to 1m of every track with loud static noise when playing mp3/ogg audio files (local/network). 

Regards,
Effenberg
Probably not at all your issue but here was getting some nonsense with vlc at the beginning of tracks for several seconds. This was alleviated by switching the default audio setting of 'keeping volume between sessions' to 'Always reset ..' which I set to 95%

You could also see if pulse is involved by switching off to alsa & picking the appropriate device

All this can be checked in simple settings, if going to the 'advanced settings' window  I'd reco starting vlc with an env of 
LIBOVERLAY_SCROLLBAR=0
or sooner than later you _may_ get some window size issues

---

### Post by UltimateCat on 2012-07-22
This website might be of some use-


[https://live.gnome.org/RhythmboxPlugins/ThirdParty](https://live.gnome.org/RhythmboxPlugins/ThirdParty)

---

