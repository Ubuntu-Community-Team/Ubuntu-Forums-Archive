---
title: "This morning's security update has broken my localhost."
date: 2011-10-19
forum: Security
---

### Post by cov on 2011-10-19
Absolutely livid.

It was working fine yesterday, but there were security upgrades to Kerberos this morning which appears to have broken my LedgerSMB installation.

I desperately need to invoice before a deadline, but cannot get in to enter the invoices.

> A user name and password are being requested by [http://localhost](http://localhost). The site says: "LedgerSMB"

My password isn't accepted, so I'm locked out.

Can anyone suggest a way to bypass this?

---

### Post by cov on 2011-10-20
Is there a way of disabling the password?

Is there a way of finding out what username the system is looking for?

There is nothing in the /var/log/apache2/access.log or var/log/apache2/error.log to indicate why it needs a password or what password or, indeed, what username it is looking for.

There is some urgency on this as I have already past a deadline.

Inevitably, of course, I am getting all the "You should have stuck with windows" comments, which, from where I am standing right now, are entirely justified.

---

### Post by star39 on 2011-10-29
If you are using ledgersmb 1.3.1 you have to use your admin login name
and the password,

Admin login name is the name you used when you made a database for your company.


Frans van der Star
email: [email]f.van.der.star@gmail.com[/email]

---

### Post by nogoodnamesleft on 2011-10-29
I assume you've tried ledgerSMB's support?

I can understand why you are upset but I don't think the operating system has anything to do with it. This sort of stuff happens all the time with computers no matter what the OS.

Can you not just roll back yesterday's backup?

In most enterprises I have seen (granted I'm rusty being retired a while) we would never ever ever ever fiddle with a working box. Only external-facing servers are kept updated to keep the hackers at bay. 

Anyway I wish you the best of luck getting this sorted, and I think once it's over and cooler heads prevail, sit down and think about whether windows would really have made a difference, or whether the issue is IT management practices.

If anyone tells you windows servers don't break due to patches, they're plain lying. There's a reason we made people fill out a request form in order to reboot a server.

---

### Post by cov on 2011-10-31
Fair enough.

The reason I am irritated with the operating system is that it was working perfectly before the upgrade broke it. And, yes, I agree that a working box shouldn't be tampered with. However, I am a one-man operation and the machine is not entirely dedicated to LedgerSMB.

I have indeed been onto the LedgerSMB support, but they are as perplexed as I am.

I have tried all combinations of username and password, none are accepted.

Googling tells me that other people have this problem, not necessarily with LedgerSMB, but I have yet to see a solution.

It would help if the error message was a little less cryptic.

I don't doubt that Windows machines have worse issues, but they do seem to enjoy more than their fair share of Schadenfreude when it happens to us Linux users.

---

### Post by nogoodnamesleft on 2011-10-31
I know I can't fix this one but if you have only a single box, I would suggest running critical apps in a virtual machine. You wouldn't actually care then if the host OS broke and you could have a different OS installation with different patch levels for each application.

e.g [https://www.virtualbox.org/](https://www.virtualbox.org/) or something (if it's stable yet).

I don't know how much you do or do not know about VMs so I apologise if I am repeating things you already know. They're essentially 'separate ubuntu install, running inside a desktop window, on your ubuntu desktop' and the whole 'virtual' disk for the entire install is a single file. You can back up and restore the entire machine just by ctrl+c and ctrl+v of that file in nautilus file manager. If the host OS breaks, reinstall, and recopy that one file, and back where you were.

Anyway I really do hope you get this sorted. 

BTW they probably won't notice if you round the invoice (up) to the nearest grand and just wing it. If they query it, it can get stuck in accounts for a couple weeks or so while you sort out your disk :-)

---

