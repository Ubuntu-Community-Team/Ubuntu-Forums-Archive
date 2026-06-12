---
title: "apache/karmic web server security"
date: 2010-11-19
forum: Security
---

### Post by gobotsoup on 2010-11-19
Sorry for the generality of this question, but any advice would be welcome. I have a web server set up on Ubuntu 9.10 (Karmic) with apache. I noticed when I looked at my apache access logs there were a bunch of ips that would hit my http port and run mysql/php scripts over and over (at least that is my assumption). So, I put up a firewall (firestarter). I'm wondering what security measure I could take to ensure these weird scripts or whatever they are don't harm my system. I would like to do this while still allowing open access to my web server (right now I have firestarter set to only allow specific ips to hit my server). Thanks!

---

### Post by movieman on 2010-11-20
Presumably they're trying to exploit holes in older versions of those scripts. The best solution is to get rid of php, since it seems to be the main route used to break into web servers, otherwise ensure everything is kept up to date so any new holes are patched ASAP.

You could also create an apparmor profile, but that's hard to do for apache as it uses all kinds of resources on the system.

---

### Post by OpSecShellshock on 2010-11-20
Probably just getting hit by SQL injection and remote file inclusion attempts. Happens to pretty much all web servers that host public facing content. Was it successful?

---

### Post by bodhi.zazen on 2010-11-20
> **gobotsoup said:**
> Sorry for the generality of this question, but any advice would be welcome. I have a web server set up on Ubuntu 9.10 (Karmic) with apache. I noticed when I looked at my apache access logs there were a bunch of ips that would hit my http port and run mysql/php scripts over and over (at least that is my assumption). So, I put up a firewall (firestarter). I'm wondering what security measure I could take to ensure these weird scripts or whatever they are don't harm my system. I would like to do this while still allowing open access to my web server (right now I have firestarter set to only allow specific ips to hit my server). Thanks!

Are you running mysql and / or php ?

It is a broad question and you should :

1. Remove unnecessary services. This is why IMO servers should be minimal installations.

2. Keep your system up to date. Karmic is getting long in the tooth and is almost at the end of life, I would urge you to upgrade to Ubuntu 10.04.

3. Google search securing apache, mysql, and php.

4. Only run "mature" applications. One of many examples would be wordpress. If you write your own php scripts, learn to secure them.

5. Learn to use Apparmor.

6. Take a look at mod_security and mod_evasive.

---

### Post by gobotsoup on 2010-11-20
thanks a lot! I'm going to try this stuff.

---

