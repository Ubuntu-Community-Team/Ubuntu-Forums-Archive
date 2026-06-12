---
title: "No System 76 driver... nvidia driver not working"
date: 2010-07-12
forum: System76 Support
---

### Post by EmilyRose on 2010-07-12
So, I did a system update on friday night right before I went away for the weekend followed by a shutdown. Now when I go to start up it hangs for a long time, then finally informs me that theres something wrong with my graphics card/drivers and wants to know if I'd like to edit my... xconfig? Or something like that, or just start in low-graphics mode once (which is what I've chosen)... when I open up the NVIDIA X Server Settings it gives me the following:

> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
 

Which I've tried/done though it doesn't seem to fix anything. When I try to run the System 76 driver, it says its only for vs 6.06-9.10 (I'm running 10.04...)

Finally, in Hardware Drivers it has:

"NVIDIA accelerated graphics driver (version current) Recommended"

Selected...

So.. yeah... help??

---

### Post by marshmallow1304 on 2010-07-12
Open a Terminal (Applications->Accessories->Terminal).  Run

```
sudo nvidia-xconfig
sudo reboot
```

typing your password when requested.



As for the System76 driver, make sure you have the latest version.  Go [here]("http://planet76.com/repositories/") and download and install the second file from the bottom.

---

### Post by EmilyRose on 2010-07-12
Yeah, I tried that already...

---

### Post by marshmallow1304 on 2010-07-13
Oops, missed that.  What does your /etc/X11/xorg.conf look like?

---

### Post by thomasaaron on 2010-07-13
Try de-selecting the nVidia driver in Hardware Drivers.
Then reboot.
Then re-enable driver.
Then reboot.

Did that work?

Also, what version of the System76 Driver are you using?

---

### Post by EmilyRose on 2010-07-13
Yup, that did it:) Thanks!! And I now have driver 2.5.1

---

### Post by thomasaaron on 2010-07-14
Excellent. Then you're good to go.

---

