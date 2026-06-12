---
title: "Hosting websites - security and code auditing"
date: 2006-08-22
forum: Server Platforms
---

### Post by hagen00 on 2006-08-22
Hi there

I was wondering. 

People that host websites surely do not audit all the code that they host. But what if they host some poorly written websites that leave backdoors open? How do they ensure that the whole server isn't compromised because of one poorly written website. 

If a cracker gains access through one website, what's stopping them from compromising the whole computer? 

Thanks for any insight. 

H

---

### Post by Useless on 2006-08-22
You can host virtual machines on your physical machine and each virtual machine can host one website.  This way only one will be vulnerable to some bad code on the developers part.  All you have to worry about is if your network on the virtual end is secure.  Thats what most hosting services do that i know of for complete security.

---

### Post by hagen00 on 2006-08-22
Thanks for the reply. 

I also posted on Linux Questions.org in the security section...and the guru there (unSpawn) had this to say (in case others are interested):

> *I was wondering.*# pkill -9 -f "cat.*curiosity" ;-p


*People that host websites surely do not audit all the code that they host.*
Since even the maintainers of PHP or PHP-based apps don't (in full) we can't expect hosters to either. Hosters usually don't have the right toolkit or programming knowledge or sense of security or time (==money). Hell, some don't even read README's.


But what if they host some poorly written websites that leave backdoors open? How do they ensure that the whole server isn't compromised because of one poorly written website.
0. packet-scrubbing network device that is capable of detecting anomalies and scans (Snort, Prelude, HW),
1. reverse proxy scrubbing requests (Apache),
2. sensor (or mod-security) or Iptables ruleset tripping over repeated bad requests,
3. real-time integrity checking (Samhain)
4. real-time logalerting, 
If a cracker gains access through one website, what's stopping them from compromising the whole computer?
5. virtualisation (Xen, Qemu, UML and the Other One)
6. running services as lesser-privileged users,
7. chrooting running services,
8. strict role separation (SELinux, GRSecurity's RBAC, RSBAC)
9. keeping a small footprint and keeping up to date with security fixes,
10. properly configuring about everything,
11. proper access restrictions
12. Running a minimal Apache, Hardened-PHP, secured MySQL,
??. sure I forgot something, you name it:


---

### Post by Gouki on 2006-08-22
A big problem of webhosting. Like the poster on LinuxQuestions said, not even the authors of the code do it, let alone the company hosting it.

I always recommend two tools when it comes to code auditing, which are [SpikeSource PHP Security]("http://developer.spikesource.com/projects/phpsecaudit/") and [RATS]("http://www.securesoftware.com/resources/download_rats.html").

---

