---
title: "Security of Ubuntu, it's Flavors, and Solus OS"
date: 2017-09-04
forum: Security
---

### Post by brijeshio on 2017-09-04
I recently moved on to the Ubuntu family since it's open source, linux based and faster. :)

 I am quite happy using it, but then I thought to myself:

**Question 1:** Are open source OS's like Ubuntu, it's flavors, and Solus OS safe to use?

**Question 2:** Have they been tested by security experts? Has a real security expert or firm ever gone through the whole source code and tested it for vulnerabilities?

**Question 3:** Have the results been publicly published?

**Question 4:** Are there security experts who vouch for them being safe to use?

**Question 5:** Which one is safest: Ubuntu, Kubuntu, Ubuntu Mate, Xubuntu, or Solus OS?

**Ubuntu, it's Flavors and Solus OS**

Please don't take it personally, but developers will always call their OS secure. My question here is whether there are any security experts or security houses taking responsibility to check them for security on a time to time basis.

Considering that there's a very large community around Ubuntu, just like WordPress, security bugs may always get known easily and fixed. But what about it's flavors? This is where it gets a bit questionable. And specifically, the Solus OS which has been written from scratch.

Kindly shed some light on this. Thanks in advance!

Regards,
Brijesh

---

### Post by vasa1 on 2017-09-04
Why are you asking about Solus here? Solus isn't a flavor of Ubuntu. Please visit the Help Center for Solus OS: [https://solus-project.com/help-center/home/](https://solus-project.com/help-center/home/)

And take some time to read this sticky even though it's from 2007: [https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)

---

### Post by TheFu on 2017-09-04
Solus is based on Linux and lots of hard work from thousands of F/LOSS projects around the world, just like every other Linux distro.   Hardly written from scratch.  The phrase we normally use is "standing on the shoulders of giants" - to mean they reused the work from lots and lots of other brilliant people.  That is smart.

