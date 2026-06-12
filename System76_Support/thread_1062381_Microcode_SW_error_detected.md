---
title: "Microcode SW error detected"
date: 2009-02-06
forum: System76 Support
---

### Post by theTOman on 2009-02-06
This new message popped-up just now... And the Pangolin doesn't connect to the Net through the wifi anymore... 

And if I try to configure it (by using the "manual configuration" option), the progress bar during the "Changing Network Interface" process goes by flukes and then, once it's done, the cursor becomes unmovable.

But closing the wifi (with the button on the front of the computer) releases the cursor and everything is ok (without being connected, of course...)

On a wired connection, everything is fine, though...

So, I guess this "Microcode SW error detected" has to do with the wifi?

Please Help! I've Googled the thing, found godzillions of Bug reports, but no clue as to what's going on or how to fix it! :(

---

### Post by thomasaaron on 2009-02-06
Make sure the hardware switch is in the ON position. Then repair your interfaces file following these directions...

> To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).   

Then reboot.

---

### Post by theTOman on 2009-02-07
Thanks Tom

For now, it seems to have done it!

:-)

---

### Post by Guille Damke on 2009-02-08
I ran into the same issue with my Pangolin when I just got it (by my mistake, nothing to do with the Pangolin). and this piece of advice solved it. Even I have helped people with other machines to have the network working doing this.
Can someone explain me (or point me somewhere) what this file and lines do in the wireless network configuration? I think that lo is a "virtual" device which any application in the OS use, and lo takes care of connecting to the physical wlan device.
thanks.

---

### Post by jdb on 2009-02-08
> **Guille Damke said:**
> I ran into the same issue with my Pangolin when I just got it (by my mistake, nothing to do with the Pangolin). and this piece of advice solved it. Even I have helped people with other machines to have the network working doing this.
Can someone explain me (or point me somewhere) what this file and lines do in the wireless network configuration? I think that lo is a "virtual" device which any application in the OS use, and lo takes care of connecting to the physical wlan device.
thanks.

```
man interfaces
```

gives a lot of info.

jdb

---

