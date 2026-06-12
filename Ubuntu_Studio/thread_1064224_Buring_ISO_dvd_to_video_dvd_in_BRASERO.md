---
title: "Buring ISO dvd to video dvd in BRASERO"
date: 2009-02-08
forum: Ubuntu Studio
---

### Post by marcgh on 2009-02-08
Hi,

I want to burn a videoplayer compatible video DVD.

I encoded an ISO file (3.3 Gb) with DeVeDe and am trying to burn this ISO with Brasero.

Brasero will start and anywhere between 20% and 30 % an error will pop-up and cancel the ongoing job. I have tried at 6x (min), 8x and 12x burning speed - still the same.

No need to say that everytime a DVD (expensive lightscribe) is gone waste!

I uninstalled Brasero and reinstalled it via add/remove programs but to no avail.

I tested the ISO file opening XP and NERO and there all goes well

Attached the Brasero log file with the error for any willing geek - for me this a very foreign language.

Thanks in advance for any assistance,
Marc

---

### Post by khelben1979 on 2009-02-08
I suggest that you try to burn that ISO file with another application.

[K3B]("http://en.wikipedia.org/wiki/K3b") might be what you're looking for.

type this from a text console:
```
sudo apt-get install k3b
```
if it's not already installed over there.

---

### Post by marcgh on 2009-02-09
Thanks Khelben, I will try that this evening.

---

### Post by cotcot on 2009-02-09
Try your next burn with RW media.
Start brasero from terminal. Maybe you get an error that helps you.
The problem might be in devede. Also here you could discover an error by starting it from terminal.
You could make your clips dvd compatible before supplying them to devede. Render them in mpeg2 on PAL or NTSC and 48 kHz audio. Select in devede under the miscelaneous tab of the 'advanced options' in the 'file properties' that the file is already dvd compatible.

---

### Post by marcgh on 2009-02-09
Hi Cotcot,
Thanks for your help!

Meantime I got another issue here about my DVD writer.
This is the link to the thread: [http://ubuntuforums.org/showthread.php?t=1065106](http://ubuntuforums.org/showthread.php?t=1065106)

Surely I will try your suggenstions as soon as I have my writer back on track - or maybe this is the problem?

Merci / Bedankt !

---

