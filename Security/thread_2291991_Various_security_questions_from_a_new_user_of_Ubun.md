---
title: "Various security questions from a new user of Ubuntu"
date: 2015-08-24
forum: Security
---

### Post by spamczarnymjest on 2015-08-24
Hello, I have some small questions concerning the security of my system. I have almost no knowledge of IT and have switched to Ubuntu to feel more secure than with Windows.

1. I dual boot Ubuntu 14.04 and Windows 7 Home Premium. Is my system easier to access now than if I used only Ubuntu? Is it still safer than Windows? I plan to log into Windows only if it is necessary (to use my job-related software and to play a game from time to time), which is let's say once a month.

2. As I dual boot systems, I have problems with using the same files (photos, music, documents - 200 GB) on two systems. I would prefer to use an external source to not slower down my system.  I figured out I can use an external hard drive. 

Is it safer to...
a) store all data in Windows
b) store all data on the external hard drive
c) store all data in Ubuntu?

3. How can I secure my external HDD so I can access it with Windows easily and do not have to type in a password each time I want to play a song (rather after plugging it in...)? It is a Toshiba STOR.E ALU 2S.

4. Is it rational to use Tor as the standard browser, if I plan to enable Youtube and similar sites? Just to let the browser feel somehow normal. I do not want to do anything illegal, I just want to feel... a bit safer than with Firefox.


I would appreciate any answer to any of these questions.

---

### Post by TheFu on 2015-08-24
First - read this. [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) No need to rewrite here what has already been covered there. You've probably already seen it and read it, so that link is for later lurkers.

Both Windows and Linux can be used in a secure fashion. It is just that Windows is a larger target due to market share, so extra care must be taken.  Security is not a "checkbox" - it is making the correct decisions to avoid risky activities than anything else.  The same precautions apply, regardless of OS - Stay patched, don't use javascript, don't use flash, don't use java in a web browser, don't visit seedy parts of the internet and I hate to say this, but block ad networks, which have tended to be hacked even from reputable sites like yahoo.com, microsoft.com, cnn.com ... it is a dangerous world out there.

Onto your specific questions:
4. I wouldn't bother.  Running tor in a secure way is hard. If you every use the same system, same browser, or login to any website outside tor, you will leak the privacy data you want TOR to stop.
3. Use NTFS if you want to share data files/media files between Linux and Windows. Doesn't matter if the storage is internal or external.  External storage devices cannot be secured without strong encryption.  I don't know of any encryption that supports both Windows and Linux besides the old, Truecrypt. I never tried it in that mode myself.
2. External hard disks are slower than internal disks. The only exception is eSATA connected which are exactly the same speed. USB is always slower. From a security standpoint, Linux file systems would be slightly more secure - much more secure if you encrypt. However, Windows wouldn't be able to access that data. For that, you need NTFS, which has next to ZERO security.  Honestly, Linux file systems have next to zero security if physical access is possible and encryption isn't used.
1. Dual boot doesn't impact network security.  Physical security is equally bad regardless of OS. With physical access for 3 min, cleaver people can pwn either OS with little effort. Whole disk encryption is the only real defense.  There are tiny holes in whole disk encryption too, but that only matters if you are target for espionage or some government. Family won't get passed it.

---

### Post by mystics on 2015-08-24
> **spamczarnymjest said:**
> 4. Is it rational to use Tor as the standard browser, if I plan to enable Youtube and similar sites? Just to let the browser feel somehow normal. I do not want to do anything illegal, I just want to feel... a bit safer than with Firefox.

Is this a matter of privacy or security? If the latter, what is it about Firefox that makes you feel insecure with using YouTube? Either way, there are plenty of Add-Ons to Firefox that can improve both privacy and security.

---

### Post by Bucky Ball on 2015-08-24
1. No.
2. You don't need an external drive. An NTFS filesystem data partition can be shared by Ubuntu and Windows with ease. 

