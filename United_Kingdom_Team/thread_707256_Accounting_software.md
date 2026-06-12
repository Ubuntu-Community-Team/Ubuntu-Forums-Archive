---
title: "Accounting software"
date: 2008-02-25
forum: United Kingdom Team
---

### Post by g7mjv on 2008-02-25
Hi People

l'm interested to know whether there is a Linux alternative to Sage.. l might be able to get my wife to start using Ubuntu if there's something available that will allow her to import customers data properly.

---

### Post by MxGB on 2008-02-25
Seconded, I would also like to know this.

I've already mentioned this on the mailing list, but you can run Sage (flakily) on wine by copying a Windows-installed copy, or even on a virtual machine running Windows. I'd recommend VirtualBox if you want to try this because once they've got the seamless mode bug fixed you can run Windows apps alongside your native windows.

---

### Post by shaggly on 2008-02-26
BUMP - I'd also like to know if anyone has come across a decent Accounting package that runs in Ubuntu / Kubuntu

---

### Post by clanglois on 2008-02-27
SQL Ledger Has been recomended to be a good solid general ledger. It's written in perl and uses mysql.

---

### Post by cybervegan on 2008-03-20
There's also the very comprehensive gnuchash which is similar in goal to quick-books. I've never used it in earnest, but it looks ok, if a bit ugly.

-cybervegan

---

### Post by iainv on 2008-03-25
I used to use Sage on my Vista machine, but have spent the weekend making the move to ubuntu for the accounting as well.

I tried GNUcash in parallel with Sage for a month or so on Vista, but it just doesn't cut it for the UK - things like the VAT functions are just not up to scratch for here.

I am running Quickbooks now through an XP Virtualbox, and though I haven't tried the online services or remote connection the core programme is perfectly stable and (almost) fully functional (the only thing which doesn't appear to work at the moment is the scripting in the help file, so you have to use the help index instead of just typing in your question)

I have to say, Quickbooksis easier than Sage, and editable so if you make a mistake it's easy to correct (and keeps an audit trail to keep HMRC happy!), and with hindsight I would have chosen it over Sage from day 1.

The only thing to beware is that Quickbooks Simplestart (which is marketed as an alternative to Sage Instant Accounts) only does cash accounting for VAT - you can't store invoices from suppliers or control stock - only record when you pay them. If you want this functionality you can upgrade, but it's about £300 for Pro, which does everything you should need. Even with the price difference i'd choose Quickbooks every time.

Iain

(Not an accountant, but do my own books and VAT returns for my company - [www.sinia.co.uk](www.sinia.co.uk))

---

### Post by Rich62 on 2010-04-29
There is a Linux only application called Jalia which is similar to Sage.  It's opensource and you can download it from [http://jalia.sourceforge.net](http://jalia.sourceforge.net)  It needs compiling so I had to get someone to do that for me.  It's about the nearest thing I can find out there to Sage whether Windows or Linux based, although I am having problems creating a new company all I can access is the demo companies.

---

### Post by finlost on 2010-05-02
Quickbooks is the only reason I haven't expunged my computers of Windows.  As long as QBs is PC/Mac based, I will need to have a Windows system.  :-&

---

### Post by Oasu4g on 2010-05-12
> **clanglois said:**
> SQL Ledger Has been recomended to be a good solid general ledger. It's written in perl and uses mysql.
PostgreSQL, actually. MySQL is not supported.

---

### Post by linuxcss on 2010-05-15
i am looking for multi-user accounting and billing software.

right now client is using older version of quicken and quickbooks in a non multi-user mode,
in VMs.

they need to have linux based multi-user version ... any suggestions?

anybody here using ledger SMB ?  or Adempiere?

If so what is pluses and minuses of them?

---

### Post by Oasu4g on 2010-05-15
From what I've seen, LedgerSMB is a less feature-filled branch of SQL-Ledger, split because of licensing reasons? I have never used it so I can't tell you much about it, but I believe it's still under a lot of development, so don't expect to see all the functionality that you might expect in a full-featured accounting package.

I believe Adempiere is also under major development. Their website is very unclear...

SQL-Ledger looks to be the best option from what I've seen, for my needs, but the downside to SQL-Ledger is that if you need help, or if you want to access documentation/a manual, you will have to pay for it. However, the software is still released under the GPL.

