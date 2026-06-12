---
title: "Newb: Can you get me past fetchmail error?"
date: 2007-10-10
forum: Server Platforms
---

### Post by Smartin on 2007-10-10
Hi,

I'm trying to get a local IMAP store going using Cyrus, whilst avoiding having an outgoing SMTP server... I'm also wanting to get better spam filtering through spamassassin.

I'm on a Feisty box.

I set up a google email account and subscribed to the ubuntu users mailing list.

I'm using Webmin to control the various servers.

Fetchmail is giving the following error:
Checking for mail on server(s) with command /usr/bin/fetchmail -v -f '/home/smartin/.fetchmailrc' -m '--mda procmail -d smartin' ..

fetchmail: 6.3.6 querying pop.googlemail.com (protocol POP3) at Wed 10 Oct 2007 20:43:58 BST: poll started
Trying to connect to 66.249.93.16/995...connected.
fetchmail: Issuer Organisation: Thawte Consulting cc
fetchmail: Issuer CommonName: Thawte Premium Server CA
fetchmail: Server CommonName: pop.googlemail.com
fetchmail: pop.googlemail.com key fingerprint: D3:B3:42:74:E5:1C:6F:30:6B:06:E4:CE:1C:8F:D6:45
fetchmail: POP3< +OK Gpop ready for requests from 83.67.10.173 s7pf1802194uge
fetchmail: POP3> CAPA
fetchmail: POP3< +OK Capability list follows
fetchmail: POP3< USER
fetchmail: POP3< RESP-CODES
fetchmail: POP3< EXPIRE 0
fetchmail: POP3< LOGIN-DELAY 300
fetchmail: POP3< X-GOOGLE-VERHOEVEN
fetchmail: POP3< UIDL
fetchmail: POP3< .
fetchmail: POP3> USER [email]myemailaddress@googlemail.com[/email]
fetchmail: POP3< +OK send PASS
fetchmail: POP3> PASS *
fetchmail: POP3< +OK Welcome.
fetchmail: POP3> STAT
fetchmail: POP3< +OK 56 263901
fetchmail: POP3> LAST
fetchmail: POP3< -ERR Not supported
fetchmail: Not supported
fetchmail: POP3> UIDL
fetchmail: POP3< +OK
-----------------
Gibberish deleted
-----------------

56 messages for [email]myemailaddress@googlemail.com[/email] at pop.googlemail.com (263901 octets).
fetchmail: POP3> LIST 1
fetchmail: POP3< +OK 1 4833
fetchmail: POP3> RETR 1
fetchmail: POP3< +OK message follows
reading message [email]myemailaddress@googlemail.com@googlemail-pop.l.google.com[/email]:1 of 56 (4833 octets)
#*****************************sh: Illegal option --
fetchmail: MDA returned nonzero status 2
 not flushed
fetchmail: POP3> LIST 2
fetchmail: POP3< +OK 2 5202
fetchmail: POP3> RETR 2
fetchmail: POP3< +OK message follows
reading message [email]myemailaddress@googlemail.com@googlemail-pop.l.google.com[/email]:2 of 56 (5202 octets)
sh: Illegal option --
fetchmail: writing RFC822 msgblk.headers
fetchmail: POP3> QUIT
fetchmail: POP3< Karlo Prstac wrote:
fetchmail: MDA error while fetching from [email]myemailaddress@googlemail.com@pop.googlemail.com[/email]
fetchmail: 6.3.6 querying pop.googlemail.com (protocol POP3) at Wed 10 Oct 2007 20:44:03 BST: poll completed
fetchmail: Query status=6 (IOERR)
fetchmail: normal termination, status 6

.. checking failed!

Fetchmail seems to be connecting to the remote pop server but then things go pearshaped.

Is the command fetchmail is using in the first few lines correct?

I have been told that procmail could pass the mail to spamassassin and then to Cyrus. Is this right? Do I need Postfix after all?

My mail client is connecting to cyrus Ok.

Grateful for any ideas.

Thanks!

Simon

---

