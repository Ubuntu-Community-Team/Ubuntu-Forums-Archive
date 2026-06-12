---
title: "Dual Boot Security Question"
date: 2009-08-18
forum: Security
---

### Post by norjms on 2009-08-18
I was recently on a business trip from the US to the UK. When we returned through customs to the US a nice gentleman from customs asked to inspect my co-workers laptop. Well once the nice man /sarcasm booted his laptop and he was greeted by the Ubuntu full disk encryption scheme. The customs agent didn’t ask for a password he just informed my co-work they were going to hold his laptop for “inspection”. Now, I know the data on the laptop is safe, but it is quite unfortunate that my co-work was without his laptop for several weeks while it was being “inspected”. So, here is my question.
	If I setup dual boot on a laptop, say Windows XP / Ubuntu and run full disk encryption on the Ubuntu and swap partition. Is there a way to hide the boot menu to access Ubuntu? I myself have a Mac and dual boot OS X and Ubuntu. Now when my laptop boots up it goes straight to OS X and only offers to boot Ubuntu if I hold down the option key when booting.  The reason I ask is that I understand there really isn’t any additional security added by hiding the OS as anyone with half a brain will be able to figure out it is there, but to the casual observer just wanting to have you turn on the computer and make sure everything “looks” right it avoids a lot of questions.
	The reason I ask is when the inspector looked at my laptop it booted straight to OS X showed a nice pretty OS X desktop with miscellaneous photos music and documents the inspector handed me back my laptop and told me to have a nice day. I also use full disk encryption, but mine was not noticed as the inspector didn’t hold down the option key when he turned it on, so here never saw anything.
	Maybe I should take my tin foil hat off or something, but I was just looking for options to still have full disk encryption enabled and not have anyone who doesn’t understand data security think you’re up to no good because they can’t just bypass your data encryption.

---

### Post by tubbygweilo on 2009-08-19
This may be a bit OTT but [Bruce Schneier]("http://www.schneier.com/blog/archives/2009/07/laptop_security.html") has a few ideas on keeping data safe when moving between countries. Lots of ideas with some requiring a good strong tin foil hat.

---

### Post by koenn on 2009-08-20
you can set up dual boot, 
then set 'hiddenmenu' in grub.
the menu won't show, and grub will boot the 'default' OS in 'timeout' seconds.

If you want to see the menu to select an other OS than the default, press [ESC] before the timeout runs out.

---

### Post by HermanAB on 2009-08-20
Noooo! Now you have given my top secret steganographic boot method away!

Another trick is to put the Linux boot loader on a memory stick or CDROM to boot a second encrypted partition and let the HDD MBR default to booting Windows ME normally off the first partition.  You can then booby trap Windows with tons of malware to infect whatever anyone would connect to it for analysis (just leave it online for a while).
;)

---

### Post by koenn on 2009-08-20
> **HermanAB said:**
> Noooo! Now you have given my top secret steganographic boot method away!
sorry :(

> **HermanAB said:**
> 
Another trick is to put the Linux boot loader on a memory stick or CDROM to boot a second encrypted partition and let the HDD MBR default to booting Windows ME normally off the first partition.  You can then booby trap Windows with tons of malware to infect whatever anyone would connect to it for analysis (just leave it online for a while).
;)
that's just ... evil. 
:)

---

### Post by rookcifer on 2009-08-20
> **norjms said:**
> I was recently on a business trip from the US to the UK. When we returned through customs to the US a nice gentleman from customs asked to inspect my co-workers laptop. Well once the nice man /sarcasm booted his laptop and he was greeted by the Ubuntu full disk encryption scheme. The customs agent didn’t ask for a password he just informed my co-work they were going to hold his laptop for “inspection”.

LOL.  I bet the customs agent was surprised when he was confronted with a strange Ubuntu prompt.  I doubt he has ever heard of it.  I only wonder what he thought could be learned from "inspection."

> 	If I setup dual boot on a laptop, say Windows XP / Ubuntu and run full disk encryption on the Ubuntu and swap partition. Is there a way to hide the boot menu to access Ubuntu? 

