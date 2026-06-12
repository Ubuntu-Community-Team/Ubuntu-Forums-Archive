---
title: "Is it really necessary to chroot the LAMP server in Ubuntu?"
date: 2010-08-21
forum: Security
---

### Post by TheAlien on 2010-08-21
Is it really necessary to chroot the LAMP server in Ubuntu? I've heard that it's pretty secure by default. But what do you think?

---

### Post by bodhi.zazen on 2010-08-21
chroot is old school.

I would use apparmor if you feel the defaults need to be hardened and look at tools such as mod_security, depending on how paranoid I was with the server.

---

### Post by unspawn on 2010-08-22
First of all *"I've heard that it's pretty secure by default."* is as bad as a reply saying *"don't worry"* w/o explanation but nonetheless a typical human approach to solving problems. As equally inadmissble as hearsay is in court the same applies to using Linux: (gaining) knowledge is key (using web-based administration panels not being a substitute for theoretical knowledge and practical experience) and *everything can be tested*: something adheres to basic rules of security or it doesn't, something is either safe or it isn't.

The "pretty secure by default" security posture may apply to the web server software itself. It doesn't apply to
- configuration errors (say loading modules you don't need),
- lax access rights (say 'chmod -R 0777 $DOCROOT') and
- no access restrictions (should everybody access /phpmyadmin ?),
- running unsafe home-brewn scripts (say to add users or to change users passwords), 
- stale releases of web stack software like web logs, web-based email, forum software, collaboration suites or administration tools (and that happens *all the time*). 
* Even if you have the *current* version of those you may be exposing holes if you don't upgrade when upgrades are released.

So in addition to what's been said already
- using sane configuration defaults,
- hardening your machine,
- *regularly testing* your setup from a remote address and
- responding to logged alerts 
should be considered defaults.

---

### Post by Bachstelze on 2010-08-22
> **unspawn said:**
> As equally inadmissble as hearsay is in court the same applies to using Linux

The same applies to using anything.

> **unspawn said:**
> something is either safe or it isn't.

Not true.  Something is (or is not) safe only in a particular context, and something that is safe in one context may be unsafe in another.  For example, most people will be perfectly safe using Apache, MySQL and PHP, and possibly AppArmor.  The NSA thinks this is not safe and use their own software.

Any security analysis that doesn't take into account the context in which the system will be used is moot.

---

### Post by bodhi.zazen on 2010-08-22
> **Bachstelze said:**
> Any security analysis that doesn't take into account the context in which the system will be used is moot.

This is a good point. Apache serving a few html from a server in your closet is not the same as running a financial website or bank.

Also, Apache security is not the same as mysql and php security.

Last you need to take into account the concerns (or at times seeming paranoia) of the person who wants a secure environment and what a security breach implies.

I think if you are going to run a server, and not "simply" manage content, you need to read and understand the security implications. Unfortunately this is an ongoing process as threats and security implications / solutions are not static.

---

### Post by unspawn on 2010-08-22
> **Bachstelze said:**
> The same applies to using anything.
What is clear to some may not be clear to others. Why else would people use phrases like "I think", "I heard", "they say", "don't worry"?..


> **Bachstelze said:**
> Something is (or is not) safe only in a particular context
Good call wrt context but my point was about **testing what you change** as that aspect usually doesn't get the attention it deserves. 

An easier example (or at least w/o potential for heated arguments) would be serving purely static HTML pages vs using say Joomla 1.5.12. Limiting scope to only net-facing web stack SW, in the first case only flaws in the web server would be exposed but in the latter case flaws in the web server plus those in the portal software (among which in this version are: arbitrary PHP execution, local file inclusion, remote file inclusion and cross-site scripting vulns *assortis*).

---

### Post by juancarlospaco on 2010-08-23
Get LXC

---

### Post by HermanAB on 2010-08-23
OK, to go back to the original question:

No, chroot doesn't buy you much, if anything.  

Apparmor, SELinux and Tomoyo are the modern ways to harden services.

However, I have had many web servers running for many years on the wild wild web, without any of the above.

---

### Post by bodhi.zazen on 2010-08-23
> **juancarlospaco said:**
> Get LXC

Although you will get many opinions, IMO LXC is still in rapid development and, again, IMHO, not yet ready for a production environment. I have some security concerns with LXC and the code is in such rapid development it is impossible to say that new problems will or will not be identified.

If you need anything more then hardening your server and apache, use apparmor or mod_security, or any tried and true security tool.

LXC is probably "OK" for personal web sites.

---

### Post by TheAlien on 2010-09-01
> **bodhi.zazen said:**
> chroot is old school.

I would use apparmor if you feel the defaults need to be hardened and look at tools such as mod_security, depending on how paranoid I was with the server.

Are there any good guides on setting up apparmor with Apache out there? Apparmor seems to be installed by default on my box, but setting it up seems a little bit not-straight-forward. :)

---

### Post by bodhi.zazen on 2010-09-01
> **TheAlien said:**
> Are there any good guides on setting up apparmor with Apache out there? Apparmor seems to be installed by default on my box, but setting it up seems a little bit not-straight-forward. :)

There should already be a profile for apache.

See also :

[Introduction to AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906")

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

[http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/index.html](http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/index.html)

---

### Post by TheAlien on 2010-09-16
> **bodhi.zazen said:**
> There should already be a profile for apache.

See also :

[Introduction to AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906")

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

[http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/index.html](http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/index.html)

Thank you bodhi!

Sorry for my late responses to this thread!

I would like to use AppArmor to control Apache, PHP and MySQL (the whole LAMP program package) on Ubuntu Server.
Is it possible to set this up for a novice like me? I was hoping for profiles on silver platters, but don't know where to get them.
I've been reading your tutorial, and could always try to make the profiles myself, but it seems a little bit scary to me, because I'm afraid of making things worse than they already may be.

Any further help from anyone is strongly appreciated, thanks! :)

---

### Post by cariboo on 2010-09-16
There are more pre-made profiles in the repositories, just install apparmor-profiles. Once the package is installed, have a look in /etc/apparmor.d.

---

### Post by TheAlien on 2010-09-25
Still no Apache2/LAMP apparmor profiles to be found. :(

I would really like to have a complete LAMP profile for Ubuntu Server.

---

### Post by bodhi.zazen on 2010-09-25
> **TheAlien said:**
> Still no Apache2/LAMP apparmor profiles to be found. :(

I would really like to have a complete LAMP profile for Ubuntu Server.

Did you install apparmor-profiles ?

If so, what is missing that you want ?

---

### Post by TheAlien on 2010-09-28
> **bodhi.zazen said:**
> Did you install apparmor-profiles ?

If so, what is missing that you want ?

usr.sbin.apache2

I already have usr.sbin.mysql, and that's good! :)

---

### Post by bodhi.zazen on 2010-09-28
The apache profile should have been included either in apache or apparmor-profiles.

If it was not I would file a bug report and download the source code to find the profile.

I would 

```
ls /etc/apparmor.d/ | grep apache
```

---

### Post by TheAlien on 2010-09-29
There's a folder there with a file: /etc/apparmor.d/apache2.d/phpsysinfo

Is that the Apache2 profile?

***EDIT***

I found the profile in the source:
[http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.5.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.5.orig.tar.gz)

I also found something to get started:
[http://ubuntuforums.org/showthread.php?t=1267605](http://ubuntuforums.org/showthread.php?t=1267605)

---

