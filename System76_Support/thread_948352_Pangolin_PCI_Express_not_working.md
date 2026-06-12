---
title: "Pangolin PCI Express not working"
date: 2008-10-15
forum: System76 Support
---

### Post by storkk on 2008-10-15
Hi, all...
My pangolin laptop is about 1 year old now, and is running Hardy. I recently bought a D-Link DWA-643 network PCI Express card, as madwifi states ([http://madwifi.org/wiki/Compatibility/D-Link](http://madwifi.org/wiki/Compatibility/D-Link)) that it works with the latest svn, which I have checked out. I did a make clean; make; sudo make install... no errors.

However, when inserting the DWA-643, nothing happens, the light doesn't blink, etc. What steps have I missed, and/or how can I get this working? The memory card reader also has never worked, as far as I could tell, but I never spent much time on it as it has never been important (I always use a USB cable). I just mention it, as it's possible the two problems could be related.

Thanks in advance for all your help,

Storkk

---

### Post by storkk on 2008-10-15
I have tried all of this, and all ran without errors


```
cd scripts
./madwifi-unload
./find-madwifi-modules.sh $(uname -r)
cd ..
```

then re-doing make install; modprobe ath_pci

no luck...
then I came accross [http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008) so I added an entry to /etc/network/interfaces

no luck :-( I just cannot see ath0 with or without -a to ifconfig.

Any ideas?

---

### Post by thomasaaron on 2008-10-15
I can't tell by the information in the thread, but if you will email me your name or order number (support at system76 dot com), I'll look to see which Pangolin you have.

My point: Do you have an express card slot on your pangolin, or is it a PCMCIA slot? Peek inside of it and make sure your card can go ALL THE WAY to the back.

---

### Post by storkk on 2008-10-15
Hi,

It's a PCI express card as is the slot, not the old PCMCIA, it fits just fine. In the very beginning I had a problem, as my machine would keep shutting down, and with your (plural) support, we traced it to the fact that the fan had not been plugged in at the factory -- so i had to undo the screws on my laptop and plug the little cable in.

Could this be the case for the PCI slot also??

Would it be better to take this privately to support at system76.com?

--edit--
oh, in case it is important, my laptop is an FL91, and i'm running Hardy at 64bit (Linux xxxxxxx 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux)

---

### Post by thomasaaron on 2008-10-15
No, that wouldn't be the problem with the express card slot.

We aren't really set up to test the third-party hardware that you are using (i.e. I don't have one of them in the shop). So, probably the forums is the best place to explore this issue. Perhaps another customer is using the same card.

You might also google the card model + Hardy and see if anyone else has run into the same problem.

---

### Post by storkk on 2008-10-15
In general, though, is that how it's supposed to work? plug it in and it gets detected automatically? I haven't fiddled around with pci cards at all in linux.

---

### Post by thomasaaron on 2008-10-15
Yes. That generally is how it is detected.

Enter this command in a terminal...

tail -f /var/log/syslog

...and then plug in your device. If it is detected, you will see it there. It may also offer some helpful messages. Post them here and let's see if we can figure it out.

---

### Post by storkk on 2008-10-15
Hrmn... 

I don't know if this will help anybody else (and it's a little worrying), but I unplugged the card again, plugged it back in; the system froze completely -- on restart, after forcefsck, ath0 is now showing up in ifconfig.

bizarre.

thanks anyway for your help... I hope others work this out without a crash :-)


Storkk

---

### Post by storkk on 2008-10-17
After one more reboot, having done nothing as far as I know to have changed anything, it has stopped working. Still shows up in lspci... just no way to get it into iwconfig or ifconfig.

--edit--
Don't have much time to fiddle around right now, but will be trying with ath9k at some point and updating the results, as it seems that atheros worked on these drivers directly, and it seems that the D-Link DWA-643 works with the experimental drivers.

---

