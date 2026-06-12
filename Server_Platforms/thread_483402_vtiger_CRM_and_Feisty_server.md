---
title: "vtiger CRM and Feisty server"
date: 2007-06-24
forum: Server Platforms
---

### Post by bmathis on 2007-06-24
Hey everyone, I'm trying to get vtiger installed on my feisty server. I've tried using the bin file thats available for download from their website and it doesn't matter what I do, I can't get vtiger to either install apache for me or find my installation of apache and thats just the first install step. Has anyone had any similar problems or success?

(their forums are no help either)

Thanks in advance

---

### Post by bmathis on 2007-07-09
found out that vtiger isnt compatible with Feisty and the devs dont know when its going to be :(

install 6.06 and the install went fine.

---

### Post by mbene on 2007-07-11
Hi, 
I have had the same problem.
Vtigercrm isnt compatible with php 5.2.1 coming with Ubuntu 7.04 version (I'm right?).
You can dowload the vtiger 5.0.3 patch for php 5.2.x from
[http://prdownloads.sourceforge.net/vtigercrm/vtigerCRM-5.0.3-PHP5.2-Patch1.tar.gz?download]("http://prdownloads.sourceforge.net/vtigercrm/vtigerCRM-5.0.3-PHP5.2-Patch1.tar.gz?download")

---

### Post by bmathis on 2007-07-11
i actually just reinstalled with Feisty using the source files.... much better then using their stack. Just setup lamp before hand and make sure the www:data user has access to all the vtiger files, you have php5-gd installed, and you're golden. I plan on writing a little tutorial about here sometime in the next couple of weeks.

---

### Post by mbene on 2007-07-12
> **bmathis said:**
> i actually just reinstalled with Feisty using the source files.... much better then using their stack. Just setup lamp before hand and make sure the www:data user has access to all the vtiger files, you have php5-gd installed, and you're golden. I plan on writing a little tutorial about here sometime in the next couple of weeks.

No php 5.2.1 patch ?

- I also installed php5-imap for vtiger webmails module ... 
- I assigned to www-data user "write permissions" on /var/www/[vtiger_document_root]/storage directory ... for "attachments" upload in some modules

---