Not with the default encryption scheme (LUKS).  You would have to use Truecrypt and create a hidden volume inside a decoy OS.

>  The reason I ask is that I understand there really isn’t any additional security added by hiding the OS as anyone with half a brain will be able to figure out it is there, but to the casual observer just wanting to have you turn on the computer and make sure everything “looks” right it avoids a lot of questions.

If one creates a properly configured hidden OS inside a decoy OS, it shouldn't be trivial to find it.

	> The reason I ask is when the inspector looked at my laptop it booted straight to OS X showed a nice pretty OS X desktop with miscellaneous photos music and documents the inspector handed me back my laptop and told me to have a nice day. I also use full disk encryption, but mine was not noticed as the inspector didn’t hold down the option key when he turned it on, so here never saw anything.

Quite amazing.  If the government wants to violate the 4th amendment they could at least hire people who have a modicum of familiarity with computers to do these "inspections."  You could have been storing nuclear secrets on your Ubuntu partition but this "inspector" would have never found it because he doesn't know what a dual-boot is.
	
> Maybe I should take my tin foil hat off or something, but I was just looking for options to still have full disk encryption enabled and not have anyone who doesn’t understand data security think you’re up to no good because they can’t just bypass your data encryption.

Go to the truecrypt website and read about hidden volumes.  If you don't want to hide the entire OS, then you could hide a certain directory.

By the way, what did the government say when they returned your friend's laptop?  Did they inquire about the encryption?

---

### Post by razorboy5 on 2009-08-20
> **koenn said:**
> you can set up dual boot, 
then set 'hiddenmenu' in grub.
the menu won't show, and grub will boot the 'default' OS in 'timeout' seconds.
 
If you want to see the menu to select an other OS than the default, press [ESC] before the timeout runs out.
 
would recommend this method 
 
or just going to Grub list and deleting Windows temporarily
then even if someone opens up GRUB menu Windows will not show on it
 
sry didn't read question properly
i guess u want to delete Ubuntu from the Grub list
and put Windows as primary boot
should work either way

---

### Post by norjms on 2009-08-21
I wonder after doing a good bit of reading if this would work.

1. Install Windows XP to a small say 20gb partition on sda1 the mbr will be written to sda.

2. setup ubuntu to: 
sda2 /swap encrypted
sda3 /     encrypted
use a sd card for /boot I'm not sure what it will show up as...maybe sdb? So /boot is on sdb then have the grub bootloader put on sdb as well.
The Windows XP boot loader should be untouched since the ubuntu one was put on sdb not sda where Windows resides.

3. set the bios to boot to these choices.
1st CD-ROM
2nd external media i.e. usb key or sd card
3rd boot to hard drive

I "think" this would with the sd card in boot to grub and present the option for ubuntu or windows and with it out would boot Windows never even indication there is another OS on the system. So, will this work like I think it will? Are there any problems I should be aware of?

I understand with some poking around someone with computer knowledge would be able to see the ubuntu install partition, but it wouldn't be blatantly obvious as see grub and having to select an OS then getting the encrypted OS challenge.

Any thoughts or comments would be appreciated

---

### Post by tubbygweilo on 2009-08-21
One is tempted to ask if the data / systems you are attempting to hide are worth hiding or valuable enough to hide then why they be on the computer in the first place? If you are having an intellectual game with those who inspect laptops entering or leaving the country then is it worth the chance of having your kit taken for examination if you loose? One may even consider a normal windows setup with nothing to hide plus a live Ubuntu CD  and say a live Parted Magic CD with which to download valuable data once you have cleared the inspection / examination area. The only other advice I can think of would be to browse [/.]("http://slashdot.org/") where I expect this question has been asked and answered many times over the last few years.

---

### Post by norjms on 2009-08-21
Does it even mater what the data is? It should be enough to believe that they have no right to your private data. Avoiding having to explain that to some inspector on a powertrip is priceless. I believe my above mentioned plan will work and I will try it as soon as I get a chance on my laptop.

---

