---
title: "postfix/dovecot problems sending/receiving extra-locally"
date: 2008-10-05
forum: Server Platforms
---

### Post by dazmcg on 2008-10-05
I've set up a mail server, seemingly ok apart from I'm having problems receiving/sending emails from/to external recipients.

Ok, installed Postfix/dovecot as per here:
[http://www.mysql-apache-php.com/#mailserver](http://www.mysql-apache-php.com/#mailserver)

note: in trying to get postfix-tls, got this message:
> Package postfix-tls is a virtual package provided by:
  postfix 2.5.1-2ubuntu1.2
You should explicitly select one to install.

So, I have it all set up, I can use mail/alpine locally to send mail LOCALLY (any mail sent to say *@gmail.com doesn't arrive) and I can connect remotely using thunderbird on a different pc/etc to connect to the server and view emails, but NOT to send.

And, from say gmail to dazmcg@MYDOMAIN, I receive no emails (posibbly due to the recentness of my amending the DNS records?)

I have an "MX" record with this entry (added >24h ago):
home.MYDOMAIN.	MX	10 mail.MYDOMAIN.

and I've just added (~couple hours ago) an "A" record:
mail.MYDOMAIN.	A	MY_HOME_PC_IP

MY_HOME_PC_IP is the same as the IP in the A record for MYDOMAIN.

(MYDOMAIN is home0imprison0me0uk - 0=.)

But i don't think this has anything to do with it, at least sending mail outside my network...?

So my postfix config file can be viewed here:
[http://imprison.me.uk/serverconfig/main.cf.txt](http://imprison.me.uk/serverconfig/main.cf.txt)

and dovecot (I dont think this makes a diff, but just in case?) here:
[http://imprison.me.uk/serverconfig/dovecot.conf.txt](http://imprison.me.uk/serverconfig/dovecot.conf.txt)

and an output of my mail.log file here:
[http://imprison.me.uk/serverconfig/tail.mail.log.txt](http://imprison.me.uk/serverconfig/tail.mail.log.txt)

(I dont really know what the www-user stuff is, probably something related to a drupal install i have?...I didn't think it was related to /this/ problem but maybe it is?)

and in my mail.err there's this line repeatedly (diff time stamp, 1 min apart or so):
> Oct  4 16:45:57 server-1 postfix/smtpd[25137]: fatal: bad boolean configuration: smtpd_tls_received_header = yes:

(server-1 is my computers name..)

Any help welcomed!! My setup is ubuntu 8.04.

IP Tables gives this:> 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

and I can telnet to MYDOMAIN on port 25 and port 143 and send mails locally/etc using hte usual commands...

THANKS!

---

### Post by MJN on 2008-10-05
It's not clear what your problem is. Is it that you cannot send to external recipients? If so, post the log covering your attempt to do so.

Mathew

---

### Post by dazmcg on 2008-10-06
> **MJN said:**
> It's not clear what your problem is. Is it that you cannot send to external recipients? If so, post the log covering your attempt to do so.

Mathew

thanks mathew, that AND I cannot receive email from external recipients (I'm guessing it's linked and to do with mail server negotiation or something?)

The logs are all linked above. Here they are again:
> So my postfix config file can be viewed here:
[http://imprison.me.uk/serverconfig/main.cf.txt](http://imprison.me.uk/serverconfig/main.cf.txt)

and dovecot (I dont think this makes a diff, but just in case?) here:
[http://imprison.me.uk/serverconfig/dovecot.conf.txt](http://imprison.me.uk/serverconfig/dovecot.conf.txt)

and an output of my mail.log file here:
[http://imprison.me.uk/serverconfig/tail.mail.log.txt](http://imprison.me.uk/serverconfig/tail.mail.log.txt)


Thanks,

Daz

---

### Post by MJN on 2008-10-06
> **dazmcg said:**
> I cannot receive email from external recipients (I'm guessing it's linked and to do with mail server negotiation or something?)
 
It's your use of a long-since expired RBL:
 
```
< 220 mail.home.imprison.me.uk ESMTP Postfix (Ubuntu)
> HELO edit.dnsvr.com
< 250 mail.home.imprison.me.uk
> MAIL FROM:<usenet@newtonnet.co.uk>
< 250 2.1.0 Ok
> RCPT TO:<postmaster@imprison.me.uk>
< 554 5.7.1 Service unavailable; Client host [64.85.73.124] blocked using relays.ordb.org; ordb.org was shut down on December 18, 2006. Please remove from your mailserver.
```Remove relays.ordb.org from your client restrictions directive.
 
> The logs are all linked above. Here they are again:Again, those logs do not show you attempting to send to an external recipient so it is not really possible to comment on why you are having difficulties with this aspect.
 
Mathew

---

### Post by dazmcg on 2008-10-06
Thanks again, 

> ```
< 220 mail.home.imprison.me.uk ESMTP Postfix (Ubuntu)
> HELO edit.dnsvr.com
< 250 mail.home.imprison.me.uk
> MAIL FROM:<usenet@newtonnet.co.uk>
< 250 2.1.0 Ok
> RCPT TO:<postmaster@imprison.me.uk>
< 554 5.7.1 Service unavailable; Client host [64.85.73.124] blocked using relays.ordb.org; ordb.org was shut down on December 18, 2006. Please remove from your mailserver.
```

My domain (imprison.me.uk) points to somewhere else (64...) which is also the dns server that manages my MX/A records. How come it's sending to postmaster@imprison  not pos..@HOME.imprison... ?

> Remove relays.ordb.org from your client restrictions directive.

I've removed this from my postfix main.conf. That's all?

> Again, those logs do not show you attempting to send to an external recipient so it is not really possible to comment on why you are having difficulties with this aspect. 

here's the log entries from a mail sent after 19:25:00

```
Oct  6 19:25:01 server-1 postfix/pickup[11058]: CB9F334AA1: uid=33 from=<www-data>
Oct  6 19:25:01 server-1 postfix/cleanup[11089]: CB9F334AA1: message-id=<20081006182501.CB9F334AA1@mail.home.imprison.me.uk>
Oct  6 19:25:01 server-1 postfix/qmgr[11059]: CB9F334AA1: from=<www-data@home.imprison.me.uk>, size=863, nrcpt=1 (queue active)
Oct  6 19:25:01 server-1 postfix/local[11090]: CB9F334AA1: to=<www-data@home.imprison.me.uk>, orig_to=<www-data>, relay=local, delay=0.06, delays=0.06/0/0/0, dsn=2.0.0, status=sent (delivered to maildir)
Oct  6 19:25:01 server-1 postfix/qmgr[11059]: CB9F334AA1: removed
Oct  6 19:25:26 server-1 postfix/smtp[11193]: connect to alt2.gmail-smtp-in.l.google.com[64.233.171.27]:25: Connection timed out
Oct  6 19:25:26 server-1 postfix/smtp[11193]: 97D6234A80: to=<dazmcg@gmail.com>, relay=none, delay=1851, delays=1701/0.02/150/0, dsn=4.4.1, status=deferred (connect to alt2.gmail-smtp-in.l.google.com[64.233.171.27]:25: Connection timed out)
Oct  6 19:25:38 server-1 postfix/smtpd[11286]: connect from localhost[127.0.0.1]
Oct  6 19:25:38 server-1 postfix/smtpd[11286]: 2006C34AA2: client=localhost[127.0.0.1]
Oct  6 19:25:38 server-1 postfix/pickup[11058]: 22B9C34AA3: uid=1000 from=<dazmcg@home.imprison.me.uk>
Oct  6 19:25:38 server-1 postfix/cleanup[11089]: 22B9C34AA3: message-id=<alpine.DEB.1.00.0810061925280.11274@server-1>
Oct  6 19:25:38 server-1 postfix/smtpd[11286]: disconnect from localhost[127.0.0.1]
Oct  6 19:25:38 server-1 postfix/qmgr[11059]: 22B9C34AA3: from=<dazmcg@home.imprison.me.uk>, size=649, nrcpt=1 (queue active)
Oct  6 19:26:02 server-1 postfix/pickup[11058]: 60EC434AA4: uid=33 from=<www-data>
Oct  6 19:26:02 server-1 postfix/cleanup[11089]: 60EC434AA4: message-id=<20081006182602.60EC434AA4@mail.home.imprison.me.uk>
Oct  6 19:26:02 server-1 postfix/qmgr[11059]: 60EC434AA4: from=<www-data@home.imprison.me.uk>, size=863, nrcpt=1 (queue active)
Oct  6 19:26:02 server-1 postfix/local[11090]: 60EC434AA4: to=<www-data@home.imprison.me.uk>, orig_to=<www-data>, relay=local, delay=0.04, delays=0.03/0/0/0.01, dsn=2.0.0, status=sent (delivered to maildir)
Oct  6 19:26:02 server-1 postfix/qmgr[11059]: 60EC434AA4: removed
Oct  6 19:26:08 server-1 postfix/smtp[11193]: connect to gmail-smtp-in.l.google.com[64.233.183.27]:25: Connection timed out
```

That was from sending an email via Alpine, from user account dazmcg to [email]dazmcg_@_geemail.com[/email]

Incidentally, I dont know why there's so much stuff from www-data in the log? Doesn't look like it's related to this?

So to sumarise, having problems:
- receiving mail from external servers
- sending mail to external servers
- connecting to my smtp server remotely from a client like thunderbird (can connect via IMAP to view the emails...)

---

### Post by alastair on 2008-10-06
The fact that :

a) You are seeing a mail.err error :

postfix/smtpd[25137]: fatal: bad boolean configuration ...

but the specified parameter (smtpd_tls_received_header) does not exist in the main.cf you link is suspicious. Makes me wonder if you are running the configuration you think.

b) You added a "note" regarding your install of postfix-tls as a "virtual" package requiring an actual choice.

Makes me wonder about the config.

Running "postconf -n" will display NON-default parameters set.

It might be worth :

a) Backing up your config /etc/postfix/main.cf
b) Uninstalling (and purging) all of Postfix
c) Reinstalling Postfix (the basic basic includes TLS I think).

----------------------------------------------------------------------

The www-data mails are from something running in the web server group - I would definitely find out what they are. The mails are being delivered successfully locally - /var/spool/mail/<user> (probably). Read these mails (or view the file) - what's in them?

This assumes your aliases are correct i.e.

/etc/aliases

is set up to push "root" mail (and postmaster etc.) to a real user i.e. <user> above. And run "newaliases" after.

--------------------------------------

The mails to Google are just timing out.

You could test this your self by just doing a telnet from this system i.e.

telnet gmail-smtp-in.l.google.com 25

and do the "HELO", "MAIL FROM" and "RCPT TO" lines as above - to your Google address.

Alastair

---

### Post by dazmcg on 2008-10-06
> **alastair said:**
> The fact that :

a) You are seeing a mail.err error :

postfix/smtpd[25137]: fatal: bad boolean configuration ...

but the specified parameter (smtpd_tls_received_header) does not exist in the main.cf you link is suspicious. Makes me wonder if you are running the configuration you think.

Could I try adding this line in? Maybe the error is from it /not/ being there?


> Running "postconf -n" will display NON-default parameters set.

Here's the output:

```
root@server-1:/var/www/Maildir/new# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
mailbox_command =
mailbox_size_limit = 0
mydestination = home.imprison.me.uk, mail.home.imprsion.me.uk, localhost.localdomain, localhost
myhostname = mail.home.imprison.me.uk
mynetworks = host 127.0.0.0/8
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_restrictions = permit_mynetworks, permit_sas1_authenticated,reject_unauth_destination
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```


> It might be worth :

a) Backing up your config /etc/postfix/main.cf
b) Uninstalling (and purging) all of Postfix
c) Reinstalling Postfix (the basic basic includes TLS I think).

