---
title: "PSI 'SSL/TLS Plugin not found' on 8.04"
date: 2008-04-23
forum: Repositories &amp; Backports
---

### Post by markcs on 2008-04-23
Hi!

I have Ubuntu 8.04 and am trying to get PSI to work... I keep getting the error 

Cannot enable SSL/TLS. Plugin not found."

I saw [this post ]("http://ubuntuforums.org/showthread.php?t=130784&highlight=psi+plugin") but after installing qca-tls I still can't get PSI to work and have the same error.

I reinstalled PSI with no luck.

Any ideas anyone?

---

### Post by Akita on 2008-04-26
Same issue here. Anyone?

---

### Post by Akita on 2008-04-26
sudo apt-get install libqca2-plugin-ossl

It was a known issue during the beta (*sigh*):

[https://bugs.launchpad.net/ubuntu/+source/psi/+bug/188699](https://bugs.launchpad.net/ubuntu/+source/psi/+bug/188699)

---

### Post by Pollywoggy on 2008-04-27
> **Akita said:**
> sudo apt-get install libqca2-plugin-ossl

It was a known issue during the beta (*sigh*):

[https://bugs.launchpad.net/ubuntu/+source/psi/+bug/188699](https://bugs.launchpad.net/ubuntu/+source/psi/+bug/188699)

I have the same problem after upgrading to Hardy Heron.
I am going to compile my own psi and see if that fixes this problem.  I can connect to port 5223 (jabber) using Kopete.

---

### Post by Pollywoggy on 2008-04-27
> **markcs said:**
> Hi!

I have Ubuntu 8.04 and am trying to get PSI to work... I keep getting the error 

Cannot enable SSL/TLS. Plugin not found."

I saw [this post ]("http://ubuntuforums.org/showthread.php?t=130784&highlight=psi+plugin") but after installing qca-tls I still can't get PSI to work and have the same error.

I reinstalled PSI with no luck.

Any ideas anyone?

Is this a problem connecting to Jabber servers?
I was having that problem after upgrading to Hardy and this is how I fixed it.

I compiled my own Psi but before compiling, I did 'sudo apt-get build-dep psi' which removed the old qca dev package and installed a new one.

I then did 'sudo apt-get source psi' and then cd'd into the psi source and into the "debian" directory in the psi source and I edited the "rules" file's configure line.  The configure line has an option to NOT build SSL support.  Just comment out that option or remove the line and then compile psi and install the resulting deb file.  Then SSL should work on port 5223.  My server does not support TLS on port 5222 so I don't know whether this same procedure will work if you are using the starttls method.

---

### Post by lkraemer on 2008-05-03
Folks,
I just posted a how to:
[http://ubuntuforums.org/showthread.php?t=780970&highlight=PSI+with+Ubuntu+8.04](http://ubuntuforums.org/showthread.php?t=780970&highlight=PSI+with+Ubuntu+8.04)

Give it a try.  Mine now works.

LK

---

### Post by jc15 on 2008-07-31
Thanks, your advise helped me to connect to my account using PSI over SSL

---

