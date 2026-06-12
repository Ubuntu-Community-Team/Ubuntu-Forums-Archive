---
title: "Sun Ultra2 Creator 3d Worstation installation"
date: 2006-11-20
forum: Sun Sparc Users
---

### Post by Jakykong on 2006-11-20
To whomever reads this post:

I am a highschool student, freshly A+ certified, and now plopped in front of a Sun Ultra2 Workstation. I'm assuming this machine has a Sparc processor inside (correct me if I'm wrong). This is a fairly old machine; I downloaded ubuntu-server 6.10's ISO, and burned it to a CD. 

With the CD in the drive, I started the workstation to find that it starts to read the CD, but does not boot from it -- instead, going to the resident OS (solaris; which is useless. Being a donated computer, we don't have the root password). I searched google with terms like "Sun Ultra2 How-To boot CD" -- to no avail. A forum search here revealed nobody posting about any ultra2 computers. Documentation on the Ubuntu website didn't reveal much useful information (I know nothing about Sun computers; I went in expecting at least SOME similarities with PCs, apparently not).

Could anyone help me get started installing Ubuntu on this workstation?

---

### Post by netztier on 2006-11-20
> **Jakykong said:**
> A forum search here revealed nobody posting about any ultra2 computers. Documentation on the Ubuntu website didn't reveal much useful information.

Then your forum search strategy and phantasy for composing keywords *definitely* needs to improve. 

Alone by using "Sun Ultra2" as search terms, I get 7 threads in which I know I have posted myself. About Sun Ultra2, too. *shakes head*. And had you asked google about installing Linux on Ultras, you'd most cerainly have found Ultralinux.org's FAQ and it's [Secion 5]("http://www.ultralinux.org/faq.html#s_5") about booting.

The key is: interrupt the boot process by hitting Stop-A on the Sun keyboard or send a break signal when connected via serial console.

Then hit "boot cdrom" at the ok> prompt, and off you go.

regards

Marc

---

### Post by portnoy714 on 2008-06-28
I've tried without success to install Ubuntu on my sun ultra2. It seems to run fine until it has to look for the cd drive and then cannot find it. Huh? How does it boot that far if it cannot find the drive? Nothing I try gets me past that point. My machine is just a stock unit with the internal cd drive. The 'boot cdrom' command gets things started just fine, it just stalls at the install point when it's looking for the cd drive.  :(

---

