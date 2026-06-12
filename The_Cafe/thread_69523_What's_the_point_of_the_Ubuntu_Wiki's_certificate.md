---
title: "What's the point of the Ubuntu Wiki's certificate?"
date: 2005-09-27
forum: The Cafe
---

### Post by jnoreiko on 2005-09-27
Every time I go to the Ubuntu wiki I get a message from firefox about 'unable to verify the site certificate' or something. There's also something about it being expired.

If it's expired, can someone update it? 
I've never really understood what these things are meant to be.
What's the point of it other than annoying people? Can we just have it removed?

---

### Post by Kvark on 2005-09-27
All websites such as the Ubuntu wiki in this case that uses an encrypted connection are expected to have a certificate from VeriSign or a smiliar company. The certificate is just an assurance from VeriSign or whoever issued it that the Ubuntu wiki really is the Ubuntu wiki.

The only ways for the wiki to get rid of that warning is to either stop using encryption or pay a certificate issuer to ensure that the wiki really is the wiki.

---

### Post by Arktis on 2005-09-27
I have always found this a little annoying as well, and it seems to be pretty unprofessional considering that it's been this way for a very long time now.

---

### Post by xmastree on 2005-09-27
All you need to do is select the 'accept permanently' option, and it shouldn't bother you again.

---

### Post by jdong on 2005-09-27
It's a minor annoyance; but shouldn't Mr. Shuttleworth get special perks from his dealings with his previously-owned CA? ;)

---

### Post by NeoSNightmarE on 2005-09-27
I just acccepted permanantly. Hasn't bothered me since :)

---

### Post by stimpack on 2005-09-27
These certificates... are very annoying not just this site but all these sites you have to accept for... are these proofs of security really worth it? I mean if I type ubuntulinux.org im pretty sure its really ubuntulinux.org because hmm I typed it. Maybe its going over my head, wouldnt be the first time.

---

### Post by DJ_Max on 2005-09-27
[QUOTE=stimpack]These certificates... are very annoying not just this site but all these sites you have to accept for... are these proofs of security really worth it? I mean if I type ubuntulinux.org im pretty sure its really ubuntulinux.org because hmm I typed it. Maybe its going over my head, wouldnt be the first time.[/QUOTE]
You don't understand what a SSL cert is then. 

[http://en.wikipedia.org/wiki/Secure_Sockets_Layer](http://en.wikipedia.org/wiki/Secure_Sockets_Layer)

Also, if you used Windows, you should know what "browser hijacking" is.

The wiki is using an unsigned SSL cert. It's still secure, just not recognized by any browser, since it hasn't been signed by any major company like Versign or Thawte.

---

### Post by NeoSNightmarE on 2005-09-27
Interesting read. I didn't know that SSL was able to handle that many encryption methods such as Triple DES and RC4. Most of the ones that I see have AES. Thanks for the link.

---

### Post by David Marrs on 2005-09-27
You only have to accept the certificate yourself if its authenticity can't be established. If the certificate was valid, the browser would trust the site automatically, but because the certificate is *not* valid, the browser asks you first if you want to trust the site yourself, because the certificate authority won't.

In the case of Ubuntulinux.com, I know their site and therefore trust it anyway, but if I were about to make a purchase from an on-line shop I hadn't used before, I'd want to be sure that it was trusted by a 3rd party. If it wasn't then I wouldn't buy from that shop.

Ubuntulinux.com simply need to renew (or remove) their certificate.

---

### Post by DJ_Max on 2005-09-27
[QUOTE=NeoSNightmarE]Interesting read. I didn't know that SSL was able to handle that many encryption methods such as Triple DES and RC4. Most of the ones that I see have AES. Thanks for the link.[/QUOTE]
No problem.

> It's a minor annoyance; but shouldn't Mr. Shuttleworth get special perks from his dealings with his previously-owned CA?
You would hope so, but once you sell a company, you usually have no relation to it anymore.

---

### Post by Kvark on 2005-09-27
[QUOTE=DJ_Max]You don't understand what a SSL cert is then. 

[http://en.wikipedia.org/wiki/Secure_Sockets_Layer](http://en.wikipedia.org/wiki/Secure_Sockets_Layer)

Also, if you used Windows, you should know what "browser hijacking" is.

The wiki is using an unsigned SSL cert. It's still secure, just not recognized by any browser, since it hasn't been signed by any major company like Versign or Thawte.[/QUOTE]
That wiki page does not give any reason at all for why websites are expected to have a certificate from a 3rd party instead of one the website itself issued if it uses encryption. Which is what this particular warning is about. This wikipage gives the reasons for this warning:

[http://en.wikipedia.org/wiki/Public_key_certificate](http://en.wikipedia.org/wiki/Public_key_certificate)

[QUOTE=David Marrs]You only have to accept the certificate yourself if its authenticity can't be established. If the certificate was valid, the browser would trust the site automatically, but because the certificate is *not* valid, the browser asks you first if you want to trust the site yourself, because the certificate authority won't.

In the case of Ubuntulinux.com, I know their site and therefore trust it anyway, but if I were about to make a purchase from an on-line shop I hadn't used before, I'd want to be sure that it was trusted by a 3rd party. If it wasn't then I wouldn't buy from that shop.

Ubuntulinux.com simply need to renew (or remove) their certificate.[/QUOTE]
That is like trusting everyone who has a drivers licence. The drivers licence just tells you that the person really is who he claims to be. It does not tell you if the person is trustable or not. These certificates work in the same way.

---

### Post by DJ_Max on 2005-09-27
[QUOTE=Kvark]That wiki page does not give any reason at all for why websites are expected to have a certificate from a 3rd party instead of one the website itself issued if it uses encryption. Which is what this particular warning is about. This wikipage gives the reasons for this warning:

[http://en.wikipedia.org/wiki/Public_key_certificate](http://en.wikipedia.org/wiki/Public_key_certificate)
[/QUOTE]
Umm, yeah, I know, I wasn't trying to show why websites are expected to have signed certs. I was trying to explain to stimpack what an SSL was.

---

### Post by az on 2005-09-27
[QUOTE=jdong]It's a minor annoyance; but shouldn't Mr. Shuttleworth get special perks from his dealings with his previously-owned CA? ;)[/QUOTE]

I think it has something to do with contractual agreements that have to do with him selling off his business.  Kinda like if I build up a lemonade business and sell it to you, you ask me not to start up another lemonade business the next day and steal away all your (my former) customers from you.

---

### Post by blastus on 2005-09-27
There's no such thing as an unsigned certificate. All certificates have to be signed one way or another. The Wiki certificate is what is known as a self-signed certificate. I've used self-signed certificates before (for Java Web Start) and they are handy when you need a certificate but you do not or cannot pay the thousands of dollars it costs for a CA to sign one.

---

### Post by wmcbrine on 2005-09-27
Why use encryption on that site, anyway? AFAICT there's nothing secret/private there.

---

### Post by jdong on 2005-09-27
[QUOTE=wmcbrine]Why use encryption on that site, anyway? AFAICT there's nothing secret/private there.[/QUOTE]

The password for the Wiki is the same as the launchpad/bugzilla password, both being very sensitive for certain people (i.e. team leaders; developers)

---

