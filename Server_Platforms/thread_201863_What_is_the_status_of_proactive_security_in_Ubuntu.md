---
title: "What is the status of proactive security in Ubuntu 6.06 ?"
date: 2006-06-22
forum: Server Platforms
---

### Post by dominic2 on 2006-06-22
Hello, this is my first post on this forum. I would like to know what is the status of proactive security in Ubuntu 6.06. All documents I find about that are outdated. I know there is a PAX enabled kernel available, even if it is not the default kernel. What about PIE (position independent executable) and SSP ? Are the Ubuntu packages for Ubuntu 6.06 compiled with these options yet or is it still post ponned to later versions ?

Thank you for your answer. :)

---

### Post by asimon on 2006-06-22
There is neither pie nor ssp in Dapper. Wishes for proactive security in Ubuntu are old but it was always labled a low-priority thing and was always postponed. I am very curious if they push something into Edgy. Ubuntu is years behind in this regard compared to some other well known distro.

Currently the devs are at the [Ubuntu Developer Summit in Paris](https://wiki.ubuntu.com/UbuntuDeveloperSummitParis) where they approve or disapprove [specs](https://launchpad.net/distros/ubuntu/+specs) and decide about the goals for Edgy.

Especially interesting is the [gcc-ssp spec](https://launchpad.net/distros/ubuntu/+spec/gcc-ssp) (have a look at the proactive security roadmap link there), which is now even of high priority and looks promising.

---

### Post by dominic2 on 2006-06-22
[QUOTE=asimon]There is neither pie nor ssp in Dapper. Wishes for proactive security in Ubuntu are old but it was always labled a low-priority thing and was always postponed. I am very curious if they push something into Edgy. Ubuntu is years behind in this regard compared to some other well known distro.

Currently the devs are at the [Ubuntu Developer Summit in Paris](https://wiki.ubuntu.com/UbuntuDeveloperSummitParis) where they approve or disapprove [specs](https://launchpad.net/distros/ubuntu/+specs) and decide about the goals for Edgy.

Especially interesting is the [gcc-ssp spec](https://launchpad.net/distros/ubuntu/+spec/gcc-ssp) (have a look at the proactive security roadmap link there), which is now even of high priority and looks promising.[/QUOTE]
Well, good to know that at least SSP may be introduced in the next version. In the mean time, except for (Hardened) Gentoo, what are those other well known distros wich have those features ? I'm using Gentoo right now because it's the only distro I know of where I can have SSP and PIE, but I'm getting sick of compiling...

---

### Post by asimon on 2006-06-22
> **dominic2]Well, good to know that at least SSP may be introduced in the next version.[/quote]
I hope for more.  said:**
> 
In the mean time, except for (Hardened) Gentoo, what are those other well known distros wich have those features ? I'm using Gentoo right now because it's the only distro I know of where I can have SSP and PIE, but I'm getting sick of compiling...
I had Fedora in mind, it has heap randomization, FORTIFY_SOURCE, SSP, pie, SELinux, and exec shield - pretty good when it comes to proactive security.

---

### Post by dominic2 on 2006-06-22
> **asimon]I hope for more.  said:**
> 
So do I.

[QUOTE=asimon]I had Fedora in mind, it has heap randomization, FORTIFY_SOURCE, SSP, pie, SELinux, and exec shield - pretty good when it comes to proactive security.
I considered Fedora Core, but then I found out that SSP and PIE are only for some selected packages like services. Guess I'll keep compiling for another 6 months, at least... ;)

---

### Post by dominic2 on 2006-07-04
[QUOTE=dominic2]So do I.


I considered Fedora Core, but then I found out that SSP and PIE are only for some selected packages like services. Guess I'll keep compiling for another 6 months, at least... ;)[/QUOTE]
Well, I double checked and it turns out I was wrong. While PIE is for selected packages only, there are more "selected" packages than I tought, the mozilla suite is one of those. Also, all packages are compilled with both SSP and FORTIFY_SOURCE. So I'll give Fedora a try. But don't be afraid, as soon as Ubuntu starts taking proactive security seriously, I'll definitly give it a try too. ;)

---

### Post by nthdegree on 2006-07-16
Finally someone who thinks a little on my terms.

Security should be top priority, Fedora, RHEL, Gentoo, Mandriva etc. are either on their way to implementing proactive protection fully or already have it.  This is my one gripe with ubuntu, it has no level of enhanced protection, unless you stay ahead of the threat patches and updates are somewhat useless.

Security should be in the idea that your protection keeps you secure while a patch is being made, vulnerabilities in software code should be discovered but never exploitable.

Come on SABDFL think of it as an investment, get a load of developers together and pay them if you have to, to get SELinux or RSBAC (both are good), PIE, Exec-Shield and SSP security set up for ubuntu.

The extra security will attract good business too, so you can afford to put more money into ubuntu and thus make things even better!

---

### Post by asimon on 2006-07-16
> **nthdegree said:**
> Security should be top priority, Fedora, RHEL, Gentoo, Mandriva etc. are either on their way to implementing proactive protection fully or already have it.  This is my one gripe with ubuntu, it has no level of enhanced protection, unless you stay ahead of the threat patches and updates are somewhat useless.
So far the only thing which happened in Edgy is enabling --fstack-protector by default, although there was no recompilation day to actually make use of it for all applications. I dunno why they don't activate FORTIFY_SOURCE too.

SELinux will probably has to happen in Debian first, and the other day I've read in a DD's blog that there is currently nobody actively working on it in Debian.

> **nthdegree said:**
> 
Security should be in the idea that your protection keeps you secure while a patch is being made, vulnerabilities in software code should be discovered but never exploitable.
A very good example is that [the newest local privilege escalation in Linux was stopped by SELinux ](http://www.redhat.com/archives/fedora-selinux-list/2006-July/msg00071.html). Even if the bad guys would have known about this exploit for months, SELinux would have protected you. This is exactly why proactive security is too good to ignore it.

---

