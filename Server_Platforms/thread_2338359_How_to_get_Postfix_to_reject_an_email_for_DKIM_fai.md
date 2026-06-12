---
title: "How to get Postfix to reject an email for DKIM failure"
date: 2016-09-27
forum: Server Platforms
---

### Post by Robert_Boutin on 2016-09-27
I notice when viewing email header information that this specific DKIM failure:

dkim=fail (1024-bit key) reason="fail (body has been altered)"

is always associated with spam or other bulk email that I simply don't want.

I would like my server to flatly reject emails with this failure.  The people who know me and send me email normally use their corporate email account, gmail, or other provider that would typically have properly configured DKIM, so at least in my individual case, the risk of rejecting ham is low.

My server is recognizing this failure, but how do I reject for it?  Is this something I would configure in postfix/main.cf?

Thanks!!

---

### Post by SeijiSensei on 2016-09-27
Show us the headers from a message that was marked with this failure.  You might be able to install **procmail** and add a rule to /etc/procmailrc that will send all such messages to a specific folder or even /dev/null.

This won't reject at the SMTP level, but at the delivery level.

---

### Post by Robert_Boutin on 2016-09-27
Thanks, here is one:

Return-Path: <bounce-fjrjk4k3gf8g8@nationalinsuranceacademy.com>
Delivered-To: [EMAIL="rboutin@mydomain.com"]rboutin@mydomain.com[/EMAIL]
Received: from localhost (localhost [127.0.0.1])
        by mail.mydomain.com (Postfix) with ESMTP id A5D87521AB2
        for <rboutin@mydomain.com>; Mon, 26 Sep 2016 17:25:08 -0400 (EDT)
X-Virus-Scanned: Debian amavisd-new at 
X-Spam-Flag: YES
X-Spam-Score: 3.018
X-Spam-Level: ***
X-Spam-Status: Yes, score=3.018 tagged_above=1 required=2
        tests=[DATE_IN_PAST_96_XX=2.07, DKIM_SIGNED=0.1, DKIM_VALID=-0.1,
        DKIM_VALID_AU=-0.1, HTML_IMAGE_ONLY_16=1.048, HTML_MESSAGE=0.001,
        SPF_PASS=-0.001] autolearn=no autolearn_force=no
Authentication-Results: mail.mydomain.com (amavisd-new);
        dkim=pass (1024-bit key) header.d=nationalinsuranceacademy.com;
        [B]domainkeys=fail (1024-bit key)
        reason="fail (message has been altered)"[/B]
        header.from=info@nationalinsuranceacademy.com
        header.d=nationalinsuranceacademy.com
Received: from mail.mydomain.com ([127.0.0.1])
        by localhost (mail.mydomain.com [127.0.0.1]) (amavisd-new, port 10024)
        with ESMTP id pFXynt0DZtid for <rboutin@mydomain.com>;
        Mon, 26 Sep 2016 17:24:51 -0400 (EDT)
Received-SPF: Pass (sender SPF authorized) identity=mailfrom; client-ip=213.238.179.114; helo=ih1aq.tristateweb.com; envelope-from=bounce-fjrjk4k3gf8g8@nationalinsuranceacademy.com; receiver=rboutin@mydomain.com 
Received: from ih1aq.tristateweb.com (ih1aq.tristateweb.com [213.238.179.114])
        by mail.mydomain.com (Postfix) with ESMTP id 6D717521A9E
        for <rboutin@mydomain.com>; Mon, 26 Sep 2016 17:24:30 -0400 (EDT)
DKIM-Signature: v=1; a=rsa-sha1; c=relaxed/relaxed; s=dkim; d=nationalinsuranceacademy.com;
 h=To:Subject:Message-ID:Date:From:Reply-To:MIME-Version:List-Unsubscribe:Content-Type:Content-Transfer-Encoding; i=info@nationalinsuranceacademy.com;
 bh=Pv6EzP3Q1iU37ryIdB6et9dy6wU=;
 b=LXq00ULMj7McyvgETPrnqzqo8N1FnYRV9sJUsndwLc0FEM7ioIi90LyG3X2M8FLCnhFSKTgFKHbz
   xU+gdEbiWJZ8b/MmIMA1DGS8RmXb1bN+lQIb4Alq6hfu4omsfRBVHAT8pN0ohXU3X208dkk+DVRv
   nawZntS3TK88hVjVLyI=
DomainKey-Signature: a=rsa-sha1; c=nofws; q=dns; s=dkim; d=nationalinsuranceacademy.com;
 b=lVmkJWOPcGuRe0ZAw+Vah0HwCfStvMva0sjgvDDIW0HXLACg4hFZ4M1nyNAzl6pou5VqZ1cpSbtV
   lQch02i0oKMNChXsdUCULb9eE8cliO09BPBQbHR7B5+eePL6ubIWS+s+Yqnw3mUAMk39BeRKfLYy
   w/ISYDx0U81a8bSdLe4=;

---

### Post by SeijiSensei on 2016-09-28
OK, so you can write a procmail "recipe" like this:
```

:0
* X-Spam-Status:.*domainkeys=fail
/path/to/some/file

```
This rule would add matching messages to "/path/to/some/file" on mail servers that use mbox format.  (You'll have to read the documentation if you use Maildir; I never have.)  That lets you review the folder of messages in case something was erroneously tagged.  If you don't care about that, then you can use "/dev/null" as the destination and send the message to a black hole.

Each rule starts with ":0" followed by a line which includes a regular expression for matching.  The "*" means to scan the entire header; there are also ways to scan the body.  Notice that the matching expression starts with the header's name, in this case X-Spam-Status.

Procmail is a very powerful tool with a wide variety of options that are documented in "[man procmailrc]("https://linux.die.net/man/5/procmailrc")".  I'd skim that for the basics then take a look at the examples shown in "[man procmailex]("https://linux.die.net/man/5/procmailex")".

Personally I can't imagine managing a mail server without procmail installed.

---

### Post by Robert_Boutin on 2016-09-28
Thanks a LOT!  I'll try this out this evening.  I don't know what I'd do without the help all of you provide.

---

### Post by Robert_Boutin on 2016-09-30
I'm an idiot.  I was researching how to use procmail and came across some chatter about ISPConfig's content filtering.  ISPConfig was already installed and seems to do exactly what I wanted, along the lines of your procmail example (maybe it even uses procmail, idk).  I created the header checks in the global content filter.  I haven't received emails for a couple days with these specific failures:

dkim=fail (1024-bit key) reason="fail (body has been altered)"
domainkeys=fail (1024-bit key)
reason="fail (message has been altered)"

I'll give it another week, that should be enough time to know for sure that it's working.

---

