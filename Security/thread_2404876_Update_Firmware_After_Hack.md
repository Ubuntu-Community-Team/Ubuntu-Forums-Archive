---
title: "Update Firmware After Hack"
date: 2018-10-29
forum: Security
---

### Post by peacefull on 2018-10-29
Dell 5378 Intel i7 KabyLake running bionic minimal install.
8gb RAM
Intel Wireless 3165

This computer has been hacked and breached.
Opened ports on UFW (high numbered ports)
(They) had disabled a paid vpn and activated desktop sharing via control panel. Who knows what else was breached or modified.

Since that time...
Secure Erased SSD via hdparm.
Re-installed and updated Bionic desktop.
Updated Dell efi/bios.

I'm still not satisfied that it's secure.

Lynis is installed but still needs to be configured for recommended changes. 
chkrootkit installed and coming up clean.
firejail for FF.
UFW default settings with "limit SSH" rules.
Wireshark installed but need a day to study the instructions. 

I want to flash firmware and drivers to help rid of any rootkit that might have been installed, and is undetectable.
How do I do this via terminal, or are the individual firmware updates applied through the bios menu?

The attack was targeted.

---

### Post by TheFu on 2018-10-30
If you've done all this and still don't trust it, time to sell the machine and get a new one.  Get it from a random retail outlet. Don't have it shipped.
You claim it is a targeted attack. What proof for that is there?  Was it your little brother or some govt?  The risks are vastly different.

---

### Post by peacefull on 2018-10-30
I was afraid you'd say that, Fu.

I really would like to update all firmware that is known to be infected by skilled hackers to be free of any possible rootkits and spyware. 

A bios/efi update rewrites the bios, correct? So, as a matter of argument, the newly updated bios wouldn't contain a rootkit (if installed). Is this right?
Assuming the above is correct, a flash/update of the wlan card and other firmware would write over the existing code to become free of rootkits?

What is the proper way of updating firmware with ubuntu/linux? I've googled this question, but end up with the bios update, which has since been done. All of the updates have been downloaded onto a USB thumb.

As I know that this was targeted....not by a state or law enforcement, but rather by a very determined psycho whom I pissed off and exposed. She is doing this by hired proxy. This much, I def know.

---

### Post by mcyber4 on 2018-10-31
I was hacked also. You need to completely flash the bios. I flashed my asus z87pro in the bios but that didn't help and I haven't found out how to completely flash it. But my PC is more than 5 years old hence I might update it anyway.
That guy even created hidden partitions. Be careful and check with testdisk.
Good luck

---

### Post by TheFu on 2018-10-31
HDD firmware can be used to hide things. This has happened before and there is not way to prove it happened or that it is clear. Testdisk won't see the HDD firmware changes.

 It is doubtful that someone is attacking only 1 device. Any smartphone or tablet is much easier to attack and use as a launch pad to gain access to the LAN and to devices connected to the LAN.

If you want to handle this yourself, then you are better than I.  I'd pay a professional to find the attack vector and other likely vectors.  The alternative is to spend the next 3-5 yrs learning about all the different devices and networking to learn myself how to prevent the attacks.  If you have that sort of time, others will likely pay you for this expertise.  

You'd stop using smartphones completely.  Get a $20 flip phone as a starting point. You'll not connect to most networks and stop using BT and wifi networking completely. You'll need to make many decisions for good security over convenience.  Most people wouldn't be willing to do that.

---

### Post by mcyber4 on 2018-10-31
> **TheFu said:**
> HDD firmware can be used to hide things.


Yes boot from usb or cd.
Then delete all with:
[LEFT][COLOR=#242729][FONT=Consolas][/FONT][/COLOR][COLOR=#242729][FONT=Consolas]dd if=/dev/zero of=/dev/[disk device] bs=512 count=1[/FONT][/COLOR][/LEFT]
completely flash your bios and save the money for a professional

---

### Post by TheFu on 2018-10-31
Using dd doesn't touch the USB firmware or disk firmware.  There are hundreds of different attack vectors.  Nobody can know them all and protecting against them is much harder than being the attacker. An attacker with time and resources will get in. The best we can hope for is to make it very difficult so they move onto easier targets.

Underestimating a dedicated opponent is a mistake you shouldn't make.

Most USB storage has firmware that can be modified with some hardware tools.
[https://nakedsecurity.sophos.com/2014/10/06/badusb-now-with-do-it-yourself-instructions/](https://nakedsecurity.sophos.com/2014/10/06/badusb-now-with-do-it-yourself-instructions/)

The firmware in all storage can hide anything the organization decides to hide. Just accessing it is sufficient.
[https://www.wired.com/2015/02/nsa-firmware-hacking/](https://www.wired.com/2015/02/nsa-firmware-hacking/)

None of this is new.  Mitigation techniques aren't convenient, but they do exist.  Just depends on how far someone is willing to go. 

 I've seen people asking for help with similar situations. These are high-profile people having their lives laid out for the public.  They have a difficult line, since they earn their income by being in public, so shutting off completely isn't possible.  The people who help them aren't cheap, but they have vast knowledge across 10 platforms and all the social media systems.  They understand networking, firmware, layered security, and have the resources to ensure physical security for all the devices and networking. Their clients are highly, highly, motivated.   I'm not involved but spent some time thinking through what it would require to secure people like that. 

I realized I couldn't help after just a few minutes of thought, these victims were in the Apple ecosystem.  A determined attacker will find a way.

---

### Post by peacefull on 2018-10-31
Great answers here. I'm still looking for the answer to the OP. 

**"What is the proper way to update/flash the firmware in ubuntu?** I've DL Dell updates and could only flash the Bios. WLan card, graphics, keyboard/camera, chipsets still need to be updated, and I'm aware that these can be infected, also.

---

### Post by peacefull on 2018-10-31
> **TheFu said:**
> If you've done all this and still don't trust it, time to sell the machine and get a new one.  Get it from a random retail outlet. Don't have it shipped.
You claim it is a targeted attack. What proof for that is there?  Was it your little brother or some govt?  The risks are vastly different.


The attacker was/is a proxy for a bona-fide psychopath whom I pissed off and exposed (some of their corruption). This person has great monetary  resources and  all the time in the world. 

This is not a city/state/gov/LE, as I have no fear of them, nor do I live in such a way be paranoid of their presence.

---

### Post by TheFu on 2018-10-31
Follow the instructions for each device.  Nobody can provide any more details than that. 

If there isn't an Ubuntu-specific version of the update programs provided by dell, then you'll need to use whatever method the device vendor provides, if any exists.

---

