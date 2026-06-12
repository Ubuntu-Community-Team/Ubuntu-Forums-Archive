---
title: "postfix configuration ubuntu 12.04 - DKIM + BATV"
date: 2014-11-22
forum: Server Platforms
---

### Post by daniel219 on 2014-11-22
Hello,


I have configured Postfix mail server on ubunto 12.04, and some of my emails are still considered to be spam (AOL and yahoo).
I added the relevant key and value in the TXT DNS entry:


key: mail._domainkey.ebookstage.com
value: v=DKIM1; k=rsa; t=y; p=aaaaaaaaaaabeuhbfuehbfuehbfeuhbfuerfubblah.....


When I use [http://www.allaboutspam.com/](http://www.allaboutspam.com/) service I still get a warning on my DKIM configuration:


[COLOR=#ff0000]Email does not contain any DKIM/Domain Keys Signature and the published Domain Keys policy does not specify whether to accept or reject unsigned Emails. Signing your Outbound emails and clearly specifying a policy to accept signed emails will minimize chances of your Email being considered as SPAM.[/COLOR]


and also about the BATV:


[COLOR=#ff0000]Email server is not using BATV format while sending out emails. BATV is recommended to ensure that your users do not become a victim of bounce floods.[/COLOR]


Any idea what seems to be the problem?


Thanks,
Daniel.

---

### Post by g-parrondo on 2014-12-01
> **daniel219 said:**
> Hello,


I have configured Postfix mail server on ubunto 12.04, and some of my emails are still considered to be spam (AOL and yahoo).

First of all, you should be aware that adding dkim and batv alone won't get you into AOL and yahoo Inbox. DKIM will help a bit with yahoo. BATV is for your own benefit only, and won't matter to servers that receive mail from you.

Yahoo will rely heavily on your senderscore.org score. Both of them will play nicer if you join their Complaint Feedback Loop. If they banned your IP address (their smtps refusing to talk to you), you may also need to fill out a Bulk Sender Form.

Another great option is to configure postfix-policyd to rate-limit outgoing mail, and configure postfix's "smtpd_sender_login_maps". This will help prevent your users from sending large amounts of spam, which will lower your sender score and probably get you in a DNSRBL. Even if you trust your users, their accounts could get compromised and be used to send spam. Be prepared.

Having a good password policy and brute-force attack protection will also help.

> **daniel219 said:**
> 
I added the relevant key and value in the TXT DNS entry:


key: mail._domainkey.ebookstage.com
value: v=DKIM1; k=rsa; t=y; p=aaaaaaaaaaabeuhbfuehbfuehbfeuhbfuerfubblah.....


Are you using opendkim? What's your ```
/etc/opendkim.conf
```

A common mistake is to have a misconfigured selector. According to your TXT entry, your selector is "mail". Does your config reflect that?

Do you see any opendkim messages in your maillog?


> **daniel219 said:**
> 
When I use [http://www.allaboutspam.com/](http://www.allaboutspam.com/) service I still get a warning on my DKIM configuration:


[COLOR=#ff0000]Email does not contain any DKIM/Domain Keys Signature and the published Domain Keys policy does not specify whether to accept or reject unsigned Emails. Signing your Outbound emails and clearly specifying a policy to accept signed emails will minimize chances of your Email being consSidered as SPAM.[/COLOR]


allaboutspam.com is telling you exactly what the problem is: you have a TXT entry that indicates you have DKIM setup, yet your mail wasn't signed with the corresponding key. Further on, your TXT entry doesn't specify what the receiver should do with unsigned emails, see that t= flag?

Make sure opendkim is setup correctly, and make sure postfix uses it by correctly setting up opendkim's milter. Check [this guide]("https://help.ubuntu.com/community/Postfix/DKIM") for detailed steps.

> **daniel219 said:**
> 
and also about the BATV:


[COLOR=#ff0000]Email server is not using BATV format while sending out emails. BATV is recommended to ensure that your users do not become a victim of bounce floods.[/COLOR]


Any idea what seems to be the problem?


Thanks,
Daniel.

As I've said, BATV is only for your own convenience. It will stop backscatter spam on your users' inbox. Setting up batv on postfix may be very complex, depending on your specific setup.

Fix your dkim setup first, checkout spf if you haven't, implement greylisting to complement your spamfilter. Then, if you still get lots of backscatter spam, look into batv.

Hope some of the suggestions help you! Dealing with AOL and Yahoo is not easy. Yahoo is particularly uncooperative sometimes.

Good luck!

---

