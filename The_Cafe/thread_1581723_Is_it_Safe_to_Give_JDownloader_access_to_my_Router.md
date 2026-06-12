---
title: "Is it Safe to Give JDownloader access to my Router?"
date: 2010-09-25
forum: The Cafe
---

### Post by navneeth on 2010-09-25
Hi. If you know about the program [JDownloader](http://jdownloader.org/), you might know that it can be configured to change your IP address, if you use a dynamic one. To achieve this, one must provide the program with the username and password to the router's homepage. Not being very knowledgeable about computer networks, I would like to ask if this is a safe thing to do? By providing that information, will a third party be able access my computer (in principle) without my knowing it?

---

### Post by DrMelon on 2010-09-25
It depends if JDownloader uploads any of that information elsewhere - but in any case, most routers disable external login connections unless specified in the router's settins.

---

### Post by navneeth on 2010-09-25
> **DrMelon said:**
> It depends if JDownloader uploads any of that information elsewhere - but in any case, most routers disable external login connections unless specified in the router's settins.

Thanks. I'll check the settings for external logins.

---

### Post by roggenschrotbrot on 2010-09-25
you can always set an external reconnect-script to be executed by jdownloader, so you don't have to pass your routers login details to the program if you don't trust the developers.

---

### Post by navneeth on 2010-09-25
> **roggenschrotbrot said:**
> you can always set an external reconnect-script to be executed by jdownloader, so you don't have to pass your routers login details to the program if you don't trust the developers.

Sounds good. If I'm not mistaken, there is a tab to run external commands. I'll look into that, as well. Thank you.

---

### Post by perspectoff on 2010-09-25
Can I have access to your router, too? I promise I'm trustworthy and will only spoof your IP address and play man-in-the-middle for honorable purposes.

No honorable program needs access to your router. That's what proxies are for, and an honorable program that really wants to redirect your traffic in some way will use a proxy (like Squid) instead. 

Just say no.

---

### Post by CharlesA on 2010-09-25
> **perspectoff said:**
> can i have access to your router, too? I promise i'm trustworthy and will only spoof your ip address and play man-in-the-middle for honorable purposes.

No honorable program needs access to your router. That's what proxies are for, and an honorable program that really wants to redirect your traffic in some way will use a proxy (like squid) instead. 

Just say no.

+1.

---

### Post by Jiaz on 2010-09-26
JDownloader can reconnect your Router to get a new IP. With a new IP you can avoid waittimes/traffic limits as free user. JDownloader can talk to the router to get a new IP.  If you dont want this, then just disable reconnect or setup external reconnect method and write it yourself.  Why not check out the sourcecode?  Why not build it yourself from sourcecode? If you don't trust JDownloader, why use it at all?  greetings jiaz

---

