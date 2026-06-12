---
title: "ettercap dns_spoof problem"
date: 2008-07-13
forum: Security
---

### Post by sherl0ck on 2008-07-13
Hi,
 I can't seem to get the dns_spoof plugin to work in ettercap for ubuntu 8.04 from repo. This is an error I get that I think causes the problem:
```
Dissector "dns" not supported (etter.conf line 72)
```
When I try to compile from source ( version 0.7.3 ) I can't seem to get passive dns enabled -
```
 Functionalities : 

 Debug mode .............  no
 Plugin support .........  yes
 Passive DNS ............  no
 Perl regex in filters ..  yes
 Iconv UTF-8 support ....  yes
```
I've used in before in backtrack without problem, so I doubt its a configuration problem.
Can anyone give suggestions how to get dns_spoof working? or how to compile with passive dns to yes?

---

### Post by simonapnic on 2008-07-13
Do a **./configure --help | grep DNS** and it should reveal some flags you can use.
As for the repository version, did you install the **ettercap-common - Common support files and plugins for ettercap package** ? I guess it's needed. Also try taking a look at etter.conf and modifying the specified line.

---

### Post by nick_edwards on 2009-05-17
has anyone found the solution to this problem I get the same error:

Dissector "dns" not supported (etter.conf line 70)

and dns spoofing does not work, wireshark shows the ARP poisoning packets but the ARP packets go straight through to the dns server?

---

### Post by Bohemenian on 2009-09-01
Bump? I've also just run into this.

---

### Post by esqmo on 2010-03-09
Try this with google translate

[http://unknowndebian.free.fr/wordpress/?p=20](http://unknowndebian.free.fr/wordpress/?p=20)

and the translated version:
[http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Funknowndebian.free.fr%2Fwordpress%2F%3Fp%3D20&sl=fr&tl=en](http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Funknowndebian.free.fr%2Fwordpress%2F%3Fp%3D20&sl=fr&tl=en)

---

