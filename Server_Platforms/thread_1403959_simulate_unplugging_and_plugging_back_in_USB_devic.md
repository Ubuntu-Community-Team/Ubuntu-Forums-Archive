---
title: "simulate unplugging and plugging back in USB devices"
date: 2010-02-10
forum: Server Platforms
---

### Post by Phobiac on 2010-02-10
I have a webcam set up as a security camera of sorts with the package motion. The webcam has an unfortunate bug (it has been reported) that causes it to become unusable at seemingly random times. I have noticed that unplugging the webcam and plugging it back in, or even more extreme restarting the server, solves this problem quite nicely in the meantime. However, as the intent is for it to be a security camera, it's pointless if I need to be there to do this whenever it screws up. I've been searching and searching for a way to do this with a command or two. I've tried removing the loaded module (uvcvideo) and loading it back in. I've found some hints that bind might be related. As of yet, I can't find a way to do this. Does anyone have any ideas?

tl;dr How can I simulate the act of unplugging a usb device and plugging it back in, with commands? I am not looking for mount and umount, the device is a webcam.

---

