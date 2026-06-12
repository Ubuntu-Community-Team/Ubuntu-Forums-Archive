---
title: "Verisign cert not trusted?!"
date: 2011-01-28
forum: Security
---

### Post by alawson on 2011-01-28
Hi all,

I'm trying to access a Verisign signed site ([https://www.secureremserv.com.au/](https://www.secureremserv.com.au/)) and getting a certificate not known error when I do.

Do I really need to import Verisign?
If so, how?

Cheers,
Andy.

---

### Post by artie_effim on 2011-01-28
what browser are you using?  what error are you getting?

---

### Post by alawson on 2011-01-28
Firefox 3.6.13 on Ubuntu 10.10 x64, and a certificate not known error. I do trust this organisation, so I setup an exemption for them.

No problems accessing this same site from Firefox 3.6.13 on Win64, however.

---

### Post by uRock on 2011-01-28
Is Verisign rejecting the site's key? That sounds more likely.

Clear your cookies and try again.

---

### Post by alawson on 2011-01-28
I cleared all the cookies that were listed for this organisation and tried again without error.

But I still have the exemption in place - can't see how to remove it. Any ideas?

---

### Post by yetiman64 on 2011-01-29
> **alawson said:**
> ....But I still have the exemption in place - can't see how to remove it. Any ideas?
In your browser have a look in Edit > Preferences > Advanced > Encryption Tab > View Certificates > Servers Tab. An entry should be there for the site you gave the exception to, with the option to delete it at the bottom of the tab when it is highlighted.

---

### Post by alawson on 2011-01-30
Thanks - not getting the warning now, so am I safe to assume it must have gotten resolved?

---

