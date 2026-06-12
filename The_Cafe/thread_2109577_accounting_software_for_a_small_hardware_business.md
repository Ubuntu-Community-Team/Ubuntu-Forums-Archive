---
title: "accounting software for a small hardware business"
date: 2013-01-28
forum: The Cafe
---

### Post by ongandrew2 on 2013-01-28
hi just wondering if you could suggest any accounting software that would do inventory, invoices, and purchase orders. got a lot of items like 3,000 items in my warehouse which i would like to use the program.

---

### Post by jejeman on 2013-01-28
You asked in wrong subforum.

---

### Post by elgordodude on 2013-01-29
Unfortunately no, Quickbooks is really the only reason I keep an XP box around. If you find something I'd be interested as well, intuiut seems to be lowering the bar, not raising it, but when I went looking a couple of years ago quickbooks was no longer wine supported after around 2004, and there were no native linux options that could produce invoices and track inventory.

I've heard good things about gnucash but it's more of a personal account manager than a business application.

---

### Post by lisati on 2013-01-29
Not a support request for Ubuntu Studio.
*Thread moved to **The Community Cafe**.*

---

### Post by mastablasta on 2013-01-29
> **ongandrew2 said:**
> hi just wondering if you could suggest any accounting software that would do inventory, invoices, and purchase orders. got a lot of items like 3,000 items in my warehouse which i would like to use the program.
 
there is openERP. but maybe that is overkill?
 
i have no experience over it. 
 
Also there might be some web based solutions for this that are OS independent. we use such a local solution for accounting.

---

### Post by HermanAB on 2013-01-29
SQL-Ledger or god forbid, Quickbooks on a WinXP virtual machine.

---

### Post by forrestcupp on 2013-01-29
> **elgordodude said:**
> Unfortunately no, Quickbooks is really the only reason I keep an XP box around. If you find something I'd be interested as well, intuiut seems to be lowering the bar, not raising it, but when I went looking a couple of years ago quickbooks was no longer wine supported after around 2004, and there were no native linux options that could produce invoices and track inventory.

I've heard good things about gnucash but it's more of a personal account manager than a business application.
Gnucash is definitely not a good replacement for Quickbooks.

What makes you say that Intuit is lowering the bar? I'm actually liking the newer versions a lot better. I'm using 2010, and I love the fact that they finally added a feature to let you attach scanned paperwork to entries. Before that, I had to rely on an expensive 3rd party solution that was a huge SQL monster. I like where they're going and how they're finally integrating things that should have been integrated from the beginning. And you just can't beat their payroll service.

---

### Post by SeijiSensei on 2013-01-29
Intuit now offers a [cloud-based version]("http://quickbooksonline.intuit.com/") if you're not averse to storing your business's financial and inventory data on its servers.  That approach avoids the need for a Windows machine if that's a real issue, but if you have a licensed Windows CD or DVD lying around, I'd install Windows inside a [VirtualBox]("http://www.virtualbox.org/") virtual machine and run the actual application from there.  One nice feature is being able to take portable snapshots of the virtual machine as a backup mechanism.

---

### Post by besial on 2013-01-29
> **HermanAB said:**
> SQL-Ledger or god forbid, Quickbooks on a WinXP virtual machine.
Or you could try Qucikbooks On Wine.  Sometimes wine doent play well with windows software, sometimes its okay, it all just depends. wine would be lighter weight then VirtualBox.

---

### Post by SeijiSensei on 2013-01-29
> **besial said:**
> Or you could try Qucikbooks On Wine.  Sometimes wine doent play well with windows software, sometimes its okay, it all just depends. wine would be lighter weight then VirtualBox.

Earlier in this thread we have:
> **elgordodude said:**
> [W]hen I went looking a couple of years ago quickbooks was no longer wine supported after around 2004....

I don't know whether that is still true, but it's why I recommended VirtualBox.  Presumably this would be running on a dedicated machine.

---

### Post by Docaltmed on 2013-01-29
GnuCash is just about perfect for this type of application. I've been using GnuCash to run my business for several years now. It handles inventory, invoicing, service and product sales; in terms of management, the reports are pretty much everything I need.

I abandoned the bloated, useless QuickBooks years ago, and have never looked back.

---

### Post by forrestcupp on 2013-01-29
> **SeijiSensei said:**
> Intuit now offers a [cloud-based version]("http://quickbooksonline.intuit.com/") if you're not averse to storing your business's financial and inventory data on its servers.  That approach avoids the need for a Windows machine if that's a real issue, but if you have a licensed Windows CD or DVD lying around, I'd install Windows inside a [VirtualBox]("http://www.virtualbox.org/") virtual machine and run the actual application from there.  One nice feature is being able to take portable snapshots of the virtual machine as a backup mechanism.Boy, the thing that completely scares me about that is thinking about what happens to all of your data when you stop paying the subscription fee.

> **besial said:**
> Or you could try Qucikbooks On Wine.  Sometimes wine doent play well with windows software, sometimes its okay, it all just depends. wine would be lighter weight then VirtualBox.Quickbooks is garbage on Wine. Even the old versions don't work well.

> **Docaltmed said:**
> GnuCash is just about perfect for this type of application. I've been using GnuCash to run my business for several years now. It handles inventory, invoicing, service and product sales; in terms of management, the reports are pretty much everything I need.

I abandoned the bloated, useless QuickBooks years ago, and have never looked back.I'll bet it was a pain to set up. I wouldn't want to use Gnucash because I like Quickbooks' payroll service too much. Other than that, Gnucash looked like it could do a lot, but it would be a major headache to try to set it up to do everything you need.

I actually use Gnucash for my personal finances, but I'm pretty happy with Quickbooks for the business.

---

### Post by Docaltmed on 2013-01-30
> **forrestcupp said:**
> 
I'll bet it was a pain to set up. I wouldn't want to use Gnucash because I like Quickbooks' payroll service too much. Other than that, Gnucash looked like it could do a lot, but it would be a major headache to try to set it up to do everything you need.

I actually use Gnucash for my personal finances, but I'm pretty happy with Quickbooks for the business.


The key with GnuCash seems to be getting the accounts right at the outset. GnuCash is true double-entry accounting, so you can get all tangled up otherwise.

I agree with you on Quickbooks payroll. The nice thing about Quickbooks is that it keeps you from having to think about things. Also, you don't get your accountant whining in your ear every year about why you should switch to QB so you could just send him the files.

Yeah, like I'm going to attach my business's entire financial history to an unsecure, unencrypted email. I've never found an accountant that uses PGP, and I can't for the life of me understood why not.

---

### Post by SeijiSensei on 2013-01-30
> **Docaltmed said:**
> Yeah, like I'm going to attach my business's entire financial history to an unsecure, unencrypted email. I've never found an accountant that uses PGP, and I can't for the life of me understood why not.

Password-protected ZIP files work well for these types of people.  Just give the accountant the password over the phone or in person.

I suspect that the proportion of people who use PGP/GPG encrypted email is in the fractions of a percent.  Even if the accountant knows how to go through the hoops required to set up GPG, you can be sure that 99% or more of her clients can't or won't.  Medical providers do not use PGP for email either, even though the HIPAA regulations clearly prohibit the transfer of "patient health information" in plain-text emails.  Some hospitals and large provider chains use SSL-based patient "portals" on their websites to handle communications between patients and providers, but I still see doctors handing out business cards with their email addresses on them.

---

