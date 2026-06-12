---
title: "Zimbra 8.0.4 FOSS - All Outgoing Mail Goes To Deferred Queue, But Sends When Requeued"
date: 2013-09-07
forum: Server Platforms
---

### Post by Kirk Schnable on 2013-09-07
I recently installed a new Zimbra email server on a Ubuntu server hosted at OVH.  I am no stranger to Zimbra, and I have had Zimbra running on my old server for over a year.

This time around, I freshly installed 8.0.4 and migrated all of my accounts over with imapsync.  Everything was going smoothly, until I realized my emails were not being sent.  They were all going into the deferred queue.  

I've done some digging in my logs, and some independent Googling, and some people online are saying the issue might be IPv6 related.  This new server does have IPv6, and the old one never had that set up.

Here's what's going on in the Zimbra logs.  I have redacted some information, like the email addresses, server hostname, and server IP involved. 

This is what happens when I try to email someone.

```
Sep  7 15:12:53 hostname postfix/smtpd[18100]: connect from hostname.mydomain.com[my.svr.ip.addr]
Sep  7 15:12:53 hostname postfix/smtpd[18100]: NOQUEUE: filter: RCPT from hostname.mydomain.com[my.svr.ip.addr]: <sender@mydomain.com>: Sender address triggers FILTER smtp-amavis:[::1]:10026; from=<sender@mydomain.com> to=<receipient@otherdomain.com> proto=ESMTP helo=<hostname.mydomain.com>
Sep  7 15:12:53 hostname postfix/smtpd[18100]: 14BA03C35EC: client=hostname.mydomain.com[my.svr.ip.addr]
Sep  7 15:12:53 hostname postfix/cleanup[18103]: 14BA03C35EC: message-id=<147085282.660.1378584773012.JavaMail.zimbra@mydomain.com>
Sep  7 15:12:53 hostname postfix/qmgr[3475]: 14BA03C35EC: from=<sender@mydomain.com>, size=1025, nrcpt=1 (queue active)
Sep  7 15:12:53 hostname postfix/smtpd[18100]: disconnect from hostname.mydomain.com[my.svr.ip.addr]
Sep  7 15:12:53 hostname amavis[423]: (00423-03) ESMTP:[::1]:10026 /opt/zimbra/data/amavisd/tmp/amavis-20130907T133123-00423-14Ue6qpr: <sender@mydomain.com> -> <receipient@otherdomain.com> Received: from hostname.mydomain.com ([IPv6:::1]) by localhost (hostname.mydomain.com [IPv6:::1]) (amavisd-new, port 10026) with ESMTP for <receipient@otherdomain.com>; Sat,  7 Sep 2013 15:12:53 -0500 (CDT)
Sep  7 15:12:53 hostname amavis[423]: (00423-03) Checking: QjJwprJj7WfE ORIGINATING/MYNETS [my.svr.ip.addr] <sender@mydomain.com> -> <receipient@otherdomain.com>
Sep  7 15:12:53 hostname postfix/dkimmilter/smtpd[18107]: connect from ip6-localhost[::1]
Sep  7 15:12:53 hostname postfix/dkimmilter/smtpd[18107]: warning: connect to Milter service inet:localhost:8465: Connection refused
Sep  7 15:12:53 hostname postfix/dkimmilter/smtpd[18107]: NOQUEUE: milter-reject: CONNECT from ip6-localhost[::1]: 451 4.7.1 Service unavailable - try again later; proto=SMTP
Sep  7 15:12:53 hostname postfix/dkimmilter/smtpd[18107]: NOQUEUE: milter-reject: EHLO from ip6-localhost[::1]: 451 4.7.1 Service unavailable - try again later; proto=SMTP helo=<localhost>
Sep  7 15:12:53 hostname postfix/dkimmilter/smtpd[18107]: NOQUEUE: milter-reject: MAIL from ip6-localhost[::1]: 451 4.7.1 Service unavailable - try again later; from=<sender@mydomain.com> proto=ESMTP helo=<localhost>
Sep  7 15:12:53 hostname amavis[423]: (00423-03) smtp resp to MAIL (pip): 451 4.7.1 Service unavailable - try again later
Sep  7 15:12:53 hostname amavis[423]: (00423-03) Negative SMTP resp. to DATA: 503 5.5.1 Error: need RCPT command
Sep  7 15:12:53 hostname postfix/dkimmilter/smtpd[18107]: disconnect from ip6-localhost[::1]
Sep  7 15:12:53 hostname amavis[423]: (00423-03) (!)FWD from <sender@mydomain.com> -> <receipient@otherdomain.com>,BODY=7BIT 451 4.7.1 from MTA(smtp:[::1]:10030): 451 4.7.1 Service unavailable - try again later
Sep  7 15:12:53 hostname amavis[423]: (00423-03) Blocked MTA-BLOCKED {TempFailedOutbound}, ORIGINATING/MYNETS LOCAL [my.svr.ip.addr]:33121 [my.svr.ip.addr] <sender@mydomain.com> -> <receipient@otherdomain.com>, Queue-ID: 14BA03C35EC, Message-ID: <147085282.660.1378584773012.JavaMail.zimbra@mydomain.com>, mail_id: QjJwprJj7WfE, Hits: -, size: 1023, 88 ms
Sep  7 15:12:53 hostname postfix/smtp[18104]: 14BA03C35EC: to=<receipient@otherdomain.com>, relay=::1[::1]:10026, delay=0.1, delays=0.01/0/0/0.09, dsn=4.7.1, status=deferred (host ::1[::1] said: 451 4.7.1 id=00423-03 - Temporary MTA failure on relaying, from MTA(smtp:[::1]:10030): 451 4.7.1 Service unavailable - try again later (in reply to end of DATA command))
```

