---
title: "Anonymous Linux"
date: 2009-05-17
forum: Security
---

### Post by shaggy999 on 2009-05-17
I came across a huge howto/faq about a year ago (I think through stumbleupon) about how to anonymize a linux installation. It was a very big and thorough faq that covered things like setting up /var/log to write to a ram drive, encrypting the home directory, various networking security optimizations... pretty much everything you could do so that if somebody got a hold of your computer they wouldn't be able to obtain much useful information and your computer would be pretty secure on the network, too.

I'm looking for that faq but I can't find it. I remember it being a huge faq, probably on the order of 100 pages long. Does anybody know what I'm talking about and maybe have a linky to it?

---

### Post by scorp123 on 2009-05-19
> **shaggy999 said:**
>  encrypting the home directory ... pretty much everything you could do so that if somebody got a hold of your computer they wouldn't be able to obtain much useful information You mean like this?
[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)
[http://www.howtoforge.com/encrypted-root-lvm](http://www.howtoforge.com/encrypted-root-lvm)

I use encrypted LVM's on my company laptops.

> **shaggy999 said:**
> 
and your computer would be pretty secure on the network, too.
 That depends on what ports are open or not and if you use a firewall (e.g. one that drops any incoming packets) or not. Even if: no firewall will help if you use unencrypted protocols such as SMTP (sending mails), POP3 (reading mails), IMAP (reading mails) or HTTP (browsing the web). Because these packets are not encrypted they can easily be intercepted. So there is not much you can do on your computer - the weak link is you, the user. If you want to be "undetectable" on the network (which is not really possible) you have to make sure you stick to encrypted protocols such as SSH and HTTPS ... or even better: use a VPN and tunnel all your connections through that. But complete network "invisibility" is not possible.

> **shaggy999 said:**
> I'm looking for that faq but I can't find it. Did you look here? :)
[http://www.google.com](http://www.google.com)

---

### Post by shaggy999 on 2009-05-19
No, I already have an entire encrypted system partition. What I had come across was generic to ANY linux installation, it was not on a blog, it looked like it had been written probably 10 years ago and was all in ASCII text like it was something posted to a newsgroup. It was easily over 100 pages and simply covered EVERYTHING related to "anonymizing" a Linux installation. It truly read like a book with chapters and subsections and everything.

I've looked everywhere for it, but I can't find it. My interest in it is not because I want to implement any of the features explained within, but because it went extremely in depth in how Linux systems work and how various types of hacks and infiltrations occur.

And yes, I've googled extensively.

---

### Post by scorp123 on 2009-05-20
> **shaggy999 said:**
> it looked like it had been written probably 10 years ago  In  that case it's hopelessly obsolete and outdated. Linux 10 years ago and Linux now ... that's a whole Galaxy full of progress and differences. 10 years ago we were at Kernel 2.0.3x something in the stable tree; people willing to experiment used kernel 2.1.x or later 2.2.x.

So if that book describes any weaknesses in the kernel (... there were a few ...) then the information is hopelessly outdated because the kernel progressed at least three generations and many million lines of code: 2.3.x (2000, unstable) => 2.4.x (2001, stable) => 2.5.x (2002, unstable) => 2.6.x (2006, stable) ...

It's 2009 now and most Linux distributions are somewhere between 2.6.18 and bleeding-edge 2.6.29 or even 2.6.30.

I doubt you can gain anything from that book except for the purpose of nostalgia and IT history. Anything they say or demonstrate in that book is hopelessly obsolete for the most part.

That's like wanting to learn modern battlefield tactics ... and reading Gaius Julius Caesar's "De Bello Gallico" (About the War in Gaul) in Latin, written by Caesar some 2000 years ago. It's interesting how he conquered the Gauls some 2000 years ago but you're not going to find out anything about modern tactics.

If you want to learn about UNIX and Linux security I suggest you forget that ancient book and stick to newer books that are up-to-date. Or even better: stick to online forums and other such places where Unix and Linux security is being discussed. Mailing-Lists that discuss current vulnerabilities and exploits are a valuable source too. Last but not least it won't hurt to keep visiting Linux forums ... there are always interesting threads that discuss exactly the topic you are interested in (at least that's my experience here with Ubuntu's forums ...).

---

