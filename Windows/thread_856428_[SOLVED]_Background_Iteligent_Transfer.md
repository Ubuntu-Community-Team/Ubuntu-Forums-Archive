---
title: "[SOLVED] Background Iteligent Transfer"
date: 2008-07-11
forum: Windows
---

### Post by DougieFresh4U on 2008-07-11
I have never heard of this background intelligant transfer service before. I'm trying to put google earth on this WinXP Pro machine but It tells me 'cannot start BITS ' When I did search for BITS it came up with no files on machine. I went to control panal-Admin task-services and it's listed there and when I open it it says anable and automatic. Can any one please guide me on this??
Thanks

---

### Post by fiddledd on 2008-07-11
Here's what MS says BITS is:

[http://www.microsoft.com/windowsserver2003/techinfo/overview/bits.mspx](http://www.microsoft.com/windowsserver2003/techinfo/overview/bits.mspx)

From my experience it's needed by Windows Update to download updates. If you want to use Auto Update the service needs to be enabled. You can try setting to Manual, if that don't work then set to Automatic.
I have it disabled on a non networked PC and enabled on others, but I have never had anything complain it was off except Windows Update.

---

### Post by DougieFresh4U on 2008-07-11
Thanks for info. but now i need to know how I can get around BITS to download google earth.

---

### Post by fiddledd on 2008-07-11
> **DougieFresh4U said:**
> Thanks for info. but now i need to know how I can get around BITS to download google earth.

According to [http://groups.google.com/group/pack-howto/browse_thread/thread/3a51022bf6313bb5/0320ed67590ecdff](http://groups.google.com/group/pack-howto/browse_thread/thread/3a51022bf6313bb5/0320ed67590ecdff)
it's the updater that requires BITS and there's a direct link there to bypass the updater so you don't need to enable BITS.

> You can download Google Earth without the Updater:
[http://earth.google.com/tour/thanks-win4.html](http://earth.google.com/tour/thanks-win4.html)

---

### Post by DougieFresh4U on 2008-07-11
[FONT="Comic Sans MS"][COLOR="Blue"]You can download Google Earth without the Updater:
[http://earth.google.com/tour/thanks-win4.html](http://earth.google.com/tour/thanks-win4.html)
[/COLOR][/FONT]


Got it, Thanks!!

---

