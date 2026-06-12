---
title: "Fedora Project Leader Max Spevack's comment on Ubuntu"
date: 2006-09-11
forum: The Cafe
---

### Post by swamytk on 2006-09-11
Here is Fedora Project Leader Max Spevack's comment on Ubuntu's binary driver distribution.

> But ultimately for Fedora the goal is Free software. Including support for proprietary drivers in our distribution would violate that tenet, but we believe it is important enough that we don't compromise. All distributions face this challenge, and it is at times a difficult question to answer. But I am proud of the fact that Fedora's choice has been consistently in favor of freedom in software.

By choosing not to ship any proprietary or binary drivers, Fedora does differ from other distributions. Ubuntu is one example, as there is very strong language about their commitment to Free and open source software, right up until the line stating that they include binary-only drivers on their CDs and in their repositories.


What do you think on it?

---

### Post by arkangel on 2006-09-11
Ubuntu also  is meant to be run only with  Free software , isnt it? this is what i read in  the ubuntu promise point 4

SO we (the users), have the chance either to continue that way or use soemthing else,  so you start installing  some close applications,  if they  were not in the repositories  we would  get these from other sources.  the same applies to fedora or any other distribution, we will get rpm instead of deb and  someone else in "Well_Known_Distro_GNU/Linux"  would be saying  the same of fedora

Linux is about choice and this is what i like about it , it is my personal  liking having  a distro that does all what i want  without paying a dime (without  counting the donations),   and if some of these app are binary closed source, let them be so, i dont fell like having an incomplete system  because some drivers are not open source(if that is the only choice i have), the only thing that would stop me  of using software is when i would have to pay for it , then i don care   whether I need it or not , "if i have to pay,  i dont need it "

Edit 
JUst to add , i do support free gnu software , if there are 2 equivalent app that do the same one free gnu , being the other close and propietary  i will choose the GNU or opensource one ,  regardles if the other is  free or nicer.

---

### Post by DoctorMO on 2006-09-11
The binary only drivers and packages arn't in the ubuntu distrobution (CD or apt-get servers) they are hosted else where.

So mainly he's wrong, just for the fact that ubuntu has a better way to aquire binary only programs doesn't mean it includes them.

---

### Post by jdong on 2006-09-11
I think the "difference" is that Fedora refuses to accept anything non-free in their repositories, and Ubuntu does accept non-free, even commercial software, to run on its platform.


I personally think comparing Fedora to Ubuntu is comparing apples to oranges (ha. orange. how appropriate for dapper). Fedora is designed to be a testing ground for RedHat to try the latest and greatest from the Linux world, in the hopes of stabilizing some innovative technology to use on its RHEL products. Ubuntu, however, is more of that RHEL product -- a product targeted at end-users and should be ready for use.

Having binary-only stuff around only hinders open source development -- look at vmware being broken in Edgy by hal/dbus as an example. However, in a product for end-users, not having a wealth of drivers or programs around will make the experience incomplete. So, both distributions in my mind are doing the right thing regarding free software, in accordance to their goals. And Ubuntu does give back to the open source community, just like Fedora. In the end, that's what matters in my mind.



BTW, I have to point out that Fedora Core 6 delayed the introduction of Xorg 7.1 because it would break ATI/NVidia's binary graphics drivers (at the time the updated versions weren't out yet). Huh? What the heck?


P.S. I'm not saying that Fedora, by being on the edge, is inherently unstable or unsuitable as a Linux distro for the average user / server admin.... In fact, I've found Fedora to be quite suitable as long as you don't need any of the binary-only drivers (else it does tend to be a hassle at times)

---

### Post by NESFreak on 2006-09-11
Ubuntu has separate repo's for that, they arent included. They are just there to give people the FREEDOM to use binary software.

---

### Post by 3rdalbum on 2006-09-11
[QUOTE=Wikipedia]
Main and Universe contain software which meets the Ubuntu licence requirements, which correspond roughly to the Debian Free Software Guidelines.[15] There is one caveat for Main, in that **it also may contain binary firmware** and selected fonts used in supported software that cannot be modified without permission so long as their redistribution is unencumbered.[/QUOTE]

It's a balancing act between being all Free, and being compatible with people's computers. Ubuntu's decision means that more computers will be compatible with Linux, which benefits us all.

---

### Post by ComplexNumber on 2006-09-11
> BTW, I have to point out that Fedora Core 6 delayed the introduction of Xorg 7.1 because it would break ATI/NVidia's binary graphics drivers (at the time the updated versions weren't out yet). Huh? What the heck?
fedora 6 isn't to be released until october.


> 
Fedora is designed to be a testing ground for RedHat to try the latest and greatest from the Linux world, in the hopes of stabilizing some innovative technology to use on its RHEL products. Ubuntu, however, is more of that RHEL product -- a product targeted at end-users and should be ready for use.
apparently, it isn't. also, ubuntu is not to be compared to RHEL. in fact, ubuntu is more cutting edge than fedora if you compare them correctly. personally, i have found fedora to be the more stable of the 2, so ubuntu has some considerable catching up to do if its intended to be compared to RHEL.

---

### Post by jdong on 2006-09-11
> **ComplexNumber said:**
> fedora 6 isn't to be released until october.

Yes, I know. I'm speaking of development activity in FC6t2/rawhide. As in, Fedora introduction of Xorg 7.1 was postponed for the sole reason of waiting for binary drivers to catch up.

> 
apparently, it isn't. also, ubuntu is not to be compared to RHEL. in fact, ubuntu is more cutting edge than fedora if you compare them correctly. personally, i have found fedora to be the more stable of the 2, so ubuntu has some considerable catching up to do if its intended to be compared to RHEL.

That might be your experience, but Ubuntu is designed to be an enterprise-ready operating system, and so is RHEL4. The age of the packages has nothing to do with it.

---

### Post by ComplexNumber on 2006-09-11
> That might be your experience, but Ubuntu is designed to be an enterprise-ready operating system, and so is RHEL4. The age of the packages has nothing to do with it. i'm not too sure if i understand the last sentence. if ubuntu is more cutting edge than fedora, and yet, is still intended to be enterprise-ready, how can the age of the package be nothing to do with it. its almost as if you're saying that ubuntu's packages are inherently more mature.
therefore, "enterprise-ready" is nothing more than a mere label.

---

### Post by jdong on 2006-09-11
Packages don't necessarily have to be more mature / aged in order for a distribution to be able to consider itself enterprise-ready... They just have to be adequately maintained for bugfixes. Look at SLED10 for example...

---

### Post by ComplexNumber on 2006-09-11
> **jdong said:**
> Packages don't necessarily have to be more mature / aged in order for a distribution to be able to consider itself enterprise-ready... They just have to be adequately maintained for bugfixes. Look at SLED10 for example...
i edited my post to add the last sentence. by my way of thinking, it should say something about the (likely) stability of the packages.

---

### Post by jdong on 2006-09-11
Your edited assessment is correct. Enterprise-ready is a label, a goal, a stated purpose, more than anything else.

---

