---
title: "Preventative Maintenance for 'Xnote' Linux Trojan"
date: 2015-02-10
forum: Security
---

### Post by chiques on 2015-02-10
Any suggestions on precautions I can take?

[http://www.techworm.net/2015/02/xnote-new-multi-purpose-backdoor-targets-linux-servers-converts-botnets.html](http://www.techworm.net/2015/02/xnote-new-multi-purpose-backdoor-targets-linux-servers-converts-botnets.html)

---

### Post by carl4926 on 2015-02-10
Don't run as root> [COLOR=#606569][FONT=Open Sans]The malware will only be installed in a system if it has been launched with superuser (root) -  [/FONT][/COLOR]

---

### Post by chiques on 2015-02-10
> **carl4926 said:**
> Don't run as root

So I'd have to run this malware 'manually' as su? It won't run as root by itself?

---

### Post by bashiergui on 2015-02-10
> **chiques said:**
> So I'd have to run this malware 'manually' as su? It won't run as root by itself?
You wouldn't run it. Attackers have brute forced internet-facing password, like on ssh. Once they get root access the bad guys run it themselves. So disable password auth on ssh and only use keys. If you don't have any services running open to the internet then you're not the target of the campaign they're talking about in the link.

---

### Post by mooreted on 2015-02-10
Unless you are running something like a website, you don't have to do anything. Your desktop computer or laptop is safe.

---

### Post by Bucky Ball on 2015-02-10
This:

> The malware will only be installed in a system if it has been launched with superuser (root) privileges.

This:

> The only saving grace for Linux users it that it will not launch itself if it doesnt have the root privileges in the target PC.

... and this:

> &#8220;The only saving grace for Linux users it that it will not launch itself if it doesnt have the root privileges in the target PC.&#8221;

_Which is why you don&#8217;t log in as &#8216;root&#8217; and instead &#8216;sudo&#8217; whenever you need root privileges_.

You need to boot your machine and log in as root to open the backdoor. No-one does, and if they do, not advisable.

---

