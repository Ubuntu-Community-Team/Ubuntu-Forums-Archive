---
title: "Postfix rejects incoming mails"
date: 2012-02-15
forum: Server Platforms
---

### Post by satimis on 2012-02-15
Hi all,

On /etc/postfix/main.cf

I must comment out;```

#home_mailbox = Maildir/

```

then mails are delivered to;
/var/mail/userA/

However running;
# ls -al /var/mail/userA```

-rw------- 1 userA mail 9326 2012-02-15 13:14 /var/mail/userA

```

I can't find mails there.

I must run;
$ su - userA
$ mail

then I find the mails.

# ls /home/userA/```

Maildir  mbox

```

# ls -al /home/userA/Maildir```

-rw------- 1 userA userA 0 2012-02-13 15:57 /home/userA/Maildir

```

# ls -al /home/userA/mbox ```

-rw------- 1 userA userA 3612 2012-02-15 01:27 /home/userA/mbox

```

Pls advise why?  How to fix the problem?  TIA

B.R.
satimis

---

### Post by volkswagner on 2012-02-15
It appears you have something written to those locations.

Have you tried reading the actual file.

```
[CODE]cat /var/mail/userA
```[/CODE]

or

```
cat /home/userA/mbox
```


Have you checked your mail logs?

---

### Post by satimis on 2012-02-15
> **volkswagner said:**
> It appears you have something written to those locations.

Have you tried reading the actual file.

```
[CODE]cat /var/mail/userA
```[/CODE]

or

```
cat /home/userA/mbox
```


Have you checked your mail logs?

Hi,


/var/mail/userA
is not directory.  It is a large file.  All incoming mails for userA were added on it.


# tail -n 20 /var/mail/userA```

Subject: 20120215 test 01
To: "userA@mydomain.com" <userA@mydomain.com>
MIME-Version: 1.0
Content-Type: multipart/alternative; boundary="-983831124-1464846305-1329282796=:67070"
Status: O
X-UID: 3

---983831124-1464846305-1329282796=:67070
Content-Type: text/plain; charset=utf-8
Content-Transfer-Encoding: quoted-printable

=0A
---983831124-1464846305-1329282796=:67070
Content-Type: text/html; charset=utf-8
Content-Transfer-Encoding: quoted-printable

<html><body><div style=3D"color:#000; background-color:#fff; font-family:ar=
ial, helvetica, sans-serif;font-size:12pt"><div></div></div></body></html>
---983831124-1464846305-1329282796=:67070--

```


/home/userA/mbox is also a text file NOT a directory, all incoming mails being added on it.


# cat /home/userA/mbox ```

From root@localhost  Mon Feb 13 15:47:13 2012
Return-Path: <root@localhost>
X-Original-To: userA@localhost
Delivered-To: userA@localhost
Received: from localhost (localhost [127.0.0.1])
        by ser01.mydomain.com (Postfix) with ESMTP id AAE0A9FE4A
        for <userA@localhost>; Mon, 13 Feb 2012 15:45:54 +0800 (HKT)
Subject: My first mail on Postfix
Message-Id: <20120213074608.AAE0A9FE4A@ser01.mydomain.com>
Date: Mon, 13 Feb 2012 15:45:54 +0800 (HKT)
From: root@localhost
To: undisclosed-recipients:;

Hi,
Are you there?
regards,
Admin

From somebody@yahoo.com  Wed Feb 15 01:25:18 2012
Return-Path: <somebody@yahoo.com>
X-Original-To: userA@mydomain.com
Delivered-To: userA@mydomain.com
Received: from nm11.bullet.mail.sp2.yahoo.com (nm11.bullet.mail.sp2.yahoo.com [98.139.91.81])
        by ser01.mydomain.com (Postfix) with SMTP id 78B479FE7A
        for <userA@mydomain.com>; Wed, 15 Feb 2012 01:25:17 +0800 (HKT)
