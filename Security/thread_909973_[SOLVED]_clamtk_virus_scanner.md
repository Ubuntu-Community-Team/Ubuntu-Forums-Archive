---
title: "[SOLVED] clamtk virus scanner?"
date: 2008-09-04
forum: Security
---

### Post by Camilia on 2008-09-04
When I open up the clamtk cleaner this file is listed -  Urlclassifier3.sqlite not scanned.

Does anyone now what this file is and why it doesn't get scanned?

---

### Post by owenll on 2008-09-04
Apparently it [holds information about phishing sites]("http://ychittaranjan.wordpress.com/2008/06/27/urlclassifier3sqlite-woes-on-firefox-3/"), but I don't know why it doesn't get scanned, sorry.

You could try googling Urlclassifier3

---

### Post by jamesrl on 2008-09-04
Do you know where the file is?  I don't have the file on my computer, so can't comment on it.

To find out you can type:
```
locate Urlclassifier3.sqlite
```

(if that doesn't give you a path, maybe try ```
sudo updatedb
``` to update the database that the command "locate" uses to find files).

From the filename, I would guess it is database that classifies URLs.  URLs are internet addresses (eg. the following is a: [http://www.somewebsite.com/~somedirectory/index.html](http://www.somewebsite.com/~somedirectory/index.html) ), and sqlite is a type of database (SQL is a language for asking a database questions (sending queries to retrieve)), and sqlite is a very basic database structure that uses the SQL language.

EDIT: Seeing the above post, I take back what i said.  I should have also searched for urlclassifier3.sqlite (which is a different file with the capital letter in linux), which I do have as part of firefox in my profile.

---

### Post by hyper_ch on 2008-09-04
it's a database created and used by firefox.

---

### Post by Camilia on 2008-09-07
> **hyper_ch said:**
> it's a database created and used by firefox.

Thus it doesn't need scanning?

---

### Post by OutOfReach on 2008-09-07
Maybe the file is too big to be a virus?

---

### Post by hyper_ch on 2008-09-07
you don't need antivirus on linux at all.

---

### Post by Camilia on 2008-09-26
In the synapse it says clamav is only for email. Thus it doesn't address problems I have had in windows. I copied pictures for advatar and got trojan viruses. Seems the only thing close to spyware check, which helped in windows, is rkhunter. 

My computer started running very slow. I had most items on flash disk so I just rebooted and put the ubuntu cd in. I don't know if it was a virus problem or that I had to many item on the security to slow down the computer.

Decided to use morzila noscript instead of a firewall and see if this prevents this from happening againl

---

