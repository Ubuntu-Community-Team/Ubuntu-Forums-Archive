---
title: "Applet similar to caffeine?"
date: 2012-11-30
forum: Ubuntu Development Version
---

### Post by GreatDanton on 2012-11-30
Is there any applet which is similar to caffeine for Ubuntu 13.04. I noticed they didn't make ppa for 12.10 and 13.04. So is there any other applet similar to caffeine?

Regards.

---

### Post by VinDSL on 2012-12-01
Can't say I know of any alternative app(s).

And, can't remember where I got it, but...

Caffeine is installed on this machine, and it works.  ;)



[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-30-nov-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-30-nov-2012-2.png")[/INDENT]

---

### Post by jfernyhough on 2012-12-01
The quantal version of caffeine works fine on raring...

$ apt-cache policy caffeine 
caffeine:
  Installed: 2.4.1+464~quantal1
  Candidate: 2.4.1+464~quantal1
  Version table:
 *** 2.4.1+464~quantal1 0
        500 [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by ronacc on 2012-12-02
you could also try compiling it from source .

---

### Post by screaminj3sus on 2013-01-19
EDIT: wrong tab

---

### Post by crepito on 2013-03-02
Hello, here's how i solved this problem.

1 -> Add ppa: sudo add-apt-repository ppa:caffeine-developers/ppa
2 -> Go to Software & Updates > Other Software > Select: [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) raring main > Edit > Change raring to quantal
3 -> sudo apt-get update && sudo apt-get install caffeine
4 -> profit :)

---

