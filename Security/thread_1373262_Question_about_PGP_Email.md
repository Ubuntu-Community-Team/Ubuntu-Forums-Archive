---
title: "Question about PGP Email"
date: 2010-01-05
forum: Security
---

### Post by Atilliar on 2010-01-05
What is the preferred email client that integrates PGP?  And does anyone know of a PGP program that can be used with Vista?

Thanks.

---

### Post by rookcifer on 2010-01-05
> **Atilliar said:**
> What is the preferred email client that integrates PGP?  And does anyone know of a PGP program that can be used with Vista?

Thanks.

For Gnome, you can use Thunderbird with the Enigmail plugin.  For KDE, you can use Kmail and it's native PGP support (that's what I use).  Google "Ubuntu GPG" and you should run across the official documentation showing how to set this up.

For Vista, I don't know -- I don't use Windows and don't care to.  However, I imagine Thunderbird's Enigmail will work with Vista just as it does on Linux.

---

### Post by kevdog on 2010-01-05
Do you want a client or web based email?

---

### Post by Atilliar on 2010-01-06
A client.  I am currently using evolution but was wondering if something was better.  What is better about Thunderbird?  I was asking about a windows PGP program for a friend who uses vista (though I'm trying to talk him into Linux).

And thanks for the info about Enigmail I wasn't aware of it (one major reason I wasn't using Thinderbird).

---

### Post by BkkBonanza on 2010-01-06
Enigmail works for TB on Windows too. I prefer TB to both Outlook and Evolution. 

All these mail clients (I believe) also support using certificates for signing /encryption. This is more widely compatible but the thing I find annoying about using certificates is that you need to get a new one each year (if you use a trusted CA). You can get one free at startssl.com for example but each year they expire.

If you're only concerned with a few friends then you can make your own CA and create certificates with long expiries. Then these can be used with most email clients with no additional plugins or pgp needed. The Ubuntu repos have tinyCA that has an easy to use gui.

---

### Post by Hallvor on 2010-01-06
> **Atilliar said:**
> What is the preferred email client that integrates PGP?  And does anyone know of a PGP program that can be used with Vista?

Thanks.

Sylpheed works with GPG in both GNU/Linux and Vista. 

[http://sylpheed.sraoss.jp/en/download.html](http://sylpheed.sraoss.jp/en/download.html)

---

