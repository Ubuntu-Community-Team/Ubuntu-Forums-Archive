---
title: "Last login disable fail via Pam.d login conf"
date: 2011-01-02
forum: Server Platforms
---

### Post by lible on 2011-01-02
I've been trying to disable the last login ip which appears which appears when I login to my server by ssh. After some reading  I determined that this is controlled by "Pam" so I attempted to edit /etc/pam.d/login.  Firstly I added a # to this line. #session    optional   pam_lastlog.so   It had no effect so I added silent to this line. session    optional   pam_lastlog.so silent Still no effect. I would appreciate any insight to this problem. Running ubuntu 10.04 : )

---

### Post by jgedeon on 2011-01-02
In /etc/ssh/sshd_config change the line "PrintLastLog yes" to "PrintLastLog no" and then restart ssh.

---

### Post by lible on 2011-01-02
Thanks jgedeon i'll give that a try

---

