---
title: "Ubuntu = no privacy?"
date: 2009-11-07
forum: Security
---

### Post by viking_maniac on 2009-11-07
Ubuntu seems to spill your privacy all over the system.
 
I was very disappointed to recently see that my encrypted home folders had so called cache folders inside /var/tmp/ with the name of each account. And I could even find the desktop wallpaper for each account inside those folders, among other things related to the accounts; scaring the heck out of me. Then I need to ask: what's the point of “encrypted homes” then?
 
/tmp/ did also seem to store a lot of stuff, though it gets deleted at each shutdown and restart by the system, still though it should not be that difficult to restore the deleted data.
 
And God knows what more is duplicated and stored around in the system!
 
Since it's very hard for the majority of the newcomers, and in general “not done in a fly”, to encrypt the whole system, like you can very easily do on Windows with either BitLocker from Microsoft or TrueCrypt 6.3 as a free option, I can suddenly see a huge security problem for e.g. corporates which need to protect their data. This regards most modern home users too. It doesn't help much encrypting your home folder, or even encrypt anything, if Linux/Ubuntu fills the tmp-folders with sensitive data. What if you have an Ubuntu laptop that gets stolen, and you're working in a corporate and need to protect the business' documents and sensitive data? It's just to take a look in the tmp folders, or any other folder that could store or duplicate private data, or try to recover tmp-files which have been used and deleted by the OS at shutdown. Not to mention burglary in your house.
 
I had the impression that Linux was the safest choice to make regarding personal security, but it looks like it's just as bad, or even worse, compared to the two worst privacy leeks of them all: Windows and Mac OS. At least Windows give you easy system encryption options to deal with this. I just don't feel like my privacy is there anymore on Ubuntu; not that I'm a super-agent or anything, but anyone should know that we all use our computers to store a lot personal info these days, and this only grows as our lifes get more and more into our computers, like passwords, account numbers, your holy diary, private e-mails, personal and private photo albums, formal documents, and etc; and therefore I'm back in Windows again for now with TrueCrypt encrypting my system. It might be that this regards all operating systems, but my own research gives me the impression that Windows Vista and 7 takes better care about your privacy than Ubuntu does. Windows do store temp files too, but most are related to the installation of new programs; and there's just one folder that collects all. And Windows has several software options to clear private data securely or encrypt the system; compared to Linux/Ubuntu that doesn't provide any; at least not an easy way to encrypt the system.
 
I should mention that this was related to Kubuntu, but they all are based on the same base system, right?
 
So what about you guys? What do you think of this and what do you do to keep your privacy in Ubuntu?

---

### Post by rookcifer on 2009-11-07
M$ only provides BitLocker on the Enterprise and Ultimate editions of Windoze.  If you are like 90% of home users and do not have these high priced versions, you get no encryption.  :(

If you are worried about tmp files (and I doubt there is anything sensitive there) then you should use the LUKS whole disk encryption option on the alternate CD.

Yes, I realize that Ubuntu does not make using LUKS as easy as, say, Fedora, but hopefully this will change in upcoming editions.  (With Fedora you can click a single button on install and encrypt the entire drive).

---

### Post by snowpine on 2009-11-07
/var is not in your /home folder, so "encrypt my home folder" won't encrypt it. :)
If you encrypt your whole drive, /var will be encrypted too.

---

### Post by viking_maniac on 2009-11-08
> **rookcifer said:**
> M$ only provides BitLocker on the Enterprise and Ultimate editions of Windoze. If you are like 90% of home users and do not have these high priced versions, you get no encryption. :(
 
I know, but TrueCrypt solves that. ;)
 
> **rookcifer said:**
> If you are worried about tmp files (and I doubt there is anything sensitive there) then you should use the LUKS whole disk encryption option on the alternate CD.
 
Thanks for this tip! I'll try this out soon; and maybe there's hope for Linux after all. :)

---

### Post by rookcifer on 2009-11-08
> **viking_maniac said:**
> I know, but TrueCrypt solves that. ;)


