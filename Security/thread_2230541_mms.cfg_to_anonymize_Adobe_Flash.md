---
title: "mms.cfg to anonymize Adobe Flash"
date: 2014-06-19
forum: Security
---

### Post by Nobody Nessie on 2014-06-19
Hello !

I tried by several ways to anonymize a litte bit my Adobe Flash player (if not, I will keep it off, and that's it). I create a directory /adobe in /etc and put in the following file, named mms.cfg with the following lines inside  (in /etc/adobe/mms.cfg) :

```
AVHardwareDisable=1
DisableDeviceFontEnumeration=1
DisableSockets=1
ThirdPartyStorage=0
LocalStorageLimit=1
AssetCacheSize=0
FileDownloadDisable=1
FileUploadDisable=1
LegacyDomainMatching=1
```

But it still does not work. My flash cookies are still enable and my fonts number readable. I did the same thing on my Windows 7 and it works perfectly. Any idea ? Thank you !

---

### Post by Nobody Nessie on 2014-06-20
Sorry, I do make questions and answers ! :D 

For this to work, your just have to add the following line in your firefox apparmor profile :

```
 /etc/adobe/* r,
```

This is what happens when we "apparmor'ed" everything ! :D

---

### Post by cogset on 2014-06-26
I'm curious,what do these lines do differently  from disabling some options in the adobe flash control panel (disable offline storage,block camera/microphone access,block peer-to-peer connectivity) and/or using an extension like BetterPrivacy in Firefox to control LSOs?

---

### Post by vasa1 on 2014-06-26
A little on the topic here: [http://askubuntu.com/questions/404637/adobe-flash-player-privacy-settings](http://askubuntu.com/questions/404637/adobe-flash-player-privacy-settings) although it doesn't address cogset's specific question.

---

### Post by cogset on 2014-07-02
Very interesting nonetheless,seems like there's more than one way in Linux to keep (or at least try to keep..) the flash plugin under control.

---