Then, the email falls into the deferred queue.  If I go to the Zimbra Admin Panel and I tell it to requeue the message, this happens... **(the message DOES send, after it's requeued)**

```
Sep  7 15:15:24 hostname postfix/postsuper[21793]: 14BA03C35EC: requeued
Sep  7 15:15:24 hostname postfix/postsuper[21793]: Requeued: 1 message
Sep  7 15:15:24 hostname sshd[21699]: Received disconnect from my.svr.ip.addr: 11: Closed due to user request.
Sep  7 15:15:49 hostname postfix/pickup[12628]: D9F4D3C35EF: uid=998 from=<sender@mydomain.com> orig_id=14BA03C35EC
Sep  7 15:15:49 hostname postfix/cleanup[21802]: D9F4D3C35EF: message-id=<147085282.660.1378584773012.JavaMail.zimbra@mydomain.com>
Sep  7 15:15:49 hostname postfix/qmgr[3475]: D9F4D3C35EF: from=<sender@mydomain.com>, size=1142, nrcpt=1 (queue active)
Sep  7 15:15:49 hostname amavis[2706]: (02706-17) ESMTP:[::1]:10024 /opt/zimbra/data/amavisd/tmp/amavis-20130905T103922-02706-weNUkqe8: <sender@mydomain.com> -> <receipient@otherdomain.com> SIZE=1142 Received: from hostname.mydomain.com ([IPv6:::1]) by localhost (hostname.mydomain.com [IPv6:::1]) (amavisd-new, port 10024) with ESMTP for <receipient@otherdomain.com>; Sat,  7 Sep 2013 15:15:49 -0500 (CDT)
Sep  7 15:15:49 hostname amavis[2706]: (02706-17) Checking: Dly56icKMJQp MYNETS [my.svr.ip.addr] <sender@mydomain.com> -> <receipient@otherdomain.com>
Sep  7 15:15:49 hostname clamd[2789]: SelfCheck: Database status OK.
Sep  7 15:15:50 hostname postfix/amavisd/smtpd[21808]: connect from ip6-localhost[::1]
Sep  7 15:15:50 hostname postfix/amavisd/smtpd[21808]: 7862B3C35EC: client=ip6-localhost[::1]
Sep  7 15:15:50 hostname postfix/cleanup[21802]: 7862B3C35EC: message-id=<147085282.660.1378584773012.JavaMail.zimbra@mydomain.com>
Sep  7 15:15:50 hostname postfix/qmgr[3475]: 7862B3C35EC: from=<sender@mydomain.com>, size=1595, nrcpt=1 (queue active)
Sep  7 15:15:50 hostname amavis[2706]: (02706-17) FWD from <sender@mydomain.com> -> <receipient@otherdomain.com>,BODY=7BIT 250 2.0.0 from MTA(smtp:[::1]:10025): 250 2.0.0 Ok: queued as 7862B3C35EC
Sep  7 15:15:50 hostname postfix/amavisd/smtpd[21808]: disconnect from ip6-localhost[::1]
Sep  7 15:15:50 hostname amavis[2706]: (02706-17) Passed CLEAN {RelayedOutbound}, MYNETS LOCAL [my.svr.ip.addr]:33121 [my.svr.ip.addr] <sender@mydomain.com> -> <receipient@otherdomain.com>, Queue-ID: 14BA03C35EC, Message-ID: <147085282.660.1378584773012.JavaMail.zimbra@mydomain.com>, mail_id: Dly56icKMJQp, Hits: -2.107, size: 1140, queued_as: 7862B3C35EC, 590 ms
Sep  7 15:15:50 hostname postfix/smtp[21805]: D9F4D3C35EF: to=<receipient@otherdomain.com>, relay=::1[::1]:10024, delay=177, delays=177/0/0/0.59, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[::1]:10025): 250 2.0.0 Ok: queued as 7862B3C35EC)
Sep  7 15:15:50 hostname postfix/qmgr[3475]: D9F4D3C35EF: removed
Sep  7 15:15:52 hostname postfix/smtp[21809]: 7862B3C35EC: to=<receipient@otherdomain.com>, relay=mta5.am0.yahoodns.net[66.196.118.35]:25, delay=2.4, delays=0.01/0.01/0.46/1.9, dsn=2.0.0, status=sent (250 ok dirdel)
Sep  7 15:15:52 hostname postfix/qmgr[3475]: 7862B3C35EC: removed
```

My IPv6 is set up and is working properly as far as I can tell.

```
root@hostname:~# ping6 google.com -c 4
PING google.com(fa-in-x64.1e100.net) 56 data bytes
64 bytes from fa-in-x64.1e100.net: icmp_seq=1 ttl=56 time=27.8 ms
64 bytes from fa-in-x64.1e100.net: icmp_seq=2 ttl=56 time=19.6 ms
64 bytes from fa-in-x64.1e100.net: icmp_seq=3 ttl=56 time=19.6 ms
64 bytes from fa-in-x64.1e100.net: icmp_seq=4 ttl=56 time=19.7 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 19.604/21.712/27.855/3.548 ms
root@hostname:~# 
```

Has anybody ever encountered this problem, or might have some suggestions on how I should proceed?

Thanks,
Kirk

---

### Post by TheFu on 2013-09-07
The problem seems to be here:
```
warning: connect to Milter service inet:localhost:8465: Connection refused

```

Are all the services running?
```
/opt/zimbra/bin/zmcontrol status
```

---

### Post by Kirk Schnable on 2013-09-08
I can confirm that all of the services appear to be running...

```
$ /opt/zimbra/bin/zmcontrol status
Host hostname.mydomain.com
    antispam                Running
    antivirus               Running
    ldap                    Running
    logger                  Running
    mailbox                 Running
    mta                     Running
    opendkim                Running
    spell                   Running
    stats                   Running
    zmconfigd               Running
$ 
```

---

### Post by Kirk Schnable on 2013-09-08
[SIZE=3]**This thread is now solved.**[/SIZE]

I got on IRC tonight, and passed this thread link around the #zimbra channel on Freenode.  JoBbZ had some advice.

Per his suggestion, I modified my /etc/hosts file.  I changed:
```
::1     ip6-localhost ip6-loopback
```
to: 
```
::1     localhost ip6-localhost ip6-loopback
```

The issue was because when the Zimbra software tried to resolve the IPv6 address for localhost, the DNS didn't resolve because it was not in /etc/hosts.

[quote="#zimbra on Freenode IRC"]<JoBbZ> I have a bug to fix that for 8.0.6
<JoBbZ> really fricking annoying
<JoBbZ> i..e, we'll fix /etc/hosts for you
<JoBbZ> but this is one of those nice cases where the ubuntu folks tried to be "helpful" and just made things broken[/quote]

Thanks JoBbZ, and I hope this helps someone else out!

Kirk

---

### Post by TheFu on 2013-09-09
Zimbra has always been extremely picky about that damn hosts file.  Too picky.  During installs, I always have to swap out the normal hosts file for a 3 liner .... completely stupid, IMHO.

The MX record demand for Zimbra to install is another pet peeve

Still, Zimbra is a great MS-Exchange replacement even with the overly picky installer.

---

### Post by Kirk Schnable on 2013-09-09
> **TheFu said:**
> Zimbra has always been extremely picky about that damn hosts file.  Too picky.  During installs, I always have to swap out the normal hosts file for a 3 liner .... completely stupid, IMHO.
I agree for the most part... but in this case, I believe it's not Zimbra's fault.  "localhost" is not a truly dual stack host out of the box the way the default hosts file is set up.  I can't blame Zimbra for that.

---

