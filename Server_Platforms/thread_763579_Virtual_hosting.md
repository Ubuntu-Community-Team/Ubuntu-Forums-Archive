---
title: "Virtual hosting"
date: 2008-04-23
forum: Server Platforms
---

### Post by satimis on 2008-04-23
Hi folks,


Ubuntu 6.05.3 drake server amd64
Apache2


I'm prepared testing virtual hosting but I have only one registered domain and one public IP.  I will register 2/3 free subdomain for this test.  However I'm not going to subscribe additional public IP.


Can I do the test with only one public IP?  If YES please advise which document will be relevant for me to follow as a guide.  TIA


B.R.
satimis

---

### Post by Oldsoldier2003 on 2008-04-23
> **satimis said:**
> Hi folks,


Ubuntu 6.05.3 drake server amd64
Apache2


I'm prepared testing virtual hosting but I have only one registered domain and one public IP.  I will register 2/3 free subdomain for this test.  However I'm not going to subscribe additional public IP.


Can I do the test with only one public IP?  If YES please advise which document will be relevant for me to follow as a guide.  TIA


B.R.
satimis

yes. you will just need to setup virtual sites in apache by creating new conf files in /etc/apache2/sites-available then enabling them with a2ensite <configfile_name>

---

### Post by vpsville on 2008-04-23
> **satimis said:**
> 
Can I do the test with only one public IP?  If YES please advise which document will be relevant for me to follow as a guide.  TIA


Yes, the whole point of virtual hosting is to share an IP among several domains.  The URL header is analyzed by apache and it loads the pages from the directory root you specify for that domain.

---

