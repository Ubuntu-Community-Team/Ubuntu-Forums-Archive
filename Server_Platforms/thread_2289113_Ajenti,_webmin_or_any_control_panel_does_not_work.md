---
title: "Ajenti, webmin or any control panel does not work"
date: 2015-08-01
forum: Server Platforms
---

### Post by carolog on 2015-08-01
Hi,

I recently setup a new Ubuntu 14.04 EC2 instance on Amazon AWS. I've already installed the LAMP stack and wordpress with it. I was trying to install Ajenti (and then when that didn't work, Webmin) and the installation went off without a hitch, but I'm not able to load the interface at https://<myip>:8000. The page times out. I then removed Ajenti and tried installaing Webmin with no luck. 

Any thoughts?

---

### Post by volkswagner on 2015-08-01
Did you open firewall ports on Ec2 control panel?

---

### Post by carolog on 2015-08-02
Arrrgh! ... how stupid of me! I opened the ports there and it worked. Thanks :)

---

