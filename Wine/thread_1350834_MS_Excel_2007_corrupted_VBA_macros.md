---
title: "MS Excel 2007 corrupted VBA macros"
date: 2009-12-09
forum: Wine
---

### Post by pexxi on 2009-12-09
Due to customer's request I need to use Microsoft Office 2007 Suite under Linux (Ubuntu Karmic x64).

It perfectly works under wine 1.1.33 without any hacks, except of running VBA macros under Excel (probably under other Office programs).

When I try to open any workbook with macros created by Windows-installation of Office, Excel shows a message: "... corrupted macros..." and macros are automatically deleted, I have no access to them.

Vice-versa, when I try to open macros created by Wine-installation of Office 2007 on any Windows machine, same error message is shown and I can't access macros.

This is not the the well-known 'dir-bug', because none of my macro-modules has name 'dir'.

Macros can't be opened by Visual Basic editor, no matter, if "Enable macros" option is selected or not. VB editor shows an "Invalid data format" message.

It is probably related to use of Unicode/diacritic in strings and macro-generated messages, but I need this functionality.

Do you have some experience with this? Thanks.

P.S.: Use of OpenOffice is out-of-the-question, because of very limited VBA possibilities and lot of errors when I try to open and run these macros under OpenOffice. I have not enough time (and time is money ;-)) to adopt Excel macros to OpenOffice's needs and then hardly test, if it works in real customer's Windows & Office 2007 environment.

---

### Post by Breutigen on 2009-12-10
Found this:

[http://www.eggheadcafe.com/software/aspnet/31967852/macros-are-corrupted-and.aspx](http://www.eggheadcafe.com/software/aspnet/31967852/macros-are-corrupted-and.aspx)

I run Office 2003 under Crossover, after the installation under Wine failed. Give it a try, I don't think there is a simple solution for that kind of problem. Even under windose you wouldn't find a quick answer.

M$ has changed so many thinks in vba in the 2007 version that it takes hours and days to fix you own code even from 2003 ( plus mix it with different xp and vista configurations.. it is a hell )

---

### Post by pexxi on 2009-12-13
Ohh, no... We have, probably, misunderstood...

I have NO PROBLEM running my macros in Excel 2000, Excel 2003 or Excel 2007 but only on WINDOWS stations (doesn't matter if XP or Vista).

But, when I try to run (even simple) macro created on Windows station (any version of Excel) in Excel 2007 under Wine, it shows error and vice-versa, when I try to run (even simple) macro created on Wine, it shows error on Windows-box. That's the problem...

So this is not problem of Excel or Office, it is a problem of Office 2007 under Wine (probably some built-in DLL doesn't work as expected - but I don't know which DLL ;-))

---

### Post by bob-linux-user on 2012-02-27
I have had the same problem. Has anyone any ideas please?

---

### Post by ssuuddoo on 2012-03-16
hmmm, also here. Problem when running macros on Excel 2007 working in Win, but not in Ubu. Will try 2 install Office 2003, maybe it'll help.

---

### Post by ssuuddoo on 2012-03-16
> **ssuuddoo said:**
> hmmm, also here. Problem when running macros on Excel 2007 working in Win, but not in Ubu. Will try 2 install Office 2003, maybe it'll help.
ok, it didn't work, the office installed flawlessly, but trying 2 run the macros makes the app die. :)

so, I going for the virtualization soft now. :) vmware? :)

---

