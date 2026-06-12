---
title: "&quot;Powered by ZEDO&quot; infection -- in Linux?"
date: 2008-06-02
forum: Security
---

### Post by eugeneccampbell on 2008-06-02
I've been getting "Powered by ZEDO" popup windows in Firefox 3.0 
under Ubuntu 8.04. Everywhere I search on Google for removing this
malware refers to Windows infections, with references to rootkit and
removal of a file called CORE.SYS and the Windows registry.

(Might this have anything to do with having installed Glubble as a
Firefox add-on? It makes radical changes in Firefox.)

The computer is not dual-boot; it is Linux only.

---

### Post by brian_p on 2008-06-03
> **eugeneccampbell said:**
> I've been getting "Powered by ZEDO" popup windows in Firefox 3.0 
under Ubuntu 8.04. Everywhere I search on Google for removing this
malware refers to Windows infections, with references to rootkit and
removal of a file called CORE.SYS and the Windows registry.

(Might this have anything to do with having installed Glubble as a
Firefox add-on? It makes radical changes in Firefox.)

The computer is not dual-boot; it is Linux only.

ZED0 is an ad service, isn't it? It's pushing it a bit to call the pop-ups malware or an infection but if they are annoying you there's no reason to put up with them.

Try the cookies.txt file in the .mozilla directory of your home directory.  Delete any reference to ZEDO or move or delete the file. See how you go on.

Are these any help?

[http://www.zedo.com/company/optout.htm](http://www.zedo.com/company/optout.htm)

[http://www.aboutus.org/ZEDO.com](http://www.aboutus.org/ZEDO.com)

---

### Post by roderick on 2008-06-03
Use AdBlock Plus as well as NoScript plugins as well to avoid such annoyances.

---

### Post by eugeneccampbell on 2008-06-03
> **brian_p said:**
> ZED0 is an ad service, isn't it? It's pushing it a bit to call the pop-ups malware or an infection

Ah, I see. A google search for the title of the popup led to page
after page of complaints by Windows users, with complaints that 
all their efforts to rid themselves of it failed. Responders on
a few forums came up with a .SYS file to delete and a Windows Registry
entry to remove, with some dire warnings about this particular item.
I knew there had to be something goofy going on somewhere if I was
getting it on my Linux box.

> **brian_p said:**
>  but if they are annoying you there's no reason to put up with them.

Try the cookies.txt file in the .mozilla directory of your home directory.  Delete any reference to ZEDO or move or delete the file. See how you go on.

Are these any help?

[http://www.zedo.com/company/optout.htm](http://www.zedo.com/company/optout.htm)

[http://www.aboutus.org/ZEDO.com](http://www.aboutus.org/ZEDO.com)

Yes. They explain that ZEDO works by installing a cookie. Thanks.

---

### Post by eugeneccampbell on 2008-06-03
> **roderick said:**
> Use AdBlock Plus as well as NoScript plugins as well to avoid such annoyances.

I've been using AdBlock but it didn't nail ZEDO. I've long used NoScript
on Firefox under Windows but didn't realize it might be a good idea with
Linux too, and had been enjoying the NoScript-less sessions while working
at home with Ubuntu. At the office under Windows, I'm constantly having
to approve scripts, usually temporarily, and it's a bit of a nuisance.

Would it be wise to start depending on NoScript with Ubuntu as well?

---

### Post by bbqsandwich on 2008-06-03
> **eugeneccampbell said:**
> I've been using AdBlock but it didn't nail ZEDO. I've long used NoScript
on Firefox under Windows but didn't realize it might be a good idea with
Linux too, and had been enjoying the NoScript-less sessions while working
at home with Ubuntu. At the office under Windows, I'm constantly having
to approve scripts, usually temporarily, and it's a bit of a nuisance.

Would it be wise to start depending on NoScript with Ubuntu as well?

Yes

You can be vulnerable to phishing/spoofing attacks via cross-site scripting no matter what your OS

[http://en.wikipedia.org/wiki/Cross-site_scripting](http://en.wikipedia.org/wiki/Cross-site_scripting)

---

