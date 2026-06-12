---
title: "Spyware/bloatware from Limewire"
date: 2009-05-30
forum: Security
---

### Post by Tholley on 2009-05-30
I just had a question about Malware from Limewire. I have used limewire for years in Windows and for the most part can tell the legit downloads from the bad ones.
 
But just running limewire, installs "Grokster" which is some kind of spyware, adware, and/or bloatware. I always run my CA spyware and delete the Grokster file (and any others found) immediately after closing. I don't have that luxury in Ubuntu.
 
I know viruses are _mostly_ a non issue, but does anybody know if Grokster affects Ubuntu or not? Is there a way to check for spyware?
 
Thanks!

---

### Post by HermanAB on 2009-05-30
How do you intend to run it - on Wine?

It is very easy to check for spyware activity using tcpdump or ngrep.  Spyware will never get far in Linux.

---

### Post by Tholley on 2009-05-30
[quote=HermanAB;7372826]How do you intend to run it - on Wine?
 
Limewire has a linux (.deb) download on thier website. Works good.

---

### Post by Tholley on 2009-05-30
I'm still new at Linux.
I showed to have tcpdump already installed, and I installed ngrep, but how do I run them?

---

### Post by HermanAB on 2009-05-31
Just read the man pages.  Pretty easy to use:
$ sudo tcpdump -A -s 256 -i eth0

This one is useful when you cannot remember your login to your email account:
$ sudo ngrep -x host 192.168.1.10 password

Then refresh your email program - la voila!

---

### Post by Liuxurong on 2009-05-31
Well... Thanks!

---

### Post by MechaMechanism on 2009-05-31
What about Frostwire?

---

### Post by MegaNinjaDeth on 2009-06-01
> **MechaMechanism said:**
> What about Frostwire?
Frostwire is a more convient alternative.

Torrents are the best.

---

### Post by bitf on 2009-06-01
LimeWire is [Nagware]("http://en.wikipedia.org/wiki/Nagware"). 
Does anyone know Why frostwire isn't in Add/Remove Programs?

---