[https://www.tecmint.com/linux-server-hardening-security-tips/](https://www.tecmint.com/linux-server-hardening-security-tips/) provides some ideas about securing a Linux system, but definitely start with the "sticky threads" in this subforum (Security).  There is some fantastic knowledge shared there.  There are also security pages on help.ubuntu.com for different aspect - basic desktop, advanced server.

I'm not a fan of rolling releases.  *New* is the enemy of stable. *Stable* is good for security.  Nothing except time with an OS and all the applications can provide any real comment about overall security. Claims mean ZERO.

---

### Post by brijeshio on 2017-09-05
> **vasa1 said:**
> And take some time to read this sticky even though it's from 2007: [https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)

Thanks, will go through the same. It's quite long. :)

> **TheFu said:**
> Solus is based on Linux and lots of hard work from thousands of F/LOSS projects around the world, just like every other Linux distro. Hardly written from scratch. The phrase we normally use is "standing on the shoulders of giants" - to mean they reused the work from lots and lots of other brilliant people. That is smart.


Never knew that. I am very new to the Linux family. I *read it on the internet* (whatever that means :D) that it has been written from scratch. On a reddit thread. But still, from my research, it is better in terms of user experience since it's latest release uses Budgie desktop environment. It looks cool and has a GUI for every setting. So far, so good. :)

> **TheFu said:**
> [https://www.tecmint.com/linux-server-hardening-security-tips/](https://www.tecmint.com/linux-server-hardening-security-tips/) provides some ideas about securing a Linux system, but definitely start with the "sticky threads" in this subforum (Security). There is some fantastic knowledge shared there. There are also security pages on help.ubuntu.com for different aspect - basic desktop, advanced server.

Really good advice on that page. Helped me a lot. Thanks for link Fu.

> **TheFu said:**
> I'm not a fan of rolling releases. *New* is the enemy of stable. *Stable* is good for security. Nothing except time with an OS and all the applications can provide any real comment about overall security. Claims mean ZERO.

Haha, so true! That is why I always prefer installing the stable version. Also, for Solus, they keep on sending in updates as they're released. It's a small team, but they look promising to me.

Thanks to both you for your replies. **But again, my question is a bit different here. Are there any security houses going through the whole source code. Also, is it tested for vulnerabilities? Any security tests, proofs, or papers to go through?**

---

### Post by TheFu on 2017-09-05
> **brijeshio said:**
> Haha, so true! That is why I always prefer installing the stable version. Also, for Solus, they keep on sending in updates as they're released. It's a small team, but they look promising to me.

Thanks to both you for your replies. **But again, my question is a bit different here. Are there any security houses going through the whole source code. Also, is it tested for vulnerabilities? Any security tests, proofs, or papers to go through?**

I think you've missed my point.  New updates with new features ARE THE ENEMY.  You only want security patches. That is very different from every new release from every project, which is full of new bugs to be exploited.

No security company can go through all the code.  There are hundreds of changes to the kernel every week.  Multiple similar changes across thousands of F/LOSS projects and nobody could possibly keep up.  Some of the code where security is required, like libopenssl has been reviewed and those reviewers responsibly reported the issues to the team, which corrected them.  All software is constantly tested.  I've never seen any "proof" as you say concerning error free software that I trusted.  Building software has many layers and if all of them aren't proven, for the exact versions of each library/tool used, forgetaboutit.

As for papers, you can google as well as we can.  Often, security people don't write a paper. They use any bug they find to promote their company by giving talks at different security conferences around the world.  It is advertising for their company.  Often, they will use a 3rd party to quietly let the teams responsible for any issues know and give them time to correct the problems, but many closed source software teams will ignore this, so the only thing the researcher can do is to release the bug, put pressure on the company to fix it from outside market forces.  Big companies seem to be slower about fixing things and have previously threatened lawsuits.

If you really care, watch the CVEs.  Those are generally for specific software projects and they come in batches as a security researcher delves into a particular library or software.  Last week, HP Openview got a spanking (like 10 new CVEs), but usually it is Microsoft, Apple, Oracle, and Adobe with most of the issues.  The Linux kernel gets them all the time too. [https://usn.ubuntu.com/usn/](https://usn.ubuntu.com/usn/) iOS and Android applications are full of issues - you don't even want to know. [https://www.cvedetails.com/vulnerability-list.php?vendor_id=1224&product_id=19997](https://www.cvedetails.com/vulnerability-list.php?vendor_id=1224&product_id=19997)

A small distro that hasn't gotten enough people interested is likely to not have anyone looking, testing, the code.  Not knowing doesn't mean the system is any more secure.

---

### Post by sgian on 2017-09-05
I don't know if this answers the security house question, but major companies occasionally address exploits in linux but not as often as Windows because there isn't as much money in it.  For example, Trend Micro on their website had this article last year [https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/linux-security-a-closer-look-at-the-latest-linux-threats](https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/linux-security-a-closer-look-at-the-latest-linux-threats) and of course at the end of the article they do a sales pitch for their product.  Also sponsored by Trend Micro is the Pwn2Own competition, in which some of the best get together and hack popular products for prizes.  [http://blog.trendmicro.com/pwn2own-2017-event-ages/](http://blog.trendmicro.com/pwn2own-2017-event-ages/)  Ubuntu made the news for being hacked in the 2017 competition and it was quickly patched. [https://www.techworm.net/2017/03/day-1-pwn2own-hacking-competition-witness-ubuntu-linux-safari-adobe-reader-edge-exploits.html](https://www.techworm.net/2017/03/day-1-pwn2own-hacking-competition-witness-ubuntu-linux-safari-adobe-reader-edge-exploits.html)  If you google the name of any security house and add linux after the name in the search entry (like Trend Micro linux) then you will find if they have studied linux.

As for which desktop environment (KDE, XFCE, Gnome, Unity) for Ubuntu is more secure, I do not know.  But each has their own differences in code that could be exploited by someone with the skills to do so.  As Linux is recently said to be 3% of the desktop market and the money for hackers is in linux servers which often don't even have a desktop environment, I personally doubt that it matters much since there isn't as much incentive for criminals to find exploits in linux desktops as compared to linux servers and the much easier to hack Windows variants.

---

