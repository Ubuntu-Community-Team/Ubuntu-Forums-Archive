---
title: "private key file encrypted apache startup"
date: 2009-09-01
forum: Security
---

### Post by bh5k on 2009-09-01
Hello,

I have been trying to enable SSL on Apache2 and have everything working well. I have Apache2 setup to automatically start and there is where I hit a problem. 

I get a message saying that "Some of your private key files are encrypted for security reasons. In order to read them you have to provide the pass phrases."

Well, this dialog halts the service from starting. What do I need to install differently or do differently to make it so I don't have to enter the pass phrase?

These are the instructions I followed to setup SSL [http://beginlinux.com/blog/2009/01/ssl-on-ubuntu-810-apache2/](http://beginlinux.com/blog/2009/01/ssl-on-ubuntu-810-apache2/)

Thanks for your help!

bh5k

---

### Post by bodhi.zazen on 2009-09-01
You can do it in several ways.

See :

[http://www.akadia.com/services/ssh_test_certificate.html](http://www.akadia.com/services/ssh_test_certificate.html)

(Step 3)

Or you can make a .pem

[http://www.cyberciti.biz/tips/how-to-install-ssl-lighttpd-https-configuration.html](http://www.cyberciti.biz/tips/how-to-install-ssl-lighttpd-https-configuration.html)

Again see the section on removing the password.

Or you can simply remove apache from the boot scripts and start it manually (how often do you reboot the server ?).

---

### Post by bh5k on 2009-09-01
That did the trick! Thanks for your help.

---

