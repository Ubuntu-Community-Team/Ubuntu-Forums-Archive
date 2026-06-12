---
title: "help with IMAP server"
date: 2007-02-24
forum: Server Platforms
---

### Post by neill on 2007-02-24
hi

i'm halfway to getting a simple email server to run on my LAN but can't work out how to configure the IMAP server

all my emails come from a series of POP3 boxes at a single ISP account 

i use getmail with maildirs and sort the mails into various folders all in my home account

/home/me/mail/account-1
/home/me/mail/account-2 etc etc

all well and good and the appropriate mails end up in the correct maildir folders

what i want to do now is serve them up to LAN clients using IMAP (so users can view the same set of mails from one of a number of PCs)

what i can't for the life of me figure out is how to set up the IMAP server such that each maildir represents a given account (from the point of view of the LAN MUA) with an associated password 

:confused: 

so in t'bird on the LAN PC i'd have an one account which 'pointed' at the maildir /home/me/mail/account-1 (with an associated password), another that 'pointed' to the account-2 maildir and so on and so on

does that make sense as a question ??

how can i do that ? or am i making some fundamental flaw in my approach and i need to do  the whole thing differently ?

thanks

neill

---

