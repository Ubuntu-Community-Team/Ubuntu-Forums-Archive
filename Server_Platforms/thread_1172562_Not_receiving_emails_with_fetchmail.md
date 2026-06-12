---
title: "Not receiving emails with fetchmail"
date: 2009-05-28
forum: Server Platforms
---

### Post by victorbrca on 2009-05-28
I'm trying to get my yahoo mail delivered to my server so I can implement an IMAP connection in the future (but I really suck at this).

I was able to get postfix to deliver local email and fetchmail to connect to my inbox, however no mail are shown when I do "mail".

Any help is welcome!! :)

```
$ cat .fetchmailrc
#set syslog;
#set daemon 90;
#set postmaster "me@yahoo.ca";

poll "pop.mail.yahoo.ca" port 995 with protocol POP3 user "me@yahoo.ca" password "######" keep ssl
smtphost "enterprise.localhost" smtpname "me@localhost"

```


```
$ fetchmail -v
fetchmail: 6.3.8 querying pop.mail.yahoo.ca (protocol POP3) at Thu 28 May 2009 04:02:27 PM EDT: poll started
Trying to connect to 209.191.69.2/995...connected.
fetchmail: Issuer Organization: Equifax
fetchmail: Unknown Issuer CommonName
fetchmail: Server CommonName: pop.mail.yahoo.ca
fetchmail: pop.mail.yahoo.ca key fingerprint: ################
fetchmail: POP3< +OK hello from popgate 2.43 on pop106.plus.mail.mud.yahoo.com
fetchmail: POP3> CAPA
fetchmail: POP3< +OK CAPA list follows
fetchmail: POP3< EXPIRE NEVER
fetchmail: POP3< IMPLEMENTATION popgate 2.43
fetchmail: POP3< PIPELINING
fetchmail: POP3< RESP-CODES
fetchmail: POP3< TOP
fetchmail: POP3< UIDL
fetchmail: POP3< USER
fetchmail: POP3< .
fetchmail: POP3> USER me@yahoo.ca
fetchmail: POP3< +OK password required.
fetchmail: POP3> PASS *
fetchmail: POP3< +OK maildrop ready, 132 messages (26061761 octets) (517707418)
fetchmail: POP3> STAT
fetchmail: POP3< +OK 132 26061761
fetchmail: POP3> LAST
fetchmail: POP3< +OK 132
132 messages (132 seen) for me@yahoo.ca at pop.mail.yahoo.ca (26061761 octets).
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:1 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:2 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:3 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:4 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:5 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:6 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:7 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:8 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:9 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:10 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:11 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:12 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:13 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:14 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:15 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:16 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:17 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:18 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:19 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:20 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:21 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:22 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:23 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:24 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:25 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:26 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:27 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:28 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:29 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:30 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:31 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:32 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:33 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:34 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:35 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:36 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:37 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:38 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:39 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:40 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:41 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:42 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:43 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:44 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:45 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:46 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:47 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:48 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:49 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:50 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:51 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:52 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:53 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:54 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:55 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:56 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:57 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:58 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:59 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:60 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:61 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:62 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:63 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:64 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:65 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:66 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:67 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:68 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:69 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:70 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:71 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:72 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:73 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:74 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:75 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:76 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:77 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:78 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:79 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:80 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:81 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:82 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:83 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:84 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:85 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:86 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:87 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:88 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:89 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:90 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:91 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:92 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:93 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:94 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:95 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:96 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:97 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:98 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:99 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:100 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:101 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:102 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:103 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:104 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:105 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:106 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:107 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:108 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:109 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:110 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:111 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:112 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:113 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:114 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:115 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:116 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:117 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:118 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:119 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:120 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:121 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:122 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:123 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:124 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:125 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:126 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:127 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:128 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:129 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:130 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:131 not flushed
skipping message me@yahoo.ca@pop-ca.mail.vip.mud.yahoo.com:132 not flushed
fetchmail: POP3> QUIT
fetchmail: POP3< +OK server signing off.
fetchmail: 6.3.8 querying pop.mail.yahoo.ca (protocol POP3) at Thu 28 May 2009 04:02:28 PM EDT: poll completed
fetchmail: normal termination, status 1

```

```
$ mail
No mail for me

```

I guess it's probably something small.

Vic.

---

### Post by victorbrca on 2009-05-28
Got it working with this:

```
$ cat .fetchmailrc
#set syslog;
#set daemon 90;
#set postmaster "me@yahoo.ca";

poll "pop.mail.yahoo.ca" port 995 with protocol POP3 user "me@yahoo.ca" password "######" **_is "me" here_** keep ssl
smtphost **_"localhost"_** smtpname "me@localhost"
```

---

