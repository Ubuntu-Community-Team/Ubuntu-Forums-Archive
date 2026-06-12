---
title: "is it possible to password protect a ext hard drive??"
date: 2009-07-02
forum: Security
---

### Post by Ichindar on 2009-07-02
hey all

i have a 1TB external hard drive that i keep all my documents on, some of them are sensitive in nature, bank details etc.

i was wondering is there any way or program i can pass word protect the hard drive so it asks for a password when its plugged into any machine and cant be accessed until you enter the password?

---

### Post by Boondoklife on 2009-07-02
Well the only way I could see this would be software or hardware based:

[INDENT]Hardware would need to have the actual drive support this in some way, maybe external finger print, etc.

Software would be something like truecrypt.
[/INDENT]The problem is going to be Hardware is going to be costly and software may have issues if you are not an admin on the computer you plug it into. 

Hope it helps

---

### Post by HermanAB on 2009-07-02
You sure can.  

You can even make it compatible with both Linux and Windoze:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)
[http://aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf](http://aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf)

---

### Post by aysiu on 2009-07-02
Encryption is the way to go. For that, I would highly recommend TrueCrypt. It's also cross-platform (available for Mac, Windows, and Linux).

---

### Post by Boondoklife on 2009-07-02
Just remember though, with either software suggestions so far, you will need admin rights on the windoes box or have an admin install the software!

---

### Post by aysiu on 2009-07-02
> **maletek said:**
> Just remember though, with either software suggestions so far, you will need admin rights on the windoes box or have an admin install the software!
Even if you use Traveler Mode?
[http://www.truecrypt.org/docs/?s=truecrypt-portable](http://www.truecrypt.org/docs/?s=truecrypt-portable)

---

### Post by Boondoklife on 2009-07-02
> **aysiu said:**
> Even if you use Traveler Mode?
[http://www.truecrypt.org/docs/?s=truecrypt-portable](http://www.truecrypt.org/docs/?s=truecrypt-portable)

Yup, > You need administrator privileges in order to able to run TrueCrypt in traveler mode (for reasons, see the chapter [Using TrueCrypt Without Administrator Privileges]("http://www.truecrypt.org/docs/administrator-privileges")). 

---

