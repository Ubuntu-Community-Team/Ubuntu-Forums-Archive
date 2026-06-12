---
title: "no sound with audio files"
date: 2008-05-11
forum: Ubuntu Studio
---

### Post by statelypenguin on 2008-05-11
I don't have sound with amarok/rhythmbox/whatever when i try to play audio files.  with amarok it says i need to install libxine-1ffmpeg, which i also cant install using synaptic.  i also can't play ogg vorbis.  it loads the song, but it just never plays, the track progress stays at 0:00.

youtube works, and videos i download to my comp work.  it's just with audio files.

it should also be mentioned that sometimes i'll just get no sound whatsoever.  youtube vids play but no sound, etc.  i then have to restart and it's back to normal. 

it really just bothers me because everything worked fine with gutsy, but ever since i've upgraded i can't get these to work.

---

### Post by hermes0710 on 2008-05-12
It seems that you are missing some basic packages. Try installing kaffeine and mplayer (other essential packages will be installed too). What do you mean you can't install libxine-1ffmpeg?

The youtube videos with no sound is a known bug and it has to do with simultaneous playback of flash video and any other media.

---

### Post by statelypenguin on 2008-05-12
i've already got gstreamer, and kaffeine didn't seem to do anything.  

when i try to install the libxine package, it brings up a list of other packages to install.  i okay that and it says.

[INDENT]Could not mark all packages for installation or upgrade

libxine1-ffmpeg:
  Depends: libxine1 (<1.1.8) but 1.1.11.1-1ubuntu3 is to be installed[/INDENT]

now i've tried asking questions as to what that means, several times, but no one ever responds, so thank you for even doing that.

---

### Post by statelypenguin on 2008-05-12
and that's an "8 )" not a stupid smiley face.

---

### Post by hermes0710 on 2008-05-12
Which ubuntu release do you use?

---

### Post by statelypenguin on 2008-05-12
hardy.  all this worked fine with gutsy.  i guess it all goes back to the libxine problem, but i asked what to do awhile ago on here and didn't get anything.

---

