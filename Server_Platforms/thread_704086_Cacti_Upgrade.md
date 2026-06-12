---
title: "Cacti Upgrade"
date: 2008-02-22
forum: Server Platforms
---

### Post by Wasca on 2008-02-22
Hi All

I just did an apt-get update, apt-get upgrade for my 6.06LTS install and it updated my cacti install

Now I can't login to my cacti install all I see is this when I browse to the cacti location

Invalid PHP_SELF Path

Could someone please help me fix this.

---

### Post by Micke2k on 2008-02-22
Hi,


i have the same problem updated Cacti from

0.8.6j-1.1ubuntu0.1 to 0.8.6j-1.1ubuntu0.2

and now i get:


Invalid PHP_SELF Path 


[http://forums.cacti.net/about25759.html](http://forums.cacti.net/about25759.html) this might be the solution.

---

### Post by Micke2k on 2008-02-22
i downgraded the package and got it to work again! there is a tutorial on this forum how to do it just google," how to downgrade package +ubuntu"


dont have time to link it got to go :)

---

### Post by Linuturk on 2008-02-22
I'd just like to say I also have this problem.

---

### Post by slackenerny on 2008-02-23
I have the same, could "fix" ist by downgrading, but that doesn't seem to be a long-term solution...

Any ideas how to permanently fix it?

---

### Post by blihtar on 2008-03-09
> **Micke2k said:**
> i downgraded the package and got it to work again! there is a tutorial on this forum how to do it just google," how to downgrade package +ubuntu"


dont have time to link it got to go :)

here is procedure
1. check version now and before
"apt-cache policy cacti"

2.you will get something like that ( screen after downgrade)
"cacti:
Installed: 0.8.6j-1.1
Candidate: 0.8.6j-1.1ubuntu0.2
Version table:
0.8.6j-1.1ubuntu0.2 0
500 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
*** 0.8.6j-1.1 0
500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
100 /var/lib/dpkg/status
"

3.then downgrade picking lower version like
"apt-get install cacti=0.8.6j-1.1"

---

