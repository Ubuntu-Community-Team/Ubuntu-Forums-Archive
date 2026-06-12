---
title: "Mail server question"
date: 2006-09-29
forum: Server Platforms
---

### Post by murraymints on 2006-09-29
Hi,

I'm trying to set up a mail server which allows users to move from all sharing a single email address to each having their own address. (e.g. instead of just [email]generic@example.com[/email] allowing [email]bob@example.com[/email], etc  as well). I would like to implement this by retrieving mail from the same pop mail server if this is possible.

So far I have follwed the various postfix and courier how-to's and have reached a state where all users have a maildir and can send mail to each other through the server and can also sent emails through the ISP's SMTP server with the correct from addresses e.g. [email]bob@example.com[/email] appearing on the emails but I a bit confused as to how to retrieve any replies to these emails.

As I understand the how-to's they all seem to descibe the server being set up as the first destination for any incoming email. I am unfamiliar with this kind of set-up but if it is relativley easy to implement then I would like more information on how to do it.

I am more familiar with email servers that are set up to retrive email from an ISP server first and then distribute the email to users. Any information on how to do this with postfix and also any info on how the different email names (bob@exmaple.com instead of [email]generic@example.com[/email]) might affect this would be greatly appreciated.

---

### Post by jimm on 2006-09-29
Hi,

