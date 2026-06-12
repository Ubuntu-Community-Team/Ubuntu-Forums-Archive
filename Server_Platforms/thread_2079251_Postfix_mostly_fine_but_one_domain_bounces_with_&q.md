---
title: "Postfix mostly fine but one domain bounces with &quot;550 Please Authenticate&quot;"
date: 2012-11-01
forum: Server Platforms
---

### Post by nickfromvan on 2012-11-01
I've set up email on an Ubuntu server for a client which has been running fine for close to 3 months but they just discovered a few days ago that a particular email address keeps bouncing their email.

From mail.log:
```
Oct 26 14:59:14 vps postfix/smtp[3591]: 899EA56005D: to=<billing@xyz.com>, relay=mail.xyz.com[XXX.XXX.XXX.XXX]:25, delay=0.54, delays=0.01/0/0.46/0.07, dsn=5.0.0, status=bounced (host mail.xyz.com[XXX.XXX.XXX.XXX] said: 550 If you really are 'abc.com' please authenticate first (in reply to MAIL FROM command))
```I asked the client to send me an email from the account she was sending from so that I could inspect the headers in detail and this is what I've got:
```
Delivered-To: someuser@somedomain.tld
Received: by XXX.XXX.XXX.XXX with SMTP id ce10csp636401ieb;
        Wed, 31 Oct 2012 17:28:55 -0700 (PDT)
Received: by XXX.XXX.XXX.XXX with SMTP id qs2mr51908742pbc.139.1351729734557;
        Wed, 31 Oct 2012 17:28:54 -0700 (PDT)
Return-Path: <webmaster@abc.com>
Received: from abc.com (abc.com. [XXX.XXX.XXX.XXX])
        by mx.google.com with ESMTP id h9si6776430pax.300.2012.10.31.17.28.54;
        Wed, 31 Oct 2012 17:28:54 -0700 (PDT)
Received-SPF: pass (google.com: best guess record for domain of webmaster@abc.com designates XXX.XXX.XXX.XXX as permitted sender) client-ip=XXX.XXX.XXX.XXX;
Authentication-Results: mx.google.com; spf=pass (google.com: best guess record for domain of webmaster@abc.com designates XXX.XXX.XXX.XXX as permitted sender) smtp.mail=webmaster@abc.com
Received: from localhost (localhost [127.0.0.1])
    by abc.com (Postfix) with ESMTP id 98BDB560082;
    Wed, 31 Oct 2012 17:28:53 -0700 (PDT)
X-Virus-Scanned: Debian amavisd-new at abc.com
Received: from abc.com ([127.0.0.1])
    by localhost (mail.abc.com [127.0.0.1]) (amavisd-new, port 10024)
    with ESMTP id 5wrmuecGSRPp; Wed, 31 Oct 2012 17:28:33 -0700 (PDT)
Received: from optra04 (randomstring.bigisp.tld [XXX.XXX.XXX.XXX])
    (using TLSv1 with cipher RC4-MD5 (128/128 bits))
    (No client certificate requested)
    (Authenticated sender: webmaster@abc.com)
    by abc.com (Postfix) with ESMTPSA id 19A95560081;
    Wed, 31 Oct 2012 17:28:33 -0700 (PDT)
From: "Webmaster" <webmaster@abc.com>
```Nothing here really jumps out at me.  I will probably ask them to try to send directly through the server's SMTP server (via webmail) rather than going through their ISP just to see if this is somehow fouling things up.  I went to [mxtoolbox.com]("http://www.mxtoolbox.com") and ran their SMTP diagnostics (all checkmarks), reverse DNS (check), and even to see if they had managed to get blacklisted (nope) just to see if there were any other issues this could be related to but everything looks fine.  I've searched high and low on Google with no luck.

One other note which may/may not be a mitigating factor, the email domain being sent from was previously hosted by email domain being sent to.  DNS/MX records were transferred 3+ months ago, but is there any way that xyz.com still "thinks" it's hosting abc.com?

Please let me know if you require any additional information and I thank  you in advance for any help or insight you may be able to offer!

---

