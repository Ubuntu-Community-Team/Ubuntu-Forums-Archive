---
title: "Linux Kernel 64 Bit"
date: 2010-09-24
forum: Security
---

### Post by jimmers on 2010-09-24
Spotted this aarticle in a ZEDNET.UK newsletter, has anuone else seen it, and should we be concerned . 
 
Linux kernel exploit roots 64-bit machines 
Tom Espiner ZDNet UK | September 22, 2010 8:38 AM PDT  
 
Attackers have used a freely available exploit to target a number of  64-bit Linux machines, according to a Linux patch management software  firm.  
The exploit is particularly pernicious, as it can leave a backdoor on  systems that have workarounds deployed, according to rebootless Linux  security update company Ksplice. The stack pointer underflow weakness  has been given a common vulnerability code of CVE-2010-3081.  
"In the last day, we've received many reports of people attacking  production systems using an exploit for this vulnerability, so if you  run Linux systems, we recommend that you strongly consider patching  this," said Ksplice chief executive Jeff Arnold in a blog post on  Saturday. Exploit code was made available on the Full Disclosure mailing  list on Wednesday. Arnold said that the flaw was introduced into the  Linux kernel in 2008 and involves every 64-bit Linux distribution.  
For more of this story, read Linux kernel exploit roots 64-bit machines on ZDNet UK.

---

### Post by jimmers on 2010-09-24
Sorry forgot the link

  	 	 	 	p { margin-bottom: 0.21cm; }a:link {  }  [COLOR=#000080]_[Linux kernel exploit roots 64-bit machines]("http://www.zdnet.co.uk/news/security-threats/2010/09/21/linux-kernel-exploit-roots-64-bit-machines-40090177/?s_cid=116")_[/COLOR]

---

### Post by CharlesA on 2010-09-24
It's been patched.

See the existing thread here:

[http://ubuntuforums.org/showthread.php?t=1577115](http://ubuntuforums.org/showthread.php?t=1577115)

---

### Post by rookcifer on 2010-09-24
Yep, been patched.  Ubuntu released the patch like a day or two after it went public.  You should have received an automatic update earlier this week. 

And this exploit is really only a danger if you have other local users on your machine.

---

### Post by movieman on 2010-09-24
> **rookcifer said:**
> Yep, been patched.  Ubuntu released the patch like a day or two after it went public.

It was patched last week, before the story really hit anywhere on the Internet outside the hardcore security sites; I saw the kernel upgrade installed and wondered what it was for until I saw the stories on major web sites a couple of days later.

---

### Post by CharlesA on 2010-09-24
> **movieman said:**
> It was patched last week, before the story really hit anywhere on the Internet outside the hardcore security sites; I saw the kernel upgrade installed and wondered what it was for until I saw the stories on major web sites a couple of days later.

Likewise. At least it was patched quickly. :)

---

