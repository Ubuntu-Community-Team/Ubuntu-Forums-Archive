---
title: "spamassassin is not working at all"
date: 2009-05-21
forum: Server Platforms
---

### Post by kustomjs on 2009-05-21
Hi Guys could anybody help me out with spamassassin with postfix because I tried to send my self a email to see if it would mark it as spam and its not.

---

### Post by llamaX on 2009-05-21
In general, you probably won't get mail coming from your own server marked as spam:

X-Spam-Checker-Version: SpamAssassin 3.2.5 (2008-06-10) on example.org
X-Spam-Level: 
X-Spam-Status: No, score=-0.8 required=5.0 tests=ALL_TRUSTED,DRUGS_ERECTILE
	autolearn=no version=3.2.5

The ALL_TRUSTED test checks for specifically for mail originating from your own server and trusted relays and tacks on -1.36 or so to the score tally.  Regardless...

Define "not working" in more detail, if you could.  Not running at all (check your headers), not marking spam appropriately, etc.?

---

### Post by kustomjs on 2009-05-21
well when I look at the headers on the webmail I dont see anything like that this what I see:

Return-Path: <kustomjs@gmail.com>
X-Original-To: [email]sales@kustomjs.com[/email]
Delivered-To: [email]sales@kustomjs.com[/email]
Received: from mail-gx0-f176.google.com (mail-gx0-f176.google.com [209.85.217.176])
    by mail.kustomjs.com (Postfix) with ESMTP id 95826F671F
    for <sales@kustomjs.com>; Thu, 21 May 2009 22:16:21 -0400 (EDT)
Received: by gxk24 with SMTP id 24so5761531gxk.10
for <sales@kustomjs.com>; Thu, 21 May 2009 19:16:22 -0700 (PDT)
DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/relaxed;
d=gmail.com; s=gamma;
h=domainkey-signature:mime-version:received:in-reply-to:references
:date:message-id:subject:from:to:content-type;
bh=J/mjKFd1mDyqtz9+n9euoNle4MFJwkqDeMOs6+aRhgU=
b=AfjNYHMjespbY3mfr3LROPmp2dKBJKATNdxWO5XaAqy32QmUdiXlKBAlaBFu2R64CX
4Ut7Z7UxmpWO10z6l9V/JAyS+lD5wRq9jp7n6F3km/2usbdROKEvX3pNyalWyOUTwOLy
dwjK/JWgfI/cCVxY6c5MZ2MOlAT5SXdakKhX8=
DomainKey-Signature: a=rsa-sha1; c=nofws;
d=gmail.com; s=gamma;
h=mime-version:in-reply-to:references:date:message-id:subject:from:to
:content-type;
b=dtqJevUIr8W1omvQ0Bb1bt9awt88pvmZdmoMLJOfrel9SGoxH+OUdq5q1sI5PvAwmC
Ydk8jPwpvszPOq0LJcx5tCNslD0SP3FMi4I5doII353pkqWrQH4zsUIhxUqHb6lH63M6
B/NHvhLpk9n9hXTak3utiT8ovLMPYSi4otbdI=
MIME-Version: 1.0
Received: by 10.90.88.16 with SMTP id l16mr2669242agb.112.1242958582621; Thu,
    21 May 2009 19:16:22 -0700 (PDT)
In-Reply-To: <4A160ACF.2020501@kustomjs.com>
References: <4A160ACF.2020501@kustomjs.com>
Date: Thu, 21 May 2009 22:16:22 -0400
Message-ID: <5b046ee30905211916qea1c923pa69a4e6d11577a13@mail.gmail.com>
Subject: Re: test
From: Tim Reichhart <kustomjs@gmail.com>
To: Tim <sales@kustomjs.com>
Content-Type: multipart/alternative; boundary=0016361648b3c9a635046a76d88d

so that means its not working.

---

### Post by llamaX on 2009-05-21
Have you enabled it in /etc/defaults/spamassassin?  Is spamd running (or are you running it another way)?  Is Postfix configured to use it in main.cf and master.cf?  Anything useful about it in your mail logs?

---

### Post by kustomjs on 2009-05-22
well where is the setup for the defaults:

```
# /etc/default/spamassassin
# Duncan Findlay

# WARNING: please read README.spamd before using.
# There may be security risks.

# Change to one to enable spamd
ENABLED=1

# Options
# See man spamd for possible options. The -d option is automatically added.

# SpamAssassin uses a preforking model, so be careful! You need to
# make sure --max-children is not set to anything higher than 5,
# unless you know what you're doing.

OPTIONS="--create-prefs --max-children 5 --helper-home-dir"

# Pid file
# Where should spamd write its PID to file? If you use the -u or
# --username option above, this needs to be writable by that user.
# Otherwise, the init script will not be able to shut spamd down.
PIDFILE="/var/run/spamd.pid"

# Set nice level of spamd
#NICE="--nicelevel 15"

# Cronjob
# Set to anything but 0 to enable the cron job to automatically update
# spamassassin's rules on a nightly basis
CRON=0
```


and what should I have in main and master.cf?

also I dont see anything about spamd on my mail logs either.

---

### Post by llamaX on 2009-05-22
Here are the relevant portions from my Postfix config, for reference.

main.cf:
```
smtpd_recipient_restrictions =
    reject_non_fqdn_recipient
    permit_mynetworks
    permit_sasl_authenticated
    reject_unauth_destination
    check_policy_service inet:127.0.0.1:60000
```

master.cf:
```
spamassassin unix -     n       n       -       -       pipe
  user=spamd argv=/usr/bin/spamc -f -e
  /usr/sbin/sendmail -oi -f ${sender} ${recipient}
```

---

### Post by kustomjs on 2009-05-22
alright I got to work but how do I get a header to say SPAM or something like that.

---

### Post by llamaX on 2009-05-22
/etc/spamassassin/local.cf:
rewrite_header Subject *****SPAM*****

Or the like.

---

### Post by kustomjs on 2009-05-22
alright its in there like you said it was now I think its roundcube problem.

---

