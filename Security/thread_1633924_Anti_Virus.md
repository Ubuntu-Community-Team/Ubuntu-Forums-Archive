---
title: "Anti Virus"
date: 2010-11-29
forum: Security
---

### Post by mmsmc on 2010-11-29
any body know any good anti viruses i can use for linux, i'm hearing mixed answers to whether linux can get infected or not

---

### Post by Axolotl9250 on 2010-11-29
I use Clam AV, which is useful if you run wine or you have colleagues or family who use Windows and you feel you want to have such an AV to protect them more than anything i.e. stop the spread. Generally speaking there are not any "viruses" in the truest sense of the word in Linux, most are on Windows and a few are on Mac as that's what most people have. However if you're like me you may be parranoid from attacks still by more experienced computer users who know more about Linux and back doors in, but there are methods to minimise the risk. But I like to think most (but not all) of the technological and creative effort in the Linux and open source community is towards making it better for everyone, not breaking into people's machines. But in general - no Linux is not prey to the classic Windows scenario of clicking to download a program and it turning out to be something far more nasty, because of such as MD5 sums, which you can check, and obtaining software from packages, there is someone always watching, and if any get altered or corrupted, someone will notice.

On your web-browser, such as Firefox, I would consider NoScript and AdBlocker Plus. To stop or allow script's you do/don't want on a page from running. In addition Tor makes it harder for people to scan your information as you browse the web.

---

### Post by FuturePilot on 2010-11-29
See the Ubuntu Security sticky. Link in my sig for convenience.

---

### Post by HermanAB on 2010-11-30
What are these virus things people are complaining about?  Maybe you should wash your hands before using your PC... ;)

---

### Post by ronnielsen1 on 2010-11-30
> What are these virus things people are complaining about?  Maybe you should wash your hands before using your PC.

:p

I was using linux about 6 months before I realized I could relax some

---

### Post by bodhi.zazen on 2010-11-30
> **mmsmc said:**
> any body know any good anti viruses i can use for linux, i'm hearing mixed answers to whether linux can get infected or not

There are no known active viruses for linux.

In terms of antivirus for linux, it depends on what you want to use antivirus for.

Scanning your linux desktop installation for viruses is an exercise in futility.

Using an antiviurs scanner to filter or monitor a file server with windows clients or email server is different.

If you are in need, I suggest clamav. There are several graphical tools.

See the security sticky and HIDS thread.

---

### Post by ronnielsen1 on 2010-11-30
Well said, bodhi.zazen.

---

### Post by Soul-Sing on 2010-12-01
> **HermanAB said:**
> What are these virus things people are complaining about?  Maybe you should wash your hands before using your PC... ;)

Nah,its not on the hands, its in peoples head. Computers are associated with virusses, and that dogma is very difficult to change.

---

### Post by Soul-Sing on 2010-12-01
> **ronnielsen1 said:**
> Well said, bodhi.zazen.

Indeed, as always.

---

### Post by I'mGeorge on 2010-12-01
Ok lads this it's how it goes, the antivirus programs available under linux are actually for windows. The best use of those it's in scanning partitions where you have windows installed 'cause under linux there are no known virus threats.

---

### Post by ronnielsen1 on 2010-12-01
**[A history of viruses on Linux]("http://www.neowin.net/news/a-history-of-viruses-on-linux")**

Good article I ran across on viruses and linux

---

### Post by malspa on 2010-12-01
> **ronnielsen1 said:**
> :p

I was using linux about 6 months before I realized I could relax some

LOL!  Same here.

---

### Post by ronnielsen1 on 2010-12-01
Name sounds familiar. Did you try Mepis for a while Malspa? I was with it from 3.34 to KDE 4.

---

### Post by malspa on 2010-12-01
> **ronnielsen1 said:**
> Name sounds familiar. Did you try Mepis for a while Malspa? I was with it from 3.34 to KDE 4.

Yeah, I remember you!  Still using Mepis, along with a number of other distros (including Ubuntu).

---

### Post by ronnielsen1 on 2010-12-01
I'm using it right now as a test but having a hard time getting used to kde4

