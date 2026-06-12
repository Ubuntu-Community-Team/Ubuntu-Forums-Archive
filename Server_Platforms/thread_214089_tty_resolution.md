---
title: "tty resolution"
date: 2006-07-12
forum: Server Platforms
---

### Post by wanabewired on 2006-07-12
evening all,

I've spent quite some time now trying to rectify this terminal resolution problem i've been having. I cannot seem to get my terminal to display properly on my TFT monitor. ](*,) The native resolution on my monitor is 1280x1024 and any other is obviously mocked up and looks awful. I've currently not got X installed and would like to keep it that way if at all possible.

I have edited my menu.lst to include:


```
kernel     /boot/vmlinuz-2.6.15-23-server root=/dev/hda1 ro splash quiet vga=791
```

...succesfully setting the resolution to 1024x768, BUT my monitor can't hack the refresh rate used on the default 1280x1024 setting (which i believe is 75hz?) My monitor requires 1280x1024 to be at 60hz. Is here a way I can overwrite this?

The graphics card is more than capable of delivering the required refresh rate/resolution/colour depth as it has achieved higher on my CRT monitor.

My monitor is a Samsung Syncmaster 913N 19" TFT

I'd be most grateful for any help.

Thanks.
Wanabewired

---

