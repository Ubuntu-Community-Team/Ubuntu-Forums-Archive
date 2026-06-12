---
title: "Open Source internal wireless card?"
date: 2007-05-23
forum: The Cafe
---

### Post by ThinkBuntu on 2007-05-23
My Atheros AR5212 is pretty bad, especially with the Madwifi driver. Does anyone know of a highly Linux-compatible wireless card, preferably internal? My laptop (ThinkPad T41) cries because of its wireless inferiority...

---

### Post by angryfirelord on 2007-05-23
My atheros card performs relatively well. What type of issues are you having?

I think Atheros is the chipset manufacturer with the best support.

---

### Post by ThinkBuntu on 2007-05-23
At my local coffee shop I get fine WiFi reception with my MacBook, as does everyone else with a Mac or PC. This is just one example, but to put it simply, it's near-impossible to get onto an open wireless network with my Atheros unless the signal's superb, like at my library.

---

### Post by jiminycricket on 2007-05-23
Intel has excellent support, I have it in my Thinkpad.

Ralink cards will *eventually* get great support since the drivers are fully open source and new ones that support Network Manager are in development.  Currently, it's a bit of a hodge-podge.

---

### Post by angryfirelord on 2007-05-23
Looks like you're not the only one: [http://ubuntuforums.org/showthread.php?t=305491&page=2]("http://ubuntuforums.org/showthread.php?t=305491&page=2")

[QUOTE="teachop"]This also happened for me, very low signal and constantly disconnect / reconnect, even right near the wireless router. My laptop is an acer aspire 3100 with the Atheros wifi built-in. Based on some other posts, I disabled the Network Manager in System> Preferences> Sessions, and set up using System> Administration> Network. After doing this, I ended up with a signal of 90%, and no more constant disconnect / reconnect. It works great, except I had to drop back to WEP from WPA because I didn't know how to select that option. All good, BUT...

I took my shiny new linux machine to work to show off a couple days ago, changed the wireless settings to get it to work there, and after I came home, I had to go around and around before I finally held my mouth right and booted and it worked again. I am sorry I cannot report the exact sequence, but it was close to this: Turn Network Manager back on; get wireless working; disable Network Manager and reboot; goof about with the settings in System>Administration>Network; reboot. It works now.

Now I cannot roam, and am totally in fear of touching the wireless settings again. But it is working fine.[/QUOTE]

Also, if you have a dapper cd lying around, try that too to make sure it's not an Edgy/Feisty problem.

---

### Post by ThinkBuntu on 2007-05-23
It isn't. I can confirm that this is a Madwifi problem, as I've experienced it with: Debian, Arch, MEPIS, Sabayon, Zenwalk, and many others...if only I could find the bloody Windows driver, I could just use ndiswrapper!

---

### Post by jimrz on 2007-05-23
> **ThinkBuntu said:**
> It isn't. I can confirm that this is a Madwifi problem, as I've experienced it with: Debian, Arch, MEPIS, Sabayon, Zenwalk, and many others...if only I could find the bloody Windows driver, I could just use ndiswrapper!

have never, at least since dapper, experienced this sort of problem on either my T42 (ibm mini-pci a/b/g) or my 600x (netgear wg511t pcmia) both with atheros 5212 using madwifi driver. both are used regularly and frequently connect to various open ap's of varying signal strength (the service at our local airport is particularly spotty/weak) and wifi performance is virtually the same as it is in windows using the OEM's drivers. the same can be said when connecting to ap's using wpa-psk encryption. the T42 is dual boot with xp and while the 600x is now unbuntu only it's wifi performance is virtually the same as when it was running win2k.

---

### Post by H.E. Pennypacker on 2007-05-23
Since this is a fairly popular question, check out:

[http://ubuntuforums.org/showthread.php?t=418904&highlight=wireless](http://ubuntuforums.org/showthread.php?t=418904&highlight=wireless)

[http://ubuntuforums.org/showthread.php?t=189940&page=3&highlight=best+wireless+card](http://ubuntuforums.org/showthread.php?t=189940&page=3&highlight=best+wireless+card)

[http://ubuntuforums.org/showthread.php?t=447404&highlight=best+wireless+card](http://ubuntuforums.org/showthread.php?t=447404&highlight=best+wireless+card)

[http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html)

---

### Post by ThinkBuntu on 2007-05-23
> **jimrz said:**
> have never, at least since dapper, experienced this sort of problem on either my T42 (ibm mini-pci a/b/g) or my 600x (netgear wg511t pcmia) both with atheros 5212 using madwifi driver. both are used regularly and frequently connect to various open ap's of varying signal strength (the service at our local airport is particularly spotty/weak) and wifi performance is virtually the same as it is in windows using the OEM's drivers. the same can be said when connecting to ap's using wpa-psk encryption. the T42 is dual boot with xp and while the 600x is now unbuntu only it's wifi performance is virtually the same as when it was running win2k.

Any tips?

---

### Post by jimrz on 2007-05-28
> **ThinkBuntu said:**
> Any tips?

not really, other than checking to make sure your card has the latest available firmware installed. they both just worked "out of the box", so all I had to do was enter the appropriate network info and set up a keyring p/w for use when connecting to wpa. guess I was just lucky, neither card has ever had any problem in ubuntu. hope you can get it sorted out.

---

### Post by odiseo77 on 2007-05-28
> **ThinkBuntu said:**
> My Atheros AR5212 is pretty bad, especially with the Madwifi driver. Does anyone know of a highly Linux-compatible wireless card, preferably internal?(...)

I have an Edimax EW-7128g (PCI, Ralink rt2500 chipset) and it works like a charm on linux. Ubuntu recognizes it out of the box; on other distros I must install the driver because it's not directly detected by the kernel, but the drivers are open source. The drivers can be found in the [serialmonkey project site]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page").

(not sure if this card can be installed on a laptop, so excuse me if it doesn't (I have no experience with laptops))

---

