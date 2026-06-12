---
title: "Ran across this."
date: 2020-08-14
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2020-08-14
Ran across this and figured I'd post it and see what others may know however don't know about it's accuracy. 

[https://www.nsa.gov/news-features/press-room/Article/2311407/nsa-and-fbi-expose-russian-previously-undisclosed-malware-drovorub-in-cybersecu/](https://www.nsa.gov/news-features/press-room/Article/2311407/nsa-and-fbi-expose-russian-previously-undisclosed-malware-drovorub-in-cybersecu/)

[https://media.defense.gov/2020/Aug/13/2002476465/-1/-1/0/CSA_DROVORUB_RUSSIAN_GRU_MALWARE_AUG_2020.PDF](https://media.defense.gov/2020/Aug/13/2002476465/-1/-1/0/CSA_DROVORUB_RUSSIAN_GRU_MALWARE_AUG_2020.PDF)

[https://www.nsa.gov/Portals/70/documents/resources/cybersecurity-professionals/DROVORUB-Fact%20sheet%20and%20FAQs.pdf?ver=2020-08-13-114246-203](https://www.nsa.gov/Portals/70/documents/resources/cybersecurity-professionals/DROVORUB-Fact%20sheet%20and%20FAQs.pdf?ver=2020-08-13-114246-203)

---

### Post by crip720 on 2020-08-14
Read a bit and seems if everybody updated to the 3.7 kernel there won't be much of problem, something about signed updates/kernels being used in 3.7.  Don't know if 3.7 is typo or enough people still using kernels below 3.7.

---

### Post by poorguy on 2020-08-14
> **crip720 said:**
> Read a bit and seems if everybody updated to the 3.7 kernel there won't be much of problem, something about signed updates/kernels being used in 3.7.  Don't know if 3.7 is typo or enough people still using kernels below 3.7.

The 3.7 kernel is what ya have to wonder about and yes it may be a typo error and if not a typo error then someone needs to find a more reliable and accurate source for intelligence.

---

### Post by crip720 on 2020-08-14
Was reading ars technica story, one of the comments seems to say 3.7 was first to allow you to use signed kernels, if you did or not was up to you.  So it might be right.  Maybe even having an updated today's kernel not enough if you don't force signing.

---

### Post by poorguy on 2020-08-14
Guess we just have to wait and see what happens.

---

### Post by kansasnoob on 2020-08-14
Linux is in use on many routers so a person might want to delve into firmware updates for their router. Speaking of which I wonder if AT&T ever pushes updates to my old Motorola NVG510? I should actually buy another router and bridge it to the AT&T router, but it's soooooooooo easy to just ride along expecting a provider to be doing the right thing. I just looked and I've had this router in service for nearly 9 years :redface:

---

### Post by poorguy on 2020-08-14
When I got att fiber internet I got all new equipment and I believe you can update the firmware of the router / modem through the set up menu.

---

### Post by poorguy on 2020-08-14
> **crip720 said:**
> Was reading ars technica story, one of the comments seems to say 3.7 was first to allow you to use signed kernels, if you did or not was up to you.  So it might be right.  Maybe even having an updated today's kernel not enough if you don't force signing.

That being the case is that something that is available through updates or the repository.

I don't understand the "forced signing".

---

### Post by crip720 on 2020-08-14
By forced signing, I meant  you make sure everything has a sign certificate.  this is copied from story.  
Agency officials said that a key defense against Drovorub is to  ensure that all security updates are installed. The advisory also urged  that, at a minimum, servers run Linux kernel version 3.7 or later so  that organizations can use improved code-signing protections, which use  cryptographic certificates to ensure that an app, driver, or module  comes from a known and trusted source and hasn&#8217;t been tampered with by  anyone else.
 &#8220;Additionally, system owners are advised to configure systems to load  only modules with a valid digital signature making it more difficult  for an actor to introduce a malicious kernel module into the system,&#8221;  the advisory stated. 

 It does seem to be above my knowledge to do.

---

### Post by poorguy on 2020-08-14
OK so if I'm understanding this than this is something that is on the developers end and not a user end.

Am I even close or way outfield.

Wow this is way over my gray cell ability and knowledge.


Thanks

---

### Post by grahammechanical on 2020-08-15
I am not denying the threat nor am I going to subscribe some conspiracy  theory. But there is a propaganda war going on. Some would like to scare  us into believing that they are super geniuses. Others would like to  use our fear to justify their own counter actions.

I do not  believe in an evil genius. I do believe in an evil incompetent. There is  mismanagement and incompetence all around us. The ability to sign a  Linux kernel has been present since kernel 3.7.

> Since Linux 3.7, the kernel has supported digital signatures on loadable  kernel modules. This facility can be enabled in the kernel with  settings in CONFIG_MODULE_SIG. These options can require valid  signatures; enable automatic module signing during the kernel build  phase; and specify which hash algorithm to use. Additionally, local or  remote keys can be used. By requiring valid digital signatures, only  known valid modules can be loaded, decreasing your system&#8217;s attack  surface.

[https://www.mcafee.com/blogs/other-blogs/mcafee-labs/on-drovorub-linux-kernel-security-best-practices/](https://www.mcafee.com/blogs/other-blogs/mcafee-labs/on-drovorub-linux-kernel-security-best-practices/)

[https://www.kernel.org/doc/html/v4.15/admin-guide/module-signing.html](https://www.kernel.org/doc/html/v4.15/admin-guide/module-signing.html)

Ubuntu  16.04 started out with kernel 4.4. Ubuntu 18.04 started with the 4.15  kernel and on my system it now has kernel 5.4. Ubuntu 20.04 starts with  5.4 kernel and will during its life time get newer kernels.

Now let us discuss Secure Boot. Do I have to? Oh no!

The  root kit exists. It is designed for Linux. But how effective is it?  Does Ubuntu install Linux kernels that are not signed? Is Canonical not  taking advantage of this security feature? Ubuntu certainly provides a  small binary package that allows Ubuntu to be loaded on a Secure Boot  system. The binary package is signed by Ubuntu and is registered with  Microsoft so that the signature key is registered in the UEFI Secure  Boot signature database.

Remember Windows XP? Remember how  Microsoft had to extend its life span because organisation were not  upgrading their hardware and running Windows 8. In the UK the other year  computers in the National Health Service. (A.K.A. hospitals) became  infected with Ransomware because it was still running many machines with  Windows XP. I bet the bosses had the latest hardware.

Do those  people at the U.S.A's National Security Agency think that Linux users  are exactly like Windows users? Do they actually think Linux users would  still be running a distribution of Linux using kernel 3.7 or lower? 

I   said I believe in evil incompetents. I also believe in stupid  incompetents as well. And that at the highest level of human activity.  Is this rootkit effective on Ubuntu versions that are still supported?

Regards.

---

### Post by poorguy on 2020-08-15
Hello grahammechanical,

I like your realistic point of view spot on as always. 


Thanks

---

### Post by mastablasta on 2020-08-16
> **grahammechanical said:**
> 
Do those  people at the U.S.A's National Security Agency think that Linux users  are exactly like Windows users? Do they actually think Linux users would  still be running a distribution of Linux using kernel 3.7 or lower? 


12.04 LTS using ESM (extended support) could have kernel lower than 3.7 in it. likely security patched. 

then distributions that are designed for old PC like DSL, Slitaz etc.

---

