---
title: "Unable to get Focusrite Saffire Pro 24 Working in KXStudio"
date: 2013-09-18
forum: Ubuntu Studio
---

### Post by jransier on 2013-09-18
Hello!Using a DELL Inspiron 1720 laptop, Just switched over from Windows Vista, now running KXStudio. I'm having issues getting jack to recognize my Focusrite Saffire Pro 24 firewire interface. Since I'm new to ubuntu/kxstudio, I really am not familiar with the way audio works in this OS. At the present moment, I've installed packages for FFADO, I appear to have all of them... When I start jack with the interface plugged in, jack tells me that it cannot start, see logs for details. This is after I set jack to firewire drivers rather than ALSA. To me, it seems as though there is a dysfunctional driver? I'm not sure how I would check to see that my computer is aware the PRO 24 is plugged in. Can anyone offer a useful perspective?Thank you!- J

---

### Post by jejeman on 2013-09-18
Give
```
dmesg | grep fw
ls /dev/fw*
```

---

### Post by jransier on 2013-09-18
joseph@joseph-Inspiron-1720:~$ dmesg | grep fw[    1.112617] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11[    1.613293] firewire_core: created device fw0: GUID 374fc0001929a5a1, S400joseph@joseph-Inspiron-1720:~$ ^Cjoseph@joseph-Inspiron-1720:~$ ls /dev/fw*/dev/fw0

---

### Post by jejeman on 2013-09-19
Next time put terminal output in CODE tags. This way I can bearly understand the output.

Your soundcard is not recognized.
You only have /dev/fw0, that is your firewire controler. You need to have also /dev/fw1.
Check the cables.
Try to plug in the device before booting the OS.

---

### Post by jransier on 2013-09-19
Ok! So I've got this result

```
^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[Bjoseph@joseph-Inspiron-1720:~$ dmesg | grep fw
[    1.092170] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    1.593322] firewire_core: created device fw0: GUID 374fc0001929a5a1, S400
[    4.675060] firewire_core: created device fw1: GUID 00130e0401c0138b, S400, 1 config ROM retries
joseph@joseph-Inspiron-1720:~$ ls /dev/fw*
/dev/fw0  /dev/fw1


```

Seems to be a step in the right direction, although the FW led is still dark on my device. Jack still won't start as I set the driver to firewire, and attempt to use it.

---

### Post by jejeman on 2013-09-20
Yes, that is gut. SoundCard is now recognized.
As for the driver, read this if you haven't already
[http://ffado.org/?q=node/1204](http://ffado.org/?q=node/1204)
Official status is still - experimental.

---

