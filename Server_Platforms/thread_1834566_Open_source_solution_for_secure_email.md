---
title: "Open source solution for secure email?"
date: 2011-08-27
forum: Server Platforms
---

### Post by maires on 2011-08-27
Currently my organization uses a hosted exchange 2010 server and we pay through the nose for email. However were in the healthcare industry so simply apt-get'ing an email server wont work. 

We can reduce our costs by a pretty large margin by going with google apps for the domain but once again vanilla google apps has to be bolstered by some secure email solution (postini encryption or zsentry etc...) and also postini message archiving and discovery (the 10 year version of archiving) 

I have searched and googled quite a bit but I am not finding anything fast... (well i found zimbra but not really impressed) 

Our organization is only 35 users and I think its rediculous to have to spend $10,000 on email... or 5,000 if we go with google apps each year. 

So my question is this: What combination of open source software can I use to provide email to my users that also gives point to point message encryption. (ie come pick your message up on our server) 

~Matt

---

### Post by meastwood on 2011-08-27
[http://www.dovecot.org/](http://www.dovecot.org/)

Dovecot is an open source IMAP and POP3 server for Linux/UNIX-like systems, written with security primarily in mind. Supports SSL/TLS

---

### Post by maires on 2011-08-28
Going in the right direction. A secure connection to the server is a must. However to satisfy HIPPA requirements I need point to point secure email. 

Essentially when you click the send button to send a secure email the server holds on to it and notifies the recipient to come pick up the message. They then have to pick it on the server. Ussually through HTTPS. 

This would probably be some sort of addon for the server or a totally seperate system.

---

### Post by Lars Noodén on 2011-08-28
Do you mean mail or groupware.  MS Exchange is trying hard to be groupware.  For that, in addition to Zimbra, you have 

Kolab
    [http://www.kolab.org/](http://www.kolab.org/)
Citadel
    [http://www.citadel.org/](http://www.citadel.org/)

If you just need mail then you have 

simta
    [http://rsug.itd.umich.edu/software/simta/](http://rsug.itd.umich.edu/software/simta/)
Dovecot
    [http://www.dovecot.org/](http://www.dovecot.org/)
Postfix
    [http://www.postfix.org/](http://www.postfix.org/)
Exim
    [http://www.exim.org/](http://www.exim.org/)
Sendmail
    [http://www.sendmail.org/](http://www.sendmail.org/)

---

### Post by haqking on 2011-08-28
> **maires said:**
> Going in the right direction. A secure connection to the server is a must. However to satisfy **HIPPA** requirements I need point to point secure email. 

Essentially when you click the send button to send a secure email the server holds on to it and notifies the recipient to come pick up the message. They then have to pick it on the server. Ussually through HTTPS. 

This would probably be some sort of addon for the server or a totally seperate system.

or HIPAA even ;-)

+1 to Zimbra or dovecot

---

### Post by SeijiSensei on 2011-08-28
I don't think there's anything in the open source world that does precisely what you want.  You could build your own system though.  Use procmail to send notices to the users when messages arrive and SquirrelMail with HTTPS to read them.  Notices could be a real pain for someone with heavy mail traffic, though.  They'd be better off just leaving Squirrel open in their browsers.  You could use an alternate subdomain for HIPAA-related traffic, I guess, though you need to enforce its use on your correspondens.

Transport encryption is pretty common these days.  TLS is usually the default for programs like sendmail.  Just replace the self-signed certificate with one purchased from a cert vendor.

Really the only effective solution for secure mail is something like GPG.  The obvious problem is that many of your users' correspondents won't have GPG enabled and wouldn't be able to implement it even if they wished to do so.

I consult to one health provider.  We're also looking into outbound content scanning to flag potential HIPAA breaches like Social Security numbers being sent in plain-text email.  We use [MailScanner]("http://www.mailscanner.info/") for virus/spam scanning, and its "Message Content Protection" add-on enables outbound scanning.  You still have to write a bunch of regex-based rules since it uses the SpamAssassin engine for scanning.

I built a system to enable patients to make appointments online using the techniques you're talking about.  No PHI is sent in any email; the messages contain only links back to our secure website.  All the PHI is encrypted and stored on a database server inside the organization.  This was a custom project written in PHP, though, not a package we could install off-the-shelf.

One other important aspect of HIPAA for e-mail is the archiving requirements.  While the regulations appear fuzzy on the matter, better to be safe than sorry.  The required archiving period is six years, I believe.  MailScanner makes this easy as well since it has a built-in archiving feature.

---

### Post by praveenkv1988 on 2011-08-28
I recommend using postfix and dovecot with SSL enabled. This works good.

---

### Post by artur.kerman2 on 2011-08-28
Since you need HIPAA compliant email, you should be looking for encrypted email service not just TLS or SSL encrypted connection to an email server.  TLS does not provide with sufficient security measures mandated by HIPAA.  I would suggest to look into services offered by SecureMedical.net/CryptoHeaven.  The costs would be much lower than what you are currently paying too.

Artur.

[http://www.cryptoheaven.com/secure-email-hosting.htm](http://www.cryptoheaven.com/secure-email-hosting.htm)

---

### Post by m.brinkers on 2011-08-29
For email encryption you might at [www.djigzo.com](www.djigzo.com). It's an open source email encryption gateway with support for S/MIME and PDF encryption. The built-in Data Leak Prevention (DLP) module can be used to prevent certain information to leave the organization via email. DLP can configured to filter on credit card numbers, bank account numbers, patient ids, excessive amounts of email addresses or other personal information in one email message etc. 

Djigzo can be installed on most Linux and Unix based systems. Installation packages are available for Ubuntu, Debian, Red Hat and CentOS. A-ready-to-run virtual appliance for VMware and Hyper-V is available. BlackBerry and Android are supported as well.

---

### Post by hawk2010 on 2011-08-29
I would also recommend Zarafa

---

### Post by SeijiSensei on 2011-08-29
Can someone explain how an encryption gateway like Djigzo works?  How is decryption implemented on the receiver's end?  If most recipients use  standard clients without any encryption, say just Thunderbird and an IMAP server, how can the sender enforce encryption?  How would the recipient know what to do with the encrypted message?

Or do these implement what the OP was looking for originally?  Do they send a plain-text notice to the recipient that an encrypted message is available and provide a method for retrieving it securely?

---

### Post by maires on 2011-08-29
Wow the thread blew up! Ok im going back and reading everything right now. I think one of the above posters was correct in that I was not using the correct terminology. 

Will report back in a bit after researching all the links you guys provided. 

~Matt

---

### Post by maires on 2011-08-29
Djigzo looks like a pretty complicated piece of software... I have been reading about it for a while and I am not 100% it offers what I want. however it does do s/mime which requires exchanging of public keys I think? 

To the above poster the ideal way (for us) is to have a web portal where the user comes to pick up the message via HTTPS. That is how we enforce the encryption to the end user. They just get a notice in their inbox that they received a secure message. 

~Matt

---

### Post by Lars Noodén on 2011-08-29
> **maires said:**
> To the above poster the ideal way (for us) is to have a web portal where the user comes to pick up the message via HTTPS. 

Then you could look at RoundCube as the mail client.

---

### Post by SeijiSensei on 2011-08-29
> **maires said:**
> To the above poster the ideal way (for us) is to have a web portal where the user comes to pick up the message via HTTPS. That is how we enforce the encryption to the end user. They just get a notice in their inbox that they received a secure message. ~Matt

You're presumably talking about people within your organization.  What about people outside?  Suppose you send me a "secure" email.  Do I get a plain-text notice and a link that enables me to pick up your message with a web browser?  Do I need to have a pre-existing account of some sort on your server?  If not, how do you enforce that I'm the one reading the message? Must I then use the browser-based client to send you a reply?

---

### Post by contactfj on 2012-05-08
Hi, Matt.  What solution did you end up using?  I would love to use google apps, but haven't found a HIPAA compliant workaround yet.  I'm also exploring hushmail and the open source solutions mentioned in this thread.  I've been quite surprised at how difficult it's been to find a reasonably priced HIPAA compliant email solution.  Thanks for your help.

Fritz

---

### Post by LHammonds on 2012-05-08
I'd be interested in any updates for HIPAA-compliant solutions as well.

[Zimbra]("http://www.zimbra.com") is a nice and standards-based solution that you can start off using the "free" version but to make use of archiving, you have to upgrade to the Network Edition...which is about on par in regards to the cost of an M$ Exchange implementation.

It has also been mentioned that you have to bolt-on additional stuff to Google Apps which also can cost a pretty penny but would be a better option if you did not have sufficient infrastructure to host a solution yourself.

Zimbra Open Source Edition (e.g. OSE, free) can enforce SSL-only connections and also comes with anti-virus, anti-spam and anti-phishing.  You can also make use of S-MIME and PGP for end-to-end encryption...but it has also been pointed out that there can be usability issues with it...but in terms of HIPAA, Zimbra systems could claim victory even if the email system is hard to interact with outside the company.  lol.  Same could be said of any system using S-MIME an PGP I guess.

Having a gateway system like [DJIGZO]("http://www.djigzo.com/") sounds like a great idea to have a system in between your mail server and Internet to handle encryption and data scanning for potential "leaks" but I wonder how many people are successfully using that system.  Seems a bit off-putting to me (however, I only spent 10 minutes looking around on the site)

LHammonds

---

### Post by kennethconn on 2012-05-08
Can you just clear up if you are only looking for secure e-mail between your 35 users and encrypted storage of messages, or are you looking for more?

---

### Post by HermanAB on 2012-05-09
Howdy,

Citadel does all mail protocols ever invented this side of Betelgeuse, including the secure ones and there is nothing easier to set up: [http://citadel.org](http://citadel.org)

---

### Post by SeijiSensei on 2012-05-09
I'll just reiterate one point I made earlier.

The problem here isn't really one of finding a secure server program; there are lots of options for that.  The problem is exchanging mail securely with people outside the organization, especially patients, who cannot be expected to have secure protocols like GPG enabled.  Nor is it reasonable to impose any such requirements on patients who may have only limited computing skills.

Pretty much the standard method I've seen hospitals and other providers adopt is the so-called "portal" approach.  Patients and other outside correspondents must have accounts on a server inside the medical provider's organization where messages for them can be stored and accessed.  This can be a mail server or a system where the messages are stored in a database and displayed via a web app.  When someone like a physician needs to send a message to a patient, that message is entered into the system.  The patient receives only a plain-text email telling her that a message is waiting for her on the system.  The patient must then log in to the server to retrieve the message, typically via SSL to a web-based client.  Any replies, or any other messages from patients to providers, must be handled via this system as well.  Every single message that contains "patient health information" must also be archived.  I believe the requirement is seven years.

Sophisticated portal software is expensive but very beneficial to patients.  For instance, I can log into my account with my providers' network and see not only communications from my physicians but also things like test results as soon as they become available.

---

### Post by kennethconn on 2012-05-09
> **SeijiSensei said:**
> I'll just reiterate one point I made earlier....
 
Your point is very well put. Do you know or use any open source solution to meet these requirements?

---

### Post by HermanAB on 2012-05-09
This is exactly what Citadel is for.

---

### Post by SeijiSensei on 2012-05-09
> **kennethconn said:**
> Your point is very well put. Do you know or use any open source solution to meet these requirements?

Off the shelf, none that I know of, though I haven't looked at [VistA]("http://en.wikipedia.org/wiki/VistA") for a long time now.  Perhaps they've added functionality to that for handing secure messaging or portal functions.  It's probably overkill if all you're looking for is a messaging solution.

Otherwise I think you'd have to put the pieces together yourselves, just as I did when I built the secure appointment system I [described]("http://ubuntuforums.org/showpost.php?p=11195353&postcount=6") earlier.  For this task I'd probably build a web app around an SQL database that handles the message store and user accounts consisting of:

1)  a secure web application to handle patient sign-ups and an interface to access their messages; 

2)  a system for storing the messages in an SQL database like PostgreSQL with content encryption; I use a simple method where I encrypt the message with AES256 then use MIME64 to create a text representation that is easily storable as a varchar field;

3)  a secure web application for staff to manage patient accounts, confirm their registrations, etc.; how this integrates with existing EHR systems is an open question and probably depends on whether the EHR system offers decent open interfaces to exchange data

4)  a web-based client to access the messages after patients log in via the secure web application;

5)  a system to send notices by email to patients' insecure external accounts when messages for them arrive on the system; you'd want to have a method for sending reminders if messages reside unread for too long

6)  archiving, backup, logging, etc.; maybe full-text search tools; [SphinxSearch]("http://sphinxsearch.com/") is a great tool for searching text in SQL databases.

That's just a bare-bones overview.  I think a small team could put this together in a couple of months using entirely free software and PHP or a similar high-level language with good web hooks.  Think there's a market for this?

> **HermanAB said:**
> This is exactly what Citadel is for.

I searched the Citadel site for material related to HIPAA, the set of US regulations that occasioned the original query.  The only thing I see mentioned is that Citadel provides archiving capabilities, which is the easiest requirement to meet.  I didn't really see anything about insecure notifications, etc.  Maybe I missed something; if so, point me to the appropriate pages on their site; I'd be curious to read what it can offer.

---

### Post by kennethconn on 2012-05-09
That's impressive SeijiSensei if you built that system yourself, thanks for taking the time to reply.

---

### Post by SeijiSensei on 2012-05-09
Well, no, not the one I just described, but the appointments system in the earlier posting.  That has many of the same components, though, just more narrowly limited to the task of making appointments rather than more general communication between patients and physicians.

---

