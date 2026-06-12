---
title: "Snort &amp; BASE problem"
date: 2012-02-04
forum: Security
---

### Post by Welly Wu on 2012-02-04
I read the NIDS (Snort) sticky thread and I am getting a problem in configuring BASE:

ERROR: The php session does not contain the array key "adodbpath". This is typically caused by not having allowed cookies. Exiting.

What is causing this problem?

How do I solve it so I can configure BASE?

---

### Post by Welly Wu on 2012-02-04
I get this problem after I follow this step in the configuration for BASE:

Step 2: Enter the path to ADODB /usr/share/php/adodb

I enter the path exactly and I get the above error message.

---

### Post by emiller12345 on 2012-02-04
have you installed adodb?
```
~$ sudo apt-get install php5-adodb
```

---

### Post by Welly Wu on 2012-02-05
Yes, I installed it. I am still getting the same error message when I try to configure BASE. What can I do to solve this problem?

---

### Post by emiller12345 on 2012-02-05
Theres a pretty good write up on the snort.org website for setting up BASE
[http://www.snort.org/assets/167/deb_snort_howto.pdf](http://www.snort.org/assets/167/deb_snort_howto.pdf)
you probably won't need all of this, but it's there if you do need it.
probably start at:
"7. Install and configure BASE"

---

### Post by Welly Wu on 2012-02-05
For some unknown reason, the problem resolved itself and I am able to configure BASE and Snort together. Now, I have to work on Oinkmaster.

---

