---
title: "OpenPGP card, other cards, etc"
date: 2010-01-24
forum: Security
---

### Post by j_arquimbau on 2010-01-24
Hi! I've been having a look on the net to secure smartcards and I've some doubts. I've been very interested in the OpenPGP card ([http://shop.kernelconcepts.de/product_info.php?cPath=1_26&products_id=42](http://shop.kernelconcepts.de/product_info.php?cPath=1_26&products_id=42)) or the card that the "Free Software Foundation Europe" ([http://wiki.fsfe.org/FellowshipSmartCard?action=show&redirect=Crypto_Card](http://wiki.fsfe.org/FellowshipSmartCard?action=show&redirect=Crypto_Card)) gives you when you become a member of the fellowship. Now, my question:

Is it possible to buy those kind of smart cards myself anywhere else. If that's the case, where? what are the name of those cryptographic smart cards? will it be compatible with ubuntu? How would you setup them to, for instance, only having three pin-insertion attemps?

Thank you all!

---

### Post by BkkBonanza on 2010-01-24
I haven't used the smart card but I followed your link and read up on it.
It seems pretty expensive. Why wouldn't you not just use a usb flash stick? You wouldn't need a special reader, and you can store keys on one and plug it in to use on any usb port. You still need to know the pin (passphrase) to get at the secret keys.

I'm just wondering what's special about the cards that they need to charge 16 euros for them?

---

### Post by j_arquimbau on 2010-01-24
What I've read is that if you put them on a flash drive, you can access them and copy them, even if you don't know the passphrase, whereas in the smartcard you cant. They might have got the passphrase by other methods like staring at you when you tipe it.
What I find insecure of the flash units is that you must import the key to your computer. That way, even if you erase the key, it might be recuperable from swap, RAM memory or even the hard drive so you should zero up the free space in computer after finishing with the key, which isn't practical if you want to use the key often.
I know that what I'm saying is quite paranoid and that it might not make much sense but... that's me! ;)
Thank you for your answer!

---

### Post by BkkBonanza on 2010-01-24
Ok. Wasn't sure about that. I would think you could use a flash drive without it being imported but I haven't tried. I have used it for my Ubuntu encrypted home key. 

I checked on Wikipedia about the Openpgp card and it says it's based on a "BasicCard" and that they are only made by ZeitControl. So I guess it's pretty limited then in how you can get one. See,

[http://en.wikipedia.org/wiki/OpenPGP_card](http://en.wikipedia.org/wiki/OpenPGP_card)
[http://en.wikipedia.org/wiki/BasicCard](http://en.wikipedia.org/wiki/BasicCard)

There is also a spec on GnuPG page that defines what the card contains and how it's programmed etc.

[http://www.g10code.com/docs/openpgp-card-2.0.pdf](http://www.g10code.com/docs/openpgp-card-2.0.pdf)


BTW the ZeitControl site says you can get BasicCards for about 1 euro each in small qty. You would have to use the specs to program them though.

[http://www.basiccard.com/](http://www.basiccard.com/)

---

### Post by j_arquimbau on 2010-01-24
Thank you, I thought BasicCard meant "Generic Card"  :o!! That was the reason I've open this thread!

---

