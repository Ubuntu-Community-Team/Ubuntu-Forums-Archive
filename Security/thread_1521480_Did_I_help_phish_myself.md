---
title: "Did I help phish myself?"
date: 2010-06-30
forum: Security
---

### Post by Scott Swinyard on 2010-06-30
I signed into my ISP web based email and opened a mail apparently from my credit card provider telling me about a new enhanced statement. I dully clicked on the box marked "view statement" and the result was page telling me that Firefox could not connect to the server at the url.

I didn't provide any information pertaining to my credit card account at any time. I didn't provide any information at all. Just clicked on the button.

Is there anyway that anyone could get any information from that that could be damaging to me?

The odd thing is that the email had the last four digits of my credit card number already listed but I called my credit card provider on the phone and this was not anything they had sent me.

---

### Post by jflaker on 2010-06-30
It is likely it was a phishing site which has since been shutdown.

Firefox not finding the URL means the site was removed.  

404 means the URL wasn't found on the server, but if you got a couldn't find server, then that is even better.....

At worst, if you actually got the 404 page, only your IP may have been logged....if the server wasn't found, then nothing was logged.

When in doubt, don't click.  Especially if your financial institution isn't in the habbit of emailing you promotions......

---

### Post by Scott Swinyard on 2010-06-30
Thanks. I take it then that there is nothing they could do with my ip?

---

### Post by yeleek on 2010-07-01
You are one of probably many people who clicked on the link.  You didn't enter details, so there is no information gained there.  There is nothing they can do with your ip (presuming you run a firewall).  And unless you've a static IP address, at somepoint your IP address will change anyway.

Wouldn't worry about it - take it as a lesson learnt :)  i.e. manually inspect the url.

---

### Post by LiQuidAiR on 2010-07-01
> **Scott Swinyard said:**
> 
The odd thing is that the email had the last four digits of my credit card number already listed but I called my credit card provider on the phone and this was not anything they had sent me.

Interesting how they were able to possess the last four digits.  I wonder if this is just a random number.  If not, then I wonder if someone compromised your bank/credit card company and was able to only achieve one level of control and needed the phishing trick to finish it off.  There must have been some system, somewhere that was compromised....

---

### Post by quequotion on 2010-07-03
> **Scott Swinyard said:**
> The odd thing is that the email had the last four digits of my credit card number already listed but I called my credit card provider on the phone and this was not anything they had sent me.

Hopefully it was just a lucky guess. Could be gleaned from just about anywhere you've used your credit card online, as the last four digits often appear on an invoice in your email (unsecured webmail?) or in your account information (although most sites require your login to view this) even more insidious, and unlikely, would be if someone got them off a printed receipt from where you used your card offline and also obtained your email address.

I don't think you gave any more information than "they" already have, but just to be sure I'd change any online shopping passwords, change any e-mail passwords, delete any unnecessary  e-invoices, and review your credit card bill ASAP. /paranoid

---

### Post by jflaker on 2010-07-10
> **Scott Swinyard said:**
> ....SNIP.....The odd thing is that the email had the last four digits of my credit card number...SNIP

They probably found a credit card receipt and did some research and found as many matching email addresses as they could.....

On a credit card receipt is your name and last 4 of your CC.  you can go to [http://pipl.com]("http://pipl.com") and find so much if you are willing to put out the effort.  For scammers, doing this for thousands of people and getting one or two people to actually go to the site and put in their info could be financially worth the effort..........

---

### Post by Sporkman on 2010-07-12
At worst they could tell that your email account is active, matched an IP address with the email account, and have determined that you might be game for more phishing attempts. :)

---