I'll try this if I dont get a response within a few hours about the bit above....


> The mails to Google are just timing out.

You could test this your self by just doing a telnet from this system i.e.

telnet gmail-smtp-in.l.google.com 25

and do the "HELO", "MAIL FROM" and "RCPT TO" lines as above - to your Google address.


doing the telnet line, it just sits there, doesn't connect...I don't understand hwo that's an issue on my side though?

Thanks for the help!

---

### Post by MJN on 2008-10-06
> **dazmcg said:**
> My domain (imprison.me.uk) points to somewhere else (64...) which is also the dns server that manages my MX/A records. How come it's sending to postmaster@imprison  not pos..@HOME.imprison... ?That was my fault. However it matters little as the end effect is the same - the ORDB RBL was blocking all incoming mail regardless who it was sent to.> I've removed this from my postfix main.conf. That's all?Yes (aside from any other issues discussed above).> doing the telnet line, it just sits there, doesn't connect...I don't understand hwo that's an issue on my side though?It looks like your ISP is blocking outbound port 25. Your best solution is likely to be to relay all outgoing mail via their SMTP server (using the relayhost directive).

Mathew

---

### Post by alastair on 2008-10-06
The "postconf -n" doesn't show much of interest - and not the "error" line complained about in one of your logs - I assume you still see that. A "tail -f /var/log/mail.log" while you restart Postfix (/etc/init.d/postfix restart) would show the error if it still exists. A Postfix reinstall (backup, purge, install) is quick and easy.

