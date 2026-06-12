---
title: "snort installation instructions"
date: 2009-12-23
forum: Security
---

### Post by mcclunyboy on 2009-12-23
hi

i am getting this error when following these instructions:

[http://ubuntuforums.org/showthread.php?t=145641](http://ubuntuforums.org/showthread.php?t=145641)

errror:

NS config: 
    DNS Client rdata txt Overflow Alert: ACTIVE
    Obsolete DNS RR Types Alert: INACTIVE
    Experimental DNS RR Types Alert: INACTIVE
    Ports: 53
SSLPP config:
    Encrypted packets: not inspected
    Ports:
      443      465      563      636      989
      992      993      994      995
    Server side data is trusted

+++++++++++++++++++++++++++++++++++++++++++++++++++
Initializing rule chains...
ERROR: /etc/snort/rules/community-smtp.rules(13) => !any is not allowed
Fatal Error, Quitting..


any help?!

---

### Post by bodhi.zazen on 2009-12-23
It appears to be a problem with your snotr rules. Where did you get them from ?

You could try looking at the rule set in question (/etc/snort/rules/community-smtp.rules) and see if you can determine the problem.

---

### Post by mcclunyboy on 2009-12-24
i think its to do with the variable defining my IP...

It defaults to "any" and i think i need to specify my own IP (or something)

Shall need to investigate further ....

---

### Post by mcclunyboy on 2009-12-27
right I got it working - almost...

i changed the variable for home network to include just my router IP...however the "alert" file doesn't contain anything  - i suspect I have a problem - any thoughts?

Again I suspect it is an issue with the variables for rule set or IP...can someone tell me a standard one.

---

### Post by bodhi.zazen on 2009-12-27
If snort is running, and you see sensors in base you are good to go.

Snort may not generate alerts right away. You can test it by scanning you box or wait ...

Of course if your server is behind a router , and you are not forwarding ports, you may never see alerts =)

---

