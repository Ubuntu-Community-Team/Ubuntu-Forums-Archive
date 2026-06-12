---
title: "Quickbooks for Linux"
date: 2007-07-21
forum: The Cafe
---

### Post by tommygunner on 2007-07-21
I'm looking to run an accounting program like Quickbooks on linux and want to know if anyone has done it with Wine or virtualization. 

If so, how does it compare to the Windows XP environment?

---

### Post by felicity on 2007-07-21
I'm not sure about running Quickbooks in wine, but you may try [GnuCash]("http://www.gnucash.org/"), it's a linux native accounting program.

Or if you still need Quickbooks, you may try running [VirtualBox]("http://www.virtualbox.org/") which runs windowsXP well.

---

### Post by tcpip4lyfe on 2007-07-21
GNUcash isn't anything like quickbooks.    I was extremely disappointed that there are no quickbooks clones that I have found for linux.  Vitrualbox is the way to go from what I've experienced.

---

### Post by jondecker76 on 2007-07-21
Some Quicken/Quickbook programs work great in wine and OpenOffice (depending on the year). I used Quicken 2006 Home & Business - And ran it fine under wine. But then I found MoneyDance and haven't used Quicken since. Moneydance isn't free, but its cheap (about $30), reliable, user friendly and cross platform.

Hope this helps

---

### Post by JAPrufrock on 2007-07-21
Check out Wine HQ [here]("http://appdb.winehq.org/appview.php?iAppId=493").  Doesn't look all that promising.  I suggest setting up VirtualBox, or something comparable.  However, if you want to use Quickbooks' POS, you will have to set up a printer, which sometimes is a no-go  (I think VirtualBox only/mainly supports printers that connect via a USB port).

---

### Post by HermanAB on 2007-07-22
Quickbooks runs on CxOffice and Wine.  I have been doing that since 2002.  

However, GNU Cash also works well for a small business:
[http://aeronetworks.ca/GNU_Cash_for_Business_users_Howto_Guide.html](http://aeronetworks.ca/GNU_Cash_for_Business_users_Howto_Guide.html)
[http://aeronetworks.ca/GnuCash.tgz](http://aeronetworks.ca/GnuCash.tgz)

For a larger business, consider SQL Ledger:
[http://www.sql-ledger.com/](http://www.sql-ledger.com/)
[http://www.linuxjournal.com/article/7290](http://www.linuxjournal.com/article/7290)

Cheers,

Herman

---

### Post by JAPrufrock on 2007-07-22
Gnucash is nice because it can handle more than one currency, and in different languages. Gnucash would work if you _don't need_ a point of sale (POS).  If you do, forget it.  Cxoffice requires $$.   _Some_ versions of Quickbooks work on Wine, but it requires fiddling.  Also, I run a 64-bit OS and haven't been able to print from a Wine app.

---

### Post by LookTJ on 2007-07-22
I suggest you start up an XP vm if you have the ram and space :)

---

