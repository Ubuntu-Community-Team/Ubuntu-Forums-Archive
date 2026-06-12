---
title: "panp9 webcam stopped working on ubuntu 13.04"
date: 2013-08-24
forum: System76 Support
---

### Post by spazzeri on 2013-08-24
Hello,

I noticed that my panp9's webcam does not work (3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux).

In Cheese preferences -> webcam, 'device' is empty (dimmed out).

guvcview starts with this error message:
> please make sure that the camera is connected and that the correct driver is installed

More details from guvcview 1.6.0:

> 
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
video device: /dev/video0 
unable to detect video devices on your system (0)
ERROR opening V4L interface: No such file or directory
Init video returned -1
VIDIOC_REQBUFS - Failed to delete buffers: Inappropriate ioctl for device (errno 25)
cleaned allocations - 100%
Closing portaudio ...OK
Terminated.

Please advise.

---

### Post by spazzeri on 2013-08-26
Oops, the camera was disconnected and just had to be turned back on.

---

