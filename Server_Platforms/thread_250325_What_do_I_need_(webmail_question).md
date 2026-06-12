---
title: "What do I need? (webmail question)"
date: 2006-09-03
forum: Server Platforms
---

### Post by Kurt` on 2006-09-03
Hi,

Basically, I want to setup a mail system where only webmail is available for my users, but they can freely send/receive to/from external sources.

I've seen a multitude of guides for setting up mail servers, but none of them really explain what does what.

I don't quite fully understand how all the parts work together (mailer daemon, courier, IMAP?), so I can't determine exactly what I will need!

Any light-shedding would be much appreciated!

Thanks

---

### Post by Uluen on 2006-09-04
Someone else can probably tell you what you need to do, in the meantime maybe this will help, wikipedia on [SMTP]("http://en.wikipedia.org/wiki/Smtp"), [POP3]("http://en.wikipedia.org/wiki/Pop3"). Basically, SMTP sends mail, POP pick it up.

You users can use squirrelmail and such for reading mail and regular POP clients to send (through your SMTP if needed).

Forgot to add, if you use a service like fetchmail, it can collect your users mail from external servers and put it in local mail for your users.

---

### Post by miahfost on 2006-09-07
The first thing you will need to send and receive mail from your server is a Mail Transfer Agent. Debian includes Exim by default but despite the fact that Ubuntu is a debian-based system, Ubuntu includes Postfix. If you want to use an MTA other than Postfix on your Ubuntu system, you will have to install a new MTA and remove Postfix because you cannot have two mail servers. (You can, but they cannot listen on the same port, and most mail servers listen for and send mail on standard mail port 25.)

There is significant documentation describe MTAs on the internet. Look very closely at the documentation for your particular MTA on how to configure it, I am familiar with Exim but have also used Sendmail and tried Postfix. No matter which MTA you chose, please be very careful, this  is not like setting up a web server. If you make a configuration mistake you can create an Open Relay which will facilitate the sending of spam as well as other materials that you would not like to be associated with. An Open Relay will also quickly get you blacklisted - preventing you, your users, and your domain from sending mail, a major inconvenience and embarassment that costs time and money to fix. 

What the MTA does is listen on port 25 for incoming connections. These connections "speak" the SMTP protocol, or  [Simple Mail Transfer Protocol]("http://en.wikipedia.org/wiki/SMTP"). When they get mail, the MTA server puts the mail in a mail box. That mailbox can then be accessed locally, which is unusual, or via POP short for [Post Office Protocol]("http://en.wikipedia.org/wiki/Post_Office_Protocol"). So, in addition to an MTA you will most certainly need a POP server. I recommend popa3d, but there are others. 

Many sites provide IMAP or the Internet Mail Access Protocol. This allows people to use so-called web mail, or rather to access their mail file via the internet. A popular client for this is Squirellmail - note that this is not an IMAP server, you will need another server for IMAP, although there are servers that do both IMAP and POP.

Again, I stress a lot of reading and careful configuration. Mail is a big hairy beast as they say, which normally takes years to manage well. However, Ubuntu has a plethora of good tools to create a stable, flexible system for handling email.

---

### Post by mentecat on 2006-09-07
Hi,
as miahfost told the MTA receives mail from other smtp servers and put it in you mailboxes. Now the web mail server needs to read your mailboxes. Some reads directly the mailbox file from the local filesystem (e.g. [openwebmail]("http://openwebmail.org/")) others read the mail using the imap protocol (e.g. squirrelmail or horde imp), in this case you must install an imap server (courier, cyrus or uw imapd). If you choose to use a webmail server that uses imap and you want to give your users only the webmail access you must prevent them from using the imap server directly with a firewall or the tcp wrapper.

---

