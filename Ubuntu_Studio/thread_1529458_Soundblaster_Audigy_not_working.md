---
title: "Soundblaster Audigy not working"
date: 2010-07-12
forum: Ubuntu Studio
---

### Post by gdesilva on 2010-07-12
I have been using Soundblaster Audigy 2 NX without any problems under 9.10 for quite some time now but it has stopped working since the kernel upgrade yesterday. The device is recognized as a usb device (lsusb) and also alsamixer also recognizes it. However, the mute led is on on the device but audio controller program indicates that it is not in mute state. The device works fine under Windows XP.

Any suggestions or pointers to aid fix this problem will be greatly appreciated.


UPDATE

I noticed that if I specify analog output in the Gnome Volume Control app then I can get sound working via the headphones but moment I specify that it is digital stereo then the device goes into mute state although the Gnome Volume Control app is not set to mute. Prior to this I had digital stereo setting working for me (I was using the optical out connection).

---

### Post by gdesilva on 2010-07-13
Fixed the problem. Started alsamixer and noticed that source for 'digital out' has mysteriously being set to 'PCM' instead of 'Front'. Once this was changed everything works as it used to. Must be a ghost in the machine:p

---

