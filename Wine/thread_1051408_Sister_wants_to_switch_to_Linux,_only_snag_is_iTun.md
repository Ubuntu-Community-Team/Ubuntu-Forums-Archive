---
title: "Sister wants to switch to Linux, only snag is iTunes."
date: 2009-01-26
forum: Wine
---

### Post by agim on 2009-01-26
Is there anyway to listen to itunes songs on Rhythmbox.
I know wine is supposed to be able to play itunes, but I would much rather find a codec to use so she can listen to rhythmbox, or some other linux program.

Can anyone give me a hand?

---

### Post by abn91c on 2009-01-26
if the songs are mp3 format you can play them. I prefer Amarok since it works like a charm with my 30gig Ipod video 5th Gen

---

### Post by damis648 on 2009-01-26
If they are DRM-Protected songs purchased from the store, you will have to burn them all and then re-rip them, it is the easiest way to remove the DRM.

---

### Post by Ketara on 2009-01-26
iTunes is generally buggy in wine, however it will run flawlessly on a virtual machine, such as virtualbox or VMware.

I have iTunes run in virtualbox, and have it set up so the iTunes library is in a "shared" drive, so that the music isn't actually stored on the virtual disk image. It's relatively easy to do.

The other bonus to that is you can sync an iPod/iPhone in virtualbox, which you cannot do in Linux without jailbreaking it and having a few headaches.

---

### Post by agim on 2009-01-26
I have read lots of conflicting posts about different packages for amarok or rhythmbox that would make it work, I am hoping someone has had some success this way.

---

### Post by abn91c on 2009-01-26
you have to install this```
sudo aptitude install libxine1-ffmpeg
``` to get mp3 to play in amarok

---

### Post by Ketara on 2009-01-26
I guess I'm a little confused about your intended goal.

What you want to do is find a way to play songs purchased from iTunes in a Linux native program? Or just MP3s?

---

### Post by agim on 2009-01-26
No, sorry, I should have been more specific. mp3's are not a problem. I would like to be able to play songs downloaded from the itunes store.

---

### Post by Ketara on 2009-01-26
I just did a bit of searching to verify, but I'm pretty sure you cannot play iTunes store purchased music on anything but iTunes, since they are protected by DRM.

[http://ubuntuforums.org/showthread.php?t=889669](http://ubuntuforums.org/showthread.php?t=889669)

The iTunes filetype is m4a, which should play in Rhythmbox fine (mine does), but the files purchased from the iTunes store will not.

As far as I can see your options are to either burn them and re-rip them like damis648 says, or to use iTunes. Personally, I use iTunes, but that's because my 2.0 firmware iPod Touch requires it =)

If you want to get iTunes working I'd be more than happy to help.

---

