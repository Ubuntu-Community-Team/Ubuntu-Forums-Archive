---
title: "Issues with new roundcube install on 14.04"
date: 2014-11-25
forum: Server Platforms
---

### Post by DigiAngel on 2014-11-25
Hey all,

So...I put up a new server that has postfix/dovecot/roundcube.  I'm sometimes seeing a "Server Error: Mailbox read-only"..below is what I see in apache's log:

[Tue Nov 25 11:19:09.050735 2014] [:error] [pid 13675] [client 192.168.1.1:37966] PHP Warning:  fclose() expects parameter 1 to be resource, boolean given in /usr/share/roundcube/program/steps/mail/get.inc on line 74, referer: [http://127.0.0.1/roundcube/?_task=mail&_action=preview&_uid=96&_mbox=INBOX&_framed=1&_search=4d4fb0e0e6ceb1d0489daee4e7794125&_caps=pdf%3D0%2Cflash%3D1%2Ctif%3D0](http://127.0.0.1/roundcube/?_task=mail&_action=preview&_uid=96&_mbox=INBOX&_framed=1&_search=4d4fb0e0e6ceb1d0489daee4e7794125&_caps=pdf%3D0%2Cflash%3D1%2Ctif%3D0)

[Tue Nov 25 11:19:09.050949 2014] [:error] [pid 13675] [client 192.168.1.1:37966] PHP Warning:  rename(/e8a832bc2973b6badaf6a5a6683e2d65.orig.jpeg,/e8a832bc2973b6badaf6a5a6683e2d65.jpeg): No such file or directory in /usr/share/roundcube/program/steps/mail/get.inc on line 82, referer: [http://127.0.0.1/roundcube/?_task=mail&_action=preview&_uid=96&_mbox=INBOX&_framed=1&_search=4d4fb0e0e6ceb1d0489daee4e7794125&_caps=pdf%3D0%2Cflash%3D1%2Ctif%3D0](http://127.0.0.1/roundcube/?_task=mail&_action=preview&_uid=96&_mbox=INBOX&_framed=1&_search=4d4fb0e0e6ceb1d0489daee4e7794125&_caps=pdf%3D0%2Cflash%3D1%2Ctif%3D0)

Any hints on what to look for here?  Thank you.

---

### Post by DigiAngel on 2014-11-25
So following this:
[https://help.ubuntu.com/community/Roundcube]("https://help.ubuntu.com/community/Roundcube")

is apparently not what works now with 14.  This: [https://www.exratione.com/2013/07/installing-roundcube-on-ubuntu-1204/]("https://www.exratione.com/2013/07/installing-roundcube-on-ubuntu-1204/") got rid of the above errors.  I still have two issues...messages marked as deleted still show up in the message list, and some inline images show up, and others do not.  I can live with it, but I did not see these issues with 12.

---

### Post by DigiAngel on 2014-11-27
And even more info:

Nov 27 04:30:12 bleh dovecot: pop3(bleh): Error: file_dotlock_create(/var/mail/bleh) failed: Permission denied (euid=1002(bleh) egid=1002(bleh) missing +w perm: /var/mail, we're not in group 8(mail), dir owned by 0:8 mode=0775) (set mail_privileged_group=mail)

None of the ubuntu docs even mention this.....set the setting above as it says and no more error.

---

### Post by DigiAngel on 2014-11-28
My last issue is inline images...does ANYONE use roundcuve on this list that has info on this?  Thank you.

---

### Post by nerdtron on 2014-11-28
Hello:
I have setup this before: [http://iredmail.org/](http://iredmail.org/)
Complete email server with Roundcube and it really install all its components in an automated way.
Can be done within 30 minutes. Test it on a FRESH install of 14.04: [http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html](http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html)

---

### Post by DigiAngel on 2014-11-28
Thanks for the advice...I even tried from source with the latest stable version...same thing.  Suspect this is a 14.0.4 issue.

---

### Post by DigiAngel on 2014-11-29
So I have a DVR...fairly certain it's not RFC compliant when it sends snapshots.  That being said, Roundcube on Ubuntu 12 displayed these images inline just fine.  But this new version, 0.9.5 does not.  Here's a header:

```
Return-Path: <>
X-Original-To: me@domain.net
Delivered-To: me@domain.net
Received: by mail.domain.net (Postfix, from userid 1001)
	id 7EA202C09D0; Thu, 27 Nov 2014 06:57:28 -0700 (MST)
X-Spam-Checker-Version: SpamAssassin 3.4.0 (2014-02-07) on
	gateway.domain.net
X-Spam-Level: **
X-Spam-Status: No, score=2.4 required=5.0 tests=ALL_TRUSTED,
	BASE64_LENGTH_79_INF,DATE_IN_PAST_12_24,INVALID_DATE,MISSING_MID autolearn=no
	autolearn_force=no version=3.4.0
Received: from localhost (qc444 [192.168.1.221])
	by mail.domain.net (Postfix) with SMTP id 0CB1B2C09CE;
	Thu, 27 Nov 2014 06:57:28 -0700 (MST)
From: me@domain.net
To: me@domain.net
Date: Thu, 27 Nov 14 06:54:15 +0800
Subject: =?utf-8?B?RFZSIEFMRVJU?=
MIME-Version: 1.0
Content-type: multipart/mixed; boundary=*****MAIL_BOUNDARY*****
Message-Id: <20141127135728.7EA202C09D0@mail.domain.net>

--*****MAIL_BOUNDARY*****
Content-Type: text/plain;charset=utf-8
Content-Transfer-Encoding: 8bit

Alarm event: Motion Detect 
Alarm input channel No.: 2  
Alarm device name: DVR
Sender IP address: 192.168.1.221

--*****MAIL_BOUNDARY*****
Content-Type: image/jpeg; name=ch02_20141127_065413_E.jpg
Content-Disposition: inline;
Content-Transfer-Encoding: base64

/9j/4AAQSkZJRgABAQAAAQABAAD/2<redacted>
```


I currently get a line with:
```
~71  KB  Show  Download
```


If I click download I get a zero byte file, if I click show I see:
```
WARNING! This attachment is suspicious because its type doesn't match the type declared in the message. If you do not trust the sender, you shouldn't open it in the browser because it may contain malicious contents.

Expected: image/jpeg(.jpg); found: application/x-empty
```


Things I've tried changing...pointing to mime.types and mime.magic...installed ImageMagick and pointed to convert and identify...no luck so far:

$rcmail_config['mime_magic'] = null;
installing ImageMagick

The odd thing is, is that some messages show just fine from the same host and same header info.  They all show up fine in Evolution.  Thank you.

---

### Post by DigiAngel on 2014-11-29
And even MORE information.  I've tried roundcube 1.0.3 and 1.1-beta as well....all including the installed 0.9.5 exhibit the same behaviour.  I've narrowed this down to an issue with not properly getting or writing files...the /temp directory is where I see this:

```
total 20
-rw------- 1 www-data www-data 8328 Nov 29 08:33 1b9255b29216c5d7a355c60c9064c238.jpeg
-rw------- 1 www-data www-data 6988 Nov 29 08:33 25abc5ad6a2d485b10f9c44c0f89a79b.jpeg
-rw-r--r-- 1 www-data www-data    0 Nov 29 08:33 331b6adcb1e01e404676249f50479fbb.jpeg

```

The file that is 0 bytes is the one that won't show...the other two display fine.

---

### Post by DigiAngel on 2014-11-30
FYI...I've opened a bug with roundcube at [http://trac.roundcube.net/ticket/1490171]("http://trac.roundcube.net/ticket/1490171").  After downloading and installing roundcube-0.7.1, the version that came with Ubuntu Server 12, this issue doesn't appear...all images show up fine as thumbnails.  For the time being I'll just be using the old verions.

---

