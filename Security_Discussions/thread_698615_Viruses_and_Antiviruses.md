---
title: "Viruses and Antiviruses"
date: 2008-02-16
forum: Security Discussions
---

### Post by Shippou on 2008-02-16
Just thought of starting this..

You know I'm really interested how viruses work (but then I don't, I repeat, I don't write viruses; I'm just interested on how they work). I just want to ask: What do you think is the most destructive Linux virus? 

Another question: Is KlamAv the only Linux antivirus? Are there others?

please give descriptions.

---

### Post by tubezninja on 2008-02-16
ClamAV is the reigning free AV scanner, but there are commercial products for Linux too (read: very pricey).

One of them is offered by Sophos:

[http://www.sophos.com/products/enterprise/endpoint/security-and-control/linux/](http://www.sophos.com/products/enterprise/endpoint/security-and-control/linux/)

And of course, the big Windows players have their own linux suites too:

[McAfee LinuxShield]("http://www.mcafee.com/us/enterprise/products/anti_virus/file_servers_desktops/linuxshield.html")

and

[Trend Micro ServerProtect for Linux]("http://us.trendmicro.com/us/products/enterprise/serverprotect-for-linux/"), though you should be aware there is [currently boycott in progress of Trend Micro products]("http://www.fsf.org/blogs/community/boycottTrendMicro.html").

Symantec also supposedly has a linux solution, but I couldn't find it on their website anywhere.

At any rate, the product descriptions belie the unfortunate motive behind commercial AV software: to make lots and lots of money (actual protection of people's computers seems a lot of times to be a distant second priority).  These solutions are intended for enterprise servers, run by businesses who don't want the embarrassment of passing on virus-infected content to people visiting their websites and downloading stuff.  These companies see no money in offering a linux desktop-based AV solution, so they don't do it.

So, for  a desktop or small hobby server, you're probably best off with ClamAV, running a firewall, and keeping on top of security updates.

---

### Post by philip720 on 2008-02-16
Avg Has A Free Anti-program For Linux

---

### Post by Shippou on 2008-02-18
You know, I heard somewhere (I can't recall when or where it exactly happened) that AV companies and virus writers somewhat have a "contract" with each other: virus writers release viruses so that AV companies can produce their "anti-virus" code and release it to the public with a price. 

What do you think?

---

### Post by bodhi.zazen on 2008-02-18
In a nutshell,

1. No OS is immune from malicious code. See my security thread to get started on Ubuntu security.

2. Don't forget about the importance of social engineering in any OS (or security in general).

3. The most important thing one can do to increase security is user education.

4. Security and convenience often conflict.

5. viruses / worms take advantage of holes or flaws in the code. The reason antivirus companies exist for Windows is Microsoft, for convenience or otherwise, fails to close known holes / flaws in the code (often for years / decades).

6. The reason you do not need antivirus in Linux is, up to now, holes or flaws in the code are patched rapidly (at least with the major distors like Debian/Ubuntu - Red Hat/Fedora - etc). 

7. +1 scaredpoet. Antivirus companies prey on your fear (and previous experience with Windows) and would have you believe their products increase Linux security. Read through my security sticky if you want to increase security.

---

