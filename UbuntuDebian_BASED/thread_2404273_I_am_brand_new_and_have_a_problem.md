---
title: "I am brand new and have a problem"
date: 2018-10-22
forum: Ubuntu/Debian BASED
---

### Post by stevesd619 on 2018-10-22
I have an older computer a sony vaio and I have dual booting linux lite and win 7. I had version 3.8 but it upgraded me to 4.4 and now I cannot get the linux bootloader to work. I am wondering if it would be better to try a different distro or what to do. Please forgive my ignorance, I am just learning. Also, I cannot find a wifi driver for linux and I have looked everywhere. It is a Marvell [COLOR=#6A6A6A][FONT=arial]**Marvell Technology Group Ltd**[/FONT][/COLOR][COLOR=#545454][FONT=arial]. [/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**88w8335**[/FONT][/COLOR][COLOR=#545454][FONT=arial] [Libertas] 802.11b/g Wireless (rev 43) I found the windows 7 driver and used ndis and everything seems to be okay on that end but I don't know how to start it and I am lost. My ethernet wired works fine but I wanted to get wifi also. It shows no device. although it showed the driver but now I cant get into linux desktop any longer. Any help would be greatly appreciated. [/FONT][/COLOR]Thank you.  p.s. I didn't know who else to turn to.

---

### Post by Jocklad on 2018-10-22
There is no Linux Lite 4.4.

The latest is 4.2 and that is still in Beta.

---

### Post by stevesd619 on 2018-10-22
thats all i get....you correct me on my mistake of version?  hahaha....

---

### Post by stevesd619 on 2018-10-22
thanks jocklad....i wish i could have gotten a bit more assistance though.   its ok  :)

---

### Post by coffeecat on 2018-10-22
*Thread moved to **Ubuntu/Debian BASED**.*

@stevesd619, it has only been three hours since you first posted. Please be patient. Forum members come from all around the world, and the one who might be able to help you may be in a completely different time-zone. Also, Jocklad made a perfectly valid point. Accurate information is needed for members to give good support.

Lastly:

[quote=stevesd619]
I didn't know who else to turn to.[/quote]

Linux Lite has its own forum here: [https://www.linuxliteos.com/forums/](https://www.linuxliteos.com/forums/)

Whilst you are welcome to ask for support here, this is not the best place. Most members here use one of the official flavours of Ubuntu - Linux Lite is not one of these - and there may be few if any here with experience of Linux Lite.

---

### Post by hackerb9 on 2018-10-22
Steve,

I had a similar WiFi card (WG311) and I do not believe you need to use NDIS. You do need to install the Libertas firmware, however. Make sure you have the [FONT=Fixedsys]linux-firmware[/FONT] package installed.

On the other hand, that's an ancient and slow WiFi card. It may make more sense just to buy a tiny USB WiFi adapter that can handle more modern WiFi protocols.

---

