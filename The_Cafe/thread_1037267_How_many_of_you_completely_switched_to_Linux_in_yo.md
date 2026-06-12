---
title: "How many of you completely switched to Linux in your business?"
date: 2009-01-11
forum: The Cafe
---

### Post by user_ex on 2009-01-11
Currently I'm managing the IT department of a medium size organization.
We're planning on switching all our XP workstations to Ubuntu.
At this point all our servers are running Linux, except for a Domain controller.
We are using Linux for out Intranet, DNS, file server, mail server, proxy, voice over IP, backups, etc.

Currently the maintenance guys spend up to 50% of their time restoring the user PCs from viruses and system crashes.
So naturally the next step would be to  migrate the desktops and the domain controller.
There are several reasons why we haven't done this before:
[LIST]
[*]We were using a Windows based ERP. We got rid of this and replaced with a Web based one. Even though the ERP seemed to work fine with Wine, it was a bit of a risk. This was the major hold-back.
[/LIST]
[LIST]
[*]Earlier versions of office (Ex. Open Office) applications had issues when working with MS Office files. This is not a real issue anymore.
[/LIST]
[LIST]
[*]User experience. We tried installing Linux for some “Beta” users about 2 years ago (Open SUSE at that time). Specially for the non skilled users, it was kind of a shock. We retried this test a couple of months back with Ubuntu 8.10 with much better results.
[/LIST]

What has been your experience in the migration from Win to Linux.
What problems have you faced and how do you solve them?
What are the applications of choice to replace the Win applications?

Thanks for your input!

---

### Post by jmejedi on 2009-01-11
My answer to your question ["What problems have you faced and how do you solve them?"]:

People taking a while to get acquainted with the new OS, solution: its a matter of time....

++++++++++++++++++++++++++++++++++++++++

My answer to your question ["What are the applications of choice to replace the Win applications?"]:

OpenOffice should-replace MS Office....





:)

---

### Post by XPuntu on 2009-01-11
I'm trying to get our CFO to give it some serious thought but Windows is a definite safety blanket. There are some things working in my favour though:

1) We don't use Vista so we're looking at $250 for the XP downgrade on all our new Dell machines
2) MS Office basic is another $150
3) Excel 2007 with the stupid "ribbon" is different enough that learning Open office 3.0 could be the same as learning Excel 2007.

But the biggest drawback is that we're using Exchange 2007 which doesn't work with Evolution. If we could get around that I'd be most of the way to switching us over.

---

### Post by earthpigg on 2009-01-11
> **XPuntu said:**
> I'm trying to get our CFO to give it some serious thought but Windows is a definite safety blanket. There are some things working in my favour though:

1) We don't use Vista so we're looking at $250 for the XP downgrade on all our new Dell machines
2) MS Office basic is another $150
3) Excel 2007 with the stupid "ribbon" is different enough that learning Open office 3.0 could be the same as learning Excel 2007.

But the biggest drawback is that we're using Exchange 2007 which doesn't work with Evolution. If we could get around that I'd be most of the way to switching us over.

start gradual, maybe? firefox with adblock plus (bandwidth is money) and openoffice (money is money).

---

### Post by caro on 2009-01-11
We haven't made the switch.  My ERP solution is Windows-based, as is my networked security system.  And we use Exchange.  I have managed to get some of my employees to use Firefox instead of IE.  

We do install some linux-based VOIP systems for customers though.

---

### Post by phrostbyte on 2009-01-11
I never understand why organizations buy Exchange. It's expensive, and EXTREMELY proprietary, basically it's like a total lock in into Microsoft products like Internet Explorer and Outlook. On top of all that it's not even that good of a groupware solution. 

Anyway [Zimbra]("http://www.zimbra.com/") is awesome .. it supports Firefox and Evolution pretty well (unlike Exchange). It also supports Outlook too with full MAPI functionality. The organization I worked for (an .edu) picked paying for Zimbra over a free Exchange solution. We picked it because it's easy to support (especially in a mixed environment, where people might have Linux desktops or use Firefox) and of course runs on Linux.

---

