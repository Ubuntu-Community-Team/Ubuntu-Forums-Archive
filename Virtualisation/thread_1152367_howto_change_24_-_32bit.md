---
title: "howto change 24 - 32bit"
date: 2009-05-07
forum: Virtualisation
---

### Post by duncan503 on 2009-05-07
Hello I come to a thing:confused: the resolution of the screen of a 32 bit. And the virtualbox  tells me to update from 24 bit to 32 bit, the question is how to change it.

Thanks

---

### Post by sonny on 2009-05-07
If I understood you correctly, you want to change your screen resolution from 24 bit to 32 bit... well that's a common mistake from new linux users... because in Linux (and windows) there's no such thing as 32 bit... the "32 bit" resolution is a plain 24 bit with 8 bits of alpha (transparency) and since in Linux transparency doesn't count (because we're so good at it) we don't have 32 bit resolutions... Microsoft add it to the screen resolution 'cuz windows didn't manage it before... so when windows could manage it they say it was a 32 bit resolution...

I hope I answered your question... if I didn't feel free to tell me... hehehehe..

---

### Post by ibuclaw on 2009-05-07
Yep, the most you can get out of the Default Screen Depth in your xorg.conf file is 24bits. The transparency is handled by the Window Manager.

Would you mind PrintScreen'ing or writing out the full error message that you are getting from VirtualBox ?
This may give us a clearer view of what exactly is happening

Regards
Iain

---

### Post by duncan503 on 2009-05-07
hi here is a cut and paste of the dialogue.
 p, li { white-space: pre-wrap; }  "The virtual machine window is optimized to work in 32 bit color mode but the color quality of the virtual display is currently set to 24 bit.
 Please open the display properties dialog of the guest OS and select a 32 bit color mode, if it is available, for best possible performance of the virtual video subsystem.
 Note. Some operating systems, like OS/2, may actually work in 32 bit mode but report it as 24 bit (16 million colors). You may try to select a different color quality to see if this message disappears or you can simply disable the message now if you are sure the required color quality (32 bit) is not available in the given guest OS."
thanks

---

### Post by bodhi.zazen on 2009-05-07
> **duncan503 said:**
> Hello I come to a thing:confused: the resolution of the screen of a 32 bit. And the virtualbox  tells me to update from 24 bit to 32 bit, the question is how to change it.

Thanks

Install the VirtualBox Guest Additions (on the guest, not host).

See also :

[http://forums.virtualbox.org/viewtopic.php?f=3&t=10904](http://forums.virtualbox.org/viewtopic.php?f=3&t=10904)

---