---

### Post by dazmcg on 2008-10-06
> It looks like your ISP is blocking outbound port 25. Your best solution is likely to be to relay all outgoing mail via their SMTP server (using the relayhost directive).

ok, my ISP turns out to be blocking port 25, (I can, and have, request for it to be opened on my IP), but I don't see how this has any bearing on incoming, emails sent from external places, which are still not arriving locally? :(

Thanks again.

---

### Post by MJN on 2008-10-06
Check your logs for the following connection (made at 23:16 BST) and following a Postfix restart as Alastair mentioned.

```
$ telnet 87.194.87.156 25
Trying 87.194.87.156...
Connected to 87.194.87.156.
Escape character is '^]'.
220 mail.home.imprison.me.uk ESMTP Postfix (Ubuntu)
ehlo mail.newtonnet.co.uk
250-mail.home.imprison.me.uk
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: usenet@newtonnet.co.uk
250 2.1.0 Ok
rcpt to: postmaster@home.imprison.me.uk
451 4.3.5 Server configuration error
quit
221 2.0.0 Bye
Connection closed by foreign host.
```Mathew

---

### Post by dazmcg on 2008-10-06
> **alastair said:**
> The "postconf -n" doesn't show much of interest - and not the "error" line complained about in one of your logs - I assume you still see that. A "tail -f /var/log/mail.log" while you restart Postfix (/etc/init.d/postfix restart) would show the error if it still exists. A Postfix reinstall (backup, purge, install) is quick and easy.

