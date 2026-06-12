---
title: "Bluetooth doesn't turn off after Natty restore"
date: 2011-07-13
forum: System76 Support
---

### Post by Shazzner on 2011-07-13
On Lemur Ultrathin. I had to reinstall Natty after I had some other issues. I already reinstalled the system and the system76 drivers, along with doing a system restore.

Unfortunately now, I'm trying to hook my bluetooth mouse up but pressing Fn-f12 doesn't activate bluetooth. Manually going to the bluetooth wizard states there isn't a bluetooth adapter plugged in.

I also can't use the webcam since the webcam button doesn't seem to work either, even though the mute, sleep, etc buttons do.

Any idea?

Edit: Sorry title should be "doesn't turn on"

---

### Post by isantop on 2011-07-14
This was a known issue with a fresh installation of Ubuntu 11.04. It was recently fixed in a kernel update to version 2.6.38-10. Make sure you have all of your updates applied, then try bluetooth out again. Did that fix it?

---

### Post by Shazzner on 2011-07-14
> **isantop said:**
> This was a known issue with a fresh installation of Ubuntu 11.04. It was recently fixed in a kernel update to version 2.6.38-10. Make sure you have all of your updates applied, then try bluetooth out again. Did that fix it?

I turned on proposed updates and updated and if I run uname -r:
```
uname -r
2.6.38-10-generic
```

Still no bluetooth I'm afraid.

---

### Post by Shazzner on 2011-07-16
Ok for some reason, today I tried the bluetooth hotkey and it magically worked. Strange.

I did add myself to the bluetooth group, but I tried restarted before with no change so I'm not sure what happened to make it work now.

---

### Post by mouhammad88 on 2011-10-09
After a long wasting time in complicated tuto and tips , i found an easy magic solution :D look at this : [http://www.edwardcrosby.com/2011/06/17/bluetooth-fix-in-linux-mint-11ubuntu-11-04/](http://www.edwardcrosby.com/2011/06/17/bluetooth-fix-in-linux-mint-11ubuntu-11-04/)

---

