---
title: "Phising / fradulent email"
date: 2014-10-12
forum: The Cafe
---

### Post by pfeiffep on 2014-10-12
Yesterday my wife (using her new Macbook Pro) received an email looking like it came from Capital One. The email stated that her account was accessed by different computers and had multiple password failures. There was a PDF attachment (no she didn't open it) which the email instructed her to open and follow the instructions to reset her password. 

She's pretty computer savy and immediately asked me whether we had such an account ... well we don't. She asked me to look at the email and take appropriate action (I am a retired security specialist).

In the full headers the return address was another indicator that the message did not originate from Capital One. I went to their site and found the correct address (abuse@capitalone.com) for reporting. 

Both my wife and I follow the general guidelines about keeping our computers safe, but I'm wondering why there isn't more attention / guidelines about reporting fraudulent emails.

---

### Post by coffeecat on 2014-10-12
I can understand why you posted in the Security sub-forum, but that is intended for technical support/questions concerning security in Ubuntu or Xubuntu/Lubuntu/etc specifically. As this is such an important discussion topic...

*Thread moved to **The Cafe**.*

---

### Post by coldraven on 2014-10-12
I find that Gmail tags this sort of thing as Spam with remarkable success. OK I lose some privacy but as I use the Firefox add-on AdBlockPlus I don't get to see the targeted adverts.

---

### Post by bashiergui on 2014-10-12
Yah Gmail is pretty amazing at filtering malicious crap. In fact security researchers had to work around Google's filter so that they could share malware samples. > Both my wife and I follow the general guidelines about keeping our computers safe, but I'm wondering why there isn't more attention / guidelines about reporting fraudulent emails.What exactly do you want to see? I can give you countless links on articles and blogs warning of phish scams. Sometimes it seems like a subject that has been beat to death.

---

### Post by pfeiffep on 2014-10-12
+1> [COLOR=#000000]coffeecat[/COLOR]
[COLOR=#000000][INDENT]**Re: Phising / fradulent email**
I can understand why you posted in the Security sub-forum, but that is intended for technical support/questions concerning security in Ubuntu or Xubuntu/Lubuntu/etc specifically. As this is such an important discussion topic...
[/INDENT]
[/COLOR]


> [COLOR=#000000]bashiergui[/COLOR]
[COLOR=#000000][INDENT]**Re: Phising / fradulent email**
What exactly do you want to see? I can give you countless links on articles and blogs warning of phish scams. Sometimes it seems like a subject that has been beat to death.[/INDENT]
[/COLOR]

I really don't need to see anything personally - I keep up with most security issues. 

I'm posting because I think most of the information propogated is concerned with not opening the emails, but IMO that falls short of what should be done. 
Analyze the email and forward it to the company or entity that is being mis-identified. 
Look at the complete headers to insure the email is fraudulent.

---

### Post by SeijiSensei on 2014-10-13
In most cases forwarding the email to the alleged sender is useless.  The message probably originated on a hijacked computer and Capital One, to take your case, has absolutely no control over the sender.  Oftentimes the sending computer is in a foreign country which makes prosecution either impossible or not worth the effort. Financial institutions never contact customers by email because of the widespread prevalence of phishing scams.  

Thunderbird now throws up a warning if you click a link whose text appearance doesn't match the URL.  In general, the simplest way to check is to hover the mouse over the link.  The real URL will appear in the status bar.  If they don't match, it's likely a scam.  For the intrepid, use the View Source tool in your mail client to see the full headers.  In Thunderbird (and Firefox), you can use Ctrl-u.

Another common scam is emails claiming to offer gift cards from well-known companies.  For some reason, this particular scam has been much more prevalent in the past few months.  Often the scammer's page will look identical to the actual website with a form asking you to enter your personal information in order to receive the gift.  The URL will, of course, usually have no relationship to the company allegedly offering the gift.  I got one today supposedly from the Kroger supermarket chain.  Following the link went through three redirects, then asked me to take part in a "survey," the reward for which would be a $50 gift card.

---

### Post by buzzingrobot on 2014-10-13
I have a Capitol One account.  They seem to use a fairly rigorous fraud control algorithm and it is not unusual for me to receive email/texts/calls from them to verify a credit card purchase. I also have opted for email alerts for any credit card transaction over X amount. 

But, no links are ever contained in those emails or texts. It's an alert telling me to contact Capitol One.  



As SeijiSensei said, any email from a financial institution that contains links is certainly a scam.

---

### Post by coffeecat on 2014-10-13
> **buzzingrobot said:**
> 
As SeijiSensei said, any email from a financial institution that contains links is certainly a scam.

Sadly, this is simply not so. Every month I get an email from the company that issues one of my credit cards telling me that my monthly statement is available, together with a link to their login page for my convenience. There is information in the email that only the bank could tell me, and the linked URL is obviously the bank's, but it would be all-too-easy to dismiss this as a phishing attempt. And this is not a small, incompetent outfit either. It's a well-known internationally-trading large credit card issuer, and a subsidiary of a major American bank.  

In contrast, the monthly email from the bank where I hold my current account simply tells me my latest e-document for my monthly statement is available if I log in, without providing a link.

---

### Post by buzzingrobot on 2014-10-13
> **coffeecat said:**
> Sadly, this is simply not so. Every month I get an email from the company that issues one of my credit cards telling me that my monthly statement is available, together with a link to their login page for my convenience. There is information in the email that only the bank could tell me, and the linked URL is obviously the bank's, but it would be all-too-easy to dismiss this as a phishing attempt. And this is not a small, incompetent outfit either. It's a well-known internationally-trading large credit card issuer, and a subsidiary of a major American bank.  

In contrast, the monthly email from the bank where I hold my current account simply tells me my latest e-document for my monthly statement is available if I log in, without providing a link.

I almost said "almost certainly".

Yeah, that sort of thing shouldn't be happening.

These days, I do all my banking with one bank-supplied app on one iPad. Two-factor authentication is required to move money out of the account.

---

### Post by pfeiffep on 2014-10-13
> [COLOR=#000000]SeijiSensei[/COLOR]
[COLOR=#000000][INDENT]**Re: Phising / fradulent email**
In most cases forwarding the email to the alleged sender is useless. The message probably originated on a hijacked computer and Capital One, to take your case, has absolutely no control over the sender. Oftentimes the sending computer is in a foreign country which makes prosecution either impossible or not worth the effort. Financial institutions [COLOR=#ee82ee]*never*[/COLOR] contact customers by email because of the widespread prevalence of phishing scams. 
[/INDENT]
[/COLOR]
I agree that forwarding the email to the return address is senseless; that's why** I went to Capital One's website** to determine how they wished to report the incident. Looking up the full headers and including them in the forward was a method I used to insure they had all the information that I could provide to proceed (also validated the fraud assumption).

I receive daily email from financial institutions that **I have registered** for daily feedback.

---

### Post by SeijiSensei on 2014-10-13
> **pfeiffep said:**
> I agree that forwarding the email to the return address is senseless; that's why** I went to Capital One's website** to determine how they wished to report the incident.

My point was that there is little or nothing Capital One can do about this.  Having a page where you can report phishing fraud is good PR for the financial institution, but I strongly doubt it has much practical significance.  I long ago stopped bothering to report scams like that.

---

### Post by tgalati4 on 2014-10-13
I do like their commercials.  Something about Vikings wielding axes makes me feel secure.  "Where is YOUR wallet?"

---

### Post by pfeiffep on 2014-10-13
> **SeijiSensei said:**
> My point was that there is little or nothing Capital One can do about this.  Having a page where you can report phishing fraud is good PR for the financial institution, but I strongly doubt it has much practical significance.  I long ago stopped bothering to report scams like that.I prefer to let the financial institution make their own decisions. IMO by not reporting they are left out of the decision process.

---

### Post by bashiergui on 2014-10-13
> **coffeecat said:**
> Sadly, this is simply not so. Every month I get an email from the company that issues one of my credit cards telling me that my monthly statement is available, together with a link to their login page for my convenience. There is information in the email that only the bank could tell me, and the linked URL is obviously the bank's, but it would be all-too-easy to dismiss this as a phishing attempt. And this is not a small, incompetent outfit either. It's a well-known internationally-trading large credit card issuer, and a subsidiary of a major American bank.  

In contrast, the monthly email from the bank where I hold my current account simply tells me my latest e-document for my monthly statement is available if I log in, without providing a link.
I hope the links are http. Ooh, and when you reset your password do they email it to you in clear text? If so then you must be using **SecureBankTrifecta**. I like their tag line: "Sleep soundly knowing your finances are wide open to anyone that bothers to intercept your traffic!"

---

### Post by SeijiSensei on 2014-10-14
> **pfeiffep said:**
> I prefer to let the financial institution make their own decisions. IMO by not reporting they are left out of the decision process.

If you manage a mail server like I do, you get scams like this every day.  Reporting them just isn't worth the effort.  The gift card scams are especially numerous at the moment.  I've had to add more filtering rules to SpamAssassin just to stem the deluge.

---

### Post by WinEunuchs2Unix on 2014-10-16
20 years ago I got an e-mail from Nigeria saying the evil, brutal, dictator is stopping them from taking their 6 million dollars out of the country and if I gave them 5 grand they would give me tons of dough for receiving the 6 million dollars into my bank account.

I forwarded it to the RCMP and they did nothing.

It is a SCAM and the police are either in on the GIG or they DO NOT care.

---

