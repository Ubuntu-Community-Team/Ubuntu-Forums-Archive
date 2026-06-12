---
title: "Searching good voip phone? help."
date: 2009-10-31
forum: The Cafe
---

### Post by forcecore on 2009-10-31
I have used almost 5 years Picophone on windows but can anyone tell me where i can get some very light ip phone (open source), i know Ekiga direct call but it is quite massive and no crypto.

Features that should be:
*Dircect ip call must have
*Light of resources (built with qt4 or wxwidgets)
*Encryption is optional (hamachi covers that)

---

### Post by forcecore on 2009-11-03
Bunping in hope that some ip phones expert will see this.

---

### Post by forcecore on 2009-11-07
Bumping, any voip experts around here? suggestions is there some lightweight phone able to directly make contact to IP?

Currently that PicoPhone is very buggy on new platforms like Ubuntu with wine and Win 7 so calling is quite terrible because of audio codec bugs and hangups, on Win XP it worked good but XP is forgotten now.

UPDATE:
Discovered phone VoIPerized but it is windows only and closed source and is quite old but features is similar to my needs.

---

### Post by gradinaruvasile on 2009-11-07
Linphone is the most stable (not feature full but best working) VoIP app i have ever seen in Ubuntu. But its Gtk based... It has direct IP to IP capability.

Twinkle seems to be good. Its Qt/Kde based also. It also has direct IP to IP capability.

Sflphone is lightweight ([http://www.sflphone.org/](http://www.sflphone.org/)) and it has KDE version too, debian/ubuntu repository. It has direct IP to IP capability and encryption (never tried the encryption though).

Zoiper is another good SIP/VoIP app. Not or KDE/Gtk but lightweight. But AFAIK it doesnt have direct IP to IP capability.

---

### Post by forcecore on 2009-11-07
Thanks, SFLphone is greatest i have seen currently but sadly it wont work on Windows and friend uses Windows only.

I watch Linphone too in future how it develops but currently it is not usable because of system tray and some other feature for everyday use.

Currently my 2 canditates is:
1: Kiax
2: Ekiga
3: Voiperized (all features what is critical except no encryption, quite old, windows only and closed source)

Suggestions still wanted.

---

### Post by gradinaruvasile on 2009-11-07
You do not need to have the same program on both computers. Just support the same features like encryption (not sure, maybe u do need the same prog for this) and direct IP calls.

Also be aware that Ekiga has problems if u have multiple network interfaces. I cannot use it cause i have 4 interfaces at work and it just doesnt work.
Kiax has apalling sound quality on my computers (tried on 3, crackling/skipping sound).

I was talking about linphone 3 - this has tray icon. I use 3.2.1, the best sound quality, works perfectly with VPN/NAT. I had to compile it though - made a .deb file with checkinstall (on Ubuntu 9.04 and 8.10). Linphone on Windows looks ugly as hell, but works nonetheless.

---

### Post by gradinaruvasile on 2009-11-07
Also u might check this out:

[http://en.wikipedia.org/wiki/List_of_SIP_software](http://en.wikipedia.org/wiki/List_of_SIP_software)

---

### Post by forcecore on 2009-11-08
I found finally superior ip phone SpeakFreely, it is quite old but very robust and encrypted too. [https://sourceforge.net/projects/speak-freely/](https://sourceforge.net/projects/speak-freely/)

Linphone caused lot problems it dropped very often and it transmitted always (no silence detection/voice activation).

I look forward Kiax 2 development too maybe they can make it better too.

---

### Post by rifak on 2009-11-08
I hear that Ooma is supposed to be amazing. you can find them at best buy.

[http://www.ooma.com/](http://www.ooma.com/)

[http://www.bestbuy.com/site/ooma+-+Telo+DECT+6.0+Cordless+VoIP+Handset+for+ooma+Telo+Home+Phone+Service+-+Black/9511469.p?id=1218117369182&skuId=9511469&st=ooma&cp=1&lp=2](http://www.bestbuy.com/site/ooma+-+Telo+DECT+6.0+Cordless+VoIP+Handset+for+ooma+Telo+Home+Phone+Service+-+Black/9511469.p?id=1218117369182&skuId=9511469&st=ooma&cp=1&lp=2)

---

### Post by forcecore on 2009-11-09
Too bad that i cannot moderate own threads.

btw current tests is very good with SpeakFreely it works very well, yesterday i used it 3 hours without any error and got it working under wine too in 9.10.

---

