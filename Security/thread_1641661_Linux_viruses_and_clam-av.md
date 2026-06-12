---
title: "Linux viruses and clam-av"
date: 2010-12-09
forum: Security
---

### Post by gdiloren on 2010-12-09
There are practically no Linux Viruses but if I catch one will it be detected by clam-av? Is a Linux virus specifically to Linux, I mean it only disrupts the Linux OS first above all. What it does? Thanks!

---

### Post by AlexDudko on 2010-12-09
Linux viruses are nothing more more a topic for conversation. Anti-virus programs detect only Windows viruses.
One can get infected running Linux only in case of abandoning any security means of the system or deliberately executing a malicious program.
Some general information on Linux viruses can be found [here]("http://en.wikipedia.org/wiki/Linux_malware").
Running SELinux makes your system more secure and immune against possible attacks.

---

### Post by bodhi.zazen on 2010-12-09
> **AlexDudko said:**
> Anti-virus programs detect only Windows viruses.

That is not true. The antivirus programs for Linux will detect (known) linux viruses and worms.

Enter "linux" in the clamav database and see for yourself:

[http://clamav-du.securesites.net/cgi-bin/clamgrok](http://clamav-du.securesites.net/cgi-bin/clamgrok)

Antivirus is in general a waste of time on Linux because, unlike other OS, when a virus is developed or discovered the underlying problem in the code is patched. Thus you can not be affected by any of the known viruses.

This is not the case in other OS, where the source is both closed and unpatched for a long time, if ever. On those OS, rather then fixing the problem, it keep recurring and you need a third party to clean up after the sloppy coding.

Linux is not windows and viruses are not a problem as of yet. It is of course possible a Linux virus will be developed, but then it would be a zero day exploit, and antiviurs software will again not help.

---

### Post by I'mGeorge on 2010-12-09
> **AlexDudko said:**
> Linux viruses are nothing more more a topic for conversation. Anti-virus programs detect only Windows viruses.


As a joke towards windows I say something like this too :-) But yeah linux has it's own share of virality even if it's not that obvious, and it shouldn't be much of a threat if the usual protection guidelines are respected. 

Hey if you have a doubt, always look  for it in Wikipedia [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by endotherm on 2010-12-09
it should be noted that there are very few viruses out there for any platform these days, because the way viruses work was made much less effective by the emergence of applications auto-updating features and stronger protections of applications (especially email client software). these days you have trojans and worms as your primary problems. for worms, patch your system as security updates are released, and for Trojans exercise good digital hygiene.

---

