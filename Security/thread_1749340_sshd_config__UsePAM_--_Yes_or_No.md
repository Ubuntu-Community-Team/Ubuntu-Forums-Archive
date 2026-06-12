---
title: "sshd_config : UsePAM -- Yes or No?"
date: 2011-05-04
forum: Security
---

### Post by mrsuess2 on 2011-05-04
I'm using ssh to connect to a Ubuntu machine from a Windows machine. I am only using key-based ssh logins and not using passwords. (I followed this tutorial: [http://www.howtoforge.com/ssh_key_based_logins_putty](http://www.howtoforge.com/ssh_key_based_logins_putty))
 
My question is in my sshd_config file, should I set UsePAM to Yes or No? Security-wise, does it make a difference one way or the other, or can I just leave it set to "yes" (the default setting)?

---

### Post by bodhi.zazen on 2011-05-04
If you are using keys you should disable password authentication (PAM).

This will increase security.

---