Yeah I installed it again, and copied the backed up config back.

There seems to be no new entries in mail.err, so that's good I guess? 

When I send email from an external email address (not gmail) I get this on my mail.log:

```
Oct  6 23:24:21 server-1 postfix/smtpd[18908]: connect from simba.gold.ac.uk[158.223.1.28]
Oct  6 23:24:21 server-1 postfix/smtpd[18908]: warning: unknown smtpd restriction: "permit_sas1_authenticated"
Oct  6 23:24:21 server-1 postfix/smtpd[18908]: NOQUEUE: reject: RCPT from simba.gold.ac.uk[158.223.1.28]: 451 4.3.5 Server configuration error; from=<***@gold.ac.uk> to=<dazmcg@MYDOMAIN> proto=ESMTP helo=<simba.gold.ac.uk>
Oct  6 23:24:21 server-1 postfix/cleanup[18794]: ED0E833EE1: message-id=<20081006222421.ED0E833EE1@mail.MYDOMAIN>
Oct  6 23:24:21 server-1 postfix/qmgr[18767]: ED0E833EE1: from=<double-bounce@mail.MYDOMAIN>, size=1241, nrcpt=1 (queue active)
Oct  6 23:24:21 server-1 postfix/local[18796]: warning: required alias not found: postmaster
Oct  6 23:24:21 server-1 postfix/local[18796]: ED0E833EE1: to=<postmaster@home.MYDOMAIN>, orig_to=<postmaster>, relay=local, delay=0.01, delays=0.01/0/0/0, dsn=2.0.0, status=sent (discarded)
Oct  6 23:24:21 server-1 postfix/qmgr[18767]: ED0E833EE1: removed
Oct  6 23:24:21 server-1 postfix/smtpd[18908]: disconnect from simba.gold.ac.uk[158.223.1.28]

```
(swapped MYDOMAIN in...)

does this explain anything? Why do I not get the same effect when I attempt to send mails from gmail to my server?

---

### Post by dazmcg on 2008-10-06
Hi Mathew
> **MJN said:**
> Check your logs for the following connection

