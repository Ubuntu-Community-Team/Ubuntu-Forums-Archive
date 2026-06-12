---
title: "(un)mute master"
date: 2013-05-01
forum: Ubuntu Application Development
---

### Post by gnuser12 on 2013-05-01
Hello Users,
I have written this little test script to mute or unmute my Sound it works for muting.
But not for unmuting. 
The script checks EITHER sound is muted and if so it unmutes OR sound is unmuted then it mutes 
The line alsa.Mixer('Master').setmute(0) should unmute, but nothing happens 
I'm using Ubuntu with fluxbox as desktop environment
What can I do ? 
here is the script
```

#!/usr/bin/python
import alsaaudio as alsa

def isMuted():
        if alsa.Mixer('Master').getmute()[0] == 1:
           #self.volume_icon.set_from_file(AUDIO_ICON)
           return True
        else: 
           #self.volume_icon.set_from_file(AUDIO_ICON_MUTED)
           return False

def mute():
     alsa.Mixer('Master').setmute(1)
     #setmute(on/off,channel)

def unmute():
      alsa.Mixer('Master').setmute(0)

if __name__ == "__main__":
    if isMuted():
        print "muted we unmute"
        unmute()
    else:
        print "not muted we mute"
        mute()


```

---

### Post by gnuser12 on 2013-05-06
Has everyone tested the script ? 
Does it work on your system ? 
I use Untuntu 12.04 LTS Sound Card: Playback: Built-in-Audio Analog Stereo(Pulse Audo Mixer)

bye

---