Received: from [98.139.91.63] by nm11.bullet.mail.sp2.yahoo.com with NNFMP; 14 Feb 2012 17:25:10 -0000
Received: from [98.139.91.49] by tm3.bullet.mail.sp2.yahoo.com with NNFMP; 14 Feb 2012 17:25:10 -0000
Received: from [127.0.0.1] by omp1049.mail.sp2.yahoo.com with NNFMP; 14 Feb 2012 17:25:10 -0000
X-Yahoo-Newman-Property: ymail-3
X-Yahoo-Newman-Id: 680324.84130.bm@omp1049.mail.sp2.yahoo.com
Received: (qmail 14302 invoked by uid 60001); 14 Feb 2012 17:25:10 -0000
DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/relaxed; d=yahoo.com; s=s1024; t=1329240309; bh=zLBTklpR453WlF2sXeiSlO+8vdFbVi9d0CEEJX7hONM=; h=X-YMail-OSG:Received:X-Mailer:Message-ID:Date:From:Reply-To:Subject:To:MIME-Version:Content-Type; b=f3HlBT0USuIYHPunqsJbPhYsQJAtPFDJ5HjQBGsCv6O6P7lqGYmhGtcpqHOe5x9es0Dh4AAwOmw9OT1/RCZTef+KA9DYMqrXJjOll/WK7gIf0kQEUGNyDl4LtTYl/Dha+zRZY7RSdxzPeePkioaukII5v5091adlsNtd+F032EM=
DomainKey-Signature: a=rsa-sha1; q=dns; c=nofws;
  s=s1024; d=yahoo.com;
  h=X-YMail-OSG:Received:X-Mailer:Message-ID:Date:From:Reply-To:Subject:To:MIME-Version:Content-Type;
  b=q6JtV0M0uL+pHduBfUy8xni+hGbTpttAhyZIYs5r0RKM2nsX9fdt2qskdxcQ54uDCdCXSngbd5A80WjrkoO0wRUI0RIs4PQKx7pSDWc9v3fcDeSc6zEqHM0ueYg3UsuPAwQoo686DnqWSJoIl5tOoDIJBU/k4RMnkOwr0Weil68=;
X-YMail-OSG: TBV2ej4VM1mUf6wpmjAYFb15489I8LMiOA1UJEMLpkhKITm
 dYX7ftUWc1BikRaxOK0QnpOG5yF.0Cx177cXICS6oHB6w2hl.mnhaI1IH039
 dHgQET7pRMGqZsf0G1j0uTf.djvqmG71y3Q8HGDHj.F9P2IkGpTXSQdylDM0
 WvoylOXIJFwCmhAaQYUjK7PzA4juTqw5IDe7nPsNPpaSWb_hbsBklEkxr5b2
 2g3qSGeCFfSllTJ5shBvSHzVH7fer0GGkfg8BdzZl2jGRrHZ5oUjSRNKuQHS
 hY0OkkVAjcJ55Z9ncQZnjghNb6K1VYxvu6HFlm3a9in8dLispjI4vJGVcT.x
 7jVr9vPn8evcNiivrH.u0U7tjI5eqmMHVyCpwjGQzEfh0Iejbt5IYjX.0XKO
 ETi7h8nprILri8kN0U6h5gN5zQeVl01nIpzlPdUzpppGrQVUfTtNP
Received: from [220.232.213.178] by web113215.mail.gq1.yahoo.com via HTTP; Tue, 14 Feb 2012 09:25:09 PST
X-Mailer: YahooMailWebService/0.8.116.338427
Message-ID: <1329240309.90525.YahooMailNeo@web113215.mail.gq1.yahoo.com>
Date: Tue, 14 Feb 2012 09:25:09 -0800 (PST)
From: Stephen Liu <somebody@yahoo.com>
Reply-To: Stephen Liu <somebody@yahoo.com>
Subject: test
To: "userA@mydomain.com" <userA@mydomain.com>
MIME-Version: 1.0
Content-Type: multipart/alternative; boundary="1783984244-1535174265-1329240309=:90525"

--1783984244-1535174265-1329240309=:90525
Content-Type: text/plain; charset=utf-8
Content-Transfer-Encoding: quoted-printable

=0A
--1783984244-1535174265-1329240309=:90525
Content-Type: text/html; charset=utf-8
Content-Transfer-Encoding: quoted-printable

<html><body><div style=3D"color:#000; background-color:#fff; font-family:ar=
ial, helvetica, sans-serif;font-size:12pt"><div></div></div></body></html>
--1783984244-1535174265-1329240309=:90525--

mydomain@ser01:~$ 
0*$ shell                                  somebody@ser 192.168.0.200 Menu:<F9>
 U  Ubuntu 11.04               3! 26m 0.08 4x3.2GHz 7.6GB,18% 2012-02-15 18:09:16

```

Tried again after uncommenting the line```

home_mailbox = Maildir/