---

### Post by plavania on 2010-06-15
Please visit the Blog section of Walking Tree on "How To's" of Adempiere. Walking Tree has extensive experience in Adempiere and built there own ERP product EagleRP on top of Adempiere. They have a strong presence in ERP Implementation and Customizations around Adempiere, for more than 4 years now with a clientele from different verticals. By end of 2010, the company is publishing a book on "How To's" for Adempiere to make life easier for all fellow implementers.
Incase you do not find the information that you are looking for already existing on their blog, try posting a question, and you can be assured of a prompt and overwhelming reply.
[http://www.walkingtree.in](http://www.walkingtree.in)
[http://wtcindia.wordpress.com/](http://wtcindia.wordpress.com/)

---

### Post by juddm on 2010-07-02
Hi,

I know this 'late' reply but I thought I would answer for completeness.

I am an accountant and I specialise in financial systems so most of my experience is with ERP and other enterprise applications.

The 'Accounting' software market broadly has three bands of products, the small business accounting, medium business accounting and ERP.

Many people have commented on what distinguishes Accounting from ERP but imho it is that you define the accounting rules first in ERP and then the system makes the accounting entries based on the process and documents you create.  The other key feature is the existence of an application dictionary, such that a consultant may extend or modify the system.  However, these lines have been blurred by marketing consultants trying to move their products up the value scale and by technical people claiming their product is a little closer to 4GL than warrants.

In your question you ask about Sage, but you don't mention which Sage product.  I assume you mean Sage Line 50 which is a fairly basic product as far as functionality goes. 

There are a few products that have been mentioned, jalia and gnucash probably being the better of the bunch in terms of oss.  

However, there will be a point where accounting systems will not serve your business and with the open source model, you may wish to move straight to the good stuff - that's ERP.

There isn't really anything OSS in the mid range and I guess this is because the ERP systems extend down to fill this space.

ERP is a little more complex to setup because you need to make your decisions up front - but you make those decisions once and then never (well... rarely) need to think about them again - and this is part of what makes ERP more efficient.

There are a number of ERP's out there in the OSS world - they fall broadly in to two families - compiere (not sure if this is oss anymore), adempiere, openbravo and ofbiz, xtuple and derivatives.

I'll disclose an interest - I work on the ADempiere project - but that's because it meets my needs most often.

Some tips:
 - if you are a small business and want to keep the costs down - get your solution hosted.  ERP can be complex to install and manage - best leave it to someone else unless you have the expertise in-house.
 - ERP is more complex to deploy because you need to make some decisions about your business first.  However, the process of designing your processes can be very valuable to your business in terms of formulating roles, defining working practises, identifying non value added activities, joining up strategy with day to day activity, creating a turnkey operation and managing quality.  So the complexity usually results in the fact that not all of the business and it's processes have been thought out or documented and so the process of implementation can help you better design your business.  My suggestion is that it is time and money well spent.  You may not 'feel' this way before you do it - but most people 'feel' this way after they have implemented imho.
 - If you're simply interested in compliance - don't do ERP.  Choose a small business accounting application and resign yourself to the accounting fees.  Only look at ERP if you are looking for a strategic system for your business.

Mike

---

### Post by linuxcss on 2010-11-19
Back in May We asked about accounting systems out there for Ubuntu.
We found a system that has a lot going for it called xtuple Postbooks.

The system leverages the postgresql open source database, along with QT, javascript, openrpt and supports multi-user access. 

In skilled hands this software can be customized to fit other businesses including companies that bill for time and expense. 

If you need expert help or customization and are interested feel free to contact us.


[www.curtissystemssoftware.com](www.curtissystemssoftware.com)

---

### Post by kcacct on 2010-12-18
> **linuxcss said:**
> i am looking for multi-user accounting and billing software.

right now client is using older version of quicken and quickbooks in a non multi-user mode,
in VMs.

they need to have linux based multi-user version ... any suggestions?

anybody here using ledger SMB ?  or Adempiere?

If so what is pluses and minuses of them?



Have you tried using clarityaccounting.com?  It's an online software and should work for you.

---

### Post by Henry12 on 2012-08-30
Zoho Books is easy to use accounting software that works on PC and Mac. It allows you to invite multiple users.




[software for accounting]("http://www.zoho.com/books/")

---

