---
title: "Debina Testing/Etch..."
date: 2006-01-08
forum: The Cafe
---

### Post by LongTooth on 2006-01-08
While Ubuntu is my main distro I do play with others. Frugalware is a very nice distro I would recommend to anyone. Foresight is beautiful and has potential but not ready for prime time. At the moment I've got GenieOS install on a test box. GenieOS is Debian proper (Sarge) with Flash, Jave, codecs and many other things added. Being Sarge its a bit long in the tooth as I'm sure most folks will agree. Nothing wrong with Sarge except that it does not have Gnome 2.12 or even 2.10. The same applies to the other programs that come with GenieOS/Debian Sarge. 

I've done quite a bit of web surfing to learn how to upgrade to Testing/Etch. The process seems simple enough but I'll be damned if my results don't end up borked beyond belief. According to accepted procedure, I'm required to change the word 'stable' to 'testing' in the /etc/apt/sources.list file. Do an update followed by dist-upgrade. Simple? Sure sounds like it. But I've yet to end up with a system that works. I've gone so far as to copy other's sources.list and still I can't get a system up and running. Am I missing something? Should I read between the lines and take another step?

If anyone can give me a hand in upgrading from Debian stable to testing I would be most appreciative.

Thanks

P.S GenieOS is another distro I would highly recommend to others. While behind the curve as far as what versions of programs are available, one can't deny the rock solid stability of a Debian system. It's just that, damnit!, it a bit on the stodgy side.

---

### Post by BSDFreak on 2006-01-08
[QUOTE=LongTooth]While Ubuntu is my main distro I do play with others. Frugalware is a very nice distro I would recommend to anyone. Foresight is beautiful and has potential but not ready for prime time. At the moment I've got GenieOS install on a test box. GenieOS is Debian proper (Sarge) with Flash, Jave, codecs and many other things added. Being Sarge its a bit long in the tooth as I'm sure most folks will agree. Nothing wrong with Sarge except that it does not have Gnome 2.12 or even 2.10. The same applies to the other programs that come with GenieOS/Debian Sarge. 

I've done quite a bit of web surfing to learn how to upgrade to Testing/Etch. The process seems simple enough but I'll be damned if my results don't end up borked beyond belief. According to accepted procedure, I'm required to change the word 'stable' to 'testing' in the /etc/apt/sources.list file. Do an update followed by dist-upgrade. Simple? Sure sounds like it. But I've yet to end up with a system that works. I've gone so far as to copy other's sources.list and still I can't get a system up and running. Am I missing something? Should I read between the lines and take another step?

If anyone can give me a hand in upgrading from Debian stable to testing I would be most appreciative.

Thanks

P.S GenieOS is another distro I would highly recommend to others. While behind the curve as far as what versions of programs are available, one can't deny the rock solid stability of a Debian system. It's just that, damnit!, it a bit on the stodgy side.[/QUOTE]

I've never had a problem upgrading from debian stable to debian testing by just changing the sources.lst and doing an apt-get update && apt-get dist-upgrade.

---

### Post by matthew on 2006-01-08
The problem could be in the GenieOS additions to Debian Sarge. I have done upgrades from straight Sarge to Etch and even to Sid without major incident.

---

### Post by Ampersand on 2006-01-08
I'm currently using demudi with Debian etch. I didn't find many problems updating although there seem to be some incompatibilities in the xlibs versions. Not particularly important, but does mean that I can't get the Cedega cvs installed...

---

