---
title: "Would you recommend AppArmor and other security measures?"
date: 2010-08-31
forum: Security
---

### Post by jcd29 on 2010-08-31
Or do you just use Ubuntu feeling safe enough without them?

If you do use AppArmor and other security measures, what do you use them for? Obviously Firefox and Chrome would be two things. But what else?

---

### Post by Bachstelze on 2010-08-31
It depends what you want to protect against. Basically anything that processes untrusted data is a candidate for apparmoring.

---

### Post by juancarlospaco on 2010-08-31
This ^

*i use LXC sometimes.*

---

### Post by bodhi.zazen on 2010-08-31
> **jcd29 said:**
> Or do you just use Ubuntu feeling safe enough without them?

If you do use AppArmor and other security measures, what do you use them for? Obviously Firefox and Chrome would be two things. But what else?

On Ubuntu I use apparmor to confine all applications that are network aware (able to connect to the internet) and to confine the guest account. In rare instances I use it to restrict users who ssh into my box.

---

### Post by anomie on 2010-09-01
[QUOTE=jcd29]Would you recommend AppArmor and other security measures?[/QUOTE]

Seriously, if you've got the time and will to learn and utilize fundamental MAC (and/or RBAC, DAC) and its more practical implementations, then by all means...

That is likely going to be a major building block of widespread "secure" computing in the future.

---

### Post by Cypher1101 on 2010-09-03
> **bodhi.zazen said:**
> On Ubuntu I use apparmor to confine all applications that are network aware (able to connect to the internet) and to confine the guest account. In rare instances I use it to restrict users who ssh into my box.

 Not to hijack the thread, but how are you confining users with Apparmor? I've searched through the man pages, Novell's on-line documentation, and a few of the sample profiles you've listed, but all I've found is how to use RBAC to build limited admin profiles (for restricted permissions on sudo) and limiting access to only the files that a user owns. I didn't know it was possible to confine a specific user as well. Could you explain the method you use to confine an account as opposed to a file or an executable?

---

### Post by HermanAB on 2010-09-03
Howdy,

Just my tuppence worth:
Systems like SELinux, Tomoyo and AppArmor are good for use on government systems.  Their use is limited on commercial systems, due to the cost - the effort to configure and maintain any of them is considerable.

---

### Post by bodhi.zazen on 2010-09-03
> **Cypher1101 said:**
> Not to hijack the thread, but how are you confining users with Apparmor? I've searched through the man pages, Novell's on-line documentation, and a few of the sample profiles you've listed, but all I've found is how to use RBAC to build limited admin profiles (for restricted permissions on sudo) and limiting access to only the files that a user owns. I didn't know it was possible to confine a specific user as well. Could you explain the method you use to confine an account as opposed to a file or an executable?

I do it with "jailbash" . jailbash is a hard link to /bin/bash and is confined by apparmor.

I wrote a brief overview here :

[http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

That post has a link to my jailbash apparmor profile. You would need to adapt.

---

### Post by bodhi.zazen on 2010-09-03
> **HermanAB said:**
> Howdy,

Just my tuppence worth:
Systems like SELinux, Tomoyo and AppArmor are good for use on government systems.  Their use is limited on commercial systems, due to the cost - the effort to configure and maintain any of them is considerable.

I would agree, apparmor currently has a high maintance as there are insufficinet default profiles.

I would disagree with selinux, selinux is much easier to deploy in Fedora 13 and the graphical tools to manage selinux are much improved. It is a targeted policy, but minimal problems.

---

### Post by Cypher1101 on 2010-09-04
I see, the solution is to force a user into a confined shell, thus confining the entire account. I'd have never thought of that:o
Thanks

---

### Post by OnlineBuddy on 2010-09-05
(sorry for being little off topic)..
.
i am in final year of my b.tech...and i have to give a seminar...i have choosen LINUX APPLICATION SECURITY..
i also want to include topic about DAC/MAC/LSM...
.
so what should i choose..AppArmor or SELinux...need help ASAP..

---

### Post by wacky_sung on 2010-09-06
> **OnlineBuddy said:**
> (sorry for being little off topic)..
.
i am in final year of my b.tech...and i have to give a seminar...i have choosen LINUX APPLICATION SECURITY..
i also want to include topic about DAC/MAC/LSM...
.
so what should i choose..AppArmor or SELinux...need help ASAP..

See [here]("http://www.cyberciti.biz/tips/selinux-vs-apparmor-vs-grsecurity.html") for the difference.I will prefer to go for grsecurity which is the easy way out.

---

