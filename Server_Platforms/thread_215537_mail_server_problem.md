---
title: "mail server problem"
date: 2006-07-14
forum: Server Platforms
---

### Post by mozyxl on 2006-07-14
**Hello **

I'm trying to install a mailserver on a ubuntu server. I've setup courier and postfix so that they can authenticate via mysql. I can add domains,users,aliases to mysql and smtp and pop3 can sucessfully athenticate me .. no problems. But when I try to fetch the mail via pop or download folder structure via imap I get strange ( at least for me :-)) errors. 

Here's what I get from my tail -f /var/log/mail.log :

[I]Jul 14 12:27:08 mail imaplogin: authdaemon: starting client module
Jul 14 12:27:08 mail imaplogin: authdaemon: ACCEPT, username [email]olle@dummydomain.se[/email]
Jul 14 12:27:08 mail imaplogin: LOCKED, user=olle@dummydomain.se, ip=[::ffff:192.168.0.1][/I]

Here's what I get from mail client:

*Your account is temporarily unavailable (+t bit set on home directory).*

It's the same for pop3 and for ssl connections. 
I've sent a mail to the dummyuser via telnet to create the Mailbox for the user, which workes like a charm. Iv'e alse tried to do "chmod -t" on Maildir but no luck. There seems to be little information when I google on this so I would be extremly glad if I could get som help with this one.

Happy summer hacking // Olle Mårtensson // Sweden // [email]olle@arkiva.se[/email]

---

### Post by mozyxl on 2006-07-14
Problem solved! 

I have my mailboxes in /var/mail/virtual/[Mailboxes] and I only tried to chmod the actually mailboxes before, but when I ran

*chmod -t /var/mail/virtual *

i't worked! Now I have to test the rest of the system so It's only a matter of time before something else turnes up.

// Olle

---

### Post by 3dmonkey3000 on 2006-09-23
i get an error saying the following message, whenever i try to login with Squirrelmail:

ERROR: Connection dropped by IMAP server.
 


Any ideas??

---

