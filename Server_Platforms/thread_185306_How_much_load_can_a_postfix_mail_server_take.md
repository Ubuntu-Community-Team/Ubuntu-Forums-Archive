---
title: "How much load can a postfix mail server take"
date: 2006-05-31
forum: Server Platforms
---

### Post by Sapphiron on 2006-05-31
Hi All

like most IT guys, I am tired of managing Company email.  Corrupt PST files due to 2GB size limit.  Very slow and sluggish Outlooks. High price of exchange.

I am looking at using a ubuntu 6.06 server to run a postfix mail server.  i plan to add in Kolab to provide Groupware and then add Horde as a web interface.    I want to get away from having to install a mail client on every desktop.  

My clients are mainly people in Financial services who are required by law to keep relevant emails for a minimum of 15 years.  This means MASSIVE mailboxes.  Some of my clients get about 2GB's of mail every 6 months per user.  The companies are pretty small though (10-20 users), so budget is limited.

The developers of Kolab and Horde have me convinced that their software can take that type of strain.

What I am not too clear about is how a Ubuntu Mail and File Server will run with about 20-100GB's of email on it.

Would the performance be OK on a Dual-Core Athlon64 Server with 2GB RAM and Gigabit LAN.  i will be putting in a hardware RAID 10 Configuration (Promise PCI-Express RAID controller).

How difficult would it be to backup all the mail to external USB drives, Can I do that on a "live" system?

How difficult is it to transfer a user's mailbox to another person's?

any other advance would be welcome.

---

### Post by garyng on 2006-05-31
I believe you are not talking about postfix but may be cyrus/courier IMAP server then. postfix is only the mail delivery agent which only deliver the mail. Using Maildir(say in courier), each mail is in a seperate file(usually under the individual home directory) which can be backup as usual and as such, it can scale pretty well if you use a good FS(reiser/xfs).

But cyrus provides better share folder support so I think you need to think about the feature first but performance wise, they would not be worse than Exchange even on the same hardware setup.

---

### Post by Sapphiron on 2006-05-31
[QUOTE=garyng]I believe you are not talking about postfix but may be cyrus/courier IMAP server then. postfix is only the mail delivery agent which only deliver the mail. Using Maildir(say in courier), each mail is in a seperate file(usually under the individual home directory) which can be backup as usual and as such, it can scale pretty well if you use a good FS(reiser/xfs).

But cyrus provides better share folder support so I think you need to think about the feature first but performance wise, they would not be worse than Exchange even on the same hardware setup.[/QUOTE]

Ok let me list my requirements:

1.  Easy to setup and install (less than 30min)
2.  Support for massive amounts of mail (100GB+)
3.  Easy and minimal administration and backup (file based, use 3rd party apps to read mail)
4.  some email analysis tools would be nice (find who's sending the most private emails)
5.  must work with Kolab and Horde.
6.  a way to prevent users from deleting mail, unless they are authurised to do so (don't know if that is done on a mail level or at Groupware level).

I am far from a linux Guru, but pretty IT savy. I have been in the IT industry long enough to know you need help from others.

What would you guys suggest for me?

---

### Post by garyng on 2006-05-31
[QUOTE=Sapphiron]Ok let me list my requirements:

1.  Easy to setup and install (less than 30min)
2.  Support for massive amounts of mail (100GB+)
3.  Easy and minimal administration and backup (file based, use 3rd party apps to read mail)
4.  some email analysis tools would be nice (find who's sending the most private emails)
5.  must work with Kolab and Horde.
6.  a way to prevent users from deleting mail, unless they are authurised to do so (don't know if that is done on a mail level or at Groupware level).

I am far from a linux Guru, but pretty IT savy. I have been in the IT industry long enough to know you need help from others.

What would you guys suggest for me?[/QUOTE]

(6) is hard and I think only cyrus would meet that need(other than commercial offering) as it has its own "mail" storage though it is not as lousy as Exchange(still file based). I know nothing about the two mentioned packages(Kolab an Horde)

An alternative way is to archive at the MTA(postfix) level which you keep every copy of mail in and out to a central location(say for legal retain reason).

---

### Post by Divan Santana on 2006-06-15
Hey!

Kolab is awesome! I suggest installing the kolab-admin frontend/GUI package that runs on Linux as well.
It is an additional package someone made recently which lets you admin Kolab better than the frontend/webpage.
It was discussed on planetkde.org recently.

Contact me for more info! :D

---

