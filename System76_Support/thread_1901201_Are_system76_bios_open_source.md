---
title: "Are system76 bios open source?"
date: 2011-12-28
forum: System76 Support
---

### Post by dodo3773 on 2011-12-28
Just curious that's all. I would like to someday move to an open bios and would like to know if I am already using one. If not is there any plans to make this move in the future?

---

### Post by hansdown on 2011-12-28
Hi,dodo3773.

Sadly, most hardware comes with propietary bios installed.

[http://blog.thesilentnumber.me/2009/08/top-5-things-wed-all-love-to-see-from.html](http://blog.thesilentnumber.me/2009/08/top-5-things-wed-all-love-to-see-from.html)

---

### Post by dodo3773 on 2011-12-28
> **hansdown said:**
> Hi,dodo3773.

Sadly, most hardware comes with propietary bios installed.

[http://blog.thesilentnumber.me/2009/08/top-5-things-wed-all-love-to-see-from.html](http://blog.thesilentnumber.me/2009/08/top-5-things-wed-all-love-to-see-from.html)

So, are you saying that it is not open (this is what I will assume by your link)? It seems like coreboot is a ways off still. It was last time I checked anyway. Also, is the bios image I am currently using licensed under GPL? I see that the drivers are. But is the bios?

---

### Post by hansdown on 2011-12-28
> **dodo3773 said:**
> So, are you saying that it is not open (this is what I will assume by your link)? It seems like coreboot is a ways off still. It was last time I checked anyway. Also, is the bios image I am currently using licensed under GPL? I see that the drivers are. But is the bios?

Not sure which computer you own, but on mine, I hold the esc key at boot up, and my bios version pops up.

It's American Megatrends.

---

### Post by dodo3773 on 2011-12-28
> **hansdown said:**
> Not sure which computer you own, but on mine, I hold the esc key at boot up, and my bios version pops up.

It's American Megatrends.

It is a system76 laptop. That is why I was asking in the system76 sub-forum. The bios is branded system76 on the boot screen if that is what you mean.

---

### Post by hansdown on 2011-12-28
There is an online petition to move to coreboot.

[http://www.petitiononline.com/system76/petition.html](http://www.petitiononline.com/system76/petition.html)

---

### Post by dodo3773 on 2011-12-28
> **hansdown said:**
> There is an online petition to move to coreboot.

[http://www.petitiononline.com/system76/petition.html](http://www.petitiononline.com/system76/petition.html)

Signed.

---

### Post by oxman on 2012-01-02
signed

---

### Post by tersogar on 2012-01-03
> **hansdown said:**
> There is an online petition to move to coreboot.

[http://www.petitiononline.com/system76/petition.html](http://www.petitiononline.com/system76/petition.html)

Signed.

---

### Post by Timothy Benton on 2012-05-06
System76 laptops are made by Clevo. Clevo probably licensed the BIOS from Phoenix, AMI, Award or some other big name company. System76 takes Clevos, rebadges them, installs Ubuntu, provides drivers and support. I don't think they are capable (right now) of easily changing to Coreboot, they would have to change their hardware supplier.

Here is the list of supported motherboards for Coreboot:
 [http://www.coreboot.org/Supported_Motherboards#Laptops](http://www.coreboot.org/Supported_Motherboards#Laptops)

I don't see any Ivy or Sandy Bridge support on there.
Probably because modern PCs use UEFI instead of BIOS
TianoCore support is more likely
 [http://sourceforge.net/apps/mediawiki/tianocore/index.php?title=Welcome](http://sourceforge.net/apps/mediawiki/tianocore/index.php?title=Welcome)

---

### Post by nll on 2012-05-20
I tried to sign the petition, but all I saw was a transparent grey box and a loading circle.

---

### Post by freechelmi on 2012-05-24
> **Timothy Benton said:**
> System76 laptops are made by Clevo. [...] System76 takes Clevos, rebadges them, installs Ubuntu, provides drivers and support. 


To be precise , it's a bit more than that. because the Bios is personnalized so the Brand Name reported by dmidecode is reall"System76" .

Also system76 have shown that New bios could be released by clevo  , dedicated to system76 machine to correct the linux OS handling.

So there are different levels of "Manufacturers" and system76 is quite close to clevo ( compared to others like Airis who don't understand why bios support is important ) 


System76 people, correct me if I'm wrong.

---

### Post by 3Miro on 2012-05-24
Couple of years ago this came up and System76 said that open source BIOS is simply not stable enough. They will move use FOSS BIOS, if one would work well enough.

---

### Post by Geremia on 2012-09-27
> **hansdown said:**
> There is an online petition to move to coreboot.

[http://www.petitiononline.com/system76/petition.html](http://www.petitiononline.com/system76/petition.html)Signed

---

### Post by Geremia on 2012-09-27
I have the Lemur 2 (Lemu2) laptop from System76. It has a Core i3 chipset, and I don't think CoreBoot supports Core i3 chips. Does it? If so, how would I install CoreBoot on my System76? Thank you

---

### Post by dodo3773 on 2012-09-27
> **Geremia said:**
> I have the Lemur 2 (Lemu2) laptop from System76. It has a Core i3 chipset, and I don't think CoreBoot supports Core i3 chips. Does it? If so, how would I install CoreBoot on my System76? Thank you

I highly doubt it. Also, your bios is motherboard stuff. Not exactly related to your processor. I would not recommend trying it unless it was completely supported. If you attempt it yourself will probably destroy your system and you will not be able to fix it without sending it in. You have been warned.

---

### Post by isantop on 2012-09-27
> **dodo3773 said:**
> I highly doubt it. Also, your bios is motherboard stuff. Not exactly related to your processor. I would not recommend trying it unless it was completely supported. If you attempt it yourself will probably destroy your system and you will not be able to fix it without sending it in. You have been warned.

This is correct. This type of problem requires motherbaord repalcement too, which is extremely expensive.

---

### Post by Geremia on 2012-09-27
> **dodo3773 said:**
> I highly doubt it. Also, your bios is motherboard stuff. Not exactly related to your processor. I would not recommend trying it unless it was completely supported. If you attempt it yourself will probably destroy your system and you will not be able to fix it without sending it in.CoreBoot's [definition of "supported"]("http://www.coreboot.org/Supported_Motherboards") is "another user got it work."

I know I have an Intel Corporation 82801 Mobile PCI Bridge, which  [this page  says CoreBoot v4 supports]("http://www.coreboot.org/Supported_Chipsets_and_Devices").

> **isantop said:**
> This is correct. This type of problem requires motherbaord repalcement too, which is extremely expensive.So, the ROM chip would need un-soldering? Or does the ROM chip just snap on?

So, does CoreBoot not support CLEVO/KAPOK boards?

(Also, my LemU2 is basically a CLEVO 3100. [Here's CLEVO's manual for the S310xx series.]("ftp://sftp.clevo.com.tw/USRMANUAL/S310xx/S310x_EUM.zip"))

---

### Post by isantop on 2012-09-28
> **Geremia said:**
> CoreBoot's [definition of "supported"]("http://www.coreboot.org/Supported_Motherboards") is "another user got it work."

I know I have an Intel Corporation 82801 Mobile PCI Bridge, which  [this page  says CoreBoot v4 supports]("http://www.coreboot.org/Supported_Chipsets_and_Devices").

So, the ROM chip would need un-soldering? Or does the ROM chip just snap on?

So, does CoreBoot not support CLEVO/KAPOK boards?

(Also, my LemU2 is basically a CLEVO 3100. [Here's CLEVO's manual for the S310xx series.]("ftp://sftp.clevo.com.tw/USRMANUAL/S310xx/S310x_EUM.zip"))

No, the only BIOS System76 laptops support are the ones released by System76. They don't support any other BIOSes, not from Clevo, not from Coreboot, but only us. I'm sorry for the inconvenience.

---

