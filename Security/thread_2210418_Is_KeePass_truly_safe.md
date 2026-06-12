---
title: "Is KeePass truly safe?"
date: 2014-03-10
forum: Security
---

### Post by JonasDeMoor on 2014-03-10
Hello,

I want to use a password manager, preferably a open source one, like KeePass. But as I'm paranoid about literally ALL things, I was wondering if this programme is safe at all to use? 

When talking about "safe", I mean: can this programme send data to cyber criminals or others? I know it's open source, so everyone can look into the source code, but I'm still worried. 

I also intend to use this programme on Windows; is [keepass.info]("http://keepass.info") the legitimate, official website?


Thank you very much in advance.

---

### Post by bapoumba on 2014-03-10
I use KeepassX [https://www.keepassx.org/](https://www.keepassx.org/)
Works on all platforms. if you are really concerned, in addition of a password, you can set it up to require a file be present on the device you open the db from.
I use it on both Linux and Mac OSX, there is a windows version.

---

### Post by texpat on 2014-03-10
Unless you are willing and able to check the source code for yourself you're pretty much stuck with trusting it as is. The keepass.info site is linked from sourceforge which makes it legit to me. A 'whois' on the URL looks OK, too.

So if your data and comms are as sensitive as mine - as in NOT - you're good to go. If they are really, really sensitive, then maybe someone else here may have pointers for you.

---

### Post by JonasDeMoor on 2014-03-12
Hello,

Thank you for the replies. So this won't contain any spyware since it's hosted on sourceforge? I'd like to hear some other opinions/experiences too.

---

### Post by thnewguy on 2014-03-12
You won't know it is safe for sure unless you either audit the code or monitor your network traffic. that being said, KeePass has been around for some time now. If it were doing things like calling home someone probably would have noticed by now.

---

### Post by HermanAB on 2014-03-14
Howdy,

Let me put it this way:
Keepass is most probably safe, since it is an old and active project, but if your computer is compromised then all bets are off.
However, if you only use Linux and Mac with Keepass, then you are most probably safe.

I use it with two databases: The common things I need on all my devices, and the sensitive things I need for work, which are only accessible on a few devices.

A good way to make Keepass accessible on all your devices, is via Dropbox, Copy, Spideroak or similar public FTP services.  Simply put the database in the dropbox (or other) folder and it will be synched to all machines and cell phones you need it on.  It really works like a charm.

---

### Post by phedon on 2014-04-22
Sometime ago (2010), Keepass has been reviewed and certified by French national Information Security org. Security audit here (in French...):
[http://www.ssi.gouv.fr/fr/produits-et-prestataires/produits-certifies-cspn/certificat_cspn_2010_07.html](http://www.ssi.gouv.fr/fr/produits-et-prestataires/produits-certifies-cspn/certificat_cspn_2010_07.html)

---

### Post by bapoumba on 2014-04-22
> **phedon said:**
> Sometime ago (2010), Keepass has been reviewed and certified by French national Information Security org. Security audit here (in French...):
[http://www.ssi.gouv.fr/fr/produits-et-prestataires/produits-certifies-cspn/certificat_cspn_2010_07.html](http://www.ssi.gouv.fr/fr/produits-et-prestataires/produits-certifies-cspn/certificat_cspn_2010_07.html)
Certified on Windows, but certified nonetheless :)

---

### Post by HermanAB on 2014-04-23
Note that if you are truly paranoid about Keepass leaking data, then you should not be using Ubuntu in the first place.  So, first install Redhat Linux, then use SELinux to isolate KeepassX...

---

