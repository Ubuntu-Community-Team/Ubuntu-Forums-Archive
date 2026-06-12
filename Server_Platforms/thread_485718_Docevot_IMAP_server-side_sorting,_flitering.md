---
title: "Docevot IMAP: server-side sorting, flitering"
date: 2007-06-27
forum: Server Platforms
---

### Post by Versusnja on 2007-06-27
Hi!

I installed a dovecot IMAP server. Very easy and flexible installation.
I need to do some server-side sorting and filtering. After some reading I realised that the most common way to do that is to use Sieve scripts.

BUT I do not have an idea of where these scripts are...

Any howto's or just path to the scrtipts are welcome.
Thank you!

---

### Post by Versusnja on 2007-06-28
Does anybody uses server side filtering at all??

I need help with SIEVE. Please reply.

---

### Post by mwerlberger on 2007-06-28
i don't use it yet but i look forward to do so. The problem is that the dovecot version that is installed with Ubuntu 6.06 dapper is not able to handle sieve scripts. Therefore one has to install the newest version and there sieve (same as ldap) are sort of plugin modules. Just goole on dovecot and sieve and you will find the docevot docu about it.

Rgds,
 Manuel

---

### Post by deuce868 on 2007-06-28
I tend to have that on the client side. Thunderbird and squirrelmail will do the message threading and handle sorting based on date/etc. I've never actually looked at doing it server side. What does it get you there?

---

### Post by mwerlberger on 2007-06-28
just read about Sieve and what you can do with it. E.g. Sorting different mails in different folders. one for Ubuntu mailinglist, one for E17 mailing list, one for my private ones, one for my business adress and all within the same mailbox. No need of a running (stupid) Thunderbird that does the sorting. Nobody speeks about threading or sorting based on date or something like that. every mail-client can do that. but does your thunderbird is able to sort e.g. mails from [email]123@456.com[/email] to a specific folder when your computer is not running and you are checking your mails from a terminal? not really :-).

Rgds,
 Manuel

---

### Post by deuce868 on 2007-06-28
Ah, ok. I use impafilter for that kind of rule based sorting on the server side. It can log into all of my different addresses and process the email. 

A little slow on the draw this morning I guess.

---

### Post by BroadArrow on 2007-07-04
> **deuce868 said:**
> Ah, ok. I use impafilter for that kind of rule based sorting on the server side. It can log into all of my different addresses and process the email. 

I think you meant "imapfilter". The project home page is [here]("http://imapfilter.hellug.gr/") but I see the package is also in the Ubuntu repositories.

I was looking for exactly the same thing and found this thread. 

Using Thunderbird isn't the ideal option as I access an IMAP account from several different machines and want emails sorted on the server as they come in so this is the next best option to the ideal of being able to set up server-side sorting via Thunderbird.

---

### Post by mwerlberger on 2007-07-04
Sounds like imapfilter is a nice thing. But i think one of the main advantages of using Sieve is the good integration in other programs like Kontact or Horde.... Of course for the server-admins it would be no problem to handle the sieve rules with text files but the "normal" user wants a simple solution. And i think also Outlook can handle Sieve scripts. But not quite sure (and i'm glad i cannot test it on my box *g*).

Rgds,
 Manuel

---

### Post by deuce868 on 2007-07-04
> **BroadArrow said:**
> I think you meant "imapfilter". The project home page is [here]("http://imapfilter.hellug.gr/") but I see the package is also in the Ubuntu repositories.

I was looking for exactly the same thing and found this thread. 

Using Thunderbird isn't the ideal option as I access an IMAP account from several different machines and want emails sorted on the server as they come in so this is the next best option to the ideal of being able to set up server-side sorting via Thunderbird.

Yea, sorry for the typo. It's great because I can use it on several accounts on different servers and it can even move emails between accounts.

---

### Post by Versusnja on 2008-04-13
Thanks for the advise. May be I will try imapfilter later. but since Dovecot naturally supports _sieve _I'd like to use it.

I'm now upgrading my server from edgy to gutsy. I know Sieve is already included in Dovecot in Gutsy, so I'm going to try it today.
If anybody has good links to documentation on Sieve setup, please post here.
Thanks.

---