Even if you do put your personal data on an external drive, the partition would still need to be in a filesystem Win can read and write to, NTFS or FAT. FAT is old and has limitations so don't go there. Bottom line: external or internal drive, the partition is best as NTFS to share with both OSs.

I have about four installs, one of them Win7, and they all use exactly the same data partition. When I open, say, 'Documents' in any install it is exactly the same contents in 'Documents' as in all of the installs.

---

### Post by linuxyogi on 2015-08-27
> 4. Is it rational to use Tor as the standard browser, if I plan to  enable Youtube and similar sites? Just to let the browser feel somehow  normal. I do not want to do anything illegal, I just want to feel... a  bit safer than with Firefox.


If you plan to enable flash for Youtube or other sites the Tor browser may become inefective.

[https://www.torproject.org/docs/faq.html.en#TBBFlash](https://www.torproject.org/docs/faq.html.en#TBBFlash)

> [h=3][Why can't I view videos on some Flash-based sites?]("https://www.torproject.org/docs/faq.html.en#TBBFlash")[/h]  Some sites require third party browser plugins such as Flash. Plugins operate independently from Firefox and can perform activity on your computer that ruins your anonymity. This includes but is not limited to: completely disregarding proxy settings, querying your [ local IP address]("http://forums.sun.com/thread.jspa?threadID=5162138&messageID=9618376"), and [storing their own cookies]("http://epic.org/privacy/cookies/flash.html"). It is possible to use a LiveCD solution such as or [The Amnesic Incognito Live System]("https://tails.boum.org/") that creates a secure, transparent proxy to protect you from proxy bypass, however issues with local IP address discovery and Flash cookies still remain. 



[URL="https://www.torproject.org/docs/faq.html.en#TBBFlash"]


[/URL]

---

### Post by SuperFreak on 2015-08-27
> **TheFu said:**
> 
3. Use NTFS if you want to share data files/media files between Linux and Windows. Doesn't matter if the storage is internal or external.  External storage devices cannot be secured without strong encryption.  I don't know of any encryption that supports both Windows and Linux besides the old, Truecrypt. I never tried it in that mode myself.



Veracrypt will work with Win/Linux/Mac

---

### Post by TheFu on 2015-08-27
Because Tor has been used for DoS attacks recently, many websites as now blocking Tor exit nodes. There are [recipes]("https://warrenguy.me/blog/detecting-tor-users-nginx-linux") to do this for nginx and other popular reverse proxies it has become such a wide-spread problem.

We've been discussing this issue in my security team too.  We'd rather not block tor users - after all, being slightly anonymous on the internet is something we want to support, but if we are being attacked from these systems and blocking them can make it stop ... seems like an easy solution.  

Most people aren't careful enough with Tor to remain anonymous online anyway. They are just using it to alter their exit IP to a different country to get around country specific blocking - especially for video sites.  There are  lists of VPN proxies around the world too - we've had to block many of those already, but only after abuse.

I thought Veracrypt was illegal due to violating TrueCrypt's copyright.  Is that not true?  I recall all the discussions but don't remember the resolution.  TrueCrypt didn't use any of the recognized OSS approved licenses.

---

### Post by SuperFreak on 2015-08-29
> **TheFu said:**
> 
I thought Veracrypt was illegal due to violating TrueCrypt's copyright.  Is that not true?  I recall all the discussions but don't remember the resolution.  TrueCrypt didn't use any of the recognized OSS approved licenses.

Was not aware of this, do you have a link to this?
FAQs for vercrypt say it is Open Source

---

### Post by TheFu on 2015-08-29
[https://en.wikipedia.org/wiki/TrueCrypt#License_and_source_model](https://en.wikipedia.org/wiki/TrueCrypt#License_and_source_model)

Don't have anything better than that - all the articles seen were lawyers asking the truecrypt guys to change the license to be compatible with OSS.  In the end, I'm not certain that Vercrypt legally can based their software off it, but INAL.

---

