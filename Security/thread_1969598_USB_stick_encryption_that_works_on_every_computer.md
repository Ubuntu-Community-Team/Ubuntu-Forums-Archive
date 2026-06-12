---
title: "USB stick encryption that works on every computer?"
date: 2012-04-30
forum: Security
---

### Post by paranat on 2012-04-30
I have a Datatraveler USB memory stick with sensitive information. I often carry it with myself, and I use it on both my own computer (with Ubuntu 12.04) and public computers with various versions of Windows. I need to encrypt the data, but it appears that the encryption program always needs to be installed on the machine in order for me to be able to access the data.

Is there a way to encrypt data on Ubuntu 12.04, so that I can use my USB memory on public Windows computers that do not have the relevant encryption program installed?

---

### Post by CharlesA on 2012-04-30
Are far as I know you will still need to install the encryption program in order to access the drive.

A better idea would be get another usb stick with nothing on it if you are going to be using it on a public machine.

---

### Post by codemaniac on 2012-04-30
> **paranat said:**
> I have a Datatraveler USB memory stick with sensitive information. I often carry it with myself, and I use it on both my own computer (with Ubuntu 12.04) and public computers with various versions of Windows. I need to encrypt the data, but it appears that the encryption program always needs to be installed on the machine in order for me to be able to access the data.

Is there a way to encrypt data on Ubuntu 12.04, so that I can use my USB memory on public Windows computers that do not have the relevant encryption program installed?

Wont it be wiser to encrypt only sensitive files , instead of the whole usb partition .You can use GPG or anything to encrypt your files .

