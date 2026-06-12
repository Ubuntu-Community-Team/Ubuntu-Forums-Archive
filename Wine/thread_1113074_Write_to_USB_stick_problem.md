---
title: "Write to USB stick problem"
date: 2009-04-01
forum: Wine
---

### Post by Rob8900 on 2009-04-01
Hi,

I have an application running in Wine where I write some data to an USB stick.

When I close my application and pull out the USB stick, the data is sometimes not saved to that USB stick. When I press "Eject" (Unmount) of the USB stick, the data is OK.

Is there any way to handle this problem???


Thanks in advance,

Rob

---

### Post by hikaricore on 2009-04-01
Unmount the stick first... this is the solution.
USB storage devices last a hell of a lot longer when the OS isn't writing data to them instantly so that data is cached and written later or when the device is unmounted.  Many people who are used to Windows doing this for them are also used to their devices having a short lifespan.  I think the benefits outweigh the annoyance of having to take a few more seconds to properly unmount.

---

### Post by Rob8900 on 2009-04-02
And is there a function to Unmount the device within my Windows application?

---

### Post by hikaricore on 2009-04-02
None that I know of but I could be wrong.
After exiting your WINE application you should be able to unmount through nautilus or whatever means you normally unmount with.

Honestly this just isn't a WINE issue.

---

### Post by Rob8900 on 2009-04-06
Hi,

Is it possible to call Linux API's in a Windows application when running this application in Wine? 

I need to unmount an USB stick to be sure all data is written to that stick.


Thanks in advance,

Rob

---

