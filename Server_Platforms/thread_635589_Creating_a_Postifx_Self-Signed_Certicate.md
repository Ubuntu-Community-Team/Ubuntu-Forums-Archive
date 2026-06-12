---
title: "Creating a Postifx Self-Signed Certicate"
date: 2007-12-08
forum: Server Platforms
---

### Post by satimis on 2007-12-08
Hi folks,


Ubuntu 7.04 server amd64
Postfix 2.3.8


Occasionally on starting squirrelmail remotely with

etiher
[https://domain.com/squirrelmail](https://domain.com/squirrelmail)

or
[https://localhost/squirrelmail](https://localhost/squirrelmail)


Following warning popup;```

Security
security Error: Domain Name Mismatch
You have attempted to establish a connection with
"www.domain.com".  However, the security certificate
presented belongs to "localhost".  It is possible though
unlikely, that someone may be trying to intercept your
communication with this website.


If you suspect the certicate shown does not belong to
"www.domain.com". please cancel the connection and notify
the site administrator.

[Vies Certificate]     [Cancel]  [OK]

```


I'm prepared creating SelfSigned SSL certificate to satisty it.  Googling brought me lot of documents.  After screening I found follows may be suitable for my application;


Creating a self-signed SSL certificate: Ubuntu
[http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html](http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html)


Postfix mail server create self-signed SSL certificates on Cent OS / Redhat linux
[http://nixcraft.com/server-configuration-tutorials/3075-postfix-mail-server-create-self-signed-ssl-certificates-cent-os-redhat-linux.html](http://nixcraft.com/server-configuration-tutorials/3075-postfix-mail-server-create-self-signed-ssl-certificates-cent-os-redhat-linux.html)


Creating a Self-Signed Certificate
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html#creating-a-self-signed-certificate](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html#creating-a-self-signed-certificate)


Which of the above shall I follow?  Please advise.  TIA



B.R.
satimis

---

### Post by MJN on 2007-12-09
The certificate is for your Apache service/service (to enable https) and not Postfix. Hence, either the first or third guide.

Mathew

---

### Post by satimis on 2007-12-09
> **MJN said:**
> The certificate is for your Apache service/service (to enable https) and not Postfix. Hence, either the first or third guide.

Mathew
Thanks.


My main purpose creating Self-signed certificate on postix is to get rid off the warning on first time starting Firefox/SquirrelMail each day or after reboot. Besides I can learn its creation which is of minor importance.


B.R.
satimis

---

### Post by MJN on 2007-12-10
Again, when you login to Squirrelmail you are not receiving the Postfix cert - it is the Apache SSL cert that you're getting. Hence, to remove the error you need to be changing your Apache certificate.

Mathew

---

### Post by satimis on 2007-12-10
> **MJN said:**
> Again, when you login to Squirrelmail you are not receiving the Postfix cert - it is the Apache SSL cert that you're getting. Hence, to remove the error you need to be changing your Apache certificate.

Mathew
Whether creating a Self_signed SSL certificate according to either the first or third guide?  Thanks


satimis

---

### Post by MJN on 2007-12-11
Yes.

When you are at your SM login page you are communicating with Apache only (not Postfix) and it is the Apache certificate that is being presented. In your case the certificate has a different CN than the URL you are typing hence the security warning. Create a self-signed certificate for Apache to use that has the correct URL as the CN and the warning will disappear (you may well still get an error that the certificate wasn't signed by a trusted authority unless you happened to have installed the certificate as trusted in your client).

Mathew

---

### Post by satimis on 2007-12-11
> **MJN said:**
> Yes.

When you are at your SM login page you are communicating with Apache only (not Postfix) and it is the Apache certificate that is being presented. In your case the certificate has a different CN than the URL you are typing hence the security warning. Create a self-signed certificate for Apache to use that has the correct URL as the CN and the warning will disappear (you may well still get an error that the certificate wasn't signed by a trusted authority unless you happened to have installed the certificate as trusted in your client).

Mathew
Thanks for your explanation.  I'll leave it for the time being.


Actually my main object on this test is building a virtual machine, VMWare server.  It happens running Ubuntu 7.04 server as Host OS taking me sometimes configuring it as a mail server.


This box was previous a mail server running OpenBSD and dynamic IP.  It was working.  I wiped out the server and added another 2G RAM for this test, now running totally 4G RAM.


The VMWare server and the Guest OS, CentOS 5, have been running on the box for some time without fine tuning.  I'll move on.   Anyway lot of thanks for your help.


P.S.  "Change Password" on SM is only partially working.  I'll come back to the thread after sorting out the problem.


B.R.
satimis

---

