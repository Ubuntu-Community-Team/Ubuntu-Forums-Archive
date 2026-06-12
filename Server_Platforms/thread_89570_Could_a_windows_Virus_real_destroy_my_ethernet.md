---
title: "Could a windows Virus real destroy my ethernet?"
date: 2005-11-12
forum: Server Platforms
---

### Post by drews_blunted on 2005-11-12
I have a fairly new sony labtop, it had windows xp on it but it broke because of a suposive virus that made the ethernetcard useless. This is not my computer, i just installed Ubuntu on it however and the ethernet still isnt working? So my question is could a windows virus really destroy or ruin hardware? should i get a usb ethernet card or something?

Anyone help would be great!

---

### Post by aysiu on 2005-11-12
Have you gone to System > Administration > Networking and looked at eth0 to see if it's using DHCP?

---

### Post by darknuala on 2005-11-12
A virus could disable things in windows to keep your internet connection from getting out anywhere.  Try booting with a knoppix disk.  If it doesn't work with that, you've probably got hardware issues.  Also, in Windows did you check the device manager?  Could you ping anything?

---

### Post by Arthemys on 2005-11-13
My first post after a long period of silence;

It's not possible on any level for a virus to toast hardware. However, I do remember that is possible to set a hard drive password using software, invariably locking the user out of their system.

---

### Post by LordHunter317 on 2005-11-14
[QUOTE=Arthemys]It's not possible on any level for a virus to toast hardware. [/quote]No, that's not actually true, though it's nearly impossible on a modern PC platform.  

On other platforms, OTOH, it's quite possible.

---

### Post by Biased turkey on 2005-11-14
Was there not a case a couple of years ago of a Windows virus that erased the BIOS ?

---

### Post by heftigrat on 2005-11-14
[QUOTE=LordHunter317]No, that's not actually true, though it's nearly impossible on a modern PC platform.  

On other platforms, OTOH, it's quite possible.[/QUOTE]

Please explain.  I've heard some scuttlebutt about those proficient in assembly code being able to literally toast hardware, but I thought that was all hogwash.  I would be interested to know more...

---

### Post by dtfinch on 2005-11-14
I saw a user delete their wireless drivers out of fear that they downloaded something they shouldn't. Silly user. The drivers have proven to be very hard to find online too.

---

### Post by Zerocool10482 on 2005-11-16
I've never heard of something like this but just try to check your settings. And try to get a direct connection to net. Use your direct connection to test and see if it's the card. But try not to buy another without testing.

---

### Post by Cyril on 2005-11-16
I believe the virus biased turkey is refering to is the chernobyl virus.  If you are infected an turn on your computer when the system date is the 26th of any month, it will attempt to erase the first 1mb of your hard disk and a portion of your bios.

---

### Post by bryan986 on 2005-11-16
It is possible to overlock devices inside windows, such as a video card, so if a virus got control over your computer, it could potentially raise the clock high enough where it would die after some time

I don't know if video cards have safeguards to prevent stuff like this

---

### Post by AmboyGuy on 2005-11-28
About that CIH (Chernobyl) virus, Check out this page on Gibson Research
[**_CIH VIRUS_**](http://www.grc.com/cih.htm)

---

### Post by Danielle on 2005-11-28
hi, it's not very likely to be a hardware problem, it's fairly more probable it's software related. to recover your connection try running the winsockfix:
[http://www.majorgeeks.com/download4372.html](http://www.majorgeeks.com/download4372.html)

you should then download, install and update ewido (anti trojan scanner), MS anti spyware, adware, BitDefender Free (very good backup AV)and unhackme (will find rootkits, trojans etc. the scan time is very fast). they are all freeware.

then turn off System Restore and boot into safe mode (tap the F8 key at boot then select safe mode) and run and delete anything they find. then download and run HijackThis and post a log at [castlecops](http://castlecops.com/f67-Hijackthis_Spyware_Viruses_Worms_Trojans_Oh_My.html)
read the [url=http://castlecops.com/t102301-Hijackthis_Guidelines_Read_Before_Posting.html]
Guidelines[/url] before posting.

or post the log at [spywarewarrior](http://spywarewarrior.com/index.php)

here are the links for the scanners
[www.ewido.net/en/](www.ewido.net/en/)
[http://www.microsoft.com/downloads/details.aspx?FamilyID=321cd7a2-6a57-4c57-a8bd-dbf62eda9671&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=321cd7a2-6a57-4c57-a8bd-dbf62eda9671&displaylang=en)
[www.majorgeeks.com/download506.html](www.majorgeeks.com/download506.html)
[http://www.snapfiles.com/get/bdfree.html](http://www.snapfiles.com/get/bdfree.html)
[http://www.greatis.com/unhackme/](http://www.greatis.com/unhackme/)
[http://www.majorgeeks.com/download3155.html](http://www.majorgeeks.com/download3155.html)

if any of the scanners won't run in safe mode just run them normally. you could also have a look at your startups. open a dos prompt and type msconfig, then have a look at startups, if there's anything there that shouldn't be uncheck it.

when you have finished turn System Restore back on :)

---