```

$ tail /var/log/mail.log ```

Feb 15 18:49:52 ser01 postfix/cleanup[2253]: 649429FE7A: message-id=<1329302925.48207.YahooMailNeo@web113212.mail.gq1.yahoo.com>
Feb 15 18:49:52 ser01 postfix/qmgr[2243]: 649429FE7A: from=<somebody@yahoo.com>, size=2985, nrcpt=1 (queue active)
Feb 15 18:49:52 ser01 postfix/local[2254]: 649429FE7A: to=<userA@mydomain.com>, relay=local, delay=0.77, delays=0.74/0/0/0.02, dsn=5.2.0, status=bounced (maildir delivery failed: create maildir file /home/userA/Maildir/tmp/1329302992.P2254.ser01.mydomain.com: Not a directory)
Feb 15 18:49:52 ser01 postfix/cleanup[2253]: F2AB89FE7C: message-id=<20120215104952.F2AB89FE7C@ser01.mydomain.com>
Feb 15 18:49:52 ser01 postfix/bounce[2255]: 649429FE7A: sender non-delivery notification: F2AB89FE7C
Feb 15 18:49:52 ser01 postfix/qmgr[2243]: F2AB89FE7C: from=<>, size=5041, nrcpt=1 (queue active)
Feb 15 18:49:52 ser01 postfix/qmgr[2243]: 649429FE7A: removed
Feb 15 18:49:53 ser01 postfix/smtpd[2247]: disconnect from nm4-vm0.bullet.mail.sp2.yahoo.com[98.139.91.190]
Feb 15 18:49:57 ser01 postfix/smtp[2256]: F2AB89FE7C: to=<somebody@yahoo.com>, relay=mta5.am0.yahoodns.net[66.94.236.34]:25, delay=4.1, delays=0/0.01/1.6/2.5, dsn=2.0.0, status=sent (250 ok dirdel)
Feb 15 18:49:57 ser01 postfix/qmgr[2243]: F2AB89FE7C: removed

```


hostname = ser01.mydomain.com
local IP of server 192.168.0.218 running on a VM of Oracle VirtualBox
On router all ports 25/45/80/110/8080 etc. are pointing to this local IP

On configuring postfix```

System Mail Name = mydomain.com

```

$ cat /etc/postfix/main.cf | grep mydestination```

mydestination = mail.mydomain.com, localhost.localdomain, localhost, mydomain.com
```


Having googled "status=bounced (maildir delivery failed: create maildir file /home/userA/Maildir)" a while without a solution to my problem.

BR
satimis

---

### Post by satimis on 2012-02-16
Hi folks,

host - Ubuntu 1104 desktop 64bit
VM - Ubuntu 1004 server 64bit
Orcle VirtualBox
(this VM was cloned on another VM, a base and newly installed Ubuntu 1004 server without postfix/apache/server software, etc. installed)
Fixed IP


I did following test twice by following;
Postfix Basic Setup Howto
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

entercountering the same problem, postfix unable to receive mails.  


The problem started at:-

fmaster@ser01:~$ cd Maildir/new```

-su: cd: Maildir/new: Not a directory

```

satimis@ser01:~$ tail /var/log/mail.log ```

Feb 16 18:39:43 ser01 postfix/cleanup[2196]: 012A59FE48: message-id=<20120216103943.012A59FE48@ser01.mydomain.com>
Feb 16 18:39:43 ser01 postfix/bounce[2199]: EF49D9FE45: sender non-delivery notification: 012A59FE48
Feb 16 18:39:43 ser01 postfix/qmgr[2189]: 012A59FE48: from=<>, size=2330, nrcpt=1 (queue active)
Feb 16 18:39:43 ser01 postfix/qmgr[2189]: EF49D9FE45: removed
Feb 16 18:39:43 ser01 postfix/local[2198]: 012A59FE48: to=<root@mydomain.com>, relay=local, delay=0.01, delays=0/0/0/0, dsn=2.0.0, status=sent (delivered to maildir)
Feb 16 18:39:43 ser01 postfix/qmgr[2189]: 012A59FE48: removed
Feb 16 18:39:46 ser01 postfix/smtpd[2191]: disconnect from unknown[xxx.xxx.xxx.xxx] (fixed IP)
Feb 16 18:43:06 ser01 postfix/anvil[2194]: statistics: max connection rate 1/60s for ([smtp:xxx.xxx.xxx.xxx] (fixed IP)) at Feb 16 18:37:41
Feb 16 18:43:06 ser01 postfix/anvil[2194]: statistics: max connection count 1 for ([smtp:xxx.xxx.xxx.xxx] (fixed IP)) at Feb 16 18:37:41
Feb 16 18:43:06 ser01 postfix/anvil[2194]: statistics: max cache size 1 at Feb 16 18:37:41