You can also install Truecrypt on Linux if you prefer.  Personally, I like the dm-crypt/LUKS solution better.

---

### Post by XCan on 2009-11-08
One can install TC on Linux, but as of now, you cannot encrypt your whole system with it after it's installed as you can on Windows using TC.

---

### Post by viking_maniac on 2009-11-08
I almost can't believe what I'm writing here; I've just installed Ubuntu 9.10 with full system encryption! I don't know yet how to celebrate this, but I'll wait until I know for sure that it works properly. It's just that I can't believe it. My dream may have come true here guys; all I wanted was Linux with system encryption; and now the world can end, I don't care. LOL!
 
It seems like it's working! I get prompted with a password field at boot-up, and when I come inside Ubuntu I see an encrypted volume with a lock on it in My Computer, along with the normal file system. 
 
I installed from the alternate install CD and followed this guide to encrypt the system:
[http://oei.yungchin.nl/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://oei.yungchin.nl/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)
 
Well, I guess it's not FULL disc encryption, since /boot/ is unencrypted, but I guess nothing private nor personal gets stored there during a session?
 
This tutorial should have been pinned or at least putted in the help section of Ubuntu. I've wasted so many hours and days since I didn't know about this feature. Even a noob like me can do this, so everyone can install a fully system encrypted Ubuntu system!
 
I'll keep my fingers crossed and hope that this is actually true. :)
 
**rookcifer**, you're _the man_!

---

### Post by FuturePilot on 2009-11-08
> **viking_maniac said:**
> 
 
Well, I guess it's not FULL disc encryption, since /boot/ is unencrypted, but I guess nothing private nor personal gets stored there during a session?
 


Nothing personal gets put there. /boot is strictly for booting the system.

---

### Post by bodhi.zazen on 2009-11-08
This is a recurring discussion on these forums and you will find many similar discussions on this topic in the recurring discussions section.

First, this is the default behaviour by design. The Ubuntu developers prefer to encourage collaboration, thus $HOME is NOT private.

Second, security is a relative term.

No one on these forums is suggesting security == install it and forget it, you need to decide for yourself what security means to you. Often there is a trade off between security and ease of use.

Relative to Windows , Ubuntu is (very much) more secure then a hardened installation of windows. In addition, these security settings are sufficient for most desktop users.

Ubuntu, like windows, can also be hardened.

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

[http://wiki.debian.org/Hardening](http://wiki.debian.org/Hardening)

You can also see the stickies at the top of these forums re: HIDS/NIDS and apparmor.

So I encourage you , and all ubuntu users, to take a more active and proactive approach to security.

---

### Post by ragtag on 2009-11-23
Swap is probably the area you should be most worried about. It's where the system puts stuff in that's in RAM, when it needs the RAM for more important stuff. It can easily contain sensitive information. Encrypting the whole drive, including swap would help.

Though, encrypting your drive only protects your data, if someone gets a hold of your computer (e.g. steals it). And it's highly unlikely that a common thief will know how to, or bother with trying to, extract data from your swap partition.

You also need to think about protecting your data when the computer is turned on. Here Ubuntu does a much better job than windows. Having BitLocker encrypt your whole disk, won't be of much help if some hacker has infected your machine with a back door program. :)

---

### Post by Dr Small on 2009-11-23
> **viking_maniac said:**
> Well, I guess it's not FULL disc encryption, since /boot/ is unencrypted, but I guess nothing private nor personal gets stored there during a session?

/boot can not be encrypted, or else how can the system load the bootloader to boot, without first being decrypted? /boot only holds GRUB and your kernel images. Nothing else. But, by /boot not being encrypted, you are subject to the "Evil Maid" attack, then:
[http://www.schneier.com/crypto-gram-0911.html#9](http://www.schneier.com/crypto-gram-0911.html#9)

---

### Post by bodhi.zazen on 2009-11-23
> **Dr Small said:**
> /boot can not be encrypted, or else how can the system load the bootloader to boot, without first being decrypted? /boot only holds GRUB and your kernel images. Nothing else. But, by /boot not being encrypted, you are subject to the "Evil Maid" attack, then:
[http://www.schneier.com/crypto-gram-0911.html#9](http://www.schneier.com/crypto-gram-0911.html#9)

Well, for the ultra paranoid, put /boot on a flash drive =)

---

### Post by Chunky Dunk on 2009-11-27
There's an interesting way to encrypt swap and /tmp (assuming both have their own seperate partitions) that I haven't seen mentioned yet. 

Basically the way it works is every time your system boots, it encrypts those partitions with a new and random key (that is generated from /dev/urandom) , then formats them for use. When you turn your computer off, that key is lost and what ever was stored in the swap or /tmp is unrecoverable, since those partitions are encrypted with a new key the next time you  start up.

There's a tutorial [here]("http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu"), although it was written for 9.04.

---

### Post by EJeanmaire on 2009-11-27
> **Dr Small said:**
> /boot can not be encrypted, or else how can the system load the bootloader to boot, without first being decrypted? /boot only holds GRUB and your kernel images. Nothing else. But, by /boot not being encrypted, you are subject to the "Evil Maid" attack, then:
[http://www.schneier.com/crypto-gram-0911.html#9](http://www.schneier.com/crypto-gram-0911.html#9)

Theoretically you should be able to encrypt /boot.  The bootloader located in the MBR should be able to de-crypt the /boot partition after the pass-phrase is given.  Correct me if I am wrong here.

---

### Post by Purple Mouse on 2009-11-27
Hi [viking_maniac]("http://ubuntuforums.org/member.php?u=865030"),
I'm a newbie to Ubuntu, installed 9.10, like the idea of disk encryption and included that in the initial setup for logon. Next set about getting the ZTE MF6363 dongle setup, followed a thread ([http://ubuntuforums.org/showthread.php?p=8398657#post8398657](http://ubuntuforums.org/showthread.php?p=8398657#post8398657)) and discovered should have followed another thread. 

So now booting up the system hangs. I went back to the USB bootup, could see the files I changed/added but couldn't access them to delete or modify. 

Is there some way I can at access the original filesystem eg via commands at terminal?

STOP PRESS After hunting around for ideas tried usb boot and identified encrypted drive throught terminal with "df -h" and "sudo su" commands to access and delete/change problem files. Rebooted on original file system. Good as new.

---

### Post by michaelzap on 2009-11-27
I was kind of excited by the new home directory encryption when it became available, but lately I've gone back to LUKS. It just works, and it encrypts everything. I really think that Ubuntu should include this option in the Live CD (as well as providing a guided mode for encrypting just one partition on a multi-OS drive), since to me the easy encryption is one of the things that makes me choose Ubuntu over other distros.

---

### Post by Objekt on 2009-12-10
Can you encrypt the system when installing Ubuntu Netbook Remix 9.10?  I put that distro on one of my netbooks recently but didn't notice the option, but then again I wasn't looking for it.

Please explain about leaving /boot unencrypted.  I have a habit of manually specifying partitions when I install any Linux, so that I end up with the disk arranged as follows:

Partition 1: / (system, including /boot)
Partition 2: swap
Partition 3: /home

Are you saying I should do it more like

Partition 1: /boot
Partition 2: Encrypted volume, containing /, swap, /home

Not sure how I would do that, but it may become obvious at installation time.

Full system encryption seems like a VERY VERY appropriate feature for Ubuntu Netbook Remix.  I can't think of any system more vulnerable to theft, and the subsequent compromise of one's personal information, than a netbook.  You naturally take a netbook with you everywhere, and it would sure make me feel better if I knew the SOB who stole it out of my luggage at the airport, for example, would be unable to see anything on the disk because of encryption.

---

### Post by bodhi.zazen on 2009-12-11
Right now to encrypt the entire system you need to use the alternate CD

[http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

you can not encrypt /boot as the system need access to the kernel to boot ...

You can encrypt your home directory if you install with the deskto CD and that may be sufficient =)

---

