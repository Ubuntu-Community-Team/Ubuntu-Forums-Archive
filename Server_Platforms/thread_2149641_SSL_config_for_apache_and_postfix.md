---
title: "SSL config for apache and postfix?"
date: 2013-05-29
forum: Server Platforms
---

### Post by kevinxsalerno on 2013-05-29
Hey guys. I am working for a small business setting them up a small dedicated box for all of their needs. It will be a LAMP + email server.

During this, I have ran into a few problems.

1. SSL/certificates, HOW DO THEY WORK?

This is required for the email server and would also be nice for the web  file manager for clients to connect to (https instead of http). I am  having trouble figuring out exactly how to set up the certificate/key  with my domain. I AM NOT RUNNING A DNS SERVER AND DO NOT PLAN TO. They  will not need it.

2. Also, because I am using a domain/DNS through godaddy, do I have to  create an MX record too? If so, what does the MX record need to be?

Is it just mydomain.com or is it smtp.mydomain.com? Does there need to be one for IMAP too?

3. How do I configure postfix to be SSL secure?

4. How do I configure postfix to work with SMTP and IMAP for mail clients like thunderbird?

---

### Post by linuxtechguy on 2013-05-29
1. Installation of an ssl certificate would depend on the type of webserver software you are using. There are guides all over the internet to install ssl certificates on any of the major webserver software.

2. Mx record only has to point to a host or domain that has the ip address that your smtp server listens on. Mx records for for smtp only and not for imap or pop3.

3. [http://www.cyberciti.biz/tips/postfix-smtp-ssl-certificate-csr-installation-guide.html](http://www.cyberciti.biz/tips/postfix-smtp-ssl-certificate-csr-installation-guide.html)

4. Postfix is an smtp server only and has nothing to do with imap/pop3. You will have to install another software to do that task.

---

### Post by kevinxsalerno on 2013-05-29
> **linuxtechguy said:**
> 1. Installation of an ssl certificate would depend on the type of webserver software you are using. There are guides all over the internet to install ssl certificates on any of the major webserver software.

2. Mx record only has to point to a host or domain that has the ip address that your smtp server listens on. Mx records for for smtp only and not for imap or pop3.

3. [http://www.cyberciti.biz/tips/postfix-smtp-ssl-certificate-csr-installation-guide.html](http://www.cyberciti.biz/tips/postfix-smtp-ssl-certificate-csr-installation-guide.html)

4. Postfix is an smtp server only and has nothing to do with imap/pop3. You will have to install another software to do that task.

Thanks for the response.

1. Apache with ajaxplorer. I am just confused by the exact wording for 'mydomain' on both the cert and the config. For example, am I suppose to always just have mydomain.com or should it always be [www.mydomain.com?](www.mydomain.com?) SSL just feels really touchy.

2. So should the smtp mx record be mydomain.com or smtp.mydomain.com?

3. Thanks.

4. Now I feel stupid. Do you know of any email software for ubuntu server that does BOTH? Or any simple imap setup that would work with postfix?

---

### Post by linuxtechguy on 2013-05-29
1. The domain is really up to you. It is best for seo to use [www.domain.com](www.domain.com) but there is no standard really. [www.domain.com](www.domain.com) started because in early days of dns there were no ways to point the domain.com to an ip address. You can easily redirect users where you want to go with a redirect on your webserver.

2. You can name it whatever you want as there is no standard really. I typically just use mail.domain.com for everything. Some hosts have separate servers that host the smtp and pop3/imap so they make seperate hosts to point to those servers. Godaddy default dns makes everything confusing because they have a ton of default hosts that are not even needed.

4. I think you should look at dovecot. It is the easiest to configure and is actively maintained. It can serve as both a pop3 and imap client as well as supporting ssl connections. There should be a ton of guides to configuring it, especially with postfix.

---

