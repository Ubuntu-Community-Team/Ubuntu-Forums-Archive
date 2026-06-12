---
title: "MailScanner in Ubuntu 14.04 lts server on VMware workstation 12"
date: 2016-04-17
forum: Virtualisation
---

### Post by alberto11 on 2016-04-17
excuse my inexperience
I can not install "mailscanner" , every attempt fails

I followed this link 
[http://wiki.ubuntu-it.org/Server/Mail](http://wiki.ubuntu-it.org/Server/Mail)

---

### Post by MAFoElffen on 2016-04-18
Okay:
[s]What is your virtualization hypervisor software?[/s] VMware workstation 12
[s]What is the VM's Server OS?[/s] 14.04 lts server edition.
What basic resources do you have allocated to that VM?
What email service package do you have installed and configured?

Mailscanner is an email filter for an email server: [UserGuide]("https://s3.amazonaws.com/mailscanner/docs/ms-admin-guide.pdf")

---

### Post by SeijiSensei on 2016-04-19
Did you follow every step in the Guide?  You cannot just install MailScanner; you need Postfix or sendmail as well, along with SpamAssassin and ClamAV at a minimum for spam and virus scanning.  

I have used MailScanner for years, but I never install it from a repository, nor do I run it on Ubuntu.  I use CentOS for servers and the version of MailScanner from its own site at [http://www.mailscanner.info/](http://www.mailscanner.info/).  If you want to run it on Ubuntu, you'll need the .deb version found here: [https://s3.amazonaws.com/mailscanner/release/v4/deb/MailScanner-4.85.2-3.deb.tar.gz](https://s3.amazonaws.com/mailscanner/release/v4/deb/MailScanner-4.85.2-3.deb.tar.gz).  Unpack the zip archive and run install.sh like this:
```

tar xzf MailScanner-4.85.2-3.deb.tar.gz
cd MailScanner-4.85.2-3
sudo ./install.sh

```
It will collect its various dependencies (there are a lot) and install them along with MailScanner itself.

---

### Post by alberto11 on 2016-04-20
> **MAFoElffen said:**
> Okay:
[s]What is your virtualization hypervisor software?[/s] VMware workstation 12
[s]What is the VM's Server OS?[/s] 14.04 lts server edition.
What basic resources do you have allocated to that VM?
What email service package do you have installed and configured?

Mailscanner is an email filter for an email server: [UserGuide]("https://s3.amazonaws.com/mailscanner/docs/ms-admin-guide.pdf")

I check and let you know ,
many thanks for link userguide

---

### Post by alberto11 on 2016-04-20
> **SeijiSensei said:**
> Did you follow every step in the Guide?  You cannot just install MailScanner; you need Postfix or sendmail as well, along with SpamAssassin and ClamAV at a minimum for spam and virus scanning.  

I have used MailScanner for years, but I never install it from a repository, nor do I run it on Ubuntu.  I use CentOS for servers and the version of MailScanner from its own site at [http://www.mailscanner.info/](http://www.mailscanner.info/).  If you want to run it on Ubuntu, you'll need the .deb version found here: [https://s3.amazonaws.com/mailscanner/release/v4/deb/MailScanner-4.85.2-3.deb.tar.gz](https://s3.amazonaws.com/mailscanner/release/v4/deb/MailScanner-4.85.2-3.deb.tar.gz).  Unpack the zip archive and run install.sh like this:
```

tar xzf MailScanner-4.85.2-3.deb.tar.gz
cd MailScanner-4.85.2-3
sudo ./install.sh

```
It will collect its various dependencies (there are a lot) and install them along with MailScanner itself.


Check your information and let you know
many thanks

---

