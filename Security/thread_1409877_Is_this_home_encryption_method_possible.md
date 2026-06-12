---
title: "Is this /home encryption method possible"
date: 2010-02-18
forum: Security
---

### Post by ushills on 2010-02-18
I would like to know if this is possible, 

I want to encrypt each users /home folder and store the unlock key on a plugged in USB stick.

When the user logs in I want the unlock key, encrypted with the users login password to unlock their home folder.

Importantly, if the /home partition is moved to another machine I should be able to open the /home folders again by just plugging in the usb stick.

Ideally, I would also like a user called backup to be able to unlock all /home folders when running a backup script.

Can this be done?

---

### Post by HermanAB on 2010-02-18
Howdy,

Most probably yes.  LUKS can handle multiple passwords and you can save the keys wherever you want.  However, you may have to make each user home a partition.

See this for some ideas:
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)

---

### Post by ushills on 2010-02-18
> **HermanAB said:**
> Howdy,

Most probably yes.  LUKS can handle multiple passwords and you can save the keys wherever you want.  However, you may have to make each user home a partition.

See this for some ideas:
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)


This would work and I could give each user a key that decrypted the whole /home partition and also therefore disable any if they got lost.

I would however prefer to use the built in encryption cryptfs that is included with 9.10 and in that case each user would have there own encrypted /home folder with a key.

I cannot find out how to do this however.

---

