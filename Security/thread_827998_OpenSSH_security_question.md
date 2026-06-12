---
title: "OpenSSH security question"
date: 2008-06-13
forum: Security
---

### Post by usermeister on 2008-06-13
Hi guys. 
I am going through Ubuntu server guide. Currently I'm on OpenSSH and reading about it on Ubuntu wiki. This is what I'm curious about...

"The default /etc/ssh/sshd_config which is used with Ubuntu's OpenSSH implementation is more secure than that found in many other distributions of GNU/Linux"
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Can someone briefly explain to me how is it more secure? I've looked through config file, but I'm not an expert, and I could use this in my school paper about Ubuntu.

---

### Post by kevdog on 2008-06-13
Hmm, that statement seems a little bit misleading.  I haven't compared config files between distributions, however compared to the cygwin sshd_config, the files are the same.

---

### Post by hyper_ch on 2008-06-13
au contraire to debian root login is disabled by default... maybe they mean that...

---

### Post by brian_p on 2008-06-13
> **hyper_ch said:**
> au contraire to debian root login is disabled by default... maybe they mean that...

Au contraire. PermitRootLogin is set to 'yes'. There is a Readme.Debian explaining why.

---

### Post by hyper_ch on 2008-06-13
oh :) thought ubuntu had set rootlogin to no :)

---

### Post by brian_p on 2008-06-13
> **hyper_ch said:**
> oh :) thought ubuntu had set rootlogin to no :)

There is:

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/45416](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/45416)

I also looked at Ubuntu's openssh-server package and the postinst has it as enabled.

---

### Post by kevdog on 2008-06-13
So I guess the answer to the question is that Ubuntu's sshd_config is really no different than the standard default.

---

### Post by usermeister on 2008-06-26
Thank you for your replies. :)

---

