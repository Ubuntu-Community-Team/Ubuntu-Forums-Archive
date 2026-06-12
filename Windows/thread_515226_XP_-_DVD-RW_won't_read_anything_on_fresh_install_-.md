---
title: "XP - DVD-RW won't read anything on fresh install - Help anyone?"
date: 2007-08-01
forum: Windows
---

### Post by ironfistchamp on 2007-08-01
Hey all,

A windows question here, I really hope someone can help me. Anyway I have just installed XP Home SP2 onto this machine and everything went fine. I get through to the Desktop and look in My Computer. The DVD drive still has the name of the install disk even though it is not in there anymore. I double click and it is reading as a blank disk even though there is nothing in it. I reboot and hope that will do the trick. Now when I put a disk in it reads it as blank. Windows is currently useless (don't say anything :p) as I can't install drivers. Anyone know a way to fix this or what could be wrong?

Thanks

Ironfistchamp

---

### Post by kamaboko on 2007-08-01
> **ironfistchamp said:**
> Hey all,

A windows question here, I really hope someone can help me. Anyway I have just installed XP Home SP2 onto this machine and everything went fine. I get through to the Desktop and look in My Computer. The DVD drive still has the name of the install disk even though it is not in there anymore. I double click and it is reading as a blank disk even though there is nothing in it. I reboot and hope that will do the trick. Now when I put a disk in it reads it as blank. Windows is currently useless (don't say anything :p) as I can't install drivers. Anyone know a way to fix this or what could be wrong?

Thanks

Ironfistchamp

I had that happen once.  Turned out to be the DVD player.  Do you have another you can toss in there to test with?

---

### Post by ironfistchamp on 2007-08-01
No 'fraid not but thanks for the reply. I may just get a new one as I have wanted to get a SATA DVD-RW. This could just be my excuse :p

---

### Post by smoker on 2007-08-02
i had this a few times on xp computers and it can usually be fixed by uninstalling the drive in 'device manager' and then restarting the computer, letting the computer find the drive again, and install all the proper drivers. this link gives more detail than i can explain easily:
[http://www.microsoft.com/windowsxp/using/setup/learnmore/devicemgr.mspx](http://www.microsoft.com/windowsxp/using/setup/learnmore/devicemgr.mspx)

best of luck

---

### Post by ironfistchamp on 2007-08-03
Great so I got the new drive. All nice and shiny. Plug it in and things look good. I do a fresh install of Windows so I know everything is totally clean. Installed, open My Computer...SUCCESS. That's awesome so I install mobo drivers and reboot. On log in... the issue is back. I try the uninstall reboot method but that didn't do it. Fresh install again and it is fine. Reboot and, would you look at that, it doesn't work again.

Can anyone shed some light on this?

Thanks

Ironfistchamp

---

### Post by dca on 2007-08-03
Was the new optical drive you got a SATA?  Or was it IDE like the one that started the issues?
 
 
note:  I won't be going to hell for helping someone install/repair XP, will I???
 
I doubt this is a BIOS issue but anything is possible....

---

### Post by ironfistchamp on 2007-08-03
This is a SATA drive. It works perfectly well in Ubuntu btw.

---

### Post by smoker on 2007-08-03
hi, a few suggestions - normally during an xp install, if you have a sata hard drive you have to press f6 at the prompt early on the install, and install sata drivers from a floppy or usb device. if you have an ide hard drive you may not have had to do this, but because the driver wasn't loaded during install, there may be a conflict.

other than that, i would check the motherboard support site for updated drivers, this may be a known bug and be fixed in uptodate drivers, and also check the support site of your dvd drive manufacturer for the same.

best of luck

---

### Post by ironfistchamp on 2007-08-03
Thanks for the reply. My motherboard treats SATA drives like IDE drives and Windows always recognises them so I don't think it is that. I have the latest firmware for the device and the latest NForce drivers (it is an NForce 4 Ultra chipset).

I can't really think of much else that could be wrong. There doesn't seem to be anything wrong. The drive is fine elsewhere it is just Windows on -this- computer.

I can't see why it wouldn't like any of my other hardware as none of it has changed since XP was last on it.

Ironfistchamp

---

### Post by smoker on 2007-08-03
hmm, another couple of suggestions - try another sata cable if you have one, or swap round hard drive and dvd drive cables, and ensure connections are sound, try another sata port for the dvd drive. also check if there is a jumper for sata1, sata2, on the dvd drive, and try alternate options. you could maybe double check the drive is showing correctly in the bios, and check what different options are available there to try.

i would also download all windows updates, maybe one may fix!

not sure if one or any of the above will be any help, but i am sure it is fixable, and the cause is probably something simple!

best of luck

---

### Post by ironfistchamp on 2007-08-04
Gah this is insane. Turned the computer on this morning and it worked fine :confused:

This is why I use Ubuntu whenever I can. Come on you game devs, pull you finger out and develop for us!

Thanks for the replies and all the help guys.

Catch yas later.

Ironfistchamp

---

### Post by smoker on 2007-08-04
> Gah this is insane. Turned the computer on this morning and it worked fine :confused:

that's the way it goes, sometimes! at least it's sorted :-)

---

