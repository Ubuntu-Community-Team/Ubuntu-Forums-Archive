---
title: "Small portable encrypt/decrypt programme"
date: 2011-03-31
forum: Security
---

### Post by mastablasta on 2011-03-31
I was wondering if any free, small, portable, cross platform programme exists for encrypting/decrpyitng simple txt files?
 
I know a couple of small ones for windows systems (nosee, dscrypt) but i wonder if there is any i could use on both linux and windows OS. the idea is to be able to carry it on USB key and the programme (or probably there will have to be 2 versions of it) would run either on windows or linux os and i could decrypt and encrypt the file if i needed to. no matter on what system i plug the USB key to.

---

### Post by Megaptera on 2011-03-31
Would TrueCrypt be any use as it is cross-platform?
This from their FAQ:
How can I use TrueCrypt on a USB flash drive?
"Create a TrueCrypt file container on the USB flash drive (for information on how to do so, see the chapter Beginner's Tutorial, in the TrueCrypt User Guide). If you leave enough space on the USB flash drive (choose an appropriate size for the TrueCrypt container), you will also be able to store TrueCrypt on the USB flash drive (along with the container &#8211; _not in_ the container) and you will be able to run TrueCrypt from the USB flash drive (see also the chapter Portable Mode in the TrueCrypt User Guide)."

---

### Post by KegHead on 2011-03-31
Hi!

I use Truecrypt w/4gb usb stick w/no problems.

Enjoy!

KegHead

---

### Post by The Cog on 2011-03-31
gpg wil lprobably do it - I know it's available for Linux, and a quick google for "gpg for windows" turned up this link: [http://www.gpg4win.org/](http://www.gpg4win.org/)

---

### Post by mastablasta on 2011-04-01
no, gpg has this:
 
> 
[LEFT][SIZE=3][FONT=NimbusRomNo9L-Regu][SIZE=3][FONT=NimbusRomNo9L-Regu][SIZE=2]You can load and install Gpg4win from the Internet or a CD.[/SIZE] [SIZE=2]To do this, **you will need administrator**[/SIZE][/FONT][/SIZE][/LEFT]
[FONT=NimbusRomNo9L-Regu][SIZE=2]**rights** to your Windows operating system.[/SIZE][/FONT]
[/FONT][/SIZE]
 
Means you need to actually install it somewhere. It has a nice manual though so i just might use it for home use... :-)
 
True crypt as i know also needs to be installed. it's not small and a little bit complicated to me.
 
What i am talking about here is simple small programmes. the ones i already mentioned have less than 100kB. they can encrypt mostly txt files only. yet they don't need any special instalation or admin permission. and for that reason you can use them anywhere where windows is installed.
 
Imagine you are on a public computer (possibly even kiosk mode to protec users form installing any viruses...) in a cybercafe and all you want to do is remember certain password to access your picassa photos. If computer is windows you would just stick the key in unencrypt the txt file, use the pass and then encrpy it back.
 
No what i wonder is if there is anyhting like that in linux world that also has a Windows alternative.

---

### Post by bodhi.zazen on 2011-04-01
you can run gpg (and most things) from a flash drive, the problem is that most of the encryption tools (including truecrypt) require administration privileges on Windows.

I think bcrypt is a potential solution:

[http://bcrypt.sourceforge.net/](http://bcrypt.sourceforge.net/)

another potential would be FreeOTFE - it uses LUKS and is cross platform.

[http://www.freeotfe.org/download.html](http://www.freeotfe.org/download.html)

See also : [http://www.mvoyager.com/cd-usb-encryption/howto/virtual-drive-letters-under-limited-user-account.shtml](http://www.mvoyager.com/cd-usb-encryption/howto/virtual-drive-letters-under-limited-user-account.shtml)

---

### Post by BkkBonanza on 2011-04-01
If you just want to store small bits of text and passwords then use **keepassx**. It is designed exactly for this, can be used from a flash stick, and is cross platform. It is primarily for storing passwords but it does also allow for storing chunks of text too. You can tag a lot of info to each entry and find it immediately, and it also has some options for auto-paste or just copy/paste. And of course it's all stored encrypted.

I've used it while travelling in Asia by just pluging in my usb stick and running the app. You can put both the linux and windows binary on the stick. I see they even have it for some phones too.

Oh, and as a bonus it has a nice password generator too.

---

### Post by Irihapeti on 2011-04-01
There is also KeePassJ2ME for Java-capable cellphones. The keepassx data file (at least, the Ubuntu 10.04 version) is compatible with KeePassJ2ME, so I just sync the files between my two Ubuntu machines and my cellphone. Very convenient.

---

### Post by steven.smith on 2011-04-01
I've always used Truecrypt. You can download the portable version and create a volume container to put on the flash drive. It is probably the best and fastest way to encrypt your contents.

---

### Post by mastablasta on 2011-04-04
> **BkkBonanza said:**
> If you just want to store small bits of text and passwords then use **keepassx**. 
 
This one seems it will do it. I had a quick look through it...
 
> 
I've used it while travelling in Asia by just pluging in my usb stick and running the app. 
 
Funny, I also need it for that area and to be able to access some things from their cybercafes haven't gone there in a while so i think/hope another trip will be next year (fingers crossed).

---

