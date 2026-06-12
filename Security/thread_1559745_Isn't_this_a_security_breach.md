---
title: "Isn't this a security breach?"
date: 2010-08-23
forum: Security
---

### Post by asdfjkl semi on 2010-08-23
When you run something with root permissions, it does not require your password to run another sudo-command for 5 minutes. Now what is to stop a tutorial page to make a javascript to run a malicious command after a certain amount of time, say four minutes?

---

### Post by uRock on 2010-08-23
NoScript and AppArmor are your friends. The only way java can run as root is if you open the browser as root, afaik.

---

### Post by mobilediesel on 2010-08-23
> **asdfjkl semi said:**
> When you run something with root permissions, it does not require your password to run another sudo-command for 5 minutes. Now what is to stop a tutorial page to make a javascript to run a malicious command after a certain amount of time, say four minutes?

As uRock said, you would have to run the browser as root in order for a tutorial page to gain root access.

---

### Post by rookcifer on 2010-08-23
Running a sudo command only allows the sudo timeout on that one terminal session.  It *does not* apply to anything else on the machine.  As the others said, you would have to run the browser as root to fall victim to such an attack.

---

### Post by cdenley on 2010-08-24
> **rookcifer said:**
> As the others said, you would have to run the browser as root to fall victim to such an attack.

Technically, if your browser is compromised in a way that allows the attacker to execute arbitrary code, they could wait for you to use sudo, kill your terminal session, re-use your tty, then use sudo before your timestamp times out without needing a password. I wrote a proof-of-concept script for such an attack a while ago. If you're worried about such an attack, set timestamp_timeout to 0 in your sudoers file.

This has been discussed before. Search the forum before creating a new thread.

---

### Post by uRock on 2010-08-24
> **cdenley said:**
> Technically, if your browser is compromised in a way that allows the attacker to execute arbitrary code, they could wait for you to use sudo, kill your terminal session, re-use your tty, then use sudo before your timestamp times out without needing a password. I wrote a proof-of-concept script for such an attack a while ago. If you're worried about such an attack, set timestamp_timeout to 0 in your sudoers file.

This has been discussed before. Search the forum before creating a new thread.
This is why NoScript and AppArmor are good tools to have configured.

---

### Post by cdenley on 2010-08-24
> **uRock said:**
> This is why NoScript and AppArmor are good tools to have configured.

Yes, but I think the concern was for privilege escalation in general, not specifically for browser exploits. I'm guessing a javascript browser exploit was only an example.

---

### Post by meskes on 2010-08-26
The Firefox Apparmor profile is inorged by default though so, if someone who doesn't wtf aa is, they're not going to know how set the profile nor are they going to know what's going on when the script causes funkiness with Firefox, which will invariably do. Which is why the script is ignored in the first place.

---

### Post by uRock on 2010-08-27
> **meskes said:**
> The Firefox Apparmor profile is inorged by default though so, if someone who doesn't wtf aa is, they're not going to know how set the profile nor are they going to know what's going on when the script causes funkiness with Firefox, which will invariably do. Which is why the script is ignored in the first place.
This is why a new user should be searching the net and learning the security tools used by their OS, such as AppArmor. The typical use of AA is explained in the Ubuntu Security thread that hopefully newcomers get to read. I think I seen it mentioned in the Ubuntu manual, but I don't think the manual went into detail.

---

### Post by TwoEars on 2010-08-27
> **asdfjkl semi said:**
> When you run something with root permissions, it does not require your password to run another sudo-command for 5 minutes. Now what is to stop a tutorial page to make a javascript to run a malicious command after a certain amount of time, say four minutes?

> **uRock said:**
> NoScript and AppArmor are your friends. The only way java can run as root is if you open the browser as root, afaik.

As a side note, Javascript is not Java.

---

### Post by uRock on 2010-08-27
> **TwoEars said:**
> As a side note, Javascript is not Java.

:D No way! Your kidding right? :D

---

### Post by jcd29 on 2010-08-27
Is this a real major concern in Linux? I thought it was very unlikely for something like this to happen outside Windows.

---

### Post by TwoEars on 2010-08-27
> **jcd29 said:**
> Is this a real major concern in Linux? I thought it was very unlikely for something like this to happen outside Windows.

Generally, don't run software as root, and you're fairly safe as the number of sites that would carry out attacks on Linux desktop operating systems is fairly small, perhaps limited to a very few.

---

### Post by uRock on 2010-08-27
> **TwoEars said:**
> Generally, don't run software as root, and you're fairly safe as the number of sites that would carry out attacks on Linux desktop operating systems is fairly small, perhaps limited to a very few.

I agree. Most of the sites that beg for Linux attention are trying to bring in more people, not taint them. One day this may change, but I hope not.

---

### Post by cdenley on 2010-08-30
> **jcd29 said:**
> Is this a real major concern in Linux? I thought it was very unlikely for something like this to happen outside Windows.

Firefox is used on both. Many firefox vulnerabilities can be exploited on either OS. The biggest concern is probably the non-free adobe flash plugin, though. The browser (with plugins) is probably the second weakest point of vulnerability for any desktop system after the actual user. This is why there is an apparmor profile for firefox.

---

### Post by Jigen on 2010-08-31
> **cdenley said:**
> Firefox is used on both. Many firefox vulnerabilities can be exploited on either OS. The biggest concern is probably the non-free adobe flash plugin, though. The browser (with plugins) is probably the second weakest point of vulnerability for any desktop system after the actual user. This is why there is an apparmor profile for firefox.

yes, but it must be enabled, since it is disabled by default. I think we (as a community, I mean) should highlight more this point to new users. I read that it is not enabled since it may break down extensions, etc. however I decided to enable it one week ago and haven't observed any problem so far (and I run approx. a dozen of extensions, such as noscript, showip, forecastfox, wot, etc.). Maybe I was just lucky?:P

---

### Post by q.dinar on 2010-09-16
older threads etc about this:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=429549](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=429549)
[http://ubuntuforums.org/showthread.php?t=1045209](http://ubuntuforums.org/showthread.php?t=1045209)
[http://ubuntuforums.org/showthread.php?t=1051348](http://ubuntuforums.org/showthread.php?t=1051348)
[http://brainstorm.ubuntu.com/idea/17754/](http://brainstorm.ubuntu.com/idea/17754/)
[https://bugs.launchpad.net/ubuntu/+bug/377244](https://bugs.launchpad.net/ubuntu/+bug/377244)
[http://ubuntuforums.org/showthread.php?t=1236036](http://ubuntuforums.org/showthread.php?t=1236036)
[http://www.welinux.ru/post/2314](http://www.welinux.ru/post/2314) - in russian

this is very big security hole if user runs many different programs. in many cases he cannot check or trust program, that it does not have behavior in it to use this hole. most programs' license say: run at own risk.
there are many programs distributed from program's official site.
even binaries in official repository hard to check, aren't they? and ubuntu team supports only part of them.

how to use sudo and protect yourself: look little scripts' source, create apparmor profile for big scripts and binaries before you install them, or create apparmor profile just before you first run them, if they do not have much thing as postinstall/preinstall scripts. if you trust the program, you can set apparmor profile to complain mode.

---