[http://www.cyberciti.biz/tips/linux-how-to-encrypt-and-decrypt-files-with-a-password.html](http://www.cyberciti.biz/tips/linux-how-to-encrypt-and-decrypt-files-with-a-password.html)

---

### Post by donsy on 2012-04-30
Check out [MySecret]("http://www.di-mgt.com.au/mysecret.html"), I've used it extensively with WindwsXP but don't know if it works with Vista or 7.

The Linux version works well with Ubuntu 32-bit, but if you want to use 64-but you may have to install ia32-libs.

---

### Post by Enigmapond on 2012-04-30
The best way is to use TrueCrypt...get it from their site. This puts an encrypted container on the USB that you move all info into. Because it's cross-platform, it will work on any computer with TrueCrypt installed or it's also portable and can be just on the stick.

---

### Post by HermanAB on 2012-04-30
I use encrypted Zip files.

Everyody has zip utilities.

---

### Post by ottosykora on 2012-05-02
use truely hardware encrypted usb stick.

Yo can use the something I have:
[http://www.corsair.com/usb-drive/flash-padlock-2-usb-drive.html](http://www.corsair.com/usb-drive/flash-padlock-2-usb-drive.html)
which enables you to enter the password on the miniature keyboard
(my personal solution for number of yoears now)

or you spend some more moeney and use :
[https://store.ironkey.com/](https://store.ironkey.com/)

which has the ability to enter the password on windows, linnux, mac even without the need of special communication software on the host computer


The use of any software solution is either possible only on dedicated hardware (controller of the stick) or need additional software to be able to use it properly and this software needs to be installed on the host and will therefore need admin rights to do so.

Truecrypt without the installed driver software on the host is not much comfortable then any zip with encryption. The zip software can be placed however on the stick itself, the key is then just the passphrase.

The is no universal software solution and probably will never be as one has allways to find a way to enter the password to the usb stick somehow.

---

### Post by rookcifer on 2012-05-02
> **donsy said:**
> Check out [MySecret]("http://www.di-mgt.com.au/mysecret.html"), I've used it extensively with WindwsXP but don't know if it works with Vista or 7.

The Linux version works well with Ubuntu 32-bit, but if you want to use 64-but you may have to install ia32-libs.

Bad idea.  For one, it is not open-source nor GPL.  For two, it uses Blowfish when it could be using AES (this implies the software hasn't been updated in a while).  And three, it does nothing GnuPG cannot do and GnuPG is already included in Ubuntu.

ottosykora said:

> use truely hardware encrypted usb stick.

Yo can use the something I have:
[http://www.corsair.com/usb-drive/fla...usb-drive.html](http://www.corsair.com/usb-drive/fla...usb-drive.html)
which enables you to enter the password on the miniature keyboard
(my personal solution for number of yoears now)

Also a bad idea.  These hardware solutions cannot be trusted.  They have a [track record]("https://www.zdnet.com/blog/hardware/encryption-busted-on-nist-certified-kingston-sandisk-and-verbatim-usb-flash-drives/6655") of being rather poor.  So poor in fact that someone should have lost their job.

---

### Post by ottosykora on 2012-05-02
> **rookcifer said:**
> 

ottosykora said:



Also a bad idea.  These hardware solutions cannot be trusted.  They have a [track record]("https://www.zdnet.com/blog/hardware/encryption-busted-on-nist-certified-kingston-sandisk-and-verbatim-usb-flash-drives/6655") of being rather poor.  So poor in fact that someone should have lost their job.

well this what is described here has not much to do with the real hardware encryption I mentioned.
There is lot of devices around which employ the encryption done by the firmware of the controller, but the whole key process is done externally.
I do not consider this as hardware encryption.
This was the  problem with U3 devices for example. Encryption seemed OK first, but it came out that attacks were too simple on the communication between the stick and the keyboard of the computer and so finaly it became too simple to get onto the so called encrypted contents.

So simple devices will use some form of local entry, like my padlock2 or have such complex communication set up that so far no attacks are known at the current level of knowledge and technology.
But when comparing 10$ to 300$, well there must not be, but might be some difference.



BTW: also padlock2 has some flaw. OK it was cleared by now, but was discovered some 6 months after launching the product. Meanwhile one has to initiate the password twice and then all is fine again.

There are similar devices with integrated finger sensor too.

There used to be some nice 3DES hardware encrypted external hard drives on the market. Yes it was 3DES, but unfortunately every time the same start vector. Finding this out is probably not so big effort.

So yes I agree, not everything called hardware encryption is worth it.

But as there is no and will be no universal software solution, some hardware solution might be only alternative.

---

### Post by beboylips on 2012-05-04
Hey,

Use TrueCrypt portable, put it alongside encrypted containers on your USB stick. No need to install, just run it.

[http://www.truecrypt.org/docs/?s=truecrypt-portable](http://www.truecrypt.org/docs/?s=truecrypt-portable)

-Beboy

---

### Post by ottosykora on 2012-05-04
> **beboylips said:**
> Hey,

Use TrueCrypt portable, put it alongside encrypted containers on your USB stick. No need to install, just run it.

[http://www.truecrypt.org/docs/?s=truecrypt-portable](http://www.truecrypt.org/docs/?s=truecrypt-portable)

-Beboy

unfortunately truecrypt can not be portable as it needs admin rights to write the drivers , so therefore it is one of those not universal useful software solutions.

It can access the container however, but will then work similar to encrypted zip file or similar.

from truecrypt site:
You need administrator privileges in order to be able to run TrueCrypt in portable mode

---

### Post by Catalyph on 2012-08-28
this is possible.

You would have to store an encryption key file on the USB disk, then in your disk encryption in ubuntu you make a second ke***** pointing to the UUID of that USB disk and the keyfile, when the USB disk is in the machine the full disk encryption will use the file on it to decrypt the rest of the disk.

Downside is that anyone that gets the usb stick can copy your key file.

---

### Post by ottosykora on 2012-08-29
> **Catalyph said:**
> this is possible.

You would have to store an encryption key file on the USB disk, then in your disk encryption in ubuntu you make a second ke***** pointing to the UUID of that USB disk and the keyfile, when the USB disk is in the machine the full disk encryption will use the file on it to decrypt the rest of the disk.

Downside is that anyone that gets the usb stick can copy your key file.

well yes, might work on ubuntu computers, but not on other os like windows etc. Encryption software itself would have to be present.

---