```

fmaster@ser01:~$ ls```

Maildir

```

fmaster@ser01:~$ cat Maildir 
No printout

fmaster@ser01:~$ ls -al Maildir ```

-rw------- 1 fmaster fmaster 0 2012-02-16 18:31 Maildir

```

satimis@ser01:~$ tail /var/log/mail.log```

Feb 16 18:50:21 ser01 postfix/cleanup[2363]: D5A6A9FE45: message-id=<1329389418.67830.YahooMailNeo@web113210.mail.gq1.yahoo.com>
Feb 16 18:50:21 ser01 postfix/qmgr[2189]: D5A6A9FE45: from=<somebody@yahoo.com>, size=2991, nrcpt=1 (queue active)
Feb 16 18:50:21 ser01 postfix/local[2364]: D5A6A9FE45: to=<fmaster@mydomain.com>, relay=local, delay=0.8, delays=0.79/0/0/0.01, dsn=5.2.0, status=bounced (maildir delivery failed: create maildir file /home/fmaster/Maildir/tmp/1329389421.P2364.ser01.mydomain.com: Not a directory)
Feb 16 18:50:21 ser01 postfix/cleanup[2363]: 756319FE48: message-id=<20120216105021.756319FE48@ser01.mydomain.com>
Feb 16 18:50:21 ser01 postfix/bounce[2365]: D5A6A9FE45: sender non-delivery notification: 756319FE48
Feb 16 18:50:21 ser01 postfix/qmgr[2189]: 756319FE48: from=<>, size=5059, nrcpt=1 (queue active)
Feb 16 18:50:21 ser01 postfix/qmgr[2189]: D5A6A9FE45: removed
Feb 16 18:50:21 ser01 postfix/smtpd[2358]: disconnect from nm25-vm0.bullet.mail.sp2.yahoo.com[98.139.91.228]
Feb 16 18:50:25 ser01 postfix/smtp[2366]: 756319FE48: to=<somebody@yahoo.com>, relay=mta7.am0.yahoodns.net[66.94.238.147]:25, delay=3.8, delays=0/0/1.7/2.1, dsn=2.0.0, status=sent (250 ok dirdel)
Feb 16 18:50:25 ser01 postfix/qmgr[2189]: 756319FE48: removed

```

satimis@ser01:~$ cat /etc/postfix/main.cf | grep home_mailbox```

home_mailbox = Maildir/

```

dig mx mydomain.com
nslookup mydomain.com
worked without problem showing mydomain.com and fixed IP

Mails came but unable to create a mailbox.


Then I made another test also following the same document.  I installed the server on another VM, running Debian 600 desktop(64 bit) which was also cloned on another Debian 600 desktop VM.  No problem was found.  The document (Howto) works perfectly on Debian 600.  Mails were received by postfix.

Please help me to understand the problem.  I have injected hours of work on this test.  TIA

B.R.
satimis

---

### Post by volkswagner on 2012-02-16
I don't understand.  you state Postfix rejects mail yet you say the mail file gets appended with all mail messages.  Is the issue just mail is not placed in individual files as you would like?  Are any messages returned to sender and not appended to the mail file?

---

### Post by uRock on 2012-02-16
Duplicate threads merged. Please do not create multiple threads for the same issue.

---

### Post by satimis on 2012-02-16
> **volkswagner said:**
> I don't understand.  you state Postfix rejects mail yet you say the mail file gets appended with all mail messages.  Is the issue just mail is not placed in individual files as you would like?  Are any messages returned to sender and not appended to the mail file?
Hi,

All mails were rejected.

If commenting out;```

home_mailbox = Maildir/

```
on /etc/postfix/main.cf. all incoming mails were delivered on Maildir or new as file.

What I don't understand is why there is no such problem on Debian?  I built 4 servers on VMs on the same box, 3 running Ubuntu 1004 and one running Deb 600 respectively.  All Ubuntu server have the same problem Postfix rejecting incoming mails.  I just discovered this problem lately after installing Postfix on Debian 60.

B.R.
satimis

---