---

### Post by brian_p on 2010-12-01
> **ronnielsen1 said:**
> **[A history of viruses on Linux]("http://www.neowin.net/news/a-history-of-viruses-on-linux")**

Good article I ran across on viruses and linux

Depends what you mean by "good".

The author sets out his stall:

> Given the tight security integrated into Linux, it is difficult to take advantage of a vulnerability on the computer, but some programmers have found ways around the security measures.

Thereafter there is no further mention of what this tight security is or the ways round it. The impression given is some some very clever techniques are employed.

Then a small dose of FUD. Yep. That'll keep them wary and on their toes! Shows them I care:

> There are several free options for anti-virus on Linux that you really should use, even if it isn't always running - a weekly or monthly scan doesn't hurt.

The remainder of the article lists a ragbag of malware which nobody in their right mind would ever install as root. But

> That doesn't mean they don't exist though.

Ok. But, so what?

---

### Post by bodhi.zazen on 2010-12-01
> **I'mGeorge said:**
> Ok lads this it's how it goes, the antivirus programs available under linux are actually for windows. The best use of those it's in scanning partitions where you have windows installed 'cause under linux there are no known virus threats.

I have two issues with your post.

1. First, linux antivirus programs scan for Linux viruses.

Type "Linux" , without quotes, in this database search:

[http://clamav-du.securesites.net/cgi-bin/clamgrok](http://clamav-du.securesites.net/cgi-bin/clamgrok)

2. Second, IMO, if you are running Windows you should learn to secure windows and use the various windows tools to clean windows. The Linux tools will identify viruses on your Windows partition, but will not clean them, and in particularly can not fix the windows registry.

IMHO, the "best" use of antivirus scanners on Linux is on mail or file servers.

=====

A few general comments on Linux and Viruses:

Much of the information on various web pages and blog pages is FUD. Many people who write these things either do not know much about Linux Security or are trying to sell you a product and are taking advantage of your Windows experience.

Linux is not windows and things such as viruses / worms are managed very differently.

Windows is closed source, and Microsoft does not release security patches in a timely manor, so you need to rely on third party antivirus or security software that is bolted onto windows. This code is written without access to the source code of course ...

In Linux we patch the source code. So if there is a Linux virus -> you then get a security update -> and you are no longer vulnerable.

There is a whole industry selling security products to Windows uses and they want you to purchase their products for Linux as well. 

So "Why not" use antivirus "just in case" ? Because you should keep your system up to date and viruses will then not be a problem.

Do you wear a helmet, bullet proof vest, parachute, as scuba gear when you drive your car "just in case"  you are shot, fall off a cliff, or drive into a lake ? All these things could happen.

In all the years I have used Linux I have never seen a virus. Does not mean it cannot happen, or that Linux is invulnerable, it just means Linux is not Windows and you can not blindly apply windows Security to Linux.

Security is a active learning process, you need to learn the vulnerabilities of Linux and how to be safe.

Read the security sticky =)

---

### Post by I'mGeorge on 2010-12-01
**@bodhi.zazen** my post supposed to be more like a joke. Of course there are viruses for linux too, and linux anti-viruses programs are meant for linux, but if you respect the usual security guidelines those viruses are far from being real threats and you should be pretty much OK so you won't have to install useless antivir software on your hdd. That's why I've specified that linux anti-viruses are more useful for windows than linux itself, as a joke, 'cause under windows it's more likely to encounter a virus than in linux even if the antivir can't really delete the infected file or disinfect it

---

### Post by bodhi.zazen on 2010-12-01
> **I'mGeorge said:**
> **@bodhi.zazen** my post supposed to be more like a joke. Of course there are viruses for linux too, and linux anti-viruses programs are meant for linux, but if you respect the usual security guidelines those viruses are far from being real threats and you should be pretty much OK so you won't have to install useless antivir software on your hdd. That's why I've specified that linux anti-viruses are more useful for windows than linux itself, as a joke, 'cause under windows it's more likely to encounter a virus than in linux even if the antivir can't really delete the infected file or disinfect it

Thank you for the clarification.

---

