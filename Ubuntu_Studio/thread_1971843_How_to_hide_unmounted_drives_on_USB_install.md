---
title: "How to hide unmounted drives on USB install"
date: 2012-05-03
forum: Ubuntu Studio
---

### Post by Cariboo1938 on 2012-05-03
I want to use UbuntuStudio 12.04-amd64 from an USB-stick and I wonder how I could hide the unmounted drives shown on Desktop? see screenshot!

---

### Post by agillator on 2012-05-03
See thread [http://ubuntuforums.org/showthread.php?t=1782823](http://ubuntuforums.org/showthread.php?t=1782823). In short, edit /etc/fstab to use a mount point anywhere but /media. Anything with a mount point of /media shows if present whether mounted or not, apparently.

---

### Post by jejeman on 2012-05-03
Right clik on desktop > desktop settings > icons tab > uncheck removable devices

---

### Post by Cariboo1938 on 2012-05-04
> **jejeman said:**
> Right clik on desktop > desktop settings > icons tab > uncheck removable devices
@jejeman:
Thank You
This was easy...

---

### Post by 0miwi0 on 2012-07-29
That option seems to have changed location over to CompizConfig Settings Manager under Desktop-> Ubuntu Unity Plugin-> Experimental-> Show Devices. Ah, my bad, you're talking about ubuntu studio

---