I think what you want is fetchmail: [http://fetchmail.berlios.de/]("http://fetchmail.berlios.de/")

It will go grab mail from an ISP or other POP server and poke it into your local users mailboxes.

Check it out and see if it works for you!

Thanks,
James

---

### Post by murraymints on 2006-10-01
Hi,

I've been trying to use fetchmail to retrieve emails from my pop server but they're not ending up in the correct user mailboxes.

I have postfix installed and it does deliver mail to the correct users if I send the mail by telneting the server.

I've including the output from fetchmail below, could someone please tell me where I'm going wrong.

Thanks,

Murray


```

murray@server:~/Maildir/new$ fetchmail -v
fetchmail: 6.3.2 querying www.mydomain.com (protocol POP3) at Sun 01 Oct 2006 01:58:53 PM NPT: poll started
fetchmail: POP3< +OK POP3 [xxx.xxx.xxx.xxx] v2000.70 server ready
fetchmail: POP3> CAPA
fetchmail: POP3< +OK Capability list follows:
fetchmail: POP3< TOP
fetchmail: POP3< LOGIN-DELAY 180
fetchmail: POP3< UIDL
fetchmail: POP3< USER
fetchmail: POP3< SASL LOGIN
fetchmail: POP3< .
fetchmail: POP3> USER murray
fetchmail: POP3< +OK User name accepted, password please
fetchmail: POP3> PASS *
fetchmail: POP3< +OK Mailbox open, 0 messages
fetchmail: POP3> STAT
fetchmail: POP3< +OK 0 0
fetchmail: No mail for murray at www.mydomain.com
fetchmail: POP3> QUIT
fetchmail: POP3< +OK Sayonara
fetchmail: 6.3.2 querying www.mydomain.com (protocol POP3) at Sun 01 Oct 2006 01:58:58 PM NPT: poll completed
fetchmail: 6.3.2 querying www.mydomain.com (protocol POP3) at Sun 01 Oct 2006 01:58:58 PM NPT: poll started
fetchmail: POP3< +OK POP3 [xxx.xxx.xxx.xxx] v2000.70 server ready
fetchmail: POP3> CAPA
fetchmail: POP3< +OK Capability list follows:
fetchmail: POP3< TOP
fetchmail: POP3< LOGIN-DELAY 180
fetchmail: POP3< UIDL
fetchmail: POP3< USER
fetchmail: POP3< SASL LOGIN
fetchmail: POP3< .
fetchmail: POP3> USER dummy
fetchmail: POP3< +OK User name accepted, password please
fetchmail: POP3> PASS *
fetchmail: POP3< +OK Mailbox open, 1 messages
fetchmail: POP3> STAT
fetchmail: POP3< +OK 1 4721
fetchmail: POP3> LAST
fetchmail: POP3< +OK 0
1 message for dummy at www.mydomain.com (4721 octets).
fetchmail: POP3> LIST 1
fetchmail: POP3< +OK 1 4721
fetchmail: POP3> TOP 1 99999999
fetchmail: POP3< +OK Top of message follows
reading message dummy@www.mydomain.com:1 of 1 (4721 octets)
fetchmail: SMTP< 220 server1.example.com ESMTP Postfix (Ubuntu)
fetchmail: SMTP> EHLO server.example.com
fetchmail: SMTP< 250-server1.example.com
fetchmail: SMTP< 250-PIPELINING
fetchmail: SMTP< 250-SIZE 10240000
fetchmail: SMTP< 250-VRFY
fetchmail: SMTP< 250-ETRN
fetchmail: SMTP< 250-STARTTLS
fetchmail: SMTP< 250-AUTH LOGIN PLAIN
fetchmail: SMTP< 250-AUTH=LOGIN PLAIN
fetchmail: SMTP< 250 8BITMIME
fetchmail: SMTP> MAIL FROM:<murray@mydomain.com> SIZE=4721
fetchmail: SMTP< 250 Ok
fetchmail: SMTP> RCPT TO:<murray@localhost>
fetchmail: SMTP< 250 Ok
fetchmail: SMTP> DATA
fetchmail: SMTP< 354 End data with <CR><LF>.<CR><LF>
#**************************.**************.*********************fetchmail: SMTP>. (EOM)
fetchmail: SMTP< 250 Ok: queued as B975A57D198
 flushed
fetchmail: POP3> DELE 1
fetchmail: POP3< +OK Message deleted
fetchmail: POP3> QUIT
fetchmail: POP3< +OK Sayonara
fetchmail: SMTP> QUIT
fetchmail: SMTP< 221 Bye
fetchmail: 6.3.2 querying www.mydomain.com (protocol POP3) at Sun 01 Oct 2006 01:59:07 PM NPT: poll completed
fetchmail: normal termination, status 0
murray@server:~/Maildir/new$

```

---

### Post by raphha on 2006-10-01
As far as I understand you, _all_ mail is received by your smarthost first.

If so, check out ETRN or ODMR (see man fetchmail or wikipedia). Another solution could be to create a filter based on the original to: and cc: field, but this might be difficult..
raph

---

### Post by murraymints on 2006-10-01
I'm not sure what you mean by smarthost but all the mail is recieved by an ISP server first, then I download it using fetch mail and then postfix delivers it to the correct maildir in the users folder (or at least thats the plan).


I think this should be do-able without using ETRN or ODMR or filters (postfix seems to work so if I can just get fetmail to pass it the mail without altering it).

Edit: I'm changing my plan so that each users email client just fetches their own mail from the ISP's server. I have set up a system before on win2000 where you could send [email]anything@thedomain.com[/email] and the mail pop connector would retrieve with it witha only one login and send it to user mail boxes. Maybe the server I was connecting to had different features or something else was different, if anyone has anymore tips I would appreciate them.

Thanks,

Murray

---

### Post by raphha on 2006-10-01
Hi,
the smarthost ist the ISP server.

If all users can log into the ISP server with their own names and pw and retreive only their mail like that (i.e., there's not only one single mailbox on the ISP server for *@yourdomain.com), than you can tell fetchmail to get mail for user x with your ISP and deliver it to user y locally. x and y can be the same, but don't have to.

If you add one line for every local user to your fetchmailrc, then you'll get what you want, I think. (plus, you have a centralized configuration file and don't need to setup up every email client on every machine differently, except for the local users name of course).
raph

---

### Post by murraymints on 2006-10-01
Thanks, for the help raphha, I have a setup similar to what you just descibed now (I was missing the "is 'sombody' here" part on each of my user lines in the .fetchmailrc file before).

I think this is the most managable setup possible with this ISP (shame they don't seem to support a global inbox or I would have a completely centralised setup instead of definining a box for each of the users at the ISP).

Thanks again for all the help

---

### Post by raphha on 2006-10-01
Hi, having one inbox is not always the most simple way, except for if you can use ETRN or ODMR, which many ISPs don't offer.
Because, if you just use fetchmails multidrop things can go wrong (see the warnings in the man-page).

So, if you have not too many local users, the setup you have is maybe even the best and easiest way to handle things...

one more point I just saw: do you use a .fetchmail file? Do you know there is a systemwide /etc/fetchmailrc file? just a thought.

have a nice day,
raph

---