```
Oct  6 23:20:21 server-1 postfix/smtpd[18604]: warning: unknown smtpd restriction: "permit_sas1_authenticated"
Oct  6 23:20:21 server-1 postfix/smtpd[18604]: NOQUEUE: reject: RCPT from 77-103-161-36.cable.ubr05.chap.blueyonder.co.uk[77.103.161.36]: 451 4.3.5 Server configuration error; from=<usenet@newtonnet.co.uk> to=<postmaster@home.imprison.me.uk> proto=ESMTP helo=<mail.newtonnet.co.uk>
Oct  6 23:20:24 server-1 postfix/master[17827]: reload configuration /etc/postfix
Oct  6 23:20:24 server-1 postfix/anvil[18607]: statistics: max connection rate 1/60s for (smtp:77.103.161.36) at Oct  6 23:19:50
Oct  6 23:20:24 server-1 postfix/anvil[18607]: statistics: max connection count 1 for (smtp:77.103.161.36) at Oct  6 23:19:50
Oct  6 23:20:24 server-1 postfix/anvil[18607]: statistics: max cache size 1 at Oct  6 23:19:50
Oct  6 23:20:25 server-1 postfix/qmgr[18662]: DFECA33D6A: from=<dazmcg@home.imprison.me.uk>, size=644, nrcpt=1 (queue active)
Oct  6 23:20:28 server-1 postfix/cleanup[18669]: 6E8C733EB2: message-id=<20081006222028.6E8C733EB2@mail.home.imprison.me.uk>
Oct  6 23:20:28 server-1 postfix/qmgr[18662]: 6E8C733EB2: from=<double-bounce@mail.home.imprison.me.uk>, size=955, nrcpt=1 (queue active)
Oct  6 23:20:28 server-1 postfix/smtpd[18604]: disconnect from 77-103-161-36.cable.ubr05.chap.blueyonder.co.uk[77.103.161.36]
Oct  6 23:20:28 server-1 postfix/local[18670]: warning: required alias not found: postmaster
Oct  6 23:20:28 server-1 postfix/local[18670]: 6E8C733EB2: to=<postmaster@home.imprison.me.uk>, orig_to=<postmaster>, relay=local, delay=0.03, delays=0.02/0.01/0/0, dsn=2.0.0, status=sent (discarded)
Oct  6 23:20:28 server-1 postfix/qmgr[18662]: 6E8C733EB2: removed
Oct  6 23:20:28 server-1 postfix/master[17827]: terminating on signal 15
Oct  6 23:20:29 server-1 postfix/master[18762]: daemon started -- version 2.5.1, configuration /etc/postfix
Oct  6 23:20:29 server-1 postfix/qmgr[18767]: DFECA33D6A: from=<dazmcg@home.imprison.me.uk>, size=644, nrcpt=1 (queue active)

```

That's you I assume. My clock is out of synch I guess :)

daz

---

### Post by MJN on 2008-10-06
Well I'd start by taking heed of the warning:

```
warning: unknown smtpd restriction: "permit_sas1_authenticated"
```(You've used a number '1' instead of the letter 'L')

Mathew

---

### Post by dazmcg on 2008-10-06
> **MJN said:**
> Well I'd start by taking head of the warning:

```
warning: unknown smtpd restriction: "permit_sas1_authenticated"
```

(You've used a number '1' instead of the letter 'L')

Mathew

HAH. brilliant. that would explain why some lines were being syntax highlighted in vim, others weren't (ones with 1 instead of L) :)

WELL SPOTTED. THANKS!!! it works now. I receive emails....You've ended about 12+h cumulative time spent on this! all because of some stupid misreading / lack of rigorousness.

Now to chase down the www-data thing :)

Thanks again for your patience alastair and MJN!!!! :guitar:

---

### Post by rovae on 2008-10-06
The wig&#8217;s cap is made entirely of French stock [full lace wig](http://www.royalmewigs.com/) or Swiss lace (custom [lace front wig](http://www.royalmewigs.com/lace_front_wigs.html) may be ordered in French or Swiss [front lace wigs](http://www.royalmewigs.com/lace_front_wigs.html)). Strands are hand-tied to the lace. Knots are blended so they are not seen. The knotting technique allows natural hair flow for multi-directional hairstyling. The process of creating a [Lace Wig](http://www.royalmewigs.com/) takes approximately 30 to 45 days to complete.

---

